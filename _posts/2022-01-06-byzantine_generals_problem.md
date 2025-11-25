---
layout: post
title: "Byzantine Generals Problem"
date: 2022-01-06
tags: [blockchain, distributed-systems]
---

## What is Byzantine generals problem

![Byzantine generals problem]({{ site.baseurl }}/assets/images/blockchain/byzantine_generals_problem.png)

Byzantine generals problem is a game theory that states: suppose you are attacking a fort from different sides, how can all the generals on all sides of the fort come to consensus without a trusted central party that everyone will attack the fort at the same time. Only if the attack happens at the same time they win, else no

Let's say, you pass a message through a soldier from your side with the time of the attack to the rest of the 3 sides. How do you know that message was reached? How do we know that the message was not infiltrated in between? Let's say you confirm if the message was reached only after getting a reply, how do you know that the reply is legitimate? How can other generals trust the source, etc.

Byzantine general problems occur only in decentralized world as there is no reliable source of information. In case of centralized systems we trust central authority to report reliable information

This is an unsolved problem until bitcoin was created.
Bitcoin claims to have solved this problem

### How bitcoin solves this?

Proof of work -> Which is the core of bitcoin solves this problem.
