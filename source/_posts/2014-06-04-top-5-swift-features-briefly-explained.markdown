---
layout: post
title: "Top 5 Swift features briefly explained: Closures, Generics, Type inference, Multiple return types and Namespaces"
date: 2014-06-04 20:00:00 +0200
comments: true
categories: ["Programming", "Swift"]
---
When announcing Swift at the WWDC 2014 on Monday (see <a href="/blog/2014/06/03/swift-announced">Swift announced</a>), five features of the new language have been highlighted during the presentation:
<ul>
<li>Closures</li>
<li>Generics</li>
<li>Type inference</li>
<li>Multiple return types</li>
<li>Namespaces</li>
</ul><br />

<strong>Closures</strong><br />
Closures are functions that have access to all data that are in scope of where the closure has been created (e.g. local variables of the function that created the closure). If that data is out of scope for any other function - e.g. the creator of the closure is a function that already has returned - then the data is still alive because the closure set a reference to this data. Thus, the garbage collection won’t trash this data, even if it was a local variable inside a function that has returned. Of course, assuming there is any reference to the closure itself.
<ul>
<li>Closures are comparable to local classes in Java.</li>
<li>Closures are similar to blocks in Objective-C.</li>
</ul><br />

<strong>Generics</strong><br />
Generics allow program code to be independent from the data types by its variables. For example, a function that uses parameters as input data doesn’t have to know for what kind of data type it is written for. Basically, the function is simply generic for any type of data.
<ul>
<li>Generics are similar to Templates in C++.</li>
<li>Objective-C is a dynamically typed language. That means the compiler does’t always check for correct types. It’s the programmer’s duty. Generics make sense in strongly typed languages like Swift where the Compiler will warn about wrong types. Thus, it’s less error-prone during runtime.</li>
</ul><br />

<strong>Type inference</strong><br />
Type inference allows to omit the type of variables. Based on the expression, Swift concludes the type automatically. However, the programmer can explicitly specify the type.
<ul>
<li>Type inference seems identical as in Python.</li>
<li>Objective-C does not support type inference.</li>
</ul><br />

<strong>Multiple return types</strong><br />
A function’s return type can be a tuple with multiple values and types.
<ul>
<li>Usage of arrays, structs, lists, etc. can be used to achieve multiple return types in almost every language. Swift’s approach with tuples is comparable to returning tuples in Python.</li>
<li>Objective-C does not support tuples but structs or special container classes can be used for this purpose.</li>
</ul><br />

<strong>Namespaces</strong><br />
A Namespace allows to group together a bunch of identifiers which all belong to the same library, package or functionality in general. Thus, namespaces avoid naming collisions. Otherwise, modern software projects that include libraries from different developers and vendors would have a hard job to assure that no class name occurs twice within the project. Interestingly, I did not find the namespace feature in Swift. Even the documentation does not contain the word "namespace".
<ul>
<li>C++ use namespaces; Java calls them packages; Python organizes namespaces by modules.</li>
<li>Objective-C does not support namespaces. That is why the classes have prefixes in their filenames like NSString or UIButton. This is typical kind of workaround when namespaces are no available.</li>
</ul><br />
