**IMPORTANT**: Since version 1.3.0, this is the main repository of Grease. Versions older than 1.1.9 can be found in the [Smalltalkhub repository](http://www.smalltalkhub.com/#!/~Seaside/Grease11). Check out the [releases list](https://github.com/SeasideSt/Grease/releases) for all version numbers in this repository.

The Grease Portability Library  [![Build Status](https://travis-ci.org/SeasideSt/Grease.svg?branch=master)](https://travis-ci.org/SeasideSt/Grease)
======
Grease enhances the ANSI Smalltalk standard. With only a few exceptions, we assume platforms are fully ANSI-compliant. Platforms want to support Seaside and standardization makes this easier for the project’s developers and its porters.

Grease defines expected APIs with unit tests. Platforms can quickly determine if they are compatible and users can examine the tests to determine exactly which behaviours they can count on.

Grease takes a pragmatic approach to compatibility. Sometimes a method behaves so differently on two platforms, for example, that we are forced to avoid it or to standardize on a new selector. To get standard exception signaling on all platforms, Grease is forced to provide special exception classes that can be subclassed. Sometimes we need to put “right” aside and settle, instead, on a solution that can be implemented everywhere.

Grease tries to be concise and consistent. Despite its pragmatic approach, we still want to be “right” as much as possible. Because it’s hard to remove functionality once it has been added, we need to carefully consider each addition before proceeding. We’re moving slowly and looking for methods that are commonly used and that have clear names and semantics.

Grease does not try to solve all problems. We are not testing Sockets or HTTP clients. We don’t expect platforms to have standard SSL or graphics libraries. Its scope may grow over time, but for now we’re focusing on extending the functionality of the core classes defined in the ANSI standard (collections, exceptions, streams, blocks, etc.) and on other pieces of functionality that are critical to the Seaside project (e.g. random number generation and secure hashing).

Grease is widely adopted. Implementations exist already for all platforms that support Seaside 3.x. As well as Seaside, new versions of Magritte, Pier, and Monticello are already being implemented on top of Grease.

## Travis builds

The [Travis CI builds](https://travis-ci.org/SeasideSt/Grease) currently test Grease for the following platforms and versions:

| Squeak          | Pharo            | GemStone             |
| --------------- | ---------------- | -------------------- |
| Squeak 5.1      | Pharo 6.0        | GemStone 3.3.4       |
|                 | Pharo 5.0        | GemStone 3.2.16      |
|                 | Pharo 4.0        | GemStone 3.1.0.6     |
|                 | Pharo 3.0        |                      |

## Installation

#### Prerequisite on Squeak and Pharo <3.0

Make sure you have the [MetacelloPreview version](https://github.com/dalehenrich/metacello-work), otherwise the load will not work.

### Squeak and Pharo >=3.0

Load the latest code from master (i.e. stable):

```Smalltalk
Metacello new
    baseline: 'Grease';
    githubUser: 'SeasideSt' project: 'Grease' commitish: 'master' path: 'repository';
    load
```
-or-

Load a specific version:

```Smalltalk
Metacello new
    baseline: 'Grease';
    githubUser: 'SeasideSt' project: 'Grease' commitish: 'v1.3.0' path: 'repository';
    load
```
-or-

Legacy: load from Smalltalkhub:
```Smalltalk
Metacello new
    configuration: 'Grease';
    repository: 'http://www.smalltalkhub.com/mc/Seaside/MetacelloConfigurations/main';
    version: '1.0.0';
    load
```

### GemStone

Grease is part of the GLASS setup. You can upgrade your version of Grease using [GsUpgrader](https://github.com/GsDevKit/gsUpgrader).
GsUpgrader works on all versions of GemStone against all versions of GLASS:

```Smalltalk
Gofer new
  package: 'GsUpgrader-Core';
  url: 'http://ss3.gemtalksystems.com/ss/gsUpgrader';
  load.
(Smalltalk at: #GsUpgrader) upgradeGrease.
```
