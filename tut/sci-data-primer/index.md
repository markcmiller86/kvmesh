---
layout: page_full
title: Scientific Data Primer
---
Our intent here is to provide a short primer on scientific data sufficient for
big data experts who are scientific data newbies. That’s a challenge. There are
a lot of technical details. This primer focuses on only the most simplistic
aspects of scientific data essential to begin developing Spark or Hadoop applications
to process the KVMesh database. This primer ignores many advanced issues such as
non-cartesian coordinate systems, arbitrary polyhedra, high order elements, mixing
materials, revolved or refined meshes regular and irregular topologies.

## Meshes
A mesh is a collection of points in 2 or 3 dimensional space connected together to form
polygonal and/or polyhedral pieces called _elements_. In general, a mesh is represented
as two lists.

* A list of the _points_ comprised of coordinate tuples (xy or xyz).
* A list of the _elements_ comprised of point-id tuples

|:---:|
|[<img src="/img/mesh_nodes_elems.png" width="400">](/img/mesh_nodes_elems.png)|
||

In many ways, this representation is analogous to a vertex-list and edge-list representation
of a graph. For example, for the 2D mesh pictured here, these two lists would look like…

``` scss
POINTS:    0:(0.0,0.0), 1:(1.0,0.0), 2:(2.0,0.0), :(3.0,0.0), ...
           ...23:(2.5,2.0), 24:(3.5,2.0), 25:(7.5,2.0)

ELEMENTS:  0:(0,1,11,10), 1:(1,2,12,11), 2:(6,17,16), 3:(6,7,17), 4:(7,22,8,18,25,17), ...
           ...10:(3,21,4,14,24,13)
``` 
Note the ordering of the points in the lists defining each polygonal element in this example.
The ordering is based on the _right-hand-rule_. The points are ordered in the direction the
tips of your fingers curl when holding your right with thumb perpendicular to the page and towards you.

![foo](/img/right_hand_rule.png)

What about the edges? For example, what about the edge joining points 0 and 1? The list of points
for an element implies its edges. For example, for element 3, the edges are E0:(6,7), E1:(7,17)
and E2:(17,6), which joins the last point in the list with the first.

## Variables
There are two basic kinds of variables; those whose data is associated with the points and those whose
data is associated with the elements. For a point-centered variable, you get 1 tuple for each point in
the mesh. For an element-centered variable, you get tuple for each element in the mesh. Additionally,
the variable’s value across an element (e.g. in the white space inside the individual boxes) varies
depending on the kind of variable it is. For an element-centered variable, its value is constant over
an element. For a point-centered variable, its value varies piecewise-linearly over an element. This is
important in any algorithm that requires the interpolation of data in the white space between the elements.
 
In addition, variables can be scalar valued, vector valued or tensor valued.
 
## Materials and other Subsets
 
## Time Series
Meshes and the variables defined upon them typically vary over time in a simulation. So, the simulation
winds up creating many instances of the mesh and variables for each time state. In addition, in certain
cases, the mesh structure can vary with time (points or elements can be either moved, added or deleted
from the mesh). The result is that different time steps are captured by writing these data objects to
different files (or at different places within the same files).
 
## Parallel Decomposition
For scalable scientific computing, meshes are decomposed into chunks and processed by different parallel
tasks. In the picture above, the colored regions represent different chunks the mesh is broken into.
