+++
author = "Zachary Kolker"
title = "Another Portfolio Refresh"
date = "2025-01-09"
description = "Gravitating towards a maintainable portfolio that looks and feels good."
+++

<link rel="stylesheet" href="/reactive_image.css" />

A portfolio site is a must as a developer. As we grow as engineers, our portfolios must adjust as well. Tempting as it may be to hop on the new Javascript framework for your refresh, maybe it is best to just [keep it simple stupid](https://en.wikipedia.org/wiki/KISS_principle).

<!--more-->

When writing documentation or even a readable pull request for you and your fellow developers, you are most likely writing Markdown. This is super common and easy to write. I took the time to shop around and see what was out there for writing up simple blogs or portfolios such as [Bridgetown](https://www.bridgetownrb.com/), [Astro](https://astro.build/), and [MkDocs](https://www.mkdocs.org/). At my current role we would often document stuffs with MkDocs, so I wanted to learn something different that would not remind me of work outside of work haha...

By using Hugo and a theme that fit the aesthetic I was going for I quickly built out this subjectively good looking site that is easy to publish and update. Sometimes it helps to be a little bit picky and evaluate all of your options before committing entirely since it took me quite some time to land on [Hugo](https://gohugo.io/).

During this refresh I also took a stroll down memory lane and reflected upon my older revisions and it really put things in perspective.

## My old React portfolio:
### 2020-09-02:2021-05-30

<img src='/react-portfolio.png' alt='old react porfolio'>
<br>
For this version, the site relied on creating a whole new JavaScript file with a non-intuitive function definition which returned some HTML which we all <em>love</em> manually editing for blog posts.
<br>
<br>
Logos were also just sourced directly from URLs which can change or get removed resulting in some unprofessional looking alternative text being displayed where the logo was supposed to live. Taught me an important lesson about saving images into an <code>/assets</code> directory or equivalent.
<br>
<br>
During job hunting season, I often felt like the website did not really reflect my skills and I eventually removed it from my resume.

---

## Flash Card App:
### 2020-09-21:2021-10-07

<img src='/loading-page.gif' alt='infinite loading of dead heroku app asset' />
<!-- hey, yeah, i did actually try doing this with a video tag but it wasn't playing nicely so now you get to suffer too -->
<br>
RIP Heroku's free tier. I hosted a lot of sites on there for various projects including my first flash-card application which I used to study programming terminology fresh out of bootcamp. The Vue page still works, however the backend written in Java that was hosted on Heroku has perished decimating my flash-card decks. A truly regrettable loss to society.
<br>
<br>
In all seriousness I still kinda like the Vue page for the raw utilitarian vibes it had. Brings back some good memories of staying up till the wee hours of the night hacking, well I guess kinda like I am doing literally right now...

---

## My First Web App:
### 2019-\?\?-\?\?:2020-??-\?\?

<img src='/ancient.png' alt='ancient beautiful raw html' />
<br>
When I was just getting started with web development, I was really encouraged by my friend to whip up my own website following <a href="https://www.freecodecamp.org/">freeCodeCamp</a>'s guides. I made an amount of progress before enrolling in Tech Elevator.

<br>
<br>
Most regrettably, I overwrote the Git history if memory serves. I might have an old copy of it on a hard drive, but doubt it will turn on anymore.
<br>
<br>
<s>So I do not have a picture, <em>but</em> imagine a 90's era website and that should get you most of the way there.</s>
<br>
<br>
Found a screenshot of the beaut'.

## Technologies Used

{{< badge text="css" icon="css" >}}
{{< badge text="heroku" icon="heroku" >}}
{{< badge text="html" icon="html" >}}
{{< badge text="hugo" icon="hugo" >}}
{{< badge text="java" icon="java" >}}
{{< badge text="javascript" icon="javascript" >}}
{{< badge text="markdown" icon="markdown" >}}
{{< badge text="postgres" icon="postgres" >}}
{{< badge text="react" icon="react" >}}
{{< badge text="vue" icon="vue" >}}
