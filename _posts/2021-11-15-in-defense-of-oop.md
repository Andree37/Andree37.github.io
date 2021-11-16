---
title: In Defense of OOP
author: André Ribeiro

date: 3021-11-15 18:35:00 +0000
categories: [Blogging, Writing]
tags: [study, oop, opinion]
mermaid: true
---

## Motivation

**Object Oriented Programming** Some developers love it - others hate it.
*OOP* is a long-standing programming paradigm that addresses the importance of organizing your code into larger more meaningful objects that model the parts of our problem.

This sometimes represents what the people actually think in the real world, arranging their code into meaningful chunks with relationships that are obvious and intuitive.

But in practice, OOP doesn't always work out this way. 

**I want to address this issue and come to defend the importance of OOP whilst instead shifting our eyes towards over-engineering.**

## Over-Engineering

![Data Preparation](/posts/in-defense-of-oop/overengineering.png){:  width="1272" height="589" style="max-width: 350px; background: white; border: 2px solid grey" .right}
There is a very high chance that you, the reader, have done a bit of over-engineering. 
<br>If you are doing a chunk of code with a lot of time in your hands, most likely you have came across the idea of "*hmmm, I could make this more interesting*".
<br>And then ultimately, created a monstrosity that can not be maintained and fails to even do the first thing *OOP* tries to do, intuitive relationships.
`This is where most of the cases against OOP come from`

_[image source][over engineering source]{: target="_blank" }_ 


Over engineering can be very hard to identify, and is quite motivated by colleges.
: Almost every project I've done in college, and I think the reader can relate to this as well, as come with a *bonus* for over-complicating by creating data-flows, managers, hierarchies, etc. that aren't well fit to the problem and ultimately by the end of the project leaves us **sick of coding in it**.

### OOP helps Over-Engineering
There are so many patterns, where we can dive [head-first][head first book]{: target="_blank"} into a complete and utter disarray when we want to implement a certain feature.

I think what happens often is that people tend to think about relationships without thinking about the end-use 


[over engineering source]: https://twitter.com/jerome_etienne/status/578591043093835776
[head first book]: https://www.amazon.com/Head-First-Design-Patterns-Brain-Friendly/dp/0596007124