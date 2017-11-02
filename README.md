[![Published on webcomponents.org](https://img.shields.io/badge/webcomponents.org-published-blue.svg)](https://www.webcomponents.org/element/LostInBrittany/granite-font-awesome)

## granite-font-awesome

*granite-font-awesome* is a wrapping of [Font Awesome](http://fontawesome.io/) CSS as [Polymer](https://www.polymer-project.org/) [shared styles modules](https://www.polymer-project.org/1.0/docs/devguide/styling.html#style-modules) (i.e. inside `<dom-module>` tags).

> Hybrid Polymer element, 1.x-2.x ready

## Doc & demo

[https://lostinbrittany.github.io/granite-font-awesome](https://lostinbrittany.github.io/granite-font-awesome)



### Using *granite-font-awesome* modules

Using  polymer [shared styles](https://www.polymer-project.org/1.0/docs/devguide/styling.html#style-modules) modules is a two-step process: you need to use a `<link>` tag to import the module, and a `<style>` tag to include the styles in the correct place.

To use *granite-font-awesome* in an element:

#### 1. Add the dependency

Add the dependency to the `bower.json` of your application:

```
   "dependencies": {
     [...]
     "granite-font-awesome": "LostInBrittany/granite-font-awesome#^4.7.0"
   }
``` 

And then recover them via `bower install`.


#### 2. Import the *granite-font-awesome* module you want to use

Usually you will simply want to import `granite-font-awesome.html` (wrap around `font-awesome.css`) or `granite-font-awesome-min.html`
(wrap around `font-awesome.min.css`).

Supossing you're using the standard folder locations for your components:
 
```
<link rel="import" href="../granite-font-awesome/elements/granite-font-awesome.html">
``` 

#### 3. Inside your component, use *granite-font-awesome* as shared style

In your element's template you add the include for the *granite-font-awesome* module:

```
<style include="granite-font-awesome"></style>
```
 
#### 4. Add the fonts to `polymer.json`

If you're building your app using `polymer-cli`, don't forget to add the fonts folder `granite-font-awesome/fonts/` to the `extraDependencies` section of your `polymer.json` file.

```
  "extraDependencies": [
    "manifest.json",
    "bower_components/font-awesome/fonts/*",
    "bower_components/webcomponentsjs/*.js"
  ],
```



#### A complete example

```
<!-- import the module  -->
<link rel="import" href="../granite-font-awesome/granite-font-awesome.html">
<dom-module id="x-foo">
  <template>
    <!-- include the style module by name -->
    <style include="granite-font-awesome"></style>
    <style>:host { display: block; }</style>
    Hi
  </template>
  <script>Polymer({is: 'x-foo'});</script>
</dom-module>
```
 


### Generating the style modules

To generate the style modules we use the [granite-css-modularizer](https://github.com/LostInBrittany/granite-css-modularizer) node script:

#### 1. Clone the repository and recover the dependencies of `granite-css-modularizer`

Clone the [granite-css-modularizer](https://github.com/LostInBrittany/granite-css-modularizer) repository and recover the dependencies using `yarn` (or `npm`) :

```
$ yarn install
yarn install v1.2.1
info No lockfile found.
[1/4] Resolving packages...
[2/4] Fetching packages...
[3/4] Linking dependencies...
[4/4] Building fresh packages...
success Saved lockfile.
Done in 0.83s.
```

#### 2. Recover Font Awesome 

Recover Font Awesome distribution using `yarn` (or `npm`):

```
$ yarn add font-awesome@4.7.0
yarn add v1.2.1
warning package.json: No license field
warning No license field
[1/4] Resolving packages...
[2/4] Fetching packages...
[3/4] Linking dependencies...
[4/4] Building fresh packages...
success Saved lockfile.
success Saved 1 new dependency.
└─ font-awesome@4.7.0
warning No license field
Done in 1.34s.
```

Currently *granite-font-awesome* uses Font Awesome version 4.7.0, if you need another version you can change simply install it.


#### 3. Generate the components

Using NodeJS and the `granite-css-modularizer.js` to transform Font Awesome CSS files into polymer elements.

```
$ node ../granite-css-modularizer.js ./node_modules/font-awesome/css ./css_modules/granite-font-awesome/elements
```

After executing it, a series of HTML files is generated in the `./css_modules/granite-font-awesome/elements` folder, each one corresponding to a Font Awesome CSS file.

```
$ ls ./css_modules/granite-font-awesome/elements/*.html
granite-font-awesome.html  granite-font-awesome-min.html
```

#### 4. Add the fonts

As Font Awesome CSS looks for the fonts files folder (as `../fonts/`), copy the content of `./node_modules/font-awesomev/fonts` into `./css_modules/granite-font-awesome/fonts/`.

```
$ cp -r  ./node_modules/font-awesome/fonts/* ./css_modules/granite-font-awesome
```


## Contributing

1. Fork it!
2. Create your feature branch: `git checkout -b my-new-feature`
3. Commit your changes: `git commit -m 'Add some feature'`
4. Push to the branch: `git push origin my-new-feature`
5. Submit a pull request :D

## Note on semver versioning

I'm aligning the versions of this element with Font Awesome version, in order to make easier to choose the right version
 
## License

[Apache 2.0](http://www.apache.org/licenses/LICENSE-2.0)
