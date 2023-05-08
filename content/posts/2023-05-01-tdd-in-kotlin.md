---
title: Demoing Test-driven Development with Exploding Watermelons
date: 2023-05-01
description: ✅ Works as intended.
cover: /img/tdd.webp
tags: [softwaretesting, kotlin]
toc: true
---

Let's learn about test-driven development using a silly Kotlin program that simulates shooting a Desert Eagle at a watermelon.

## What is software testing?

Software developers can make mistakes, and these mistakes can sometimes occur in unforeseen ways.

Suppose we have an input field for a number. What happens if you enter a normal number, a very small number, a very big number, or a negative number? There are many cases to consider to ensure that your code **works as intended**.

It’d be annoying to manually test your code each time by typing in different possible values. To remedy this, you could write a script for each test scenario, and then run that script whenever you want to test many cases and be more certain that your code works as intended.

## What is test-driven development?

Test-driven development (TDD) is when you write the test *before* writing the actual code.

You start off by explicitly stating “this is what I expect to happen in this scenario”. By doing this, you won’t lose sight of what you actually want to achieve when coding the implementation and will hopefully make less mistakes.

Many dev teams report significantly fewer defects and improvements in code quality when they follow this practice. It's better to deal with issues now than later.

## Demo

For demonstration purposes, I used a fun object to practice TDD with: the Desert Eagle handgun. Why? Because it's cool.

[The source code can be found on GitHub](https://github.com/DreStation/tdd-in-kotlin).

### The first test case

I start by defining what I want the gun to do when fired, and then create the test before writing the actual code.

```kotlin
@Test
fun `Fire once and have 6 rounds remaining`() {
    val de = DesertEagle() // Has 7 rounds in a mag
    de.fire(1) // Shoot 💥🔫
    assertEquals(6, de.rounds) // Ensure that there are 6 rounds left
}
```

This test will ❌ fail if I don't have 6 rounds left like I expected. It'll also fail because I haven't created the DesertEagle class or a `fire()` function yet.

To be honest, I did notice that my coding strategy changed since I had an idea of the end result beforehand. I believe it was an ✅ improvement to my code quality.

### Testing other cases

This simple `fire()` function has many possible cases, just from having one parameter for the amount of `triggerPulls`. The cases that I accounted for were:

- Fire all 7 rounds and have 0 rounds remaining
- Fire 7+ times and ensure rounds don't go below 0
- Ensure error occurs when inputting 0 or negative ints

For fun, I added a `isSafetyActive` variable to disallow firing if the safety is on and an accompanying test.

### Testing the system as a whole

When testing an application, it's important to not only test individual parts, but also the system as a whole. Think of it like testing multiple moving parts of a machine.

Our DesertEagle is lonely. Let's add a Watermelon for it to shoot!

What I want to happen is for a watermelon to be marked as "exploded" when it is shot.

So once again, I'll create the test before the real implementation, and go from there.

```kotlin
@Test
fun `Watermelon should explode when shot once`() {
    val de = DesertEagle()
    val wm = Watermelon()
    de.isSafetyActive = false

    de.fire(1, wm)
    assertTrue(wm.hasExploded)
}
```

This test will ❌ fail if `hasExploded` is false, opposite of what I expected.

For fun, I tested what would happen if I shot the watermelon a ridiculous amount of times.

```kotlin
@Test
fun `Watermelon should certainly explode when shot 2 bil+ times`() {
    val de = DesertEagle()
    val wm = Watermelon()
    de.isSafetyActive = false

    de.fire(Int.MAX_VALUE, wm) // The max value for an integer is 2,147,483,647
    assertTrue(wm.hasExploded)
}
```

## TLDR

Test-driven development involves writing tests before writing actual code, which helps developers stay focused on what they want to achieve and catch issues earlier.

If you're part of a dev team or working on anything mission-critical, you should use it!

It's also satisfying to see green check marks for 100% code coverage.