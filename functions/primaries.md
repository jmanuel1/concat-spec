---
layout: default
title: Primaries
prev: Atoms
prev_url: atoms.html
---

{{ page.title }}
================

Primaries are borrowed from Python 3, but with some differences.

An [attribute reference][attrref] in the form `"." identifier` pops the topmost
object on the stack and pushes that
attribute of the object.

An expression enclosed in brackets (`"[" expression "]"`) is a
[subscription][subscription]. The stack effect is
`subscriptable index -- \subscriptable[index]\`.

A slice list enclosed in brackets (`"[" slice_list "]"`) is a [slicing][slice]
on the topmost object on the stack. Conversion of the slice list is as in
Python, resulting in a slice object or tuple of slice objects. The stack effect
is `sliceable slice_obj -- \sliceable[slice_obj]\`.

If a slicing can be interpreted as a subscription, then it is.

Complete Syntax
---------------

    primary ::= atom | attributeref | subscription | slicing
        attributeref ::= "." identifier
        subscription ::= "[" expression "]"
        slicing      ::= "[" slice_list "]"
            slice_list   ::= slice_item ("," slice_item)* [","]
            slice_item   ::= expression | proper_slice
            proper_slice ::= [expression] ":" [expression] [ ":" [expression] ]

  [attrref]: https://docs.python.org/3/reference/expressions.html#attribute-references
  [slice]:   https://docs.python.org/3/reference/expressions.html#slicings
  [subscription]: https://docs.python.org/3/reference/expressions.html#subscriptions
