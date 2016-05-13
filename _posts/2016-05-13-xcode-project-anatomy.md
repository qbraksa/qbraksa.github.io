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

First of all, each iOS Project comes with two targets by default, one for building the actual app, and the other for running the Tests. The reason we have two targets for the same project, is because each Target will use different source files to build the end *Product*, one will use the classes we wrote to implement the app functionalities, while the other target will use for example, the classes we wrote to test the code previously implemented.

So creating a target is a way to say "hey Xcode, to build Product X, use just these few files". 

We may need more than the default targets if we plan on building a watchOS app for example, since we'll defintely be using different classes for that app that won't belong to the iOS app for example.

### How to define different flavors of Targets ? 

Now sometimes when building a particular *Target*, we may want to build it in a different way or deactivate certain things, for example deactivate c*ode optimization* when debugging. We can achieve that by overriding the value in the *Target*’s **Build Settings** tab, but what if we want for the same *Target* to toggle quickly between two variations of **Build Settings**. 

Well that's where **Build configurations** comes in, these are defined Project-wide since they can be applied to more than one *Target* at a time (through Schemes).

By default Xcode projects comes with two build configurations by default, the first is **Debug** and the second is **Release**.

Switching between these two will change values in the *Target*'s **Build Settings**. So if you go the **Build Settings** Tab you’ll find for each setting you usually have the option to define a different value for each *Build Configuration* type currently in your project.

For example for the **Debug** build configuration you would deactivate code optimization, while in **Release** build configuration, code optimization will be usually activated by default.


### Schemes 

This is what ties everything together and by everything I mean *Actions*, *Targets* and *Build configurations*.

A scheme will specify for each *Action*, which targets to produce when running that action and also which build configuration to apply to those targets. 

Let’s suppose when debugging the app we wanna call a the development version of an API endpoint, but when archiving it, we want it to call the staging or production API. 

In my opinion the best way to achieve that, is to create different *Build configuration* for each environment (e.g development, staging, production), and for each environment you would define a different API base URL.

Next you’ll have to generate a new scheme for each environment and also make sure that for each action you specify which *Build configuration* to use.

So a Scheme is saying hey Xcode, when I invoke *Action X* please produce *Target X* and *Target Y*, but also make sure to apply the following *build configurations* which may contain different API base URL for example. 

Actions are by the way the standard *Build*, *Run*, *Profile*, *Analyze*, *Archive* that you've seen a billion times by now.

