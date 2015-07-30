---
layout: post
title: Why should use NuGet for references
---

I worked on a task to review references on all projects of a product.
I saw many points to be improved and made alot of changes to make the code cleaner,
easier to maintain, having better architect by applying abstraction,
convert third-party dependencies to first-party...
This is not only a pure coding task but also it requires code review & analysis,
understanding on abstraction, architecture, design patterns and best practices.

##Current situation

The product has a few solution files and each one contains from a few to dozens of projects.
There are different ways of referencing between project to project at different layers
and also project with external libraries.

###Internal project references
There are some projects on Foundation layer and all dlls are copied to a folder
"depedencies/internal". If needed, a project refnerences to the dll under this folder.

###External dependency references
Some external libraries are copied to a folder "dependencies/external", a project will reference
to the dll under this folder. Some other dependencies will be referenced by using nuget packages.

###The issues
With these ways of managing dependencies, upgrade to a new version of any library is hard
(both internal & external), because dependency's version number is specified in target project.

![_config.yml]({{ site.baseurl }}/images/posts/project-reference-dll-with-version.png)

