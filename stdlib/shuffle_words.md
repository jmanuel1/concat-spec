---
title: Shuffle Words
layout: default
---


  [stack]: {{ site.github.url }}/stack.html
  [stash]: {{ site.github.url }}/stash.html

{{ page.title }}
================

**Shuffle words** exist to rearrange the top of the [stack][stack].

    # Factor's `over` shuffle word
    def over: stack[-3]

    4 2 stack[:-1] str print  # [4, 2]
    over stack[:-1] str print  # [4, 2, 4]

Default Shuffle Words
---------------------

These shuffle words are available to programs by default. Note that none of
these
identifiers are reserved.

| Shuffle Word | Action |
| --- | --- |
| `swap` | same as `$shufflewords.swap` |
| `dup` | same as `$shufflewords.dup` |
| `pop` | same as `$shufflewords.pop` |
| `ident` | same as `$shufflewords.ident` |
| `roll` | same as `$shufflewords.roll` |

Shuffle Words in `shufflewords`
-------------------------------

These are borrowed from Factor and Forth.
<!-- TODO: implement shufflewords -->

| Shuffle Word | Action |
| --- | --- |
| `roll` | Pops one argument *n*, then rotates the top *n* + 1 items on the stack so the the (*n* + 1)th topmost becomes the top. |
| `pop` | pops the topmost value off the stack (does **not** return a value) |
| `pop2` | same as `pop pop` |
| `pop3` | same as `pop pop pop` |
| `nip` | remove the second topmost object from the stack (same as `swap pop`) |
| `dup` | duplicate the topmost value on stack (same as `stack[-2]`) |
| `nip2` | same as `$shufflewords.nip $shufflewords.nip` |
| `dup2` | duplicate the 2 topmost values on the stack (same as `$shufflewords.over $shufflewords.over`) |
| `dup3` | duplicate the 3 topmost values on the the stack (same as `$shufflewords.pick $shufflewords.pick $shufflewords.pick`) |
| `over` | duplicate the second topmost object (same as `stack[-3]`) |
| `over2` | duplicate the second and third topmost objects (same as `$shufflewords.pick $shufflewords.pick`) |
| `pick` | duplicate the third topmost object on the stack (same as `stack[-4]`) |
| `ident` | do nothing |
