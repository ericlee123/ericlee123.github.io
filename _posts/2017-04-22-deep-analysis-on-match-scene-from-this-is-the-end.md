---
layout: post
title: 'Deep Analysis on Match Scene from This is the End'
tags: [thoughts]
description: >
  Complicated math incoming.
---

I was watching _This is the End_ with my friends the other day, and among the
various goofs and gaffs, we witnessed the match scene.

<div style="text-align: center;">
<iframe width="512" height="288"
        src="https://www.youtube.com/embed/qasKaqsRLuc"></iframe>
</div>

Just to provide a little context of the scene I will be talking about, in case
any traces of the scene was removed from all corners of the internet, a couple
people are stuck in a house due to a zombie apocalypse. They need water, but
it's in a basement that can only be accessed from the outside. To decide who
goes, Seth Rogen lights a match and hides it with a bunch of other matches, and
whoever pulls the burnt match has to risk his life to get some water.

As the scene was unfolding, I assumed that they would all pick a match at the
same time and then reveal who picked the burnt match. Then, when Craig
Robinson volunteers to go first, I had a little internal monologue. _Is he
dumb?_ _Why would you volunteer to go first? Wouldn't it be better to let
others go first so they incur risk before you do?_ But after discussing with
my friends for a bit, we concluded that he was a genius because going early
is better than going last because you have a larger population of matches and
thus a smaller chance of drawing the burnt match. As the movie progressed, my
mind stayed behind. _Maybe it doesn't matter who goes first. Or maybe there is
some optimal turn to go based on the number of matches._ Anyway, let's figure
this out with basic math.

In this scenario, if Craig were to go first, he has a 1 in 7 chance of picking
the burnt match. Now, say he decides to wait to be the third person to draw a
match, if it gets to that. The probability of his drawing a match is 6/7 * 5/6 *
1/5. This even extends to the event of drawing a match as the second to last
person: 6/7 * 5/6 * 4/5 * 3/4 * 2/3 * 1/2. The numerators and denominators
nicely cancel out with neighboring terms, so that no matter which turn Craig
waits until, the probability is 1/7. Just to be thorough, let's take into
account every possible outcome in the event that Craig decides to wait to be
the third person. The probability that he draws the burnt match is 1/7, the
probability that he doesn't is 6/7 * 5/6 * 4/5 = 4/7, and the probability that
someone before him draws the burnt match is 2/7, as each person before him also
has a 1/7 chance of drawing the match. All of the probabilities nicely sum to
7/7.

In conclusion, yes, this is all very simple math. I wouldn't be surprised if
this is common knowledge in a field like game theory or combinatorics. This
also explains why Craig was so quick to go first. He quickly crunched the
numbers and realized it didn't matter.
