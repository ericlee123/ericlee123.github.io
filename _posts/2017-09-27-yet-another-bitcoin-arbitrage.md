---
layout: post
title: 'Yet Another Bitcoin Arbitrage'
tags: [projects]
description: >
  We should have won.
---

## Setting

"Hackathons are just about chaining API's together." As my project partner,
[Sam Maynard](https://samm81.github.io/) delivered this truth to me, I felt the
magical hope I had towards life diminish slightly. What I thought were
congregations to debut new technologies ended up just being competitions to see
who could write _some_ wrapper around already existing API's provided by tech
giants. I say _some_ because I was unable to deduce what kind of metric was
used to rank projects at the hackathon I went to. Not to mention,
[HackRice 7](http://hack.rice.edu/) was my very first hackathon, so this was all
news to me. In any case, we didn't let the harsh reality deter us, we set forth
to coming up with an interesting project that would solve an interesting problem
in an interesting way. After much discussion and staring at the prize page, we
decided upon a project.

Predict exchange rates between cryptocurrencies in order to be prepared for when
arbitrage occurs in the market.

## Conflict

Now, whether you are familiar with financial/cryptocurrency markets or not, I
know exactly what you're thinking. "Eric, ya dingus, there are definitely a
million people who monitor arbitrage for cryptocurrencies. They are, for sure,
faster than you and have more capital." "Predicted values? Is this future
arbitrage? Isn't that just trading?" "Are you trying to model something similar
to stock prices? People devote entire careers to this. You're not going to
crank anything interesting out." First of all, reader, chill out. This is a
hackathon project. Second of all, don't worry, we thought of it too; I'll
address these points after some explanation.

There are some current problems people face when attempting to perform arbitrage
in cryptocurrency markets. One, certain transactions take an hour to verify,
which means it will be an hour before you get your capital back. In this time,
exchange rates could easily change in such a way that a plan you had initially
would be no longer profitable. Two, transaction fees can render potential
profits to be losses. Three, within an exchange, there really shouldn't exist
any opportunities for arbitrage, but across exchanges, there might. However,
following my first point, it takes time to move capital between exchanges.
Given these three characteristics, it can be difficult for individual,
small-scale investors, who don't have enough liquidity in each currency, to be
ready to take advantage of arbitrage were it to become available.

## Rising Action

After much deliberation, Sam and I decided on our project pipeline. It would
start with data collection. Then we would use the collected data, exchange rates
in our case, to generate statistical models that would give us estimates for
values in the near future. Finally, we would enter these predicted values into
a custom graph search algorithm that would return a suggested sequence of
actions to take in order to maximize profit.

To address the points above, we considered this "arbitrage" because it was
technically as fast as a small investor could move money around, given the time
constraints. Also, we weren't particularly invested in the accuracy of the
models, we simply needed some predicted values, good or bad, to show a proof of
concept. Of course, more accurate models would lead to more accurate profits.

So we set to work. Sam worked on writing a program to periodically retrieve
data from [CoinMarketCap](https://coinmarketcap.com/) while I wrote the custom
graph search algorithm. For simplicity, we decided to just consider the US
dollar, Bitcoin, and Ethereum. We modeled the problem as such. Each exchange,
Gemini, Bitfinex, etc., consisted of 3 nodes and 3 edges to form a triangle.
Each node represented a currency and each edge the exchange rate within the
exchange. So within this graph, we would need to find a sequence of actions that
would result in the maximum ending capital. The reason we needed our own graph
search algorithm is because the edges "changed values" over time, we needed to
find the maximum value path, and there are multiple goal states (we considered
a goal state to be any node that matched the starting currency type, regardless
of the exchange). Finally, to generate predicted values, we used
[fbprophet](https://facebook.github.io/prophet/) for its simplicity, although it
really doesn't seem to be built for stochastic processes, like stock prices.

To verify that our program's suggestions actually turned a profit, we wrote
a script that would feed a prefix of our collected data into the program,
perform the suggested actions on real data, and then output the estimated and
actual value.

## Climax

Our program worked! Given $100, it would, on average, return a sequence of
actions with an expected value of $105. Using our verification script, weirdly
enough, actual profits were always under the expected values. For an expected
value of $105, the actual profits would be around $102. This may have been due
to the
[optimizer's curse](https://faculty.fuqua.duke.edu/~jes9/bio/The_Optimizers_Curse.pdf),
but I am not sure. We were just happy it would return a profit. Most likely,
with better statistical models, the actual value would be closer to the
expected.

## Falling Action

Well, we weren't finalists. But we did win a company prize from the gracious
HBK. It seemed like the people who were finalists had something to present,
whether it be some graphs, slides, or even just a visual demo. I do concede, if
we had to present, people would have just heard us drone on while watching
nonsensical output scroll away on a terminal.

## Resolution

Would I put my own money on this? Maybe. I feel like every part of the
program is solid, except the prediction, which is extremely important. Maybe if
I were able to provide some confidence intervals, I would have more faith in
using this as an investment tool. All in all, it was a fun weekend, and a good
first experience for hackathons. Check out Sam's experience
[here](https://samm81.github.io/hackrice/).

<div style="width:100%">
  <img src="/public/img/storyline.jpg"/>
</div>

If you would like to check the repo out, go
[here](https://github.com/samm81/YABA).
