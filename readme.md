# TreeDataNext.js

TreeDataNext is a modern JavaScript library for creating and customizing tree data structures in web applications. It is an evolution of the original [treeData.js](https://github.com/raphamorim/treeData.js) library, with added flexibility and customization options.

## Features

- Utilizes ES6 features for a more modern and efficient approach to building tree structures.
- Allows real-time customization of tree nodes during the build process.
- Returns a Promise containing the final node once the build process is complete.
- Offers an intuitive API interface, making it easier for developers to create and manipulate tree structures.

## What's a Tree data structure?

In computer science, a tree is a widely used abstract data type (ADT) or data structure implementing this ADT that simulates a hierarchical tree structure, with a root value and subtrees of children, represented as a set of linked nodes.

A tree data structure can be defined recursively (locally) as a collection of nodes (starting at a root node), where each node is a data structure consisting of a value, together with a list of references to nodes (the "children"), with the constraints that no reference is duplicated, and none points to the root.

## How to use

It's super simple to use this javascript plugin.

**1.** Include the CSS file to your document

```html
<link rel="stylesheet" href="treedata-next.css" />
```

**2.** Include the JavaScript file to your document

```html
<script src="treedata-next.js"></script>
```

**3.** Create your tree structure

Unlike [treeData.js](https://github.com/raphamorim/treeData.js) library which uses object to define tree structure, TreeDataNext.js uses an array of objects instead.
Each `object` in the array represents a `NodeItem`

```javascript
let tree = [
     { id: "father", value: "Root Node", parent: null },
     { id: "a", value: "CTO", parent: "father" },
     { id: "b", value: "Manager", parent: "a" },
     { id: "c", value: "Director", parent: "b" },
     { id: "d", value: "Distributor", parent: "c" },
     { id: "e", value: "Client", parent: "b" },
     // More Tree Data
];
```

**4.** Build your tree

```javascript
new TreeDataNext(tree)
    .build(function(element, depth, nodeItem) {
          // Custom modifications to tree elements
    })
    .then(function(finalNode) {
          // Append the constructed elements to your document
          document.querySelector('#my-container').appendChild(finalNode);
    });
```

## Elucidation:

<table>
  <thead>
    <tr>
      <th>Method</th>
      <th>Param Type</th>
      <th>Param Required</th>
      <th>Description</th>
      <th>Returns</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>
          <code>new TreeDataNext()</code>
     </td>
      <td>Array</td>
      <td>Yes</td>
      <td>
          An array of objects, each representing a node in the tree. <br>
          Each object should have an 'id', 'value', and 'parent' property.
      </td>
      <td>
          TreeDataNext Instance
      </td>
    </tr>
    <tr>
      <td>
          <code>.build()</code>
     </td>
      <td>Function</td>
      <td>No</td>
      <td>
          A callback function that is called for each element being built. This function receives three parameters: <br>
          <ul>
               <li><code>element</code>: (the list element which is the actual node)</li> 
               <li><code>depth</code>: (the depth of the current element being built)</li>
               <li><code>nodeItem</code>: (the object in the tree structure that was used to create the element)</li>
          </ul>
      </td>
      <td>
          Promise
      </td>
    </tr>
  </tbody>
</table>

## About

Forked from [raphamorim](http://github.com/raphamorim) by [ucscode](http://github.com/ucscode)
