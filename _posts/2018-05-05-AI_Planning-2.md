---
layout: post
title: Intelligent Planning-2                              # Title of the page
subtitle: "The algorithm for a better plan"                    # A subtitle can be displayed below your title
tags: [gsoc,aimacode,artificial intelligence]
---

Finally, my exams are over and I can devote my full time to AIMA. In the previous post, I had begun to work on Intelligent Planning Algorithms. In this post I will continue my work on the same.
<!--more-->

In the last blog I programmed states and Action schemas as collection of atomic sentences. Well, I will now change them to Literals so as to provide a better functionality. The next job is to check that whether a given action `a` is applicable in a given state `s`. We say that 'a' is applicable in 's' if the preconditions are satisfied by s. Since both the preconditions and state is a list of literals, therefore we check if the state list contains the literals present in the preconditions.

````java
boolean isApplicable(State s, ActionSchema a){
        return s.getFluents().containsAll(a.getPrecondition());
    }
````
Now let's create a small function to parse the preconditions and effects so that representing them becomes easier. Now each such statement can be defined as a conjunction of literals. Therefore to isolate each literal, we first tokenise a given string about the '^' symbol and after that we will get a list of literals. These literals can then be further tokenised around `(` ,`)` and `,` symbols to get the literal name and the terms associated with the literals. Finally we return a list of literals. So here is the method to parse a given string to give fol like implementation.
````java
public static List<Literal> parse(String s){
        s = s.replaceAll("\\s+","");
        String[] tokens = s.split("\\^");
        Literal literal;
        ArrayList<Literal> literals = new ArrayList<>();
        for (String token :
                tokens) {
            String[] terms = token.split("[(,)]");
            ArrayList<Term> literalTerms= new ArrayList<>();
            Term term;
            String termString;
            Boolean negated = false;
            for (int i = 1; i <terms.length ; i++) {
                termString= terms[i];
                if(termString.equals(termString.toLowerCase())){
                   term  = new Variable(termString);
                }
                else{
                    term = new Constant(termString);
                }
                literalTerms.add(term);
            }

            String name = terms[0];
            if(name.charAt(0)=='~'){
                negated = true;
                name = name.substring(1);
            }
            literal = new Literal(new Predicate(name,literalTerms),negated);
            literals.add(literal);
        }
        return literals;
    }
````
Now let's write some tests for our parser :
````java
public void parserTest() {
        String precondition = "At(C1,JFK) ^ At(C2,SFO)";
        ArrayList<Literal> literals = (ArrayList<Literal>) Utils.parse(precondition);
        for (Literal literal :
                literals) {
            System.out.println(literal.toString());
        }
    }
````
