---
layout: post
title: The Gaussian Integral                                # Title of the page
subtitle: "Experiments with random variables"                    # A subtitle can be displayed below your title
#feature-img: "assets/img/gsoc2016.jpg"              # Add a feature-image to the post
#thumbnail: "assets/img/gsoc.png"   # Add a thumbnail image on blog view
tags: [probability,calculus,mathematics]
---

The Gaussian integral is probably one of the most important integrals in math, physics and of late computer science too.
<!--more-->

So, today I was reading about random variables with a normal distribution and I came across this not so obvious integral $$ \int_{-\infty}^{\infty} e^{-x^2} dx $$. Obviously, out of curiosity, I tried verifying the results by an unsuccessful attempt at integrating it. I tried several alternatives including integration by parts and various substitutions. Sadly, I could not even simplify it further. The integral only got more complex as I tried to simplify. So, I finally gave up and thought of reverse engineering the solution. So, I went to Wolfram Alpha and inquired about the solution and to my relief, this is what came out :

$$ \int{e^{-x^2}}\,dx\, = \frac{1}{2}\sqrt{\pi}\,erf(x) $$

On further investigation I found out that $$ erf(x) $$ represents the [error function](https://en.wikipedia.org/wiki/Error_function) and it is quite complicated in nature. [The Risch algorithm](https://en.wikipedia.org/wiki/Risch_algorithm) proves that no elementary function exists for the error function. This means that it cannot be represented as some simple arithmetic combination of our common functions. Mathematically, the $$ erf(x) $$ is defined as follows:

$$ erf(x)\, = \frac{1}{\sqrt{\pi}}\int_{-x}^{x}e^{-t^2}\,dt $$

Now, since the hopes of finding the indefinite integral were shattered. I went on to explore the methods of finding the original integral and came across a very elegant solution. The integral $$ \int_{-\infty}^{\infty} e^{-x^2} dx $$ can be calculated as follows :
$$
  Let\, I = \int_{-\infty}^{\infty} e^{-x^2} dx

$$


  Now consider,

$$ I^2 = \int_{-\infty}^{\infty} e^{-x^2}dx\, \int_{-\infty}^{\infty} e^{-x^2}dx$$

$$
 \quad= \int_{-\infty}^{\infty} e^{-x^2}dx \int_{-\infty}^{\infty} e^{-y^2}dy
 $$

 $$
\quad = \int_{-\infty}^{\infty}\int_{-\infty}^{\infty}e^{-(x^2 + y^2)}dx\,dy
  $$

Looking at the form obtained, polar coordinate substitutions appear to be inevitable. So we substitute as follows:

$$ x\, = \, r\cos\theta $$

$$ y\, = r\sin\theta $$

$$ \implies dx\,dy = \lvert J \lbrack r , \theta \rbrack \rvert dr\,d\theta = r dr d\theta $$

Substituting it back in the integral we get

$$ I^2 = \int_{-\infty}^{\infty}\int_{0}^{2\pi}e^{-r^2}d\theta\,rdr  $$

$$ \quad = \int_{-\infty}^{\infty}2\pi e^{-r^2}rdr
 $$

On substituting $$ r^2 = p $$ we have

$$ I^2 = \int_{0}^{\infty} \pi e^{-p}dp $$

$$ \quad = \pi \lbrack e^{-p} \rbrack_{\infty}^{0}$$

$$\implies I^2 = \pi $$

So, finally we get the following result :

$$  \therefore \int_{-\infty}^{\infty} e^{-x^2} dx = \sqrt{\pi}  $$
