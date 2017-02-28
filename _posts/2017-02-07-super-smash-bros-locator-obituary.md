---
layout: post
title: 'Super Smash Bros Locator Obituary'
tags: [projects]
description: >
  The end of an era.
---

I recently received an email from Google notifying me that they would restrict an app I made a
while back if I did not provide a privacy policy or whatever. This app, Super Smash Bros Locator,
was something I made a while back, a child spawned from my love of creation and [Super Smash
Brothers Melee for the Nintendo Gamecube](https://twitter.com/onlypostsmelee). In short, the idea
was that you could find people around you on a Google Maps layout, meet up, and play smash. Anyway,
I logged onto my my developer console to see what the issue was and quickly set my eyes on
some heartbreaking statistics.

![sad-statistics](/public/img/ssbl/sad-statistics.png "feels bad")

I took this as a sign that I should euthanize my project before something uncouth happens like
Nintendo taking legal action against me or something; I don't know. So I want to give my first
ever side project a proper funeral before I put it to sleep.

---

I liken the life of Super Smash Bros Locator to that of the butterfly, kind of. As a caterpillar,
Super Smash Bros Locator was clunky, slow, lacking elegant design, ultimately
unfit to survive, but nonetheless cute. For flaws, off the top of my head, I remember handwritten SQL
statements, a backend that was literally a fat if block that conditioned on a string passed in
through the HTTP headers, and a irrational mix of Android activities and fragments on the frontend.
However, it was a good effort. Having never touched backend before, I had something working
for a single, uh I mean simple, use case.

At some point along this caterpillar's life, development slowed down as I had implemented a good set
of basic features, and my service passed my test case of logging in and randomly inputting stuff in
an attempt to break something. Having confirmed this excellent robustness, I was in
a "now what?" kind of state. At the time, I was also a freshman desperately trying to land a summer
internship, and among my interactions with various engineers, one of them suggested that I should
just release my app into the wild. Also as a desperate freshman, I took this advice as an
unquestionable mandate of heaven, and so I [released](https://www.reddit.com/r/smashbros/comments/2w5vd9/ive_created_an_android_app_to_help_you_play_smash/) it. As soon as my caterpillar landed its
fuzzy feet on the jungle floor (the Google Play store), it instantly combusted and was trampled by
the jungle's assortment of creatures. All sorts of bugs, unexpected features, and null pointer
exceptions were reported. Despite all this, I managed to get around 2000 users in 2
days; it was exciting to a bunch of little GameCube controllers pop up all over Google Maps.
I would obsessively check the number of entries within the MySQL database and naturally conclude that
I was simply the best programmer to ever do it.

<div style="width:100%">
  <img src="/public/img/ssbl/top-new-free.png" style="float:left;width:49%"/>
  <img src="/public/img/ssbl/gc-on-map.png" style="float:right;width:49%"/>
</div>

Seeing the large influx of users and even larger influx of bug reports, I decided to overhaul
everything. I got the help of my pair programming partner, [Ashwin](http://madavan.me/), to rewrite
the backend with Spring, Hibernate, and all those good web technologies goodies that I was not
aware of. I rewrote the Android app part, adding some nice material design elements, consistent
activity/fragment usage, etc. If you have been following my caterpillar analogy, this is the part
where the caterpillar is chilling in the cocoon.

After a couple weeks of work, our cocoon was ready to hatch, and we [re-released](https://www.reddit.com/r/smashbros/comments/317fob/ive_created_an_android_app_that_helps_you_play/) with the shiny new
backend and an equally sleek frontend to match. Unfortunately, what we saw and what our users saw
were complete opposites. We saw a sleek, 2.0, VR ready, deep TensorFlow ready, fresh butterfly,
but our users saw the same unfit-to-survive caterpillar with a pair of paper-mache wings haphazardly
glued onto its back.

<div style="width:100%;height:200px">
  <img src="/public/img/ssbl/majestic-butterfly.jpg" style="float:left;width:52.56%;height:100%" title="what we saw"/>
  <img src="/public/img/ssbl/caterpillar-with-wings.png" style="float:right;width:45%;height:100%" title="what they saw"/>
</div>

Essentially, users saw the same clunky app the I released the first time around. Given, the
polished new version did have its own share of bugs. For instance, on this release, upon revamping
the backend, everyone ended up in some large public group chat when they would try and send an
individual message. It _was_ interesting to see a massive conversation between hundreds of people,
but it was still unintentional.

A couple bug fixes and app updates later, here we are. A year ago, the backend would have gotten
around 50 hits a day, but that has dwindled. I've determined that the ~10 hits I get per
day is no longer worth the $15 I spend a month on maintaining the EC2 instance, and the privacy
policy was the final straw. The app lost a lot of crucial momentum that it should have
maintained from the first release. I feel like if everything went smoothly at the beginning, the app
might have had a larger base of regular users and grown to take a spot right next to Facebook
Messenger in top free apps, but somehow that didn't happen.

In conclusion, I would say the most valuable thing I got from this experience is a taste of what
it's like to create something and have people use it. Now I know what some of you might be
thinking. _Wow Eric. That's pretty dumb. I could write some dumb app, put it on the Play Store,
and get users._ Yeah I guess you could. I don't really know what to say to that.
