---
layout: post
title: "Projects: Back to C"
microblog: false
audio: 
date: 2018-08-16 23:49:19 -0800
guid: http://owensd.micro.blog/2018/08/17/projects-back-to.html
---
One of the things I really enjoy doing in my space time is playing D&D. Now, I don't get a lot of time to do it, and when I do get to, I mostly play online. I've tried pretty much all of the tools out there from [Roll 20](http://roll20.net), [Fantasy Grounds](http://fantasygrounds.com), [D&D Beyond](http://dndbeyond.com), Discord, and combinations of all of the above.

The problem: none of them actually solve my needs.

This brings me to my current hobby project: an online game management tool. Now, the fundamental problem with Roll 20 and Fantasy Grounds is that they are relatively closed eco-systems; you really need to buy into (quite literally!) in order to make the most of it. Now, Fantasy Grounds is far more flexible and you can basically encode anything you want, it's a lot of time to do so.

So, that's where my project comes into play. I really like the premise around [D&D Beyond](http://dndbeyond.com), however, it's also a fairly closed ecosystem providing no APIs to interact with it. However, since D&D Beyond is mainly a D&D Book archive, I can work with that.

---

Now... the goals of the project are as follows:

  1. Create a system that works on macOS, iOS, and Windows. My players use varied systems and I need to support all three of those.
  2. Create an open ecosystem where there is a fluid flow of information coming into the app and going out of the app. If you love Ulysses or Scrivener for writing your campaigns, use it! The app is to help you run your table top session, not management everything else for you.
  3. High performance, low battery impact. A D&D session can be 3~5 hours long and I don't want people reaching for their chargers part way in or losing access to their character if they are on their laptop or iOS device, especially if we are at the table.
  4. A learning project for certain things that I just don't know too much about, such as low-level graphics frameworks.
  5. The foundation for other projects that I have that I'd like to work on... *secret projects*. 
  
One of the key features, if not the primary feature, is an interactive mapping environment. This is going to likely be a top-down view of a true 3D environment with dynamic lighting, character line-of-sight handling, and turn management tools (including things like measuring movement distances and area of effect areas templates).

---

This brings us to technology and language choices. Now, remember, this is going to be a truly cross-platform app. It also has the need of being run offline or over local-networks only.

The basic choices are:

  - web-technology based, such as Electron or Atom
  - game engine based, such as Unreal or Unit
  - using some type of cross-platform application layer
  - handmade, native app
  
For various reasons that I don't really want to fully go into here, an Electron-based app is out. High performance, low battery life, small footprint, full offline, and cross-platform make a solution like this challenging, especially for a 3D engine. Sure, WebGL is pretty good, and there is WASM, but ultimately, this is really an unproven technology for this type of application. Also, I'd need a different solution on mobile vs. desktop, which starts to complicate the picture as well.

Ok... so Unreal or Unity based? I haven't fully rejected this idea, but it would likely only be for the map rendering portion as the vast majority of the rest my content is going to be primary text-based UIs (character sheets, rule references, story content, etc...). Unity... I've played around with it in the past and it just didn't stick with me, so I'd use Unreal if I went this route. The question always is does this dependency warrant the design decisions and complexity? I'm not sure.

Cross-platform layer... no. 

A native app. Now, this brings the downside of having to re-build the UI layer for each support platform, and for a hobby and one-man-team, that kinda stinks. BUT! I think it's totally worth it. This choice also brings with it full control over all aspects of the project and how it is shaped. There's a lot to be said about this. 

---

Language choices: really, there is only really one option that brings straight-forward interop between the various languages choices that may come up: C.

Rust requires bindings and unsafe code; this ends up being a good amount of work to accomplish.

C++ is C++. It's a very complex and large language. Interop with other languages can be problematic as well. 

Swift, well, it's simply not cross-platform and isn't going to meet my needs for a Windows install. So it's out by default.

C is the only language that brings to the table straight-forward interop with all of the platform UI languages (I'll likely use C# for Windows and ObjC or Swift for macOS and iOS). If I use Swift and I chose C++, I'd have to write a long of interop bindings between the two and that is just a waste of time.

So I'll be using C and the internet can collectively gasp at my choice. 😀
