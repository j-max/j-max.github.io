---
layout: post
title: Classes for Organization
---
As I work my way through the [Flask Megatutorial](https://blog.miguelgrinberg.com), I realize I may have made a mistake about classes.  At work, I was fairly stubborn about using classes only when they depended on state.  I thought that if classes weren't intended to be used with state in mind, then they shouldn't be used.  Functions should be preferred.  I think I limited myself unnecessarily.  Grinberg uses a Config class to store variables.  He uses it as an organizational structure.  The class attributes might never change.  They have static state.  This just means classes are used for a different purpose: organization.  One can access the attributes easily, as they are all stored in the same object. 