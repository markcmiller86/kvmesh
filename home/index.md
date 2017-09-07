---
layout: page_full
type: gallery
gallery-id: sci-data-intro
title: What is KVMesh?
---

{% include gallery_lightbox.html %}

KVMesh is an example of mesh-based scientific data stored in a form suitable
for processing by Big Data technologies such as
[Apache Spark](http://spark.apache.org) or [Hadoop](http://hadoop.apache.org).

<br>

As the pictures here illustrate, mesh-based scientific data has well a defined data model,
is highly structured and often rich and diverse in logical, geometrical and mathematical
relationships. This is in stark contrast to
[unstructured](https://en.wikipedia.org/wiki/Unstructured_data) text and
[key-value](https://en.wikipedia.org/wiki/Key-value_database) pairs typical of Big Data workflows.

<br>

These two forms of data, mesh-based scientific data versus unstructured text and key-value pairs,
could not represent two more incompatible data formats. Thus, a fundamental question is how to
express mesh-based scientific data as unstructured text and key-value pairs so that it
can be naturally and easily processed within off-the-shelf Big Data workflows.

<br>

The critical insight is to treat the nodes and zones of a scientific mesh as a
_collection of entities with attributes_. Key-value pairs are then easily constructed
using the mesh entities as the _keys_ and their attributes (materials, variables, etc.)
as the _values_.

<br>

Towards this end, the KVMesh database is a massive folder hierarchy of
[CSV](https://en.wikipedia.org/wiki/Comma-separated_values), key-value files 
from a vareity of data sources representative of various scientific computing applications.

<br>

With the KVMesh database, we hope to facilitate and inspire research and development
of Big Data approaches to scientific data query, analysis and visualization.
