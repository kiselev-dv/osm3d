# osm3d
Osm 3d specification

**version:** *0.1-draft*

**status:** *draft*


## Abstract
This is the data model specification to describe OSM objects in 3d

## Requirements

* Data types of OSM3d should be esily extensible the same way as OSM features
* OSM3d should support:
  * 3d geometries with different level of details (LOD)
  * Semantics (type and usage of the objects)
  * Reations between objects
  * Data bindings between OSM3d and OSM

## OSM binding

To connect osm3d data objects and models with osm, use `type=osm3d` relation.
All the memmbers of the relation should not be processed duiring creation of the simple 3d osm fetures, 
because 3d geometry for them is described in osm3d model.  

Empty role just indicates that object 3d geometry is described in osm3d model.
Howewer you can use `id:<some_id>` to connect osm objects with features inside osm3d.

For example, let's take an intersection https://www.openstreetmap.org/#map=17/44.64367/-63.65467

We want to be able not only to create a geometry for bridge, tunnel, ground and highways, we want to keep a semantic connection with OSM, so it would be possible to say which 3d geometry primitives represents which highway.

To do so, 
* create `type=osm3d` relation in OSM
* add highways, bridges, tunnels and other osm objects with `id:*` roles. It's a good idea to use meaningfull ids. 
  Like `id:hwy-102.1` for highway 102 segments.
* In OSM3d data structure, create a feature or relation with corresponding ids.
  It's not yet specified should that be a separate id, or some kind of a tag at this moment. 
  But the idea is to match osm3d features by some kind of id with osm objects using roles of osm osm3d relation.

## Structure

### Root element

```xml
<OSM3d>
 <!--- Versions support the same optimistic lock synchronization as OSM elements --->
 <version></version>
</OSM3d>
```


## Encoding

Examples uses xml, but data objects might be encoded in any other format, the data structure it self is what important and what this document is tend to describe.

## Examples

### Mall

### Airport

### Appartment building

### Residential house

### Complex highway intersection

### Bridge
  
## Comparison with CityGML

## Comparison with Collada

## Comparison with BIM
