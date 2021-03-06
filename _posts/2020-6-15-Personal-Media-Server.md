---
layout: post
title: Setting up a Personal Media Server in the Cloud
tags: plex sonarr jackett rclone jekyll blog github-page
---

One of my friends had recently told me they'd been watching movies on a [Plex](https://www.plex.tv/) server sitting in a friend’s apartment in Sydney. I’ve always liked the idea of running my own media server but I’ve steered clear in the past because of the noise and electricity use. Having an old laptop whirring away in the corner of my lounge room does not sound appealing to me.

I’ve been paying for a Digital Ocean droplet running Ubuntu which costs about $7AUD a month. It’s probably not the best or cheapest service but I’ve used it in the past so it was easy to jump right. I also bought a nice .xyz domain name through namecheap because why not, it was like $3AUD for the year.

I already use [Github Pages](https://blog.mikeclark.xyz/Jekyll-Now/) to host static sites. Originally the Droplet was only going to be used to host my Wordpress projects, but I figured I should probably do something more with it for the price I’m paying.

Which leads me to these great lists of self-hosted services and applications:

[https://github.com/awesome-selfhosted/awesome-selfhosted](https://github.com/awesome-selfhosted/awesome-selfhosted#video-streaming)

[https://github.com/n1trux/awesome-sysadmin](https://github.com/n1trux/awesome-sysadmin)

  

There are a lot of programs on here that I will end up tinkering with over the next few weeks, but at the moment a personal media server sounded like the best idea. Here’s what I ended up with:

  

- **Plex** - Streaming Platform
- **Sonarr** - Media Organizer and Auto Downloader
- **Transmission** - Torrent Client
- **Jackett** - Torrent Search Service linked to Pirate Bay and Isohunt
- **Google Drive** - Unlimited Storage

The cheapest Droplet tier service only has 20GB of storage, so I looked to **Google Drive** because of [this article](https://phandroid.com/2020/05/19/how-to-get-google-drive-unlimited-storage/) I came across recently about unlimited storage for cheap. I've recently started working as a Wordpress developer and have  my personal Drive account upgraded to Gsuite Business, so that works for me.

I already had Apache, phpmyadmin and I few other services running on the Droplet, so from there I want to stream media and **Plex** seemed like the way to go. I really don’t like that there’s essentially advertising for the Plex paid service within the app hosted on my server, but the technology and support are very robust.

And **Transmission** has a good rep for the torrent client. From there I needed a web interface for downloading and managing shows, and I came across **Sonarr** which is a great piece of software once it's all configured properly. You can enter shows and their download rules, and each episode is automatically downloaded for you; very user friendly.

**Jackett** is a service that connects torrent search engines with Sonarr, which I connected to The Pirate Bay and Isohunt. I would’ve just left it at Pirate Bay but it failed to find the first show I’d searched for, so I added Isohunt which I was surprised to find out is even still around. From there I added rclone to sync my downloads folder with Google Drive, and that's it.

There are still a few bits to finish off, like restarting the MySQL service if it unexpectedly stops, and running rclone automatically when torrents are completed, but for now it does the job pretty well.

The only current TV shows I’m watching at the moment are Survivor and Ru Paul’s Drag Race, and Drag Race is on Stan which I pay for, so all this work is really just to automatically download Survivor whenever the new season comes out.

But hey I downloaded a season of The Sopranos way quicker than I ever would have with my home NBN connection, so that's pretty cool ✌️.
