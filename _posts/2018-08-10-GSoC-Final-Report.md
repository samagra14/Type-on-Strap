---
layout: post
title: Google Summer of Code Final Report                                # Title of the page
subtitle: "My experiments with code"                    # A subtitle can be displayed below your title
feature-img: "assets/img/pexels/book-glass.jpeg"              # Add a feature-image to the post
thumbnail: "assets/img/pexels/book-glass.jpeg"   # Add a thumbnail image on blog view
tags: [Artificial Intelligence,aimacode,gsoc]
---

This is the final report for the work done during GSoC 2018. For a detailed view on my experience during GSoC see this post.

### The Project
AIMA-Java project is a java implementation of algorithms from [Russell](http://www.cs.berkeley.edu/~russell/) and [Norvig's](http://www.norvig.com/) [Artificial Intelligence - A Modern Approach](http://aima.cs.berkeley.edu/).

My responsibilities within this project included the design and further implementation of the algorithms from the third and fourth editions of this book. I was responsible for testing the new code as well as writing tests for the older versions. At times, the work also involved significant digging into the literature to implement some necessary function which was abstracted from the books for the sake of simplicity.

List of all the pull requests submitted during the GSoC period can be seen [here](https://github.com/aimacode/aima-java/pulls?utf8=%E2%9C%93&q=is%3Apr+author%3Asamagra14+).

### List of my major contributions:

* Implementation of probability model and distribution: [#341](https://github.com/aimacode/aima-java/pull/341), [#349](https://github.com/aimacode/aima-java/pull/349), [#354](https://github.com/aimacode/aima-java/pull/354)
* Decision Theoretic Agent: [#351](https://github.com/aimacode/aima-java/pull/351)
* NQueens implementation and testing:[#389](https://github.com/aimacode/aima-java/pull/389), [#390](https://github.com/aimacode/aima-java/pull/390), [#392](https://github.com/aimacode/aima-java/pull/392)
* Improvements to the 2D Map package: [#393](https://github.com/aimacode/aima-java/pull/393), [#396](https://github.com/aimacode/aima-java/pull/396), [#400](https://github.com/aimacode/aima-java/pull/400)
* Chaining algorithms(Forward, backward and GUI apps) for inference using first order logic: [#401](https://github.com/aimacode/aima-java/pull/401), [#402](https://github.com/aimacode/aima-java/pull/402), [#410](https://github.com/aimacode/aima-java/pull/410)
* Planning using GraphPlan: [#407](https://github.com/aimacode/aima-java/pull/407), [#408](https://github.com/aimacode/aima-java/pull/408)
* Cross Validation wrapper: [#408](https://github.com/aimacode/aima-java/pull/408)
* Hierarchical Search: [#411](https://github.com/aimacode/aima-java/pull/411)
* Learning logical theories( Current Best Learning, Version Space Learning and Minimal Consistent Det): [#414](https://github.com/aimacode/aima-java/pull/414), [#416](https://github.com/aimacode/aima-java/pull/416)
* Notebooks: [All PRs](https://github.com/aimacode/aima-java/pulls?q=is%3Apr+author%3Asamagra14+label%3Anotebooks)
* Implementation of Partially Observable Markov Decision Processes and their Value Iterations: [#429](https://github.com/aimacode/aima-java/pull/429), [#430](https://github.com/aimacode/aima-java/pull/430)
* 4th edition search: [#431](https://github.com/aimacode/aima-java/pull/431)

### Challenges
 * This project is a unique combination of math with programming. There are many algorithms which require various complex mathematical techniques. These techniques if implemented sub optimally can lead to an exponential boom in the complexity of the algorithm. And hence, it was necessary to go through the literature for the most optimal approach.
 * The most important achievement of my project was the introduction of **java notebooks**. This was not easy. I had to test a large number of kernels for their library support, their architecture and what kind of graphical manipulations can be performed using them.

### Future
* There is tremendous scope of work in the project. The **notebook section**** is completely new. Only a few chapters have been implemented in the form of notebooks. The general approach to any notebook is as follows:
  * Explain briefly the **ideas from the book**.
  * Explain the API by implementing the interfaces for some custom approach to the explained ideas. For eg: extend the `Problem` class to implement some **custom problem**.
  * Solve the same problem using already implemented APIs from the code and **compare the merits** of using the APIs from the repository if such APIs exist.
  * Apply algorithms on **various problems** related to the domain.
  * There are a few sections from the book( for eg: Dimensionality Reduction or Ontological Engineering) where the authors have explained the **concept without providing a formal algorithm**. Such topics must be covered in the notebooks.
* The parser used for First Order Logic **does not recognise natural numbers as well as binary operators**. This parser must be extended to recognise them. One way to do this is to include **Peano's axioms** as default axioms to the FOL inference procedures and then derive the entire number system from them. This technique however will render many problems intractable. Another way is to use a **java High Order Logic kernel**. This is necessary for solving some problems that involve measurements along with logic.
* The APIs for probabilistic inference do not **support Continous Random Variables**. Their support must be added.
* Along with continuous RVs, some popular probabilistic distributtions such as the **normal distribution** must be added. **Geometric random variables, poisson random variables** and **binomial random variables** will also be a great addition.
* At present, the learning algorithms are **not parameterised**. These algorithms can be parameterised so as to use the **cross validation wrapper**.
* Inspired by Dr Norvig's [pytudes](https://github.com/norvig/pytudes/), we can include notebooks exploring popular problems from computer science(for eg: The Traveling salesman problem).
