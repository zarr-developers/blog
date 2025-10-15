---
layout: post
title: 'Usage conventions'
description: This post describes work done at the Zarr Summit 2025 to develop a standard approach and infrastructure for defining Zarr usage conventions.
date: 2025-10-15
categories: blog
permalink: /usage-conventions-zarr-summit-2025/
---

This blog post shares outputs from one of the work streams at the recent Zarr Summit focusing on how to define, share and apply Zarr usage conventions for application-specific metadata. This is work in progress and feedback is very welcome, please comment via @@TODO.

## A very brief intro to attributes

Zarr provides a mechanism to store additional metadata together with arrays and groups. These metadata are useful for downstream applications and users, but are not essential to the basic reading and writing of data. In other words, a vanilla Zarr implementation can safely ignore these attributes, it just needs to support storing arbitrary JSON in the attributes and then retrieve it again later. Here's an example of attributes in an array or group metadata file, based on an example from the [v3 core spec](https://zarr-specs.readthedocs.io/en/latest/v3/core/index.html#metadata):

```json
{
    "zarr_format": 3,
    ...
    "attributes": {
        "foo": 42,
        "bar": "apples",
        "baz": [1, 2, 3, 4]
    }
}
```

## The need for attribute usage conventions

Although a Zarr implementation can ignore attributes, downstream applications and users will depend on them to implement specialised behaviour and interpret data. Several user communities would like to define conventions for how they use attributes, to achieve interoperability between downstream applications. For example, the [OME project](https://ngff.openmicroscopy.org/) is developing conventions for using attributes to describe microscopy datasets. Another example is the [GeoZarr project](https://github.com/zarr-developers/geozarr-spec) which is developing conventions for encoding spatial reference systems, coordinate axes, and geospatial transformations. A third example is [VCF Zarr](https://github.com/sgkit-dev/vcf-zarr-spec/blob/main/vcf_zarr_spec.md) which maps the variant call format for genomic data into Zarr.

Projects like these and others could benefit from a common approach to documenting and sharing their attribute usage conventions, and to applying these conventions within Zarr metadata. This could help to reduce duplication of effort, avoid attribute naming collisions between usage conventions, support some standard tooling such as metadata validation, and more robustly drive application-specific behaviour.

## A brief history of Zarr usage conventions

How best to define usage conventions has been under discussion for some time and several proposals have been put forward.

@@TODO ZEP4

@@TODO ZEP10

There are also a number of usage conventions already defined and in use. E.g., xarray uses several attributes to store @@TODO, and has documented that @@WHERE. @@TODO OME mentioned above has a draft @@WHERE.

## "Conventions" not "extensions"

One point of confusion regarding the ZEP10 approach has been that the zarr-extensions repo is proposed as a place to document usage conventions and register attributes. However, this is not really an extension to Zarr in the strict sense, because the word "extension" is used to mean things which expand or modify the behaviour of a zarr implementation, connecting to defined extension points within the core spec. Rather, usage conventions are specialising zarr for a particular application or domain. Everyone at the summit was behind calling these "conventions" rather than "extensions".

## Challenges with the centrally-registered attributes approach

There are several other limitations with the registered attributes approach. One problem is that decisions about who to allow to register which attributes sits with the Zarr Steering Council (ZSC). The ZSC can be slow, and also may not have the domain knowledge needed to know who should be responsible for which namespace. This came up specifically within the context of geo/proj @@TODO. 

Support for decentralising, so people can move forwards in parallel without any delays.

Also support for separation of concerns - this isn't really anything to do with Zarr core spec or implementations, it's about the downstream community of users and application developers. So doesn't make sense for ZSC, better to have mechanisms for coordination and communication that work better for those communities.

## New designs considered for decentralised usage conventions

We considered two main designs for writing attributes in a way that makes usage conventions explicit within the metadata.

### Approach A - STAC-style declarations

The first approach considered was inspired by how the STAC community declares what they call metadata extensions. STAC is often cited as an example of how decentralised coordination of usage conventions is possible. Here's an example of the proposed design for zarr attributes...

```
@@TODO example
```

### Approach B - Encapsulated metadata

An alternative approach was to encapsulate all metadata for a particular usage convention nested under some globally unique identifier. Here's an example that was sketched...

```
@@TODO example
```

### Discussion of pros and cons

We discusses the pros and cons of these approaches. @@TODO

Those present decided to move forwards with prototyping a spec and infrastructure based on approach B, to help as a basis for wider feedback and consultation.

## A spec and template repo for defining usage conventions

We developed a draft spec for defining usage conventions. @@TODO link. @@TODO summary of what the spec covers.

We also developed a template GitHub repo for defining a usage convention. The idea is that anyone who wants to define a new usage convention can fork this repo. It provides a template spec and JSON schema, @@TODO anything else.

## Making usage conventions discoverable

If usage conventions are decentralised, there is no need for a central registry. There is, however, benefit in providing a website for sharing and discovery.

@@TODO how did we suggest to do this.

## Old-style conventions

New usage conventions such as the geo:proj proposal could use this, where little or no existing data is out there, so no migration challenges.

But there are a number of existing usage conventions with data out in the wild. These will have specs, still benefit from some way to share and find them. Propose to also host these somehow?

## Next steps

@@TODO