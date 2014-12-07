Random3Dcity
============

A procedural modelling engine for generating buildings and other features in CityGML in multiple levels of detail (LOD).

![Overview](http://3dgeoinfo.bk.tudelft.nl/biljecki/code/img/R3-interior.png)


# Datasets

If you are interested only in the datasets, visit my personal webpage to download a prepared collection
 of datasets: [http://3dgeoinfo.bk.tudelft.nl/biljecki/Random3Dcity.html](http://3dgeoinfo.bk.tudelft.nl/biljecki/Random3Dcity.html)

# Introduction

This experimental software prototype was developed as a part of my [PhD research](http://3dgeoinfo.bk.tudelft.nl/biljecki/phd.html), and it has been designed and developed from scratch.

Procedural modelling engines natively supporting CityGML and designed for generating semantically structured 3D city models in multiple LODs are not available. This project presents an effort to fill this gap.

The engine is composed of two modules. The first one is procedural: it randomly generates buildings and their elements according to a comprehensive set of rules and constraints. The buildings are realised through parametres which are stored in an XML form.

The second part of the engine reads this data and constructs CityGML data in multiple LODs.


## Conditions for use


This software is free to use. However, you are kindly requested to acknowledge the use of this software by citing it in a research paper you are writing, reports, and/or other applicable materials; and mentioning the [3D Geoinformation group at the Delft University of Technology](http://3dgeoinfo.bk.tudelft.nl/). A research paper is under submission, hence please contact me to give you a reference to cite.

Further, I will be very happy to hear if you find this tool useful for your workflow. If you find it useful and/or have suggestions for its improvement, please let me know. Further, I am maintaining a list of users that I notify of corrections and updates.


## Academic reference with a detailed methodology

Coming soon. Journal paper under submission.


## Features and technical details

### Roof types and building parts

The engine supports five types of roofs: flat, gabled, hipped, pyramidal, and shed. Further, it supports also building parts such as garages and alcoves.

![Roofs](http://3dgeoinfo.bk.tudelft.nl/biljecki/code/img/R3-roofTypes.png)


### 16 Levels of detail

The engine supports generating data in 16 levels of detail. The following composite render shows an example of four LODs:

![LOD-composite](http://3dgeoinfo.bk.tudelft.nl/biljecki/code/img/R3-LOD-composite.png)

The following image shows the specification of our novel LOD specification ("Delft LODs") according to which the models are generated. This specification will be published in details.

![LOD-specification](http://3dgeoinfo.bk.tudelft.nl/biljecki/code/img/R3-refinedLODs.png)

### Geometric references

Besides the LODs, the engine generates multiple representations according to geometric references within LODs, e.g. an LOD1 with varying heights of the top surface (height at the eaves, at the half of the roof, etc.)

![Geometric references](http://3dgeoinfo.bk.tudelft.nl/biljecki/code/img/R3-LOD1cb.png)


### Solids

Each representation is constructed its corresponding solid.

![Solids](http://3dgeoinfo.bk.tudelft.nl/biljecki/code/img/R3-assemblingSolid.png)


### Vegetation and streets

An experimental feature is the generation of vegetation and streets.

![Other-features](http://3dgeoinfo.bk.tudelft.nl/biljecki/code/img/R3-roads.png)


Documented uses
---------------------

Besides my [PhD](http://3dgeoinfo.bk.tudelft.nl/biljecki/phd.html) in which I did a lot of experiments and benchmarking with CityGML data, the engine has been used for testing validation and repair software, and other purposes such as error propagation. For the full showcase visit the [data page](http://3dgeoinfo.bk.tudelft.nl/biljecki/Random3Dcity.html).


Usage and options
---------------------

### Introduction to randomising the city

To generate buildings run

```
python randomiseCity.py -o /path/to/the/building/file.xml -n 4000
```

where `n` is the number of buildings to be generated. If you don't specify the number of buildings, by default the program will generate 1000 buildings.

To realise these buildings as a 3D city model in CityGML in multiple levels of detail run:

```
python generateCityGML.py -i /path/to/the/building/file.xml -o /path/to/CityGML/directory/
```
Don't forget to put the `/` at the end of the directory.

### Rotation

If you want to have the buildings rotated randomly, in both commands toggle the flag `-r 1`.

### Building parts

Building parts are generated with the flag `-p 1`.

### Vegetation and street network

Vegetation and street network are generated with the flags `-v 1` and `-s 1`, respectively.

### Solids and geometric references

`generateCityGML.py` generates solids with the option `-ov 1`, and all geometric references with `-gr 1`.

### gml:id according to UUID

It is possible to generate an UUID for each <gml:Polygon> with the option `-id 1`.


Performance
---------------------

The speed mainly depends on the invoked options. With all the options the engine generates around 100 buildings per minute. The computational complexity is not strictly linear, and a high number of buildings (>20000) will likely eat all of your RAM making the process slower.


Special datasets
---------------------

I have prepared a number of intentionally impaired datasets suited for different types of experiments, such as overlapping buildings and simulated geometric errors. For the full list visit the [data page](http://3dgeoinfo.bk.tudelft.nl/biljecki/Random3Dcity.html)

![Intentional errors](http://3dgeoinfo.bk.tudelft.nl/biljecki/random3dcity/errors/overlapping/overlapping.png)


Contact me for questions and feedback
---------------------
Filip Biljecki

[3D Geoinformation Research Group](http://3dgeoinfo.bk.tudelft.nl/)

Faculty of Architecture and the Built Environment

Delft University of Technology

fbiljecki at gmail dot com

[Personal webpage](http://3dgeoinfo.bk.tudelft.nl/biljecki/)


# Acknowledgments

+ This research is supported by the Dutch Technology Foundation STW, which is part of the Netherlands Organisation for Scientific Research (NWO), and which is partly funded by the Ministry of Economic Affairs. (Project code: 11300)

+ People who gave suggestions and reported errors