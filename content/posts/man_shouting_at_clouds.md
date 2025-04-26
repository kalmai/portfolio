+++
author = "Zachary Kolker"
title = "Man Shouting at Clouds"
date = "2025-04-26"
description = "My take aways from cloud hosting."
+++

<link rel="stylesheet" href="/reactive_image.css" />

I too made a new years resolution, spin up a production server for <a href="/posts/grokking_rails/">my side project</a>. My journey into free/freemium cloud hosting had multiple stops with mixed results.

<!--more-->

In the past services like [Heroku](https://www.heroku.com/) served as a free way to host a side project to serve a handful of users. This was great while it lasted, but all good things must come to an end. Knowing that my amazing <a href="/posts/grokking_rails/">my side project</a> is most likely not going to make the same impact of sliced bread, I had no desire to fork over more money to our backyard monopolies to host my application. I was encouraged by [DHH's presentation](https://youtu.be/-cEn_83zRFw?si=pCXbMwwJIwv87usQ) and [Fireship's video](https://youtu.be/cw34KMPSt4k?si=Det3bWIgfLrQqr4r) to get my feet wet.

I began with Google [Cloud Run](https://cloud.google.com/run), as per Fireship's path laid out for me, which forced me to dockerize my application. The postgres database shoved inside of the docker image was having issues communicating with each other. This frustrated me greatly and striving to be a lazy developer, I wanted to find something that would solve all my issues with minimal changes, how naive I was...
 - pricing: [???](https://cloud.google.com/run#pricing)
 - pros: Encourages dockerization
 - cons: Poor [docker hub](https://hub.docker.com/) integration and vendor lock-in

My next stop was at [render](https://render.com/). I feel like this is the spiritual successor to [Heroku](https://www.heroku.com/) and would recommend it assuming cold starts and background jobs are not things you care about. The cold starts does not have to be a problem if you are have a script to hit your site every few minutes (this burns through your free per month credits very quickly), but that begets the question of "_why host on your platform if I need to run a job on my machine?_". In my situation, cold starts caused background jobs to not start which is critical making [render](https://render.com/) an invalid candidate.
 - pricing: [freemium](https://render.com/pricing)
 - pros: CI/CD Integration and stupid simple configuration
 - cons: Resources are pretty limited and cold starts suck

Of course my dabbling in cloud computing would not be complete without forking over some credit card details to [AWS](https://aws.amazon.com/). AWS sucks (products are great though), and makes me truly appreciate deployment engineering. I signed up and forgot about AWS until I hastily filled out a survey and ended up with 300 dollars of credits to use, turns out they have an expiration date similar to EC2's free tier and my zero-sum budget.
 - pricing: Confusing for my monkey brain
 - pros: Awesome products
 - cons: Terrible documentation and pricing is indecipherable

<img src='/angry-lemming.gif' alt='aggressive lemming' />

DHH does suggest that programmers are afraid to touch computers which is why we are lighting stacks upon stacks of money on fire in the clouds. I do not fear the computer, I do not touch grass, I know that I _can_ and _will_ get this server hosted for fractions of pennies of my electric bill. The [lemming](https://lemming-trusty-dane.ngrok-free.app/) will rise again!

## Technologies Used

{{< badge text="aws" icon="aws" >}}
{{< badge text="cloud run" icon="cloudrun" >}}
{{< badge text="docker" icon="docker" >}}
{{< badge text="render" icon="render" >}}
