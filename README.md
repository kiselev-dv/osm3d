# osm3d
Osm 3d specification


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
