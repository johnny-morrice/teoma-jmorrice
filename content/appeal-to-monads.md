+++
date = "2016-03-08T14:59:01Z"
draft = false
title = "Appeal to Monads"
importance = "interest"
genre = ["prose", "rant"]
projects = []
+++

# Fallacy: An Appeal to Monads

*...In terms of the thought process behind how these structures are implemented I believe some similarities can be drawn, which does give me the impression that idea is not necessarily a bad one. In that same way that moving closer to the equator typically implies warmer weather.*  -- ["Monads" and the continuous spectrum of goodness proximity.](https://groups.google.com/d/msg/golang-nuts/FUQO1jMoG8E/yR84rmTAAAAJ)

The Appeal to Monads is a form of logical fallacy which creeps up in programmer discussions.  Typically, a programmer presents some data structure and claims it is *like* a Monad, and is therefore good.

## Form of fallacy

For some program, X, the following argument is made:

**Premise 1.** X is Y

**Premise 2.** Monads are Y

**Premise 3.** Monads are Good.

**Conclusion.** Therefore, X is Good.

## Premises 1 and 2: *X is Y* and *Monads are Y*

This is a formal way of saying "X is *like* a monad".  Y is (presumed to be) the set to which some or all monads belong.  For X also to be a member of Y, it must share some property with the Monad.

## Premise 3.  *Monads are good.*

Monads are a form of abstraction that requires parametric polymorphism.  If your language does not support parametric polymorphism, you won't get a monad.

Imagine using a monad in a language that allows arbitrary mutation of state.  Your monad tries to make some guarantee over its computation.  At some point, a call is made to external code.  Something happens which you were trying to prohibit.  What is the point?

Unless you write in a functional language that has:

* Parametric polymorphism
* Strict prohibition of side effects

There is little utility to be found using monads: in your case monads are **bad**.

## Conclusion.  *Therefore, X is good.*

Even if monads are good, your thing is not a monad.  Perhaps it is superficially *like* some type of monad.  But it does not follow that it will be good; it does not follow that it would be good for the same reason that the monad was good.

## A counter example.

Handling uranium with your ass is kinda like what happens at a nuclear power station.

<small>I mean, nuclear engineers use gloves and have a point to what they are doing, but never mind that.</small>

Nuclear power stations are legit.

Therefore, sticking uranium up your ass is legit.

Everyone agrees that nuclear power is legit, right?

## How to avoid making this mistake

* Use the existing idioms of your programming language instead of wrongly applying Haskell idioms to PHP/Assembler/Brainfuck.
* Refrain from writing enthusiastic blog posts concerning IT industry buzzwords.
* Learn Haskell, to understand the concept.
* Appreciate that some concepts are more powerful when they refer to a specific thing, instead of absorbing all possible similar and not-so-similar ideas.
* If you desperately want to use monads, *why not write your program in a language that supports them?*

## Examples in the wild

### PHP

*Because monadic error handling will certainly prevent your PHP code from breaking.*

[Taking Monads to OOP PHP]
(http://blog.ircmaxell.com/2013/07/taking-monads-to-oop-php.html)

Bonus: begins with *For now, let's not worry too much about what a Monad is.*

### Ruby

*If it looks like a duck, and walks like a duck, it's probably an ephemeral construct of category theory.*

[Refactoring Ruby with Monads](http://codon.com/refactoring-ruby-with-monads)

Because Pipelining makes Promises easy.  My pipelining code is *like* a Monad.  Monads are good...




