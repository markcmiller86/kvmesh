---
layout: page_full
title: KVMesh Data Primer
---

|:---:|
|[<img src="/img/csv_folder_hierarchy.png" width="400">](/img/csv_folder_hierarchy.png)|
||

The KVMesh database is designed to meaningfully represent data as though it spans the entire
[DOE Complex](https://www.google.com/maps/d/viewer?mid=1k6BA3nD5tqE98OettUjwjX91UOE&hl=en_US&ll=39.84380152391495%2C-97.53683650000005&z=4)
in a coherent and uniform way. The idea of a single, coherent database that spans the
entire DOE complex in a uniform way is a revolutionary concept in its own right. However,
the true power of Big Data technology and what it makes possible cannot be fully demonstrated
without starting from a sufficiently wide _scope_.

<!--
This
is because today there is little or no uniformity in database design in any one DOE site
or even within one user or application domain let alone the entire complex. Essential
data is scattered about in computer files of various formats, tape archives, microfiche,
film, blueprints, as well as hand user's notebooks.
-->

In a nutshell, the KVMesh database is a massive folder hierarchy of
[Bzip](https://en.wikipedia.org/wiki/Bzip2) compressed 
[CSV](https://en.wikipedia.org/wiki/Comma-separated_values)
text files. The hierarchy is based on these observations...

* DOE sites have _Computing Centers_
* Computing Centers have _Users_
* Users have _Datasets_
* Datasets have _States_
* States have _Meshes_
* Meshes have _Blocks_
* Blocks have _Data_
  * Mesh topology (connectivity)
  * Materials
  * Fields

<br>

The leaves in this taxonomy is where raw data actually lives. It includes such things as the
list of _mesh entities_ (e.g. nodes and zones) comprising a block, the
_coordinates_ of a block, _fields_ (e.g. pressure, velocity, mass) defined on a
block, the _material decomposition_ of a block, etc. In particular,
each topological entity is _uniquely_ identified across the _entire_ KVMesh database.

By setting upper bounds on the total number of objects to be permitted in each of these
categories, we can establish an upper bound on the total number of bits required in a
mesh entity _key_ to uniquely identify it across the entire KVMesh database. By proper
design of mesh entity _keys_, given any mesh entity, we can identify which DOE site it
came from, which computing center at that site, which user at that center, which dataset of
that user, which state of that dataset, which mesh of that state and which block of
that mesh.

With this over-arching design, we enable a Big Data workflow with the ability to perform queries
of arbitrary _scope_. The underlying Big Data machinery required to perform any query of any
scope is basically the same and is independent of scope. The only difference is the compute
resources required to respond in a given target time constraint. For example, a query for
maximum temperature of one user's dataset for one state vs. the maximum temperature over
all states vs. the maximum temperature over several different datasets is the _same_ query
except executed from different points in the folder hierarchy.

We plan to present more details here on this page at
a future data. Until then, please refer to
[this page](https://visitbugs.ornl.gov/projects/silo/wiki/Apache_Spark_and_VisIt#Design-of-a-Mesh-and-Field-Database-Suitable-for-Spark-Applications).
