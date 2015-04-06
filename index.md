---
title: Introduction
layout: default
prev: Table of Contents
prev_url: toc.html
---

{{ page.title }}
================

To This Document
----------------

This is the Concat programming language specification. To understand this
document, you need to understand the purpose of the different styles. This
paragraph is body text.

    Text that looks like this is code.
    
[This is a link to Google](http://www.google.com/).

<p class='implementation-detail'>
    This is a detail of the implementation the author plans to write, and not
    actually part of the language.
</p>

In the top right is a link to the table of contents. At the bottom are links to
the previous and next sections.

To This Language
----------------

Concat is a Python-based, concatenative, stack-based, point-free programming
language.

    'Hello from Concat' print
    
[Expressions][expressions] are postfix to match the concatenative style. There is a dedicated
negation operator `(-)` to remove the need for parentheses.

    b (-) b 2 ** 4 a * c * - sqrt + 2 a * / # (-b + sqrt(b**2-4*a*c))/(2*a)
    
But wait a second! There are no variable names. All objects exist on the stack
(except named functions). Here is the same example as a function with no variable
names.

    def quadratic_root:
        swap (-) dup 2 ** swap stash stash
        4 * preserve(*) unstash swap - sqrt unstash + swap pop
        swap 2 * /

What's with the lack of formal parameters? There are none - that's what makes
the language point-free. Instead of formal parameters, the stack is implicitly
passed (see [Function Calls][functioncalls]). Also, what's `swap`, `dup`,
`(un)stash`, `pop` and `preserve`? `preserve` is an
[inline decorator][inlinedecorators], and the others are
[stack modifiers][stackmodifiers].

The real power comes when composing functions...

    # Python's itertools recipes
    from itertools import *
    import collections
    
    def take: swap islice list
    def tabulate: count map
    def consume:
        if None is:
            pop
            @{maxlen: 0}collections.deque
        else:
            dup islice None next
        pop # get rid of None
    # ...
    
### Concat-Python Interop

<p class='implementation-detail'>
    The implementation I plan to write will translate directly into Python,
    meaning code from both languages should interop perfectly.
</p>

  [stackmodifiers]:    stack_modifiers.html
  [expressions]:       expressions.html
  [functioncalls]:     function_calls.html
  [inlinedecorators]:  inlinedecorators.html