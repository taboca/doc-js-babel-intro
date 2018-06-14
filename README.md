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

But this works because of you have defined a preset in a .babelrc:

```
{
  "presets": ["env"]
}
```

And because you have installed 

```
 npm install babel-preset-env --save-dev
```

Legacy note: priorly to this a developer had to install specific presets, such as "babel-preset-es2015". From looking Babel site [1] it was deprecated and now you can simply get the [2] "babel-preset-env" instead. 

[1] https://babeljs.io/docs/en/babel-preset-es2015/

[2] https://babeljs.io/docs/en/babel-preset-env

Altenativelly, you could remove the .babelrc and pass the --presets env: 

```
 npx babel test.js --presets env
```

 




