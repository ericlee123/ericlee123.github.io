---
layout: post
title: 'Genetic 7 Wonders'
tags: [projects]
description: >
  Why do my projects keep dying?
---

## Context

During college, I have developed a strong affinity for board games. My
group of friends is not interested in sports, degenerate activities, or going
outside in general, so board games served the purpose of setting a landscape
for us to scheme and strategize against one another. My gateway board
game was The Settlers of Catan. Unlike "lame" board games like Sorry,
Battleship, Chutes and Ladders, and what I am probably incorrectly classifying
as American board games, Catan showed me board games could be fun and not the
alternative activity in the case of a power outage. Catan brought me into a
world created by people with very European sounding names, such as Klaus Teuber
(Catan) and Klaus-Jürgen Wrede (Carcassonne). However, I was eventually steered
away from Catan due to, despite what
[Wikipedia](https://en.wikipedia.org/wiki/Catan) says, how I perceived luck to
play too big of a role in the outcome. I had to find something to fill the deep
void that Catan left in my soul.

## 7 Wonders

Amidst my spiritual journey, I found 7 Wonders. It checked all the boxes; it
was fast-paced, sufficiently complex (maybe even too complex), and most
importantly, designed by some European guy, Antoine Bauza. For those who
are new to 7 Wonders, its goal is just like that of any other board game,
to maximize victory points, except there are 2<sup>100</sup> different ways to
do so.

## Genetic Algorithm

In the face of 7 Wonders' extreme complexity, I had the idea that a good way to
optimally play the game would be to write a genetic algorithm. It was a simple:
have constants for certain elements in the game that would influence
what card should be chosen at each turn. My program follows the standard recipe
for genetic algorithms. First, a population with randomized weights is created.
For each generation, each person plays a game where all of the other
players are greedy. A greedy strategy chooses the card that
maximizes the number of victory points at each turn. There were only two other
strategies I could think of: random and weighted, weighted being the strategy I
was trying to optimize. I decided greedy would be the best strategy to train
against because it the "default" way to play 7 Wonders. I also tried training my
population against itself at every generation, but the results were mixed. (I
think training the population against itself would possibly end up with weights
being tuned to some sort of suboptimal metagame that would develop among the
population.) After playing the population against a greedy strategy, each
player would be assigned a fitness score based on their final number of victory
points. In my algorithm, I set the fitness equal to the square of the victory
points as to further bias towards better performing players. To generate the
next generation, the population would breed using a roulette selection method.
Also, with a small probability, mutations would give the weights a small nudge.

To actually assess whether or not the population improved, at the end, I
compared the evolved population with a greedy, a random, and the first
generation population of equal size. Specifically, given a pair of populations,
each player would play a game with greedy opponents and the total number of
victory points would be summed up for each population. I performed this 100
times for each pair to mask the effects of random chance.

## Results

It doesn't work. In fact, according to my methods of measuring improvement my
genetic algorithm makes the population worse. The comparison at the end shows
that the evolved population loses against the first generation with a very high
probability. It also seems like the higher the number of generations the
population evolves for, the higher the probability becomes. Both the evolved
and first generation perform better than a greedy or random strategy. Because
of this, it almost seems like the process of evolution accomplishes nothing
except making things worse.

<div style="padding-top:8px;padding-bottom:16px;">
  <img src="/public/img/7w/evolution-results.png"
       style="display:block;
              margin:auto;
              width:66%;"/>
  <figcaption style="text-align:center;font-size:14px;color:gray;">Generations: 100, Population Size: 1000</figcaption>
</div>

To begin my postmortem, I do acknowledge that I could have made my weights
better and more specific, but based on my current results I doubt that would
improve much, if at all. There are 2 things that come to mind as to why my
genetic algorithm failed to work.

First is the parameter space. I came up with a set of 9 constants for each
notion of value: money, military points, resources, science, etc. Additionally,
I have 3 sets of these, one for each age. Basically, I have this 27 dimensional
space to find some sort of combination of weights at a local maximum. Without a
large enough population, it's possible that this 27 dimensional space would not
be densely packed enough to find any coherent local maximum.

The second idea that comes to mind is how big of a role
randomness plays in 7 Wonders. Empirically, when I have played this game with
my friends, there is little consistency with how we place among games.
It's possible we all just suck, but it's unlikely. My theory
is 7 Wonders is extremely luck based, but this aspect is hidden behind a
plethora of rules and game mechanics. To support my claim, I'll explain my
thought process for developing a strategy. Let's say I have a strategy that I
want to follow throughout the game, for example, focusing on building science
cards. The success of this strategy will largely depend on which cards my
opponents choose from as the game progresses. If they also want to concentrate
on science, then we will be competing for the same resources. Okay, that's fine;
it's not expected that such a simple strategy would consistently perform well.
I'll modify my strategy to follow for "paths" that my opponents aren't taking,
which, in theory, would mean less competition, for the resources I seek. Given
that everyone's cards are public, I can infer what my opponents are going for
by looking at their board. Now, what if the "paths" my opponents
take do not work out for them, and they decide to switch plans midgame? From
my experience this happens more often than not. From my experience, rarely does
the distribution and cycling of cards line up perfectly with my initial plans.
At this point, my current model of the game is a group of people each with their
own not-necessarily-unique plan, that has a high chance of switching, possibly
more than once. This is something my shoddy little genetic algorithm cannot
perform well with. It seems like the largest deciding factor of success is what
cards end up in your hand as the game goes on. It's not complete chaos, but to
me, it seems very close. Perhaps, a super large multilayer deep neural network
that takes the entire state of the game as input and outputs a score for each
card could do well.

## Conclusion

I've decided to put this on project indefinitely on hold, maybe to be picked up
again after I learn more about machine learning or artificial intelligence. The
[code](https://github.com/ericlee123/genetic-7-wonders) can be found on my
GitHub for anyone who does not want to go through the nightmare of coding up
every mechanic of 7 Wonders.s
