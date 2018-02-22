---
layout: page_full
title: What is KVMesh?
---

KVMesh is an example of a wide variety of mesh-based scientific data stored
in key-value form suitable for processing by Big Data technologies such as
[Apache Spark](http://spark.apache.org) or [Hadoop](http://hadoop.apache.org).

|:---:|:---:|:---:|
|[<img src="/img/sci_data_2.jpg" width="300">](/img/sci_data_2.jpg)|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|[<img src="/img/sci_data_relationships.png" width="300">](/img/sci_data_relationships.png)|
|||

The pictures here (click to enlarge them) illustrate that mesh-based scientific data
has well a defined data model, is highly structured and often rich and diverse in
logical, geometrical and mathematical relationships. This is in stark contrast to
[unstructured](https://en.wikipedia.org/wiki/Unstructured_data) text and
[key-value](https://en.wikipedia.org/wiki/Key-value_database) pairs typical of Big
Data workflows.

These two kinds of data, mesh-based scientific data versus unstructured text and
key-value pairs, could not represent two more incompatible data formats. Thus, a
fundamental question is how to express mesh-based scientific data as unstructured
text and key-value pairs so that it can be naturally and easily processed within
off-the-shelf Big Data workflows.

The critical insight is to treat the nodes and zones of a scientific mesh as a
collection of _entities_ with _attributes_. Key-value pairs are then easily constructed
using the mesh entities (nodes, elements, blocks, etc.) as the _keys_ and the
attributes (materials, variables, etc.) as the _values_.

Towards this end, the KVMesh database is a _research and demonstration database_. It is
a massive folder hierarchy of [CSV](https://en.wikipedia.org/wiki/Comma-separated_values)
text files consisting of key-value pairs from a vareity of data sources representative
of various aspects of mesh-based scientific data.

With the KVMesh database, we hope to facilitate and inspire research and development
of Big Data approaches to mesh-based scientific data query, analysis and visualization.
