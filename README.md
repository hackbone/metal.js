Wires Metal
===========

Classes, Mixins, Errors, and more.

[![Travis Status](http://img.shields.io/travis/marionette-wires/wires-metal/master.svg?style=flat&amp;label=travis)](https://travis-ci.org/marionette-wires/wires-metal) [![Code Climate Score](http://img.shields.io/codeclimate/github/marionette-wires/wires-metal.svg?style=flat)](https://codeclimate.com/github/marionette-wires/wires-metal) [![Coverage](http://img.shields.io/codeclimate/coverage/github/marionette-wires/wires-metal.svg?style=flat)](https://codeclimate.com/github/marionette-wires/wires-metal) [![Dependency Status](http://img.shields.io/david/marionette-wires/wires-metal.svg?style=flat)](https://david-dm.org/marionette-wires/wires-metal)

## Usage

### Classes

Classes are objects that you can instantiate with `new Class()`. You can also create a **subclass** from any existing class by calling its `extend()` method.

```js
import {Class} from 'wires-metal';

var MyClass = Class.extend({
  initialize(options) {
    console.log(`Created! ${options.greeting} ${options.subject}!`);
  }
});

var myClass = new MyClass({
  greeting: 'Hello',
  subject: 'World'
});
// >> Created! Hello World!
```

### Mixins

When working with multiple classes, sometimes you want to share functionality between them. You can easily do this by creating a new `Mixin` and adding it to all the classes that need it.

```js
import {Mixin, Class} from 'wires-metal';

var MyMixin = new Mixin({
  alert(message) {
    console.log(`Alert! ${message}`);
  }
});

var MyClass = Class.extend({
  initialize() {
    this.alert('You have successfully used a Mixin!');
  }
});

MyClass.mixin(MyMixin);

var myClass = new MyClass();
// >> Alert! You have successfully used a Mixin!
```

### Super

When working with subclasses, sometimes you want to modify one of the parent's methods and then calling the parent method inside. You can easily do this by calling `_super`.

```js
import {Class} from 'wires-metal';

var FirstClass = Class.extend({
  initialize() {
    console.log('First Class checking in!');
  }
});

var SecondClass = FirstClass.extend({
  initialize() {
    this._super();
    console.log('Second Class checking in!');
  }
});

var secondClass = new SecondClass();
// >> First Class checking in!
// >> Second Class checking in!
```

## Contibuting

### Getting Started

[Fork](https://help.github.com/articles/fork-a-repo/) and
[clone](http://git-scm.com/docs/git-clone) this repo.

```
git clone git@github.com:marionette-wires/wires-metal.git && cd wires-metal
```

Make sure [Node.js](http://nodejs.org/) and [npm](https://www.npmjs.org/) are
[installed](http://nodejs.org/download/).

```
npm install
```

### Running Tests

```
npm test
```

===

© 2014 James Kyle. Distributed under ISC license.
