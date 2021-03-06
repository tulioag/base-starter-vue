# Base Starter for Vaadin components with Vue.js

## Prerequisites

First [install yarn](https://yarnpkg.com/docs/install).

## Build Setup

``` bash
# install dependencies
$ yarn install

# serve with hot reload at localhost:8080
$ yarn serve

# build for production with minification
$ yarn build
```

For detailed explanation on how things work, consult the [docs for vue-loader](http://vuejs.github.io/vue-loader).


## Recreating this project from scratch

Perform the following commands in a terminal window
``` bash
# install vue-cli
$ yarn global add @vue/cli

# initialize the project
$ vue create hello-world
# Keep all the options at their defaults

$ cd hello-vue
$ yarn install

$ yarn add @vaadin/vaadin-core
$ yarn add @webcomponents/webcomponentsjs
```

Add `vue.config.js` file with the following content:

``` javascript
module.exports = {
  transpileDependencies: [/@vaadin\/.*/, /@polymer\/.*/, /@webcomponents\/.*/]
}
```

Open `src/main.js` and

In the `import` section, add:

``` typescript
import '@webcomponents/webcomponentsjs/custom-elements-es5-adapter.js';
import '@webcomponents/webcomponentsjs/webcomponents-bundle.js';
```

Open `src/App.vue`
*	Replace all HTML in the `<template>` with:
``` html
<div>
  <vaadin-text-field ref="textField" id="text" placeholder="Type Something"></vaadin-text-field>
  <vaadin-button @click="clicked">Click Me!</vaadin-button>
  <h2>Hello {{msg}}!</h2>
</div>
```

* In the `<script>` section

Add imports

``` typescript
import '@vaadin/vaadin-button/vaadin-button.js';
import '@vaadin/vaadin-text-field/vaadin-text-field.js';
```

Inside `default` add the click event:

``` javascript
methods: {
  clicked() {
    this.msg = this.$refs.textField.value;
  }
}
```
