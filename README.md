# DIY Film Festival

aka

# Pirate Television

What if you could program your own film festival? Always been into pirate TV? The contents of this repository contain a lot of instructions to tie together (mostly) free services and a little website to give to an audience. The website will look like Twitch with a live video player and a groupchat.

The primary motivation to do this is due to Twitch lawyers whom appear to have decided it's time to enforce content policies again now that quarentine is over for most of us. The intended audience to set up a website like this are people who do not identify as "coders". There will be a requirement to modify some HTML, which isn't really code but might look a little unusual if you haven't seen it before. Don't worry, it's easy. Without further interruptions...

# HWG
 
This will require a minimum of five (5) different accounts on four services. So it's definitely some assembly required, thus the name DIY Film Festival.

1. [Github account](https://github.com/signup?ref_cta=Sign+up&ref_loc=header+logged+out&ref_page=%2F&source=header-home).
2. [Account on ok.ru](https://ok.ru/dk?st.cmd=anonymRegistrationEnterPhone). You don't even need an email address by default, just a phone number for an SMS verification. Feels shady but it's probably fine. 
3. [Account on restream.io](https://restream.io/signup). If you have a Google or Facebook account you can use one of those.
4. [restream.io's default](https://support.restream.io/en/articles/834809-connect-ok-ru-to-restream) ok.ru integration.
5. [Account with](https://minnit.chat/register?threesteps) minnit.chat

The good news is most of these are free. They are also easy to use.

## Hosting

This is where your website will live and where you can make changes to it. I recommend the free option but if you want to pay some money, there's a subscription option too.

### Github Pages (zero dollars)

Github is a platform used by software engineers to develop code collaboratively. It also can host websites, neat! Here's how to set one up. **jargon watch** *a repo* is what you are looking at right now. *forking a repo* is what you are about to do. It's a fancy way of making a copy with a reference back to the original.

1. [Create an account on Github](https://github.com/signup?ref_cta=Sign+up&ref_loc=header+logged+out&ref_page=%2F&source=header-home).
2. [Fork this repository](https://github.com/lazzarello/diy-film-festival/fork) by clicking the icon that says fork.
3. When you see a screen looking similar to this one again, click the little gear that says Settings.
5. In the left menu that says Code and automation, click Pages.
6. Under Source, from the pulldown select `main` and click Save.
7. After a moment there should be a link to a URL where you can view this website, like, right now.

[Read the docs for more info on how DNS in Pages works, if you're curious](https://docs.github.com/en/pages/quickstart)

### Add a custom domain name (optional)

1. Add a domain (more on this in the DNS chapter) through Settings => Pages => Add a domain
2. Type a domain where you can read and write records. Jump ahead to the DNS section if you don't know how to do this.
3. Follow the instructions on the screen to add the required records to your name host.
4. Click Verify. The warning that it may take 24 hours was not relevant for my first attempt. It took about 5 minutes.
 
[Read the docs for more info on how DNS in Pages works, if you're curious](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/about-custom-domains-and-github-pages)

### Squarespace (non-zero dollars)

Squarespace seems to be popular and advertises on broadcast television so there's a non-zero chance you've heard of it before. I haven't used it so can't be the best voice here. The website says it features [award winning templates](https://www.squarespace.com/websites/designer-templates) if you're into that kind of thing. Perhaps someone else can write up Squarespace docs.

## Video Streaming

This part can be a bit confusing but don't worry I hope it's all covered here.

### Audience delivery with ok.ru (zero dollars)

Ok dot ru is a Russian social network like Facebook. It has a live video streaming feature which doesn't seem to have any limits on how many users can view an embedded video. CathodeTV regurarly has > 100 viewers! Neat!

1. Create an account on ok.ru
2. Go to the [live broadcast section](https://ok.ru/video/myLives). It will be blank until you complete the next step. Keep it open because you'll need to get some information from it later.
3. When the next step is complete come back here and copy the URL from the video that is live. You'll only need the numerical ID, which will be at the end.
 
### Video proxy with Restream.io ( 4 hours a week for zero dollars )

Restream sits between OBS (the source) and the audience delivery. For a considerably higher amount of money, it can also do audience delivery. More on that later. It makes it easy to add a single stream key to OBS in a set-it-and-forget-it way. After that it will rebroadcast (restream, get it?!) to a multitude of other popular platforms like Twitch and Facebook. We're not concerned about these platforms, so we first head to russia, as described in the preceding chapter.

1. Create an [account on restream.io](https://restream.io/signup)
2. Add the stream key to OBS.
3. After creating an account on ok.ru from the previous chapter
4. Create a destination using the [default ok.ru template](https://support.restream.io/en/articles/834809-connect-ok-ru-to-restream).
5. Go back to OBS and click Start Streaming in the main window.

At this point you should have the stream flowing. The final step is to update your website to display this stream. *TODO: how does cathode get a persistent URL from restream to ok.ru?*

Edit the file named `index.html` in this repository so the link at the bottom where it says VIDEO STREAMING to match the numerical ID of the live broadcast on [ok.ru live page](https://ok.ru/video/myLives).

### Video encoding with OBS (free and open)

Default restream.io stream destination. Go to Settings => Output => Video Bitrate = 5000
Add VLC Video Source under Sources, add files to the playlist.
Move to the next chapter.

## Group Chat

Minnit chat embed name part...search for GROUPCHAT in the file `index.html` and modify it for the embed code provided from the chat service.

## DNS

It's very likely you're looking for a custom name. In case you aren't, the following is the default for Github Pages.

### Default Name (zero dollars)

If you don't care about a URL ending in github.io, you can keep the default from the tutorial. For example, the author's is http://lazzarello.github.io

Otherwise here's the process. It's not simple. follow along...

### Custom DNS with name dot com (variable pricing)

Depending on the name you which to register and if it's available, this runs about $15 a year.
Post the instructions from Github Pages for custom DNS.

## Shout outs to

* Spectacle Theater
* CathodeTV
* Fort90 at Wonderville
* Museum of Home Video
* Moviepass
* Miss Molly Rogers
* Unlimited Hangouts
* Piss Hospital
* Sicko Vision
* 
### Extra Credit

https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site
Create an "apex domain" at your DNS provider if you want a URL like example.com to go to the same place as stream.example.com.
Create the CNAME record to point to the Github Pages load balancer.
Click the Enable TLS thing to do the encryption we all deserve
