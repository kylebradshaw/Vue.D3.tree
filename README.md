# Vue.D3.tree
[![GitHub open issues](https://img.shields.io/github/issues/David-Desmaisons/Vue.D3.tree.svg?maxAge=2592000)](https://github.com/David-Desmaisons/Vue.D3.tree/issues)
[![Npm version](https://img.shields.io/npm/v/vued3tree.svg?maxAge=2592000)](https://www.npmjs.com/package/vued3tree)
[![vue2](https://img.shields.io/badge/vue-2.x-brightgreen.svg)](https://vuejs.org/)
[![MIT License](https://img.shields.io/github/license/David-Desmaisons/Vue.D3.tree.svg)](https://github.com/David-Desmaisons/Vue.D3.tree/blob/master/LICENSE)


Vue component to display tree based on [D3.js](https://d3js.org/) layout.

![demo](./documentation/treedemo.gif)

## Usage

```html
<tree :data="tree" :node-text="name" layoutType="circular">
</tree>
```
```javascript
import tree from 'vued3tree'

export default {
  components: {
    tree
  },
  data() {
      return {
          tree: {
            name: "father",
            children:[{ 
                name: "son1",
                chidldren:[ {name: "grandson"}, {name: "grandson2"}]
            },{
                name: "son2",
                children:[ {name: "grandson3"}, {name: "grandson4"}]
            }]
       }
    }     
  }
}
  //...
```

## Properties

| Name      | Required | Type/Value              | Default     | Description |
| ---       | ---      | ---                     | ---         | ---         |
| data      | no    | `Object`                     | null        | Data representing tree structure, children nodes are represented by children property
| nodeText   | yes | `String`  | null|  name of the property of the node to be used as a display name |
| type      | no    | 'tree' or 'cluster'       | 'tree'      | kind of layout: [tree](https://github.com/d3/d3-hierarchy/blob/master/README.md#tree) or [cluster](https://github.com/d3/d3-hierarchy/blob/master/README.md#cluster) |
| layoutType | no | 'circular' or 'euclidian' |  'euclidian'       | Circular or euclidien layout |
| marginX    | no | `Number`          | 20       | margin for X axis in pixel |
| marginY    | no | `Number`           | 20            | margin for Y axis in pixel |
| duration   | no | `Number`  | 750|  Animation duration in milliseconds |


## Events

* `clicked`

Sent when the node name is clicked

* `expand`

Sent when the node is clicked and the node children are expanded

* `retract`

Sent when the node is clicked and the node children are retracted

For all events, the argument passed is `{element, data}` where `element` represents the node build by `D3.js` and `data` is the node raw data.


### Build Setup

``` bash
# install dependencies
npm install

# serve with hot reload at localhost:8080
npm run dev

# build for production with minification
npm run build
```

