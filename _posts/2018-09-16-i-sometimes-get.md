---
layout: post
microblog: true
audio: 
date: 2018-09-15 17:50:51 -0800
guid: http://owensd.micro.blog/2018/09/16/i-sometimes-get.html
---
I sometimes get far too angry about programming annoyances. Latest example:

    private var session: URLSession? = nil

Simple, but no... I need to do this:

    private var session: URLSession?

    public init(session: URLSession? = nil) {
        self.session = session
    }
