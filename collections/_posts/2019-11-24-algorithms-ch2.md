---
layout: post
title:  "Introduction to Algorithms: Chapter 2 — Getting Started"
date:   2019-10-24 00:00:00 -0400
---

Last weekend I received Peter Reinhart's *The Bread Baker's Apprentice* in the mail from the library. I love baking bread, especially sourdough, but my recent baking endeavors have been a mixed bag. Wading through food websites and food blogs for good recipes and sound baking advice can be quite the challenge. What I was really after was a professional's take on bread baking, which is why I decided to turn to Reinhart's book, about which I'd heard very good things.

What is clear from Reinhart's writing is that he is passionate about both bread and teaching. His years as a baker and experiences learning from France's bread making greats have not made his writing feel arrogant or snobbish. Neither do his writings include frivolous anecdotes that have become so ubiquitous in food blogs. Rather, his writing is focused and approachable, and he makes this humble home baker feel ready to tackle some of his recipes (or "formulas" as he calls them).

Some of my most successful bread bakes thus far have been simple sourdough boules. There's no better feeling as a baker than when you pull out your loaf to find that checks all the boxes: good crumb and rise, nice caramelization on the outside, etc. The process of taking such simple ingredients — flour, water, salt, yeast — and creating something so seemingly complex is really special.

It occurred to me this week that this was also why I enjoyed learning about mathematical induction proofs. The building blocks for these proofs are so simple, yet they come together to create a logical and well-structured argument. (I once read somewhere that a proof was an argument that could withstand the criticism of a highly caffeinated adversary.) In this post, I'd like to explain how I understand and approach mathematical induction in the context of exercise 2.3-3 of *Introduction to Algorithms*. The problem is as follows.

Use mathematical induction to show that when \\\(n\\\) is an exact power of 2, the solution of the recurrence

$$
T(n)=\begin{cases}
2 & \text{ if } n=2 \\ 
2T(n/2) + n & \text{ if } n=2^{k}, \text{ for } k > 1
\end{cases}
$$

is \\\(T(n) = n\lg{n}\\\).

Now, mathematical induction proofs have two parts: a base case and an induction step. These steps were first explained to me with a comparison to "proving" that you can climb a ladder. The base case is like the first rung of the ladder. The base case is important just like the first rung of a ladder is important; if the first rung of a ladder is too high to reach or it can't hold the weight of the person climbing it, we can't go any further in our prove. The induction step works by saying, "Well, let's assume that I'm on rung k. Can I then prove them I can reach the k+1 rung?" Proving that I can advance a rung of the ladder coupled with the base case completes the proof. It's not a perfect analogy, but you'll hopefully see the similarities as we progress.

The base case for this problem is the case where \\\(n = 2\\\). \\\(T(n) = 2\\\) by the recurrence above. This is equivalent to \\\(T(2) = 2\lg{2} = 2\\\).

The induction step requires us to first assume that the statement is true for \\\(n = 2^k\\\), \\\(T(2^k) = 2^k\lg{2^k} = k2^k\\\). Using this assumption, we must show that the statement is true for \\\(n = 2^{k+1}\\\).

$$
\begin{align*}
T(2^{k+1}) &= 2T(\frac{2^{k+1}}{2}) + 2^{k+1}\\ 
 &= 2T(2^k) + 2^{k+1}\\ 
 &= 2[k(2^k)] + 2^{k+1}\\ 
 &= k(2^{k+1}) + 2^{k+1}\\ 
 &= 2^{k+1}(k+1)\\ 
 &= 2^{k+1}(\lg{2^{k+1}})\\ 
 &= n\lg{n} \text{, where }n = 2^{k+1}
\end{align*}
$$

The final step is to simply restate what we have proved. In this case, we have shown that the recurrence above is true for values of \\\(n\\\) where \\\(n\\\) is an exact power of 2.
