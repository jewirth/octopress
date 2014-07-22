---
layout: post
title: "Swift announced"
date: 2014-06-03 20:00:00 +0200
comments: true
categories: ["Programming", "Swift"]

---

At Apple’s WWDC on Monday, 2nd June, 2014, Craig Federighi announced a new programming language called Swift. The main focus shall be:
<ul>
<li>Fast</li>
<li>Modern</li>
<li>Safe</li>
<li>Interactive</li>
</ul>

Especially the last point was emphasized as “a level of interactivity in development that you’ve never seen on a platform“. Federighi announced Swift as faster:

Complex object:
<ul>
<li>Swift:   3.9x</li>
<li>Objective-C:  2.8x</li>
<li>Python:   1x</li>
</ul>

RC4 encryption:
<ul>
<li>Swift:   220x</li>
<li>Objective-C:  127x</li>
<li>Python:   1x</li>
</ul>

But actually, Federighi did not compare Swift against Objective-C. Instead, he compared Swift and Objective-C with reference to Python. Thus, giving extrem high values. One could say, he compares apples to oranges since Python is run by an interpreter while Swift is compiled to native code. Also, Swift and Objective-C are used in totally different domains than Python. I don’t think that anyone will ever use Swift where Python has been used before. Otherwise, drop me a line and I will update this article.

The benchmark for Swift with reference to Objective-C would be this:
<ul>
<li>Complex object sort: 139% the speed of Objective-C</li>
<li>RC4 encryption:  173% the speed of Objective-C</li>
</ul>

However, at the end it’s all processor instructions and we don’t know how the performed benchmarks were implemented and optimized. Since Federighi just said faster without explicitly mentioning runtime, maybe the speed comparison was meant about the typing of source code. In that unlikely event, I really wonder who wrote the Python code.

The really interesting fact seems that Swift combines two great things:
1. The speed of native code, like Objective-C.
2. The functionality and ease of a modern high-level language like Python.

So, what’s the catch? Anyone?