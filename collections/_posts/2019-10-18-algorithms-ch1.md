---
layout: post
title:  "Introduction to Algorithms: Chapter 1 — The Role of Algorithms in Computing"
date:   2019-10-18 00:00:00 -0400
---

During the summer after my sophomore year of college, I knew I wanted to find an internship. I finally landed one at .decimal in May 2012. While this was hugely beneficial for both my career and education, I sometimes look back on my studies with a bit of regret. Toward the end of my undergraduate degree, I was working full time hours (even though my official title was "Software Development Intern"). This left little time for studying. My grades were good, but I felt I lacked some of the depth of understanding that other students had.

I would like to return to some of the fundamentals that I learned as an undergraduate student through a series of blog posts covering the popular computer science textbook *Introduction to Algorithms* (third edition) by Cormen, et. al. This first blog post covers "Chapter 1: The Role of Algorithms in Computing."

# The Field of Computer Science

On the second floor of the .decimal offices, there are a few private offices and a large open area. It was large enough to fit 15 or so cubicle offices. While I was there, however, it was typically used to store a diverse and ever-rotating collection of things that didn't have a place elsewhere: spare desks and tables, a ping-pong table, trade show setups, etc. During the early days of Thinknode, I had this large open area to myself as an office. It was dimly lit, and the only windows overlooked the shop floor.

One day, a potential new hire came to the office. I was tasked that day with showing him around our codebase and introducing him to the trial project we wanted him to tackle on a contract basis (tooling for our unit testing suite). The conversation drifted to our chosen fields of study. I was still in school at the time, and I told him about my plans to pursue a Master's in computer science. He was pursuing a programming degree on the advice of an advisor who told him that computer science offered no real advantage over a programming degree in the job market. I didn't agree with his advisor, but I had trouble at the time articulating the value of computer science as a degree program. Through the intervening years, I've learned a lot about what computer science is and what it brings to the table.

My impression of my limited exposure to programming curriculums (including the many online programming "bootcamps") is that they tend to focus on the nuances of programming languages and the latest-and-greatest web frameworks, but they fail to prepare the learner for some of the real world challenges that face them once they've moved beyond building a to-do list application (though I'm sure there are some exceptions out there). In contrast, I would describe my computer science education as not very programming language focused at all. Indeed, you might even call the approach "language agnostic." Admittedly, much of the Introduction to Computer Science class — the first required class for Computer Science students — focused on the C programming language. Beyond that, however, most classes were geared toward Computer Science theory, including the data structures and algorithms that make things like natural language processing and machine learning possible.

Let's take a moment and consider this key question from Chapter 1 of *Introduction to Algorithms*.

> Suppose computers were infinitely fast and computer memory was free. Would you have any reason to study algorithms?

At the core of computer science is the knowledge of algorithms and data structures. As the authors point out, this knowledge gives us the ability to show that a program will terminate with the correct answer. Of course, computers are not infinitely fast, and memory is not free, so we must learn how develop efficient solutions to complex programs. This is where the value of computer science lies.

I'm really excited to begin this deep-dive back into the fundamentals of computer science. Even with nearly a decade of computer science education and software engineering work experience, I expect to learn (or re-learn) a bunch! Without further ado, let's dive in to the first chapter's problem!

# Running Times

The first problem in the book is **Problem 1-1: Comparison of running times**. I've included the problem as well as a table with my solution.

> For each function *f(n)* and time *t* in the following table, determine the largest size *n* of a problem that can be solved in time *t*, assuming that the algorithm to solve the problem takes *f(n)* microseconds.

Before I provide the table with my answers, it's important to note that it was simple enough to arrive at a mathematical expression for the final answer, especially when the exact number would be too big to fit into the table. However, for some cells, it was easier to derive the answer as an integer using a simple python script. You can find the python implementation of this derivation and my answers to the rest of the chapter exercises on my [red-mobile GitHub repository](https://github.com/kyleburnett/red-mobile).

<table>
    <thead>
        <tr>
            <td></td>
            <td>1 second</td>
            <td>1 minute</td>
            <td>1 hour</td>
            <td>1 day</td>
            <td>1 month</td>
            <td>1 year</td>
            <td>1 century</td>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>\(\lg n\)</td>
            <td>\(2^{10^6}\)</td>
            <td>\(2^{6 \cdot 10^7}\)</td>
            <td>\(2^{36 \cdot 10^8}\)</td>
            <td>\(2^{864 \cdot 10^8}\)</td>
            <td>\(2^{2592 \cdot 10^9}\)</td>
            <td>\(2^{31536 \cdot 10^9}\)</td>
            <td>\(2^{3155760 \cdot 10^9}\)</td>
        </tr>
        <tr>
            <td>\(\sqrt{n}\)</td>
            <td>\(10^{12}\)</td>
            <td>\(36 \cdot 10^{14}\)</td>
            <td>\(1296 \cdot 10^{16}\)</td>
            <td>\(746496 \cdot 10^{16}\)</td>
            <td>\(6718464 \cdot 10^{18}\)</td>
            <td>\(994519296 \cdot 10^{18}\)</td>
            <td>\(9958821177600 \cdot 10^{18}\)</td>
        </tr>
        <tr>
            <td>\(n\)</td>
            <td>\(10^6\)</td>
            <td>\(6 \cdot 10^7\)</td>
            <td>\(36 \cdot 10^8\)</td>
            <td>\(864 \cdot 10^8\)</td>
            <td>\(2592 \cdot 10^9\)</td>
            <td>\(31536 \cdot 10^9\)</td>
            <td>\(3155760 \cdot 10^9\)</td>
        </tr>
        <tr>
            <td>\(n \lg n\)</td>
            <td>62746</td>
            <td>2801417</td>
            <td>133378058</td>
            <td>2755147513</td>
            <td>71870856404</td>
            <td>797633893349</td>
            <td>68656519951424</td>
        </tr>
        <tr>
            <td>\(n^2\)</td>
            <td>1000</td>
            <td>7745</td>
            <td>60000</td>
            <td>293938</td>
            <td>1609968</td>
            <td>5615692</td>
            <td>56176151</td>
        </tr>
        <tr>
            <td>\(n^3\)</td>
            <td>100</td>
            <td>391</td>
            <td>1532</td>
            <td>4420</td>
            <td>13736</td>
            <td>31593</td>
            <td>146679</td>
        </tr>
        <tr>
            <td>\(2^n\)</td>
            <td>19</td>
            <td>25</td>
            <td>31</td>
            <td>36</td>
            <td>41</td>
            <td>44</td>
            <td>51</td>
        </tr>
        <tr>
            <td>\(n!\)</td>
            <td>9</td>
            <td>11</td>
            <td>12</td>
            <td>13</td>
            <td>15</td>
            <td>16</td>
            <td>17</td>
        </tr>
    </tbody>
</table>

Exponential growth is always pretty interesting to see when it's laid out in a table or chart like that, huh?
