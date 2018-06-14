 ## Using babel to run an es2015-based script test.js

Babel basic install with NodeJs. If you have npm, Node, and npx installed, you can then proceed: 

``` 
npm init
```

After initializing your project, let's install Babel and the command line project: 

```
npm install babel --save-dev
npm install babel-cli --save-dev
```

### Let's write your ES2015 script

Module script: 

```
export default {
  foo: 'bar'
}
```

Import script: 

```
import { foo } from './module-test';

console.log(foo);
```



```
npx babel test.js
```

Using npx will search for the executable, you can also do the following 

```
./node_modules/babel-cli/bin/babel.js test.js 
```

Which should do nothing and output: 

```
import { foo } from './module-test';

console.log(foo);
```

So you need to have the es2015 transpiler function installed whcih can be done installing the Babel extension entitled "babel-preset-env"

```
 npm install babel-preset-env --save-dev
```

Legacy note: priorly to this a developer had to install specific presets, such as "babel-preset-es2015". From looking Babel site [1] it was deprecated and now you can simply get the [2] "babel-preset-env" instead. 

[1] https://babeljs.io/docs/en/babel-preset-es2015/

[2] https://babeljs.io/docs/en/babel-preset-env

You can test now the transpilation: 

```
 npx babel test.js --presets env
```

And you can write less informing a Babel configuration as a hidden file: 

But this works because of you have defined a preset in a .babelrc:

```
{
  "presets": ["env"]
}
```

And test with a shorter command: 

```
npx babel test.js --presets env
```

With the output being: 

```
'use strict';

var _moduleTest = require('./module-test');

console.log(_moduleTest.foo);
```

## Learnings

The notion of accessing a property, foo, from a module, is a basic need. In ES2015, the concept entitled *destructuring* refers to the ways you can access, or unpack, certain values or properties from objects: 

```
import { foo } from './module-test';

```

## Issue with this article

It's not clear the different between the above and the following: 

```
import foo from './module-test';
```

See this https://stackoverflow.com/questions/33524696/es6-destructuring-and-module-imports?utm_medium=organic&utm_source=google_rich_qa&utm_campaign=google_rich_qa


## References

https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Destructuring_assignment

