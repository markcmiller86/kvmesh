---
layout: page_full
title: Why KVMesh?
---
We have created the KVMesh database to encourage research on the application of Big Data
technologies to HPC problems with emphasis on the data analysis activities
traditionally performed with visualization and analysis tools such as [VisIt](visit.llnl.gov),
[EnSight](https://www.ensight.com), or [ParaView](http://www.paraview.org).

<br>

The level of effort to develop such tools is high. Each represents perhaps 50-150 person years
of software development investment. In addition, proficiency in software development often requires
mastery of many separate technologies such as
[Lustre](http://lustre.org),
[GPFS](http://www.ibm.com/support/knowledgecenter/SSFKCN/gpfs_welcome.html),
[HDF5](https://www.hdfgroup.org/hdf5),
[netCDF](https://www.unidata.ucar.edu/software/netcdf),
[CMake](https://cmake.org),
[VTK](http://www.vtk.org),
[MPI](http://mpi-forum.org),
[OpenMP](http://www.openmp.org),
[Python](https://www.python.org),
[Qt](https://www.qt.io),
[XML](https://www.w3.org/XML),
[JSON](http://www.json.org),
[IceT](http://icet.sandia.gov),
[OpenGL](https://www.opengl.org),
[GLEW](http://glew.sourceforge.net),
and more recently portable performance technologies such as
[VTK-m](http://m.vtk.org/index.php/Main_Page),
[RAJA](https://github.com/LLNL/RAJA), and
[Kokkos](https://github.com/kokkos/kokkos)
not to mention various hardware vendor's compilers and operating systems.
Hiring, developing and retaining software engineering
staff with these combinations of skills is both challenging and costly.

<br>

## Enormous Leverage Opportunity
![VisIt Data Flow](/kvmesh/img/Wikibon-big-data-forecast-2016.jpg)

The graph here represents world-wide investments and projected investments in Big Data
infrastructure software, hardware, and support services.
In particular, this graph does not include the projected additional $100-$200 billion in
_applications_ created with this infrastructure. So, this graph is about _development_
of the Big Data toolbox and not about _use_. It is analogous to the kind of money we
spend in the development of tools like EnSight, ParaView and VisIt.

<br>

For comparison, the red and yellow lines show the entire budget of
the Department of Energy (DOE) [DOE](https://www.energy.gov) and the budget of the
Exascale Computing Project (ECP) [ECP](https://exascaleproject.org), respectively. Both are dwarfed in
comparison to current and projected Big Data investments. Bottom line, if there is a way for the HPC
community to leverage Big Data technology, the potential payoff for HPC would be enormous!

<br>

In particular, consider that more and more colleges are offering degree programs in 
_data sciences_ whereas high performance computing programs are getting scarcer.

<br>

## Visualization **is** Data Analysis
![VisIt Data Flow](/kvmesh/img/visit_line_counts.jpg)

The picture here illustrates a rough architectural data-flow model for how visualization tools
and VisIt in particular process data.

<br>

Processing begins with user's data stored in _parallel_ files in an ever growing variety of formats.
With various I/O libraries
(e.g. [HDF5](https://www.hdfgroup.org/hdf5), [netCDF](https://www.unidata.ucar.edu/software/netcdf))
and parallel I/O paradigms (e.g. N:N, N:M, N:1), user's _native_ data is read and
instantiated it into a handful of standard scientific data objects
(e.g. [vtkUnstructuredGrid](http://www.vtk.org/doc/nightly/html/classvtkUnstructuredGrid.html),
[vtkFloatArray](http://www.vtk.org/doc/nightly/html/classvtkFloatArray.html)).
Next, any one of a number of analysis operations (e.g. threshold, iso-volume, onion-peel,
connected-components, etc., etc., etc.) are performed producing _derivative_ data objects. Next,
colors, surface normals, textures, lighting, camera and other visual attributes are added to generate
a renderable _scene_. Finally, the scene is rendered in parallel. The resulting parallel
images are composited together and the final image is then delivered to the user's screen.

<br>

Given these various steps in data processing, we breakdown the relative lines of code in VisIt
for 3 broad categories of functionality; _Control_, _2/3D Graphics & Image Processing_ and
_Scientific Data Analysis (SDA)_. The fraction of total lines of code for SDA has represented
more than 50% of the code since before 2007 and today exceeds 75%. In other words, SDA represents
a majority of the software development manpower invested in VisIt. Furthermore, as VisIt has evolved,
investment in SDA functionality continues to outpace other functionalities. We would not be surprised
if similar experiences hold for other tools.

<br>

## Visualization **as** Database Query
![VisIt Just Tolerable Query Latencies](/kvmesh/img/visit_jtql.jpg)

[_Techopedia_](https://www.techopedia.com) defines _database query_ as
> a request for data or information from a database [...].
> This data may be generated as [textual] results returned by [a query language] 
> or as pictorials, graphs or ... trend analyses from data-mining tools.

<br>

The HPC community does not typically think of interactive visualization as database _query_.
Nonetheless, it certainly fits the definition here. Each time the user adjusts some aspect
of what they are visualizing, we can think of that adjustment as a _query_ and the result
the tool produces as the response to that query. 

<br>

Some _adjustments_, such as zooming, panning or rotating the view, are very simple. Because
they are simple, user's have an expectation that the response also be fast. Other adjustments,
such as changing clip planes, thresholds, iso-values, etc. involve more computation and so
user's accept longer delays.

<br>

When we talk about the length of delay between the query and the response, we're talking about
_latency_. In the picture here we illustrate, roughly, _just tolerable query latency_ for
various round-trip queries deeper and deeper into the visualization tool data flow. In particular,
we show that longer latencies are more tolerable for queries that reach in towards the SDA end of
the data flow. This is important because it is here that Big Data, although latency prone, has a good fit.

<br>

## Apply Big Data where it Fits
![Just Tolerable Query Latency](/kvmesh/img/visit_big_data_hybrid.jpg)

So far, research into the application of big data technologies for scientific
visualization has too frequently focused on either just the rendering end alone
or on the whole end-to-end data flow. Subsequent results have been mixed at best.

<br>

* Latencies are often too big for interactive use.
* Data and/or algorithmic overheads are often unacceptably high.
* The data model mismatch is often seen as an insurmountable obstacle.

<br>

However, as we illustrate in the picture here, we believe the proper application of Big Data
technologies to HPC visualization is to augment the Scientific Data Analysis functionalities
of these tools. The other functionalities (Control and 2/3D Graphics & Image Processing) are
probably best handled by existing technologies (Qt, Python, OpenGL).

<br>

And, as we explain in the preceding section, SDA is precisely where we are presently making
our biggest software engineering investments in these tools and where we expect investments
to continue to grow. This is also were latencies and overheads are most tolerable.
