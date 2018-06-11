---
layout: post
title: The two envelopes paradox                                # Title of the page
subtitle: "Experiments with random variables"                    # A subtitle can be displayed below your title
#feature-img: "assets/img/gsoc2016.jpg"              # Add a feature-image to the post
#thumbnail: "assets/img/gsoc.png"   # Add a thumbnail image on blog view
tags: [gsoc,aimacode,artificial intelligence,probability]
---

You are handed two envelopes. and you are told that one of them contains
m times as much money as the other, where m is an integer with  m greater than 1. You
open one of the envelopes and look at the amount inside. You may now keep this
amount, or you may switch envelopes and keep the amount in the other envelope.
What is the best strategy?
<!--more-->

This is a much-discussed puzzle in the theory of averages and probabilities. Well, our intuitive
reasoning tells us that it doesn't matter. There is no way of knowing which envelope to consider and this line of thought is absolutely fine. But now, think of the bigger picture. Suppose, you are asked to make this choice a million times. What would be your strategy then?

You will definitely try to find some pattern and some cheats to maximise your money. Here comes math to the rescue. Mathematics tells us that the best strategy would be to always switch the envelope! How? Let's have a look.

First, let us mathematically formulate the situation. You are given an envelope that contains $$ \$ x $$. There is a second envelope that may either contain $$ \$ mx $$ or $$ \$ x/m $$. Now, you may choose either the second envelope or keep the first. Now, let us assume that you always change the envelope, what is the average amount (or the expected amount) that you earn?

To calculate the average let's make certain assumptions. The only assumption is that there is no bias towards any of the envelopes and hence, the second envelope might equally likely contain the possible values. So half of the times you will get an amount of $$ mx $$ and $$ x/m $$ for the other half.

$$ \therefore Average = 1/2 \times mx + 1/2 \times x/m  = \frac{(m^2 + 1)x}{2m} $$

Now clearly, $$ m^2 + 1 > 2m $$

$$ \therefore Average = \frac{(m^2 + 1)x}{2m} \gt x $$

This means that if we always chose the second envelope, then we have a profit on an average. Well, this seems absurd. Why would this happen?

The result starts to make sense if we look at the relative loss and gain on choosing the second envelope. If the second envelope has less money, then our relative loss becomes:

$$ \frac{\frac{x}{m}-x}{x} = \frac{-(m-1)}{m}  $$

Our, relative gain on the other hand is:

$$ \frac{mx-x}{x} = (m-1) $$

So, clearly, our relative gain is much larger (m times larger) than our relative loss. This means, that even if we lose half of the times, then also, our profit will be more than our loss. Hence, when we look at a large number of such experiments, then, by choosing the second envelope we are actually gaining money. And, hence the result.

Math can surely act strangely at times.
