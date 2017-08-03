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

![modularity-basics](/img/modularity-basics-1.png)

See the **official [Fedora Modularity documentation](https://docs.pagure.org/modularity/)** for more information

## modulemd

Modules are defined in a [modulemd](https://pagure.io/modulemd) file.

As opposed to traditional distributions, where all packages are built and shipped in a single monolythic release, Modularity needs a mechanism of defining which package goes to which module. And that's modulemd.


### The specification

The modulemd file allows you to describe your module:
 * module description
 * licensing
 * build-time and runtime dependencies
 * module API
 * module components and artifacts

Modulemd is agnostic of packaging formats (at the same time, it's implemnted for RPM only now).

 * [the specification](https://pagure.io/modulemd/blob/master/f/spec.yaml)
 * [a real example](http://pkgs.fedoraproject.org/cgit/modules/nodejs.git/tree/nodejs.yaml?h=f26)
 * [list of existing modules](http://pkgs.fedoraproject.org/cgit/modules)
 * interesting modules:
   * platform module
     * TODO: link; platform should have builds available during first week of August, 2017
     * is still a work in-progress
   * base-runtime
   * shared-userspace
   * common-build-dependencies
   * common-build-dependencies-bootstrap
 * runtime dependencies
 * build-time dependencies
 * module components
 * filtering
 * API


## Workflow

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
