# DEPRECATED
*ES2015 modules should be compiled into ES5 before they are used.*

--

# Import ES6 Modules
Import and use es6/es2015 modules directly without the need to pre-compile them.

**Previously:**
```js
import myES6Package from 'my-es6-module';
/* 
 * ---------------- ERROR: ----------------
 * This will throw an error because babel 
 * will not compile npm modules.
 * ----------------------------------------
*/
```

**With this package:**
```js
import myES6Package from 'my-es6-module';

// Start using the package with es6 code!
```

## Install
This module should be installed globally!   

> Note: This module is only tested with babel as precompiler! However other precompilers should work just fine.

## How to use
In order to use this you have to mark a npm package as an es6 package. You can do this by adding the field `es6Dependencies` to your projects `package.json` file.

Example:
> Format: "npm-package": "the-es6-start-file.js"

```json
{
    "name": "your-module",
    "es6Dependencies":{
        "the-npm-package":"main.js",
        "other-package": true
    }
}
```
> Note: When you use true: when available the es6 path from the package will be used otherwise the main path will be used.

When you are done modifing your `package.json` you can choose between the next two executing methods.

### Command Line
To let this module do it's magic run the `es6` command from your project directory.

### Make it all automatic.
Or add the `es6` command to your `package.json` like this:
```json
{
    "postinstall":"es6"
}
```

## Reverse
You can to reverse everything by using: `es6 -r` or `es6 --reverse`

## Build in support
If you have an npm module and want to support this can you do this by adding this to you `package.json` file.

```json
{
    "es6":"path/to/your/main/es6/file.js"
}
```

or 

```json
{
    "main":"src/index.js",
    "es6":true
}
```
> Note: When you use true the main path will be used to load your module in es6 mode.

## How does this work?
You can already use non compiled es6 modules with babel but they can not be installed in `node_modules`. Somehow babel will not compile the packages in this directory. This module will move the es6 packages from `node_modules` to `es6 modules` and create a redirect package in `node_modules`.

## Why did I make this?
In order to use es6 npm modules they have to be precompiled. I found this to be very annoying.  I'm actively developing a few packages at the same time which will eventually all work together in the system that i'm building. I had to precompile every change and when I did forget that step I had to precompile and recommit. Not my ideal workflow. So I found a way to use my es6 modules without precompiling them and this little library is the result.

## Contribute
Feel free to use this and/or help me improving this module. If you have found a bugs/issue or if you want/know an improvement please create an issue.

## Author
* Danny van der Jagt.
