---
layout: post
title: Matlab, 1 dimensional data in the 3rd dimension
date: 2018-09-20 14:26 +0100
categories: Engineering
tags:
 - matlab
---

Some times your data comes out of Matlab like:

    simout1.data(1:5)

    ans(:,:,1) =

         0


    ans(:,:,2) =

        0.3816


    ans(:,:,3) =

        0.7054

Just give it a `squeeze`  to bbring the data back to a single dimension.

    squeeze(simout1.data(1:5))

    ans =

             0
        0.3816
        0.7054
        0.9225
        1.0000
