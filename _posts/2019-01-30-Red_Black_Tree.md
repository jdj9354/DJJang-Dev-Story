---
layout: post
title:  "Red Black Tree"
comments: true
categories: algorithm
date:   2019-01-30 23:05:00 +0900
---

> # Red Black Tree

<pre>
Red Black Tree is a kind of Binary Search Tree which is optimize tree depth.
Tree depth is limited to O(logn).

Red Black Tree should follow rules,

1. All Nodes are red or black node.
2. Root node is a Black Node.
3. Leaf Node (NIL) is a Black Node
4. Children of Red Node should be Black Node (Node Double Red)
</pre>

> # Search
<pre>
It's same with binary search
</pre>

> # Insertion
<pre>
Newely inserted node is red node. So, when inserting process is repeated, above rule can be corrupted.

In order to solve above problem, there are two ways.


1. Recoloring
Color of siblings of parent is RED

1) Set as BLACK on parent, siblings of parent.
2) Set as Red on parent of parent. 
Ignore when parent of parent is root node. If parent of parent is not root node, Double Red can be arised again.


2. Restructuring
Color of siblings of parent is BLACK or NULL

1) Arrange value of inserted node, parent, parent of parent.
2) Set middle value as parent, and set other values as children.
3) Proceed coloring, parent as BLACK, Children as RED
</pre>

> # Deletion
<pre>
1. Same way of insertion can be applied (Recoloring, Restructuring)
2. Red node can be deleted, without any operation.
</pre>


> # Time Complexity

|Algorithm|Average|Worst case|
|---|---|---|		 
|Space|O(n)|O(n)
|Search|O(log n)|O(log n)|
|Insert|O(log n)|O(log n)|
|Delete|O(log n)|O(log n)|