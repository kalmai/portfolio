+++
author = "Zachary Kolker"
title = "Major, Minor, Many Updates"
date = "2026-02-04"
description = "Rails and Neovim and Rust, oh my!"
+++

<link rel="stylesheet" href="/reactive_image.css" />

As a wise bug once said,
<blockquote>"Change... is good" <a href="javascript:(audio=>{audio.volume=0.6;audio.play()})(new Audio('/portfolio/change-is-good.oga'))"><i title="kha'zix saying change is good" class="fa-solid fa-play"></i></a>

-- <cite>Kha'Zix</cite>
</blockquote>

<!--more-->

## Deal Notifier

Post achieving MVP for my side project, code-named the [lemming](https://lemming-trusty-dane.ngrok-free.app/), my understanding of the project and the goals had grown. I knew I needed to start addressing some of the pain points and bugs that had accumulated since setting up my productionesque environment.

Game day promotions change from year to year. Until I automate updating them, I needed an easier way to maintain supported promotions and not have to create a database migration every time I wanted to change wording, etc. This led to the creation of my [upsert lib](https://github.com/kalmai/rails-deal-notifier/pull/45). Honestly the hardest part was figuring out how to format my YAML file to be easyish to parse.

Emails being sent out too often or not at all was also a bug that I enjoyed squashing. In the code, I was evaluating promotions in two different ways which led to some odd behavior. Once more, the [KISS principle](https://en.wikipedia.org/wiki/KISS_principle) helped me simplify my application to promote forward progress and other bug squashing.

More recently, when the new year rolled around, there were no games being stored in the database. This is a problem because we need games to evaluate whether we can get free stuff, and also this was a bug with the way I was evaluating whether a league was in season or not. When the project began, I was more afraid of hitting public APIs than I am now and only wanted to make requests when a league is in season. The way I calculated the range was error-prone, well more like only working in the later half of the year prone. Since I was already hitting public APIs for data every day anyways, I realized I could just check whether or not a league was in season if there were games stored in the database. At first I was having a hard time coming up with a nice ActiveRecord query to grab all of the leagues that were in season. Turns out I was overthinking it and a simple but powerful `group by` clause solved my problem.

Something I have been working on recently has been adding a way for users to have more control over their notifications since my wife does not like me eating pizza very often, and especially not [Jet's Pizza](https://www.jetspizza.com/), I do not want to be reminded of their mouthwatering heart attacks. Free pizza aside, I have had [this testdouble](https://testdouble.com/insights/building-passwordless-email-auth-in-rails) bookmark saved for quite some time and figured this would be the perfect opportunity to try implementing login and per user control. As I was implementing it, I began tunnel visioning on `SecureRandom.urlsafe_base64 => "rM4B8Q_sGFG2nsKI0SZ8Jw"` and thinking "man, that token is way too short and if I'm gonna need a expiration timestamp anyways maybe UUID7 would work?". Finding [UUID7](https://en.wikipedia.org/wiki/Universally_unique_identifier) information was not actually that bad, but figuring out how to parse out the timestamp was a challenge at the time. Referring to [this blog post](https://park.is/blog_posts/20240803_extracting_timestamp_from_uuid_v7/) I was able to figure out how to parse the timestamp out of a UUID7 string, albeit through copying and pasting into my browser console and scratching my head. With the following code you can easily grab the timestamp even though for the ultimate purposes of adding authentication to my application, it is wholly inefficient to do some string processing versus a direct comparison to a timestamp, I really just wanted to share I guess haha...

```ruby
uuid_7 = SecureRandom.uuid_v7
encoded_uuid_7 = Base64.urlsafe_encode64(uuid_7)
# can decode with Base64.decode64(encoded_uuid_7)

hexidecimal_unix_timestamp = uuid_7[0..12].gsub('-', '')
millisecond_decimal_unix_timestamp = Integer(hexidecimal_unix_timestamp, 16)
decimal_unix_timestamp = millisecond_decimal_unix_timestamp / 1000
time = Time.at(decimal_unix_timestamp)
```

All of this work to realize that we had only increased our token count by 26 characters, a whopping 118.18% increase!

## Lazification of my Neovim

Being a Neovim user for many years, I had always been aware that there was another way to manage plugins being [lazy.nvim](https://lazy.folke.io/) versus [vim-plug](https://github.com/junegunn/vim-plug). Perhaps the name or thinking my setup at the time was fine, I never really made the transition in spite of most plugin maintainers seeming to prefer `lazy.nvim`. After discussing it with a close friend of mine, I figured I would give it a go. Honestly, the first few days trying to figure it out absolutely sucked. This was because [LazyVim](https://www.lazyvim.org/) and [lazy.nvim](https://lazy.folke.io/) are two completely different things in spite of the extremely similar names...

Anyways, upon making this groundbreaking discovery, progress was actually surprisingly quick and intuitive. I initially tried to outsource my understanding to a LLM, but as per usual the attempt was pathetic and a waste of time. I did cherry pick some features I liked from mistakenly installing `LazyVim` more times than I would like to admit such as smooth scrolling and an animation to indicate the scope you are in. I also hated previously looking up method documentation in my browser when modern [LSP](https://en.wikipedia.org/wiki/Language_Server_Protocol)s come with it which led me to installing a completion engine.

Overall, I am glad that I made the transition since my previous Neovim configuration often read like a foreign language when trying to make any adjustments. If you want to give a vim-like editor a go, I would suggest [LazyVim](https://www.lazyvim.org/), [Helix](https://helix-editor.com/), or even [yours truly's dope new config](https://github.com/kalmai/dotfiles/tree/gnome-linux-lazy).

## Becoming Rusty

!['happy ferris the rust mascot'](/rustacean-flat-happy.svg)
Last year I made a new years resolution to spin up a productionesque environment for my [deal notifier](https://lemming-trusty-dane.ngrok-free.app/) application. This year I wanted to focus more on going back to basics, specifically learning a new programming language, [Rust](https://rust-lang.org/). For some reason these technical near years resolutions are easier to achieve than physical ones...

In my current role, I find myself writing a lot of [Ruby](https://www.ruby-lang.org/en/). I love writing ruby, but often I find myself thinking "what was the right method to do this again?" instead of actually how to implement the algorithm that is necessary. As nice as the abstractions and built-in enumerables are that Ruby provides, I want to brush off the low-level wizard hat I used to wear. This is not the first time I have attempted to learn Rust, I made the mistake of purchasing [The Rust Programming Language](https://a.co/d/05fFv7C1) book and made some progress. However, after picking this goal up once more I did some more reading and discovered that you can just execute `rustup doc --book` (assuming [rustup](https://rust-lang.org/tools/install/) has been installed) and the exact book I purchased will show up in the browser for free, but the most current version of Rust, not the 2018 version from all those years ago...

I was considering learning [Crystal](https://crystal-lang.org/) and migrating my current side project back to the [OG repository](https://github.com/kalmai/sports-deal-notifier), well more like [this one](https://github.com/kalmai/amber-deal-notifer) since I had learned toward the end of my journey of writing pure Crystal that there was a Rails-like alternative. However, Rust seems to have more marketability than Crystal sadly, but least I will not sound crazy saying that "I write Crystal" since many do not seem to know it exists.

## Technologies Used

{{< badge text="rails" icon="rails" >}}
{{< badge text="lua" icon="lua" >}}
{{< badge text="rust" icon="rust" >}}
