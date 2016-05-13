---
title:        "Xcode project anatomy"
# jekyll-seo-tag
# description:  "A short description of the page's content"
# image:        "http://placehold.it/400x200"
author:       "Zakaria Braksa"
---

## Project

Think of an Xcode project as a nice way to package few things together. Those things would be references to source files, targets, schemes and build configurations. 

### Targets

Targets are instructions to build one product, each target has : 

* Build Settings
* Build Phases
* Build Rules

### Why have multiple Targets ? 

First of all, each iOS Project comes with two targets by default, one for building the actual app, and the other for Tests. The reason we have two targets for the same project, is because each Target will use different source files to build the Product, one will use the classes we wrote to implement the app functionalities, while the other target will use for example, the classes we wrote to test the previous code.

So creating a target is a way to say hey I want to use only these particular source files or so. 

We may need more than the default targets if we plan on building a watchOS app for example, so we’ll be basically using different classes for that app, but it’s all in the same Project. 

### How to define different flavors of Targets ? 

Now sometimes when building a particular Target, we may want to build it in different ways or deactivate certain things, for example deactivate code optimization when debugging, we can achieve that by overriding the value in the Target’s Build Settings tab, but what if we want for the same Target to toggle quickly between two versions of Build Settings. 

Well say hello to Build Configurations, these are defined Project-wide since they can be applied to more than one Target at a time (via Schemes).

By default Xcode projects comes with two build configurations, the first is Debug and the second is Release.

And switching between these two will change values in the Target Build Settings. So if you go the Build Settings Tab you’ll find for each setting there you have the option to define a different value for each Build Configuration you have defined in your Project.

For example the **Debug** build configuration would deactivate code optimization, while in **Release** build configuration, code optimization will be usually activated !


### Schemes 

This is what ties everything together, by that I mean Actions, Targets and Build Configurations.
A scheme will specify for each action, what targets to include when running that action and also which build configuration to apply to those targets. 

Let’s suppose when debugging the app we wanna call a local API, but when archiving it, we want it to call the remote API, one way to do that, is create differnet Build configuration, and for each one define a different API URL, next we’ll go the scheme and for each action, Run vs Archive, we’ll select same Target, but choose different Build configurations that will be applied on that Target. 

So a Scheme is saying hey, for each action, select which targets to build, and which build configurations to the targets we just 

### Actions

These are the standards Build, Run, Profile, Analyze, Archive.

