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
      value: any
    </td>
    <td align="center">DirectedGraph | Graph</td>
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
 <tr><th>return</th></tr>
 <tr>
  <td>number</td>
 </tr>
</table>

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
console.log(directedGraph.getVerticesCount()); // 5
console.log(graph.getVerticesCount()); // 5
```

### .addEdge(srcKey, destKey, weight)
adds an edge with a weight between two existings vertices. Default weight is 1 if not defined. The edge is a direction from source to destination when added in a directed graph, and a connecting two-way edge when added in a graph.

<table>
  <tr><th align="center" colspan="3">params</th></tr>
  <tr><td><b>name</b></td><td align="center"><b>type</b></td><td><b>description</b></td></tr>
  <tr><td>srcKey</td><td>number or string</td><td>the source vertex key</td></tr>
  <tr><td>destKey</td><td>number or string</td><td>the destination vertex key</td></tr>
  <tr><td>weight</td><td>number</td><td>the weight of the edge</td></tr>
</table>

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
directedGraph.addEdge('v1', 'v2', 2);
directedGraph.addEdge('v1', 'v3', 3);
directedGraph.addEdge('v1', 'v4', 1);
directedGraph.addEdge('v2', 'v4', 1);
directedGraph.addEdge('v3', 'v5', 2);
directedGraph.addEdge('v4', 'v3', 1);
directedGraph.addEdge('v4', 'v5', 4);

graph.addEdge('v1', 'v2', 2);
graph.addEdge('v2', 'v3', 3);
graph.addEdge('v1', 'v3', 6);
graph.addEdge('v2', 'v4', 1);
graph.addEdge('v4', 'v3', 1);
graph.addEdge('v4', 'v5', 4);
graph.addEdge('v3', 'v5', 2);
```

### .hasEdge(srcKey, destKey)
checks if the graph has an edge between two existing vertices. In directed graph, it returns true only if there is a direction from source to destination.

<table>
  <tr><th align="center" colspan="3">params</th></tr>
  <tr><td><b>name</b></td><td align="center"><b>type</b></td><td><b>description</b></td></tr>
  <tr><td>srcKey</td><td>number or string</td><td>the source vertex key</td></tr>
  <tr><td>destKey</td><td>number or string</td><td>the destination vertex key</td></tr>
</table>

<table>
 <tr><th>return</th></tr>
 <tr>
  <td>boolean</td>
 </tr>
</table>

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
console.log(directedGraph.hasEdge('v1', 'v2')); // true
console.log(directedGraph.hasEdge('v2', 'v1')); // false

console.log(graph.hasEdge('v1', 'v2')); // true
console.log(graph.hasEdge('v2', 'v1')); // true
```

### .getEdgesCount()
gets the number of edges in the graph.

<table>
 <tr><th>return</th></tr>
 <tr>
  <td>number</td>
 </tr>
</table>

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
console.log(directedGraph.getEdgesCount()); // 7
console.log(graph.getEdgesCount()); // 7
```

### .getWeight(srcKey, destKey)
gets the edge's weight between two vertices in the graph. If there is no direct edge between the two vertices, it returns null. It also returns 0 if the source key is equal to destination key.

<table>
  <tr><th align="center" colspan="3">params</th></tr>
  <tr><td><b>name</b></td><td align="center"><b>type</b></td><td><b>description</b></td></tr>
  <tr><td>srcKey</td><td>number or string</td><td>the source vertex key</td></tr>
  <tr><td>destKey</td><td>number or string</td><td>the destination vertex key</td></tr>
</table>

<table>
 <tr><th>return</th></tr>
 <tr>
  <td>number</td>
 </tr>
</table>

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
console.log(directedGraph.getWeight('v1', 'v2')); // 2
console.log(directedGraph.getWeight('v2', 'v1')); // null
console.log(directedGraph.getWeight('v1', 'v1')); // 0

console.log(graph.getWeight('v1', 'v2')); // 2
console.log(graph.getWeight('v2', 'v1')); // 2
console.log(graph.getWeight('v1', 'v1')); // 0
console.log(graph.getWeight('v1', 'v4')); // null
```

### .removeVertex(key)
removes a vertex with all its edges from the graph by its key.

<table>
  <tr><th align="center" colspan="3">params</th></tr>
  <tr><td><b>name</b></td><td align="center"><b>type</b></td><td><b>description</b></td></tr>
  <tr><td>key</td><td>number or string</td><td>the vertex key</td></tr>
</table>

<table>
 <tr><th>return</th></tr>
 <tr>
  <td>boolean</td>
 </tr>
</table>

<table>
 <tr>
  <th colspan="2">runtime</th>
 </tr>
  <tr><td>Graph</td><td>O(K) : K = number of connected edges to the vertex</td></tr>
  <tr><td>Directed Graph</td><td>O(E) : E = number of edges in the graph</td></tr>
</table>

#### Example

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
  <tr><th align="center" colspan="3">params</th></tr>
  <tr><td><b>name</b></td><td align="center"><b>type</b></td><td><b>description</b></td></tr>
  <tr><td>srcKey</td><td>number or string</td><td>the source vertex key</td></tr>
  <tr><td>destKey</td><td>number or string</td><td>the destination vertex key</td></tr>
</table>

<table>
 <tr><th>return</th></tr>
 <tr>
  <td>boolean</td>
 </tr>
</table>

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
directedGraph.removeEdge('v1', 'v3'); // true
console.log(directedGraph.getEdgesCount()); // 4

graph.removeEdge('v2', 'v3'); // true
console.log(graph.getEdgesCount()); // 4
```

### .removeEdges(key)
removes all connected edges to a vertex by its key.

<table>
  <tr><th align="center" colspan="3">params</th></tr>
  <tr><td><b>name</b></td><td align="center"><b>type</b></td><td><b>description</b></td></tr>
  <tr><td>key</td><td>number or string</td><td>the vertex key</td></tr>
</table>

<table>
 <tr><th>return</th><th>description</th></tr>
 <tr>
  <td>number</td><td>number of removed edges</td>
 </tr>
</table>

<table>
 <tr>
  <th colspan="2">runtime</th>
 </tr>
  <tr><td>Graph</td><td>O(K) : K = number of connected edges to the vertex</td></tr>
  <tr><td>Directed Graph</td><td>O(E) : E = number of edges in the graph</td></tr>
</table>

#### Example

```js
const dg = new DirectedGraph();
dg.addVertex('v1');
dg.addVertex('v2');
dg.addVertex('v3');
dg.addEdge('v1', 'v2');
dg.addEdge('v2', 'v1'); // this is counted as a direction in directed graph.
dg.addEdge('v1', 'v3');
dg.removeEdges('v1'); // 3

const g = new Graph();
g.addVertex('v1');
g.addVertex('v2');
g.addVertex('v3');
g.addEdge('v1', 'v2');
g.addEdge('v1', 'v3');
g.removeEdges('v1'); // 2
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
