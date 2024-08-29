---
layout: post
title: "What's new in Zarr V3 Specification?"
description: Blog Post on Zarr V3 Specification
date: 2024-08-30
categories: blog
permalink: /zarr-v3/
---

## Hi, Zarr Community! 👋🏻

I hope you're doing well! We recently released the first and second alpha
versions of Zarr-Python V3; check [here](https://pypi.org/project/zarr/#history). 
With the official release around the corner, there's a lot to look forward to.
But before we dive headfirst into integrating Zarr-Python V3 into our workflows,
I want to take a moment to provide an overview of the key changes and enhancements
we've made in this new version.

For detailed information and the full specification, please refer to the 
[Zarr V3 Specification](https://zarr-specs.readthedocs.io/en/latest/v3/core/v3.0.html).

### 🏃🏻‍♂️‍➡️

Zarr has long been a favourite in the scientific community for storing large,
n-dimensional array data. With the release of the Zarr V3 specification, the
format has taken a significant leap forward, addressing the needs of an
increasingly diverse and demanding user base. In this post, we'll explore the
key changes introduced in Zarr V3, focusing on its enhanced interoperability,
cloud-native performance, and extensibility.

### Enhanced Interoperability 🔁

Zarr V2 was deeply intertwined with the Python ecosystem, particularly relying
on NumPy for many of its core operations. While this made it highly efficient
for Python users, it also limited its usability across different programming
languages and environments. With Zarr V3, the specification has evolved towards
a more language-agnostic approach.

This shift is more than just a technical detail; it represents a major step
towards making Zarr a truly universal format. By decoupling the core
specification from Python-specific concepts, Zarr V3 becomes easier to
implement in other languages, opening the door for broader adoption in diverse
computing environments. The specification has also been streamlined, removing
unnecessary complexities to create a leaner, more focused core that can be
efficiently implemented across various platforms. 

### Cloud-Native Performance ☁️

Zarr V2 was originally optimized for local file storage, where latency is
minimal. However, as data storage increasingly moves to the cloud, with its
higher latency per operation, performance issues have become more apparent. In
response, Zarr V3 has introduced a restructured approach to metadata storage
that significantly improves performance in cloud storage environments.

One of the key changes is the consolidation of the `.zarray` and `.zattrs` files
into a single `zarr.json` file. Previously, `.zarray` contained essential
information about the array, such as its shape, data type, and chunking, while
`.zattrs` held custom attributes. Now, this information is combined in
`zarr.json`, simplifying access and reducing the number of I/O operations
required.

Additionally, the structure of the array has been optimized. Chunks are now
grouped into individual directories based on their size, which minimizes the
overhead of retrieving data from cloud storage. Here's a visual comparison
between V2 and V3 arrays:

<p align="center">
 <img src="../assets/images/arrays_v2_v3.png" alt="arrays_v2_v3" width="900">
 <center> Zarr V2 & V3 Arrays </center>
</p>

Similarly, the structure of groups has been rethought, with multiple `zarr.json`
files being used to manage different levels of metadata. The top-level
`zarr.json` contains basic attributes and node type information, while the
`zarr.json` files within arrays hold the essential information about the
arrays. Here's a visual comparison between V2 and V3 groups:

<p align="center">
 <img src="../assets/images/groups_v2_v3.png" alt="groups_v2_v3" width="900">
 <center> Zarr V2 & V3 Groups </center>
</p>

These changes collectively make Zarr V3 far more efficient in high-latency
environments like cloud storage.

### Increased Extensibility 💪🏻

Zarr's adoption has grown rapidly across various scientific domains, from
geospatial and bio-imaging to genomics and data science. Each of these fields
has unique requirements, and Zarr V3 addresses this diversity through a
extensibility framework.

Extensions in Zarr V3 allow users to add new features and capabilities without
altering the core specification. This is particularly important for
accommodating the evolving needs of different communities. For example, the
extension mechanism lets users manipulate metadata fields, introduce new data
types, modify the chunk grid to support irregular chunks, and even add new
codecs.

One exciting new feature made possible by this extensibility is the [sharding
codec](https://zarr.dev/zeps/accepted/ZEP0002.html), which enables the grouping
of multiple chunks into individual shards. Sharding is particularly useful when
dealing with thousands of chunks, as it simplifies I/O operations in cloud
storage environments where managing a large number of chunks can be challenging.
This is how a sharded array looks like:

<p align="center">
 <img src="../assets/images/sharded_array.png" alt="sharded_array" width="450">
 <center> Zarr Sharded Array </center>
</p>

### Comparison with Zarr V2 Specification ⚖︎

Zarr V3 introduces several important changes in terminology and structure
compared to Zarr V2, reflecting the broader evolution of the format. Here are
some of the key differences:

- `dtype` renamed to `data_type`: The field previously known as `dtype`, which
  specifies the data type of the array, has been renamed to `data_type` in Zarr
  V3. This change makes the terminology clearer and more consistent across
  different programming languages.

- `chunks` replaced with `chunk_grid`: In Zarr V2, the chunks field was used to
  describe how data was divided into chunks. In Zarr V3, this has been replaced
  with `chunk_grid`, which offers a more flexible and descriptive way to
  organize data chunks, including support for more complex chunking
  strategies.

- `dimension_separator` replaced with `chunk_key_encoding`: The
  `dimension_separator` field in Zarr V2, which defined how chunk coordinates
  were represented, has been replaced with `chunk_key_encoding` in Zarr V3.
  This change allows for more sophisticated encoding options that can better
  suit different storage systems.

- Separator changed from `.` to `/`: In Zarr V2, the `.` character was used as a
  separator in chunk keys. Zarr V3 adopts `/` as the separator, aligning with
  common filesystem practices and improving compatibility with cloud storage
  systems.

- filters and compressor combined into `codecs` field: The fields filters and
  compressor, which were used separately in Zarr V2, have been unified into a
  single codecs field in Zarr V3. This change simplifies the metadata and
  provides a more cohesive way to manage data transformations and compression.

### Conclusion

The Zarr V3 specification represents a significant evolution of the format,
addressing the challenges of interoperability, cloud performance, and
extensibility. By decoupling from Python-specific dependencies, optimizing
metadata handling for cloud environments, and introducing a flexible extension
mechanism, Zarr V3 is poised to become the go-to solution for a wide range of
scientific data storage needs. As the Zarr community continues to grow, these
enhancements will help ensure that Zarr remains at the forefront of data storage
technology.

~Sanket Verma

<script src="https://giscus.app/client.js"
        data-repo="zarr-developers/blog"
        data-repo-id="R_kgDOGxrWVg"
        data-category="General"
        data-category-id="DIC_kwDOGxrWVs4CU5q_"
        data-mapping="pathname"
        data-strict="0"
        data-reactions-enabled="1"
        data-emit-metadata="0"
        data-input-position="top"
        data-theme="light"
        data-lang="en"
        crossorigin="anonymous"
        async>
</script>