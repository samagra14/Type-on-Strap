---
layout: post
title: Intelligent Planning                                # Title of the page
subtitle: "The algorithm for a better plan"                    # A subtitle can be displayed below your title
tags: [gsoc,aimacode,artificial intelligence]
---
The coding period has begun. Well, not officially but I have started to do my work. Mainly because I just cannot wait for this awesome phase to begin with.
<!--more-->

So the first task on my plate is to program intelligent planning algorithms. I started out with laying out a structure for the Action Schema. It is a PDDL representation of the actions that can be taken in a particular state by an agent. PDDL stands for Planning Domain Definition Language. An action schema is a lifted representation of actions. For example here is an action schema for flying a plane from one location to another:

Action( Fly(p,from,to),<br>
&nbsp;&nbsp;&nbsp;&nbsp;PRECOND: At(p,from) $$ \land $$ Plane(p) $$ \land $$ Airport(from) $$ \land $$ Airport(to),<br>
  &nbsp;&nbsp;&nbsp;&nbsp;EFFECT: $$ \neg  $$ At(p,from) $$ \land $$ At(p,to))

The schema consists of an action name, a list of all the variables used in the schema, a precondition and an effect. Hence I came up with the following items to represent an action:
````java
private String name;
List<Term> variables;
List<AtomicSentence> precondition; //treated as a conjunction of fluents
List<AtomicSentence> effects;//treated as a conjunction of fluents
List<AtomicSentence> effectsPositiveLiterals;
List<AtomicSentence> effectsNegativeLiterals;
````
The `AtomicSentence` interface was already present in the first order logic implementations. The terms in an action schema can include both constants as well as variables.

The action object is simply an ActionSchema in which all the Terms are constants.

Now we need to define a state for PDDL. Each state is represented as a conjunction of fluents that are ground functionless atoms. So state is simply a list of AtomicSentances which are assumed to be in the conjunctive form.
````java
public class State {
    List<AtomicSentence> fluents;
}
````

The result of executing an Action `a` in state `s` is defined as a state `s'` which is represented by the set of fluents, formed by starting with `s`, removing the fluents that appear as negative literals in the action's effects and adding the fluents that are positive literals in the action's effects.  
````java
State result(State s, ActionSchema a){
        s.fluents.removeAll(a.getEffectsNegativeLiterals());
        s.fluents.addAll(a.getEffectsPositiveLiterals());
        return s;
    }
````
Finally, we have to define the structure for a specific problem. A problem consists of an initial state, a set of `ActionSchemas` and a goal. The initial state consists of ground atoms (atomic sentences without variables). The goal is just like a precondition: a conjunction of literals.

````java
public class Problem {
    State initialState;
    Set<ActionSchema> actionSchemas;
    State goalState;
}
````
I will open a PR for these changes right away with a WIP label as I have to prepare for my practical exam tomorrow. My next job will be to add some syntactic sugar to these PDDL data types and connect them to the FOLParser.
