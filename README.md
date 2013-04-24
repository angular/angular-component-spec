# Specification for reusable AngularJS components

_**Attention**: This document is a **WIP**! Since we want to collect as many opinions as possible, feel free to fork and send a Pull Request, or leave a comment on the [kick-off disussion](https://gist.github.com/PascalPrecht/5411171). We hope that once this specification is called final, developers of angular components will do things the same way, which will allow the Angular Team to provide better tooling._

### Preface
This specification should help you as a developer, as well as a consumer of angular components, to find, use and develop reusable angular components for the [Bower Package Manager](http://bower.io). It covers to parts:

1. The **consumer** perspective
2. The **creator/forker** perspective

The consumer perspective covers all topics on finding and using angular components, whereas the creator or forker part gives an in-depth description of how to create, structure and publish an angular component, as well as which naming conventions to follow for the component itself and the resulting bower package.

### Dependecies

This specification also expects that needed tools are already installed and ready to use. Which means the following commands should be used to install the needed tools on a local machine:

**Node Package Manager**

Visit [https://nodejs.org/download/](https://nodejs.org/download)

**Bower Package Manager**
```
$ npm install -g bower
```

### Definitions in this specification

This specification contains expressions like _modules_, _components_ and _packages_. These are the definitions:

#### Package
_Package_ is a Bower concept. For the time being,  one can think of the terms _package_ and _component_ as being interchangeable in the context of Bower. In general, _package_ is the thing that you can download, and contains a _component_, which is a group of one or more assets. Saying one can think of them as interchangeable for now, is because there's a one-to-one correspondence of package to component.

#### Component
_Component_ is a Bower concept. A _component_ is a repo which contains some files for client-side use in a web browser. This may include, but is not limited to, JavaScript, CSS, HTML, and images. A Bower _component_ has a component.json (or bower.json) file that describes the _component_ and its dependencies.

#### Module
When the word _module_ appears, this specification means an AngularJS module. An AngularJS Module may have multiple directives, services, or filters. For _components_, each _module_ typically has its own file. Bower _components_ typically contain just one AngularJS _module_, though in theory there can be more.

## AngularJS Components Consumer

_This part of the **Reusable AngularJS components** specification is highly inspired by @btford 's [blog post](http://briantford.com/blog/angular-bower.html)._ 

### Table Of Contents

* [Searching and Finding](#searching-and-finding)
    * [Search for packages](#search-for-packages)
    * [Finding packages with keywords](#finding-packages-with-keywords)
* [Installing packages](#installing-packages)
    * [Installing unregistered packages](#installing-unregistered-packages)

### Searching and Finding

#### Search for packages
Since registered angular components should follow a **naming convention**, finding them can be achieved by simply searching for all registered Bower packages which have an _angular_ in their registry name.

````
$ bower search angular
````
Should return a list of registered bower packages with an _angular_ in their name.

#### Finding packages with keywords
Bower doesn't currently support a search with keywords. Filtering packages by keyboard can be done by using <code>bower search</code> in combination with the <code>grep</code> command. So the following command searches for angular packages with the keyword "phonegap".

````
$ bower search angular | grep "phonegap"
````

### Installing packages
Once the right package is found, one can install it using the Bower <code>install</code> command. E.g. installing AngularJS itself as a package would look like this:

````
$ bower install angular
````

This will download the specified package into the folder which is configured as components folder via <code>.bowerrc</code>.

#### Installing unregistered packages
It is possible that there's an AngularJS component on GitHub, which is not registered as bower component. This could have several reasons:

* The author doesn't plan to publish it as a bower component
* The name the author wants to register it is already been taken
* The package is actually registered but the endpoint is broken (which unfortunately happens a lot of times, and there's currently no way to take care of that as a package maintainer. See [https://github.com/twitter/bower/issues/120](https://github.com/twitter/bower/issues/120)

In that cases one can install the package by specifying the GitHub user and the repository. This works for **every** GitHub repository.

````
$ bower install <username>/<repository>
````


## AngularJS Components Creator
