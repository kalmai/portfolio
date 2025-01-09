+++
author = "Zachary Kolker"
title = "Grokking Rails"
date = "2025-01-07"
description = "My journey towards a better understanding of my favorite framework."
+++

Notify myself and other users who sign up when they can act upon free non-gambling related game-day promotions.

<!--more-->

This projects goal was to get a car wash which resulted in me learning to despise timezones, just like you, and learn more about taking a rails project from start to MVP.

Reflecting back on all the commits made to the repository, I really learned some strength and weaknesses of different approaches with different tools.

For example, redis is an easy caching solution that I began the project with. However as the project grew I needed to actually persist past results and I did not want to bother with expiring caches. Around that time I was reading about how smaller applications could probably get away with just simply using postgres. This resulted in a pretty heavy handed refactor which I think landed the project in a better spot to maintain and make changes quickly.

If you would like to discuss my passion project of getting a car wash for free, a 20 dollar value, feel free to reach out and I would be more than happy to explain how/why I have sunk many *many* hours into this effort.

## Technologies Used

{{< badge text="aws" icon="aws" >}}
{{< badge text="docker" icon="docker" >}}
{{< badge text="postgres" icon="postgres" >}}
{{< badge text="rails" icon="rails" >}}
{{< badge text="redis" icon="redis" >}}
{{< badge text="ruby" icon="ruby" >}}
{{< badge text="sendgrid" icon="sendgrid" >}}

## Links

- [repo](https://github.com/kalmai/rails-deal-notifier)
- [prod](https://github.com/kalmai/rails-deal-notifier) WIP
