---
layout: post
title: "The Peguta Honeypot"
date: 2014-12-23 20:18:37 -0500
comments: true
categories: [ security, honeypot, apache, password management ]
---
While searching for a way to enable LastPass to fill passwords for SSH sessions (yes - keys are better. I don't always get to use them, though) I ended up stumbling upon [this page](https://peguta.com/articles/lastpass-hacked).

It goes on and on about how secure they are and how much better they are and even goes on to use some vague buzzwords. So I ended up curious as to who these guys are, having never heard of them (orange flag). I Google'd their name and what I found was... just not really good.

Basically no results outside of their site. Red flag 1.

There appears to be no discernible business model anywhere. It simply lists a bunch of features and all the great things you can do "for free" with nary a mention of an upsell or a premium plan or some kind of enterprise thing. Red flag 2.

<!-- more -->

Finally I spotted one of my favourite sites in the search results. I am anything but a pen-tester and I'm not really involved directly in netsec (sysadmin is more my trade). The site basically automatically tells you a basic guess as to what a site is running - webserver, web framework, software like WordPress etc. They don't need free advertising so I won't name them; it's not hard to find similar services.

What they revealed was a veritable mess of things I would not expect from any serious company.

They are running Apache. Their SSL cert is from StartSSL. Their DNS is registered through GoDaddy.

A single one of these things is excusable. Two might be forgivable. Three is simply not something you would ever see from a reputable technology company. You don't build a platform that's actually as robust as they're claiming and trust Apache or GoDaddy. Red flag 3.

Poking around a little more, I found that their "terms" link is dead - https://peguta.com/terms - red flags 4, 5 and 6. Finally, after creating a throwaway email account and signing up, I was greeted with this:

{% img http://i7.minus.com/iQiq405sKeXP5.png %}

Anyways, that's my rant. Thoughts?

PS: No, there's nothing wrong with Apache. It just isn't fast without tweaking, and other webservers will run circles around it out of the box - so very few people actually bother tweaking it. Yes, I know people often stick Apache in front of Ruby apps and other shiny stuff. But eventually they get big enough that they need to start using nginx to feed those apache workers - at which point most companies make the sane decision and just drop apache, switching to an nginx + app stack.
