---
title: Shuffle Words
layout: default
---


  [stack]: {{ site.url }}/stack.html
  [stash]: {{ site.url }}/stash.html

{{ page.title }}
================

**Shuffle words** exist to rearrange the top of the [stack][stack]. They should
be wrapped in the `concat ShuffleWord .` decorator.

    import concat
    
    # Factor's `over` shuffle word 
    @concat ShuffleWord .
    def over: concat stack . -4 []
    
    4 2 $print (concat stack . :-3 [] str) apply pop # [4, 2]
    over $print (concat stack . :-3 [] str) apply pop # [4, 2, 4]
    

`concat.ShuffleWord` Decorator
------------------------------

`concat.ShuffleWord` is implemented as a class, subclassing from
`collections abc . Callable .`
    
Default Shuffle Words
---------------------

These shuffle words are available to programs by default. Note that none of these
identifiers are reserved.

<table>
    <thead>
        <tr>
            <th>Shuffle Word</th>
            <th>Action</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td><code>swap</code></td>
            <td>same as <code>concat swap .</code></td>
        </tr>
        <tr>
            <td><code>dup</code></td>
            <td>same as <code>concat dup .</code></td>
        </tr>
        <tr>
            <td><code>pop</code></td>
            <td>same as <code>concat pop .</code>
            </td>
        </tr>
        <tr>
            <td><code>ident</code></td>
            <td>same as <code>concat ident .</code></td>
        </tr>
    </tbody>
</table>

Shuffle Words in `concat`
-------------------------

These are borrowed from Factor.

<table>
    <thead>
        <tr>
            <th>Shuffle Word</th>
            <th>Action</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td><code>concat pop .</code></td>
            <td>pops the topmost value off the stack (does <strong>not</strong>
                return a value)</td>
        <tr>
            <td><code>concat pop2 .</code></td>
            <td>same as <code>pop pop</code></td>
        </tr>
        <tr>
            <td><code>concat pop3 . </code></td>
            <td>same as <code>pop pop pop</code></td>
        </tr>
        <tr>
            <td><code>concat nip .</code></td>
            <td>remove the second topmost object from the stack (same as
                <code>swap pop</code>)
            </td>
        </tr>
        <tr>
            <td><code>concat dup .</code></td>
            <td>duplicate the topmost value on stack (same as
                <code>concat stack . -3 []</code>)
            </td>
        </tr>
        <tr>
            <td><code>concat nip2 .</code></td>
            <td>same as <code>concat nip . apply concat nip . apply</code>
            </td>
        </tr>
        <tr>
            <td><code>concat dup2 .</code></td>
            <td>duplicate the 2 topmost values on the stack (same as
                <code>concat over . apply concat over . apply</code>)
            </td>
        </tr>
        <tr>
            <td><code>concat dup3 .</code></td>
            <td>duplicate the 3 topmost values on the the stack (same as
                <code>concat pick . apply concat pick . apply concat pick . apply
                </code>)
            </td>
        </tr>
        <tr>
            <td><code>concat over .</code></td>
            <td>duplicate the second topmost object (same as
                <code>concat stack . -4 []</code>)
            </td>
        </tr>
        <tr>
            <td><code>concat over2 .</code></td>
            <td>duplicate the second and third topmost objects (same as
                <code>concat pick . apply concat pick . apply</code>)
            </td>
        </tr>
        <tr>
            <td><code>concat pick .</code></td>
            <td>duplicate the third topmost object on the stack (same as
                <code>concat stack . -5 []</code>)
            </td>
        </tr>
        <tr>
            <td><code>concat ident .</code></td>
            <td>do nothing</td>
        </tr>
    </tbody>
</table>