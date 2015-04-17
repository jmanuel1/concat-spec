---
layout: default
title: Primaries
prev: Atoms
prev_url: atoms.html
---

{{ page.title }}
================

Primaries are borrowed from Python 3, but with some differences.

An [attribute reference][attrref] in the form `"." identifier` gets that
attribute of the topmost object on the stack.

A function list enclosed in brackets (`"[" function_list "]"`) is a
[subscription][subscription] on the topmost object on the stack.

A slice list enclosed in brackets (`"[" slice_list "]"`) is a [slicing][slice]
on the topmost object on the stack.

Complete Syntax
---------------

    primary ::= atom | attributeref | subscription | slicing
        attributeref ::= "." identifier
        subscription ::= "[" function_list "]"
        slicing      ::= "[" slice_list "]"
            slice_list   ::= slice_item ("," slice_item)* [","]
            slice_item   ::= function | proper_slice
            proper_slice ::= [function] ":" [function] [ ":" [function] ]

  [attrref]: https://docs.python.org/3/reference/expressions.html#attribute-references
  [slice]:   https://docs.python.org/3/reference/expressions.html#slicings
  [subscription]: https://docs.python.org/3/reference/expressions.html#subscriptions