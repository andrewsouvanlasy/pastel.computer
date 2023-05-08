---
title: What is an API?
date: 2022-08-21
description: Using a toaster as an example.
cover: /img/toaster.webp
---

API stands for Application Programming Interface.

An API gives you a specific way to interact with something, an _interface_ if you will. You don't care how it works under the hood, you just want to make use of it.

Let's use a toaster as an example. All you need to do is insert bread and call the `Toast()` function through the button. The button sends the electrical signal and heats the bread, but that's all hidden from you. In a moment's time, you'll have toast!

In fancy programming terms, the concept of hiding details is called **abstraction**. ToasterAPI exposes the `Toast()` function to the user while hiding the implementation.

In the real world, there are all sorts of APIs available, such as:

- Google Maps
- Twitter
- OpenSky Network (flight tracking)

My favorite use of an API actually combines the three APIs I listed. ~~[@ElonJet](https://twitter.com/ElonJet) is a Twitter bot which tracks Elon Musk's private jet (it's 100% legal btw)~~ sadly this has been suspended 😿.
