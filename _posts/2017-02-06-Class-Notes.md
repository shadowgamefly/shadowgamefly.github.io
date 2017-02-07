---
layout: post
title: 02/07/2017 class notes
description: "random course notes"
modified: 2017-02-01
tags: [ISA, notes]
---

## Internet Scale Application : Databases

### unordered list

1. Use cases
    1. Consistency Model : read after write consistency but doesn't worth to implement except in need, strict vs relax model
    2. Availability : if it needs to be able to Write/Read
    3. Performance requirement : Baesd on categories, each one kind has certaion performnrnce
    4. Security requirement: different security level for different types of data

2. Scales
    1. huge number of saved
    2. physical storage Technologies
    3. access patterns : reads actually read blocks
    4. physical limit : speed of light, determine information travel speed

3. Technologies

4. CAP Theorem : Consistency, Availability, Partitions(systems have communication time limit)
  1. usual solution: two layers, one with high Con, low Avail, and the other vise versa


  |         | Big           | Small  |
  | Read      | fast | slow |
  | Write     | fast | medium |
