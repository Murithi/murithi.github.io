---
layout: post
title: "Module Pattern in Javascript"
date: 2017-10-16
author: Murithi M'Inoti
comments: true
---
Characteristics

1. Needs one outer enclosing function that runs at least once
- Almost always to have an outer enclosing scope
singleton module - only once 
module factory - runs more than once to be called more than once to create more than one instance

2. Needs to be atleast one internal function that has closure over the internal state. Inte