# Modularity workshop

**This is still a work in progress.**

This workshop should teach you how you can create your own modules.

The plan is to utilize existing guides and just link to them.

Before we start, feel free to look into [Stephen Gallagher's](https://github.com/sgallagher) blog posts on module packaging:
 * [Sausage Factory: An introduction to building modules in Fedora](https://sgallagh.wordpress.com/2017/05/30/sausage-factory-an-introduction-to-building-modules-in-fedora/)
 * [Sausage Factory: Advanced module building in Fedora](https://sgallagh.wordpress.com/2017/06/30/sausage-factory-advanced-module-building-in-fedora/)


## High-level agenda

1. [1-minute-intro to modularity](#1-minute-intro)
2. [modulemd](#modulemd)
3. [Workflow](#workflow)
4. [`mbs-build`](#mbs-build)
5. [Testing](#testing)
7. [Feedback](#we-need-your-feedback)
8. Beer


# The workshop


## 1-minute-intro

Modularity cuts Linux distributions into **modules**, giving them **independent lifecycles**, and making them available in **multiple streams**. Giving more options of choice to users, and flexibility and control to packagers.

<img src="/img/modularity-basics-1.png" width=600px>

See the **official [Fedora Modularity documentation](https://docs.pagure.org/modularity/)** for more information

## modulemd

Modules are defined in a [modulemd](https://pagure.io/modulemd) file.

As opposed to traditional distributions, where all packages are built and shipped in a single monolythic release, Modularity needs a mechanism of defining which package goes into what module. And that's modulemd.

Have a look at a real example of [nodejs module](http://pkgs.fedoraproject.org/cgit/modules/nodejs.git/tree/nodejs.yaml?h=f26).

## Workflow

All modules will use a [platform module](http://pkgs.fedoraproject.org/cgit/modules/platform.git/tree/platform.yaml) as a build and runtme dependency. Platform is the base system and common, shared userland.

To create a module, you need to define a **top-level package set** representing your module, and **resolve missing dependencies** between your package set and the platform module. A simple example:

<img src="/img/defining-modules-1-simple.png" width=600px>

### More complex module

Unfortunatelly, it's not easy every time. Many packages will have **complex dependencies**:

<img src="/img/defining-modules-2-complex-bad.png" width=600px>

As you might have guessed, **bundling all dependencies is not the right thing to do** in this example. Instead, we need to identify **other modules**, and use these as dependencies. Some packages might also become part of the platform module. 

<img src="/img/defining-modules-2-complex-good.png" width=600px>

At the **beginning of development of the F27 Server**, all of these modules will need to get indentified and built. However, when we are done with the initial set, packagers will be able to use what's already available which will make creating additional modules significantly easier.


[Guide](https://docs.pagure.org/modularity/development/building-modules.html)

 * guidelines (TODO)
 * [branching](https://fedoraproject.org/wiki/Changes/ArbitraryBranching#Current_status)
 * bootstrapping

### Modularity tools

[Link](https://pagure.io/modularity/modularity-tools)

```
$ mod-tools rpm2module nodejs npm
```


### Figuring out dependencies

[Link](https://github.com/fedora-modularity/depchase)


## `mbs-build`

[Link](https://pagure.io/fm-orchestrator/)

[Local builds](https://docs.pagure.org/modularity/development/building-modules/building-local.html)
[Infrastructure builds](https://docs.pagure.org/modularity/development/building-modules/building-infra.html)


## Testing

~~Modularity testing framework~~ [Meta test family](https://github.com/fedora-modularity/meta-test-family)

[MTF Guide](http://meta-test-family.readthedocs.io/en/latest/user_guide/index.html)


## We need your feedback!
