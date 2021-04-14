# @datastructures-js/graph

[![build:?](https://travis-ci.org/datastructures-js/graph.svg?branch=master)](https://travis-ci.org/datastructures-js/graph) 
[![npm](https://img.shields.io/npm/v/@datastructures-js/graph.svg)](https://www.npmjs.com/package/@datastructures-js/graph)
[![npm](https://img.shields.io/npm/dm/@datastructures-js/graph.svg)](https://www.npmjs.com/package/@datastructures-js/graph) [![npm](https://img.shields.io/badge/node-%3E=%206.0-blue.svg)](https://www.npmjs.com/package/@datastructures-js/graph)

<table><tr><td>
  <img alt="graph" src="https://user-images.githubusercontent.com/6517308/71645678-802cd500-2ca1-11ea-96fb-11a71fd95191.jpg">
</td></tr></table>

# Table of Contents
* [Install](#install)
* [API](#api)
  * [require](#require)
  * [import](#import)
  * [new](#new)
  * [.addVertex(key, value)](#addvertexkey-value)
  * [.hasVertex(key)](#hasvvertex-key)
  * [.getVerticesCount()](#getverticescount)
  * [.addEdge(srcKey, destKey, weight)](#addedgesrckey-destkey-weight)
  * [.hasEdge(srcKey, destKey)](#hasedgesrckey-destkey)
  * [.getEdgesCount()](#getedgescount)
  * [.getWeight(srcKey, destKey)](#getweightsrcKey-destKey)
  * [.removeVertex(key)](#removevertexkey)
  * [.removeEdge(key)](#removeedgesrckey-destkey)
  * [.traverseDfs(srcKey, cb)](#traversedfssrckey-cb)
  * [.traverseBfs(srcKey, cb)](#traversebfssrckey-cb)
  * [.clear()](#clear)
  * [Vertex](#vertex)
 * [Build](#build)
 * [License](#license)

## install
```sh
npm install --save @datastructures-js/graph
```

## API

### require

```js
const { Graph, DirectedGraph } = require('@datastructures-js/graph');
```

### import

```js
import { Graph, DirectedGraph } from '@datastructures-js/graph';
```

### new
creates a new graph

```js
const directedGraph = new DirectedGraph();

const graph = new Graph();
```

### .addVertex(key, value)
adds a vertex to the graph.

<table>
  <tr>
    <th align="center">params</th>
    <th align="center">return</th>
    <th align="center">runtime</th>
  </tr>
  <tr>
    <td>
      key: number | string
      <br />
      value: any
    </td>
    <td align="center">Graph | DirectedGraph</td>
    <td align="center">O(1)</td>
  </tr>
</table>

```js
directedGraph
  .addVertex('v1', 1)
  .addVertex('v1', 1)
  .addVertex('v2', 2)
  .addVertex('v3', 3)
  .addVertex('v4', 4)
  .addVertex('v5', 5);

graph
  .addVertex('v1', true)
  .addVertex('v2', true)
  .addVertex('v3', true)
  .addVertex('v4', true)
  .addVertex('v5', true);
```

### .hasVertex(key)
checks if the graph has a vertex by its key.

<table>
  <tr>
    <th align="center">params</th>
    <th align="center">return</th>
    <th align="center">runtime</th>
  </tr>
  <tr>
    <td>
      key: number | string
    </td>
    <td align="center">boolean</td>
    <td align="center">O(1)</td>
  </tr>
</table>

```js
console.log(directedGraph.hasVertex('v7')); // false
console.log(graph.hasVertex('v1')); // true
```

### .getVerticesCount()
gets the number of vertices in the graph.

<table>
  <tr>
    <th align="center">return</th>
    <th align="center">runtime</th>
  </tr>
  <tr>
    <td align="center">number</td>
    <td align="center">O(1)</td>
  </tr>
</table>

```js
console.log(directedGraph.getVerticesCount()); // 5
console.log(graph.getVerticesCount()); // 5
```

### .addEdge(srcKey, destKey, weight)
adds a weighted edge between two existings vertices. Default weight is 1 if not defined. The edge is a direction from source to destination when added in a directed graph, and a two-way connection when added in a graph.

<table>
  <tr>
    <th align="center">params</th>
    <th align="center">return</th>
    <th align="center">runtime</th>
  </tr>
  <tr>
    <td>
      srcKey: number | string
      <br />
      destKey: number | string
      <br />
      weight: number
    </td>
    <td align="center">Graph | DirectedGraph</td>
    <td align="center">O(1)</td>
  </tr>
</table>

```js
directedGraph
  .addEdge('v1', 'v2', 2)
  .addEdge('v1', 'v3', 3)
  .addEdge('v1', 'v4', 1)
  .addEdge('v2', 'v4', 1)
  .addEdge('v3', 'v5', 2)
  .addEdge('v4', 'v3', 1)
  .addEdge('v4', 'v5', 4);

graph
  .addEdge('v1', 'v2', 2)
  .addEdge('v2', 'v3', 3)
  .addEdge('v1', 'v3', 6)
  .addEdge('v2', 'v4', 1)
  .addEdge('v4', 'v3', 1)
  .addEdge('v4', 'v5', 4)
  .addEdge('v3', 'v5', 2);
```

### .hasEdge(srcKey, destKey)
checks if the graph has an edge between two existing vertices. In directed graph, it returns true only if there is a direction from source to destination.

<table>
  <tr>
    <th align="center">params</th>
    <th align="center">return</th>
    <th align="center">runtime</th>
  </tr>
  <tr>
    <td>
      srcKey: number | string
      <br />
      destKey: number | string
    </td>
    <td align="center">boolean</td>
    <td align="center">O(1)</td>
  </tr>
</table>

```js
console.log(directedGraph.hasEdge('v1', 'v2')); // true
console.log(directedGraph.hasEdge('v2', 'v1')); // false

console.log(graph.hasEdge('v1', 'v2')); // true
console.log(graph.hasEdge('v2', 'v1')); // true
```

### .getEdgesCount()
gets the number of edges in the graph.

<table>
  <tr>
    <th align="center">return</th>
    <th align="center">runtime</th>
  </tr>
  <tr>
    <td align="center">number</td>
    <td align="center">O(1)</td>
  </tr>
</table>

```js
console.log(directedGraph.getEdgesCount()); // 7
console.log(graph.getEdgesCount()); // 7
```

### .getWeight(srcKey, destKey)
gets the edge's weight between two vertices. If there is no direct edge between the two vertices, it returns `Infinity`. It also returns 0 if the source key is equal to destination key.

<table>
  <tr>
    <th align="center">params</th>
    <th align="center">return</th>
    <th align="center">runtime</th>
  </tr>
  <tr>
    <td>
      srcKey: number | string
      <br />
      destKey: number | string
    </td>
    <td align="center">number</td>
    <td align="center">O(1)</td>
  </tr>
</table>

```js
console.log(directedGraph.getWeight('v1', 'v2')); // 2
console.log(directedGraph.getWeight('v2', 'v1')); // null
console.log(directedGraph.getWeight('v1', 'v1')); // 0

console.log(graph.getWeight('v1', 'v2')); // 2
console.log(graph.getWeight('v2', 'v1')); // 2
console.log(graph.getWeight('v1', 'v1')); // 0
console.log(graph.getWeight('v1', 'v4')); // null
```

### .removeVertex(key)
removes a vertex with all its edges from the graph.

<table>
  <tr>
    <th align="center">params</th>
    <th align="center">return</th>
    <th align="center">runtime</th>
  </tr>
  <tr>
    <td>
      key: number | string
    </td>
    <td align="center">boolean</td>
    <td>
      Graph: O(K) : K = number of connected edges to the vertex
      <br />
      DirectedGraph: O(E) : E = number of edges in the graph
    </td>
  </tr>
</table>

```js
directedGraph.removeVertex('v5');
console.log(directedGraph.getVerticesCount()); // 4
console.log(directedGraph.getEdgesCount()); // 5

graph.removeVertex('v5');
console.log(graph.getVerticesCount()); // 4
console.log(graph.getEdgesCount()); // 5
```

### .removeEdge(srcKey, destKey)
removes an edge between two existing vertices

<table>
  <tr>
    <th align="center">params</th>
    <th align="center">return</th>
    <th align="center">runtime</th>
  </tr>
  <tr>
    <td>
      srcKey: number | string
      <br />
      destKey: number | string
    </td>
    <td align="center">boolean</td>
    <td align="center">O(1)</td>
  </tr>
</table>

```js
directedGraph.removeEdge('v1', 'v3'); // true
console.log(directedGraph.getEdgesCount()); // 4

graph.removeEdge('v2', 'v3'); // true
console.log(graph.getEdgesCount()); // 4
```

### .removeEdges(key)
Removes all connected edges to a vertex and returns the number of removed edges.

<table>
  <tr>
    <th align="center">params</th>
    <th align="center">return</th>
    <th align="center">runtime</th>
  </tr>
  <tr>
    <td>
      key: number | string
    </td>
    <td align="center">number</td>
    <td>
      Graph: O(K) : K = number of connected edges to the vertex
      <br />
      DirectedGraph: O(E) : E = number of edges in the graph
    </td>
  </tr>
</table>

```js
const dg = new DirectedGraph();
dg
  .addVertex('v1')
  .addVertex('v2')
  .addVertex('v3');
  .addEdge('v1', 'v2')
  .addEdge('v2', 'v1') // this is accounted as a direction in directed graph.
  .addEdge('v1', 'v3');
  .removeEdges('v1'); // 3

const g = new Graph();
  .addVertex('v1')
  .addVertex('v2')
  .addVertex('v3')
  .addEdge('v1', 'v2')
  .addEdge('v1', 'v3')
  .removeEdges('v1'); // 2
```

### .traverseDfs(srcKey, cb)
traverses the graph using the depth-first recursive search.

<table>
  <tr><th align="center" colspan="3">params</th></tr>
  <tr><td><b>name</b></td><td align="center"><b>type</b></td><td align="center"><b>description</b></td></tr>
  <tr><td>srcKey</td><td>number or string</td><td>the starting vertex key</td></tr>
  <tr><td>cb</td><td>function</td><td>the callback that is called with each vertex</td></tr>
</table>

<table>
 <tr>
  <th>runtime</th>
 </tr>
 <tr><td>O(V) : V = the number of vertices in the graph</td></tr>
</table>

#### Example
```js
directedGraph.traverseDfs('v1', (v) => console.log(`${v.getKey()}:${v.getValue()}`));
/*
v1:1
v2:2
v4:4
v3:3
*/

graph.traverseDfs('v1', (v) => console.log(v.serialize()));
/*
{ key: 'v1', value: true }
{ key: 'v2', value: true }
{ key: 'v4', value: true }
{ key: 'v3', value: true }
*/
```

### .traverseBfs(srcKey, cb)
traverses the graph using the breadth-first search with a queue.

<table>
  <tr><th align="center" colspan="3">params</th></tr>
  <tr><td><b>name</b></td><td align="center"><b>type</b></td><td align="center"><b>description</b></td></tr>
  <tr><td>srcKey</td><td>number or string</td><td>the starting vertex key</td></tr>
  <tr><td>cb</td><td>function</td><td>the callback that is called with each vertex</td></tr>
</table>

<table>
 <tr>
  <th>runtime</th>
 </tr>
 <tr><td>O(V) : V = the number of vertices in the graph</td></tr>
</table>

#### Example

```js
directedGraph.traverseBfs('v1', (v) => console.log(`${v.getKey()}:${v.getValue()}`));
/*
v1:1
v2:2
v4:4
v3:3
*/

graph.traverseBfs('v1', (v) => console.log(v.serialize()));
/*
{ key: 'v1', value: true }
{ key: 'v2', value: true }
{ key: 'v3', value: true }
{ key: 'v4', value: true }
*/
```

### .clear()
clears all vertices and edges in the graph.

<table>
 <tr>
  <th>runtime</th>
 </tr>
 <tr>
  <td>O(1)</td>
 </tr>
</table>

#### Example

```js
directedGraph.clear();
console.log(directedGraph.getVerticesCount()); // 0
console.log(directedGraph.getEdgesCount()); // 0

graph.clear();
console.log(graph.getVerticesCount()); // 0
console.log(graph.getEdgesCount()); // 0
```

### Vertex

#### .getKey()
returns the vertex key.

<table>
 <tr><th>return</th></tr>
 <tr><td>string or number</td></tr>
</table>

#### .getValue()
returns the vertex associated value.

<table>
 <tr><th>return</th></tr>
 <tr><td>object</td></tr>
</table>

## Build
```
grunt build
```

## License
The MIT License. Full License is [here](https://github.com/datastructures-js/graph/blob/master/LICENSE)
