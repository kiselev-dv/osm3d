# OSM 3d specification

**version:** *0.1-draft*

**status:** *draft*


## Abstract
This is the data model specification to describe OSM objects in 3d

## Requirements

* Community defined Semantics classes. Data types of OSM3d should be extensible the same way as OSM features.
* OSM3d should support:
  * 3d geometries with different level of details (LOD)
  * Semantics (type and usage of the objects)
  * Relations between objects
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

Document should describe a bounding volume, and different LODs groups/objects:

* root
  * LOD 1
  * LOD 2
  * LOD 3
  * Relation 1
  * Relation 2

The exact meaning of different levels are subject to discuss as well as should we associate some exact values like geometric error or pixel size, with different levels, or should we describe it explicitly for each `LOD` object in a document.

While this document in a draft state, it's also possible not to include Features into LOD objects but instead reference LOD level for Features or geometry.

Relations implements the same idea as OSM relations. Without roles assigned to members - it's just a group or collection of `Features`, with tags describing semantic of that *relation*. Memmbers might have a role in relation, the same way as a members of osm relations.

Relations can include other *relations* as a *memmbers* under some *role* or without a *role*.

We might want to keep relations at the root level, because we might want to connect object on a different LOD levels in one relation.

The main meaningfull object is `Feature` which consists of `geometry`, and a set `tags`.

* LOD 1
  * Feature 1
  * Feature 2
    * tags
    * geometry
  * Relation 1
  * Relation 2

Features can be parented to each other, so the transformations applied to parent Feature applied to children as well.
This is useful for geometries so you can move/show/hide them all together,
but this should not be interpreted as Object Oriented inheritance [1].

Feature type and properties are determined by *tags*. Tag combinations and their meaning are developed by community.

## Geometry

The type of the Feature and it's attributes are determined by it's tags or relations membership.
But Feature geometry is described by some explicit geometry class or type. Like

* `mesh`
* `extrusion`
* `loft`
* `boolean`
* `box`
* `way`  // This is a LineString in wkt notation, but named as `way` to match OSM terminology
* `node` // This is a Point in wkt notation, but named as `node` to match OSM terminology

### Generative geometry

This is a draft list, for the first version of this specification I would use some of well described 3d geometry subbset.

It's also might be useful to specify some generative geometry types here.

By generative geometries here considered geometries described as a set of rules to generate the geometry, not as a static vertices and faces oppose to Mesh. Loft and array are good examples of such concept.

## Encoding

Examples uses xml, but data objects might be encoded in any other format, the data structure it self is what important and what this document is tend to describe.

## Examples

### Mall

### Airport

### Apartment building

### Residential house

### Complex highway intersection

### Bridge

## Comparison with CityGML

## Comparison with Collada

## Comparison with BIM

# References
[1](https://en.wikipedia.org/wiki/Inheritance_(object-oriented_programming))
