##What's this

A very basic Library object that is meant to store *things*. All it does is you can put stuff into it, or get stuff from it. I use it as a base object for more specific libraries that store specific types of things, so they can have more specific methods.

##Requirements

Defined in a [Require.js](http://requirejs.org/) format, so you need an AMD loader.

##Usage

###Creating a new library

```javascript
var lib = new Library();
//or you can pass initial library contents:
var lib2 = new Library([ { name: 'a' }, { name: 'b' } ]);
```

###Retrieving items

```javascript
lib2.getItem('a'); //{ name: 'a' }
```

###Adding items

When you add an item, you can specify the key as the second parameter, but it is optional. 

```javascript
lib.addItem({ x: 2 }, 'key1');
lib.getItem('key1'); //{ x: 2 }
```

If not given, Library will attempt to read the key from the property of item specified in `Library.nameProperty`. The default setting is `'name'`. See the following example:

```javascript
lib.addItem({ name: 'xy' });
lib.getItem('xy'); //{ name: 'xy' }

lib.nameProperty = 'whatever';
lib.addItem({ whatever: 'fos' });
lib.getItem('fos'); //{ whatever: 'fos' }
```

In this basic implementation `addItem` will simply overwrite data for a key that already exists.

You can also add a whole bunch of items at once with `addItems`, but in this case the key will be read automatically, you cannot specify it.

```javascript
lib.addItems([{ name: 'a2' }, { name: 'a3' }, { name: 'a4' }]);
lib.getItem('a3'); //{ name: 'a3' }
```

###Checking if key exists

```javascript
lib.exists('fos'); //true (we just added it in the previous example :))
```

###Documentation

All the methods are documented with [JSDoc3](https://github.com/jsdoc3/jsdoc), you can find the generated HTML documentation in the **docs** folder.