---
layout: post
title: Using NuGet packages instead of direct reference
---

I worked on a task to review references on all projects of a product.
I saw many points to be improved and made alot of changes to make the code cleaner,
easier to maintain, having better architect by applying abstraction,
convert third-party dependencies to first-party...
This is not only a pure coding task but also it requires code review & analysis,
understanding on abstraction, architecture, design patterns and best practices.

##The situation

The product has a few solution files and each one contains from a few to dozens of projects.
There are different ways of referencing between project to project at different layers
and also project with external libraries.

###Internal project references
There are some project on Foundation layer, which has built and all dlls are copied to 
a folder "depedencies/internal". If needed, a project refnerences to the dll under this folder.

###External dependency references
Some libraries are copied to a folder "dependencies/external", a project will reference to the dll
under this folder. Some other dependencies will be referenced by using nuget packages.

