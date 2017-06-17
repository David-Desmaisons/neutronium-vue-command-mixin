# neutronium vue command mixin
<p align="center"><img width="100"src="https://raw.githubusercontent.com/David-Desmaisons/neutronium-vue/master/template/src/assets/logo.png"></p>
Mixin to integrate MVVM ICommand with vue

[![Npm version](https://img.shields.io/npm/v/neutronium-vue-command-mixin.svg?maxAge=2592000)](https://www.npmjs.com/package/neutronium-vue-command-mixin)
[![MIT License](https://img.shields.io/github/license/David-Desmaisons/neutronium-vue-command-mixin.svg)](https://github.com/David-Desmaisons/neutronium-vue-command-mixin/blob/master/LICENSE)
[![Npm version](https://img.shields.io/npm/v/neutronium-vue-command-mixin.svg?maxAge=2592000)](https://www.npmjs.com/package/neutronium-vue-command-mixin)

## Usage
Provide mixin to easily integrate ICommand in vue.js using Neutronium.
Component this mixin exposes:

## Props
### `command`
Type: `Object`<br>
Required: `true`<br>

The property corresponding to the C# command.

### `arg`
Type: `Object`<br>
Required: `false`

The argument that will be passed to comand when execute is called.

## Computed
### `canExecute`
Type: `Boolean`<br>

true if Command CanExecute is true.

## Method
### `execute`

Call the corresponding command with the argument `arg`

## Events
### `beforeExecute`

Called before calling command execute if CanExecute is true. 

The event argument provides two properties: 
* `arg`: `Object` the command argument, 
* `cancel`: `false` set it to true to cancel the execution

### `afterExecute`

Called after calling command execute. 

The event argument is the command argument. 

## Example
Declaring buttonCommand component in a .vue file (using semantic ui):
 
```javascript
<template>
  <div class="ui button" :class="{'disabled': !canExecute}" @click="execute">   
    <slot></slot>  
  </div>
</template>
<script>
import comandMixin from 'neutronium-vue-command-mixin'

export default {
  mixins:[comandMixin]
}
</script>

<style>
</style>
```

Using buttonCommand:

```javascript
<button-command :command="compute" :arg="argument">
	Submit
</button-command> 
```


## Install using npm:
```bash
npm install neutronium-vue-command-mixin --save
```
