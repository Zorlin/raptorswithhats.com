---
layout: post
title: Exploring LibreNMS
---

Tonight I'm going to have a look at LibreNMS. It's a network monitoring, managing and auditing tool that looks quite interesting and is slowly building up a community.

I'm going to run it on Claudio, which may get crowded - it already hosts this blog, a private Snipe-IT instance, and hopefully LibreNMS + NetBox.

netbox is awesome - I'm hoping to set it up for personal use and document my cloud servers and Wings Lab, but more on that in some other post.

I'm not sure where LibreNMS ends and netbox begins in terms of functionality. I know there will be some overlap.

My primary interests in LibreNMS are:
* Discovering and monitoring websites
* General service and network monitoring
* Keeping track of needed package updates
* General auditing

Looks like there's a [guide for Ubuntu 16.04](https://docs.librenms.org/#Installation/Installation-Ubuntu-1604-Nginx/) - score.

It wants to install to /opt/librenms, but my preference is to install to /var/www/librenms, so I'll have to disobey some of the instructions. It's possible /opt would be a better location, but I've already got Snipe-IT running from /var/www/ so it seems wise to keep things consistent.

Additionally, it's unclear whether I need to disable strict mode on MariaDB. I went ahead and set lower_case_table_names=0 in its own conf.d file, but skipped unsetting strict mode. I expect any issues with this setup will become very apparent very quickly.

Actually, it looks like [this page](https://community.centminmod.com/threads/check-mysql-strict-mode.9489/) indicates strict mode is NOT enabled. Handy.

It looks like it wants php7.0 - will be using Ondrej Surys PPA to provide that. I'd actually prefer php7.1 but don't feel like being a guinea-pig.

I'll go ahead and install the required packages. Some of them I'd prefer to install manually (Composer especially) but it should be fairly harmless to go with their recommendations.

Now onto nginx... and again, the guide is being a bit silly. This is a PHP application, there's no reason for it to be defined in /etc/nginx/conf.d in my opinion. I'll put it in /etc/nginx/sites-available instead.

At this stage I had to create a DNS entry.
