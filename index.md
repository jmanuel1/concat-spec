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

```python
'Hello from Concat' print
# output: Hello from Concat
```

[Expressions][expressions] are postfix to match the concatenative style. There
is no negation operator: to do that use, `0 <num> -`.

    0 b - b 2 ** 4 a * c * - sqrt + 2 a * / # (-b + sqrt(b**2-4*a*c))/(2*a)

But wait a second! There are no variable names. All objects exist on the stack
(except named functions). Here is the same example as a function with no variable
names.

    def quadratic_root: # (a, b, c)
        swap 0 swap - dup 2 ** swap _r _r
        4 * dup2 * r_ swap - sqrt r_ + swap pop
        swap 2 * /

What's with the lack of formal parameters? There are none - that's what makes
the language point-free. Instead of formal parameters, the stack is implicitly
passed (see [Function Calls][functioncalls]). Also, what are `swap`, `dup`,
`r_`, `_r`, and `pop`? They are are [shuffle words][shufflewords].

The real power comes when composing functions...

    # TODO: get all examples to work
    # Python's itertools recipes
    from itertools import *  # mostly automatically turned into a concat interface
    import collections

    def take: swap islice list
    def tabulate: count map

    def consume:  # (iterator, n)
        if dup None is:
            pop
            0 collections.deque
        else:
            dup pick  # iterator n n iterator
            3 roll islice
            None next
        pop # get rid of None
    # ...

### Concat-Python Interop

<p class='implementation-detail'>
    The implementation I plan to write will translate directly into Python,
    meaning code from both languages should interop pretty well.
</p>

  [shufflewords]:      {{ site.url }}/stdlib/shuffle_words.html
  [expressions]:       expressions.html
  [functioncalls]:     function_calls.html
