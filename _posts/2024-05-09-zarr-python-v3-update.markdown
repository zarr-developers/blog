---
layout: post
title: "Toward Zarr-Python 3.0"
description: A status update on the development of Zarr-Python 3
date: 2024-05-09
categories: blog
permalink: /zarr-python-v3-update/
---

We released Zarr-Python [2.18.0](https://zarr.readthedocs.io/en/stable/release.html#release-2-18-0) this week. Although this release was quite light in terms of user-facing changes, it represents the beginning of a new phase for the project. In this post, we’ll walk through our plan for Zarr-Python 3.0 and what users of the library can expect in the coming months.

## Zarr-Python 2.18

Before we get into the 3.0 release, we’ll first cover a few details about the 2.18 release series. The first thing to know is that we will continue to support 2.18 with bug fixes up until the release of 3.0. Additionally, we expect to use the 2.18 series to communicate changes in the Zarr-Python API, which will come in 3.0. For example, this week's release included a number of new deprecation warnings for parts of the Zarr-Python API that we expect to remove in 3.0 (e.g. exotic stores, experimental v3 API).

## What to expect with Zarr-Python 3.0

In mid-2023, we formed a [working group](https://github.com/zarr-developers/zarr-python/discussions/1480) to look at modernizing Zarr-Python and, crucially, adding support for the [V3 specification](https://zarr-specs.readthedocs.io/en/latest/v3/core/v3.0.html). One of the early outcomes of this effort was a [design document](https://github.com/zarr-developers/zarr-python/blob/056657ca5ed70aa3d77a9e2db42253fca39800b0/v3-roadmap-and-design.md) detailing the plan for a major refactor to the library. The goals for the refactor effort are to:

- Provide a complete implementation of Zarr V3 through the Zarr-Python API,
- Clear the way for exciting extensions / ZEPs (i.e. [sharding](https://zarr-specs.readthedocs.io/en/latest/v3/codecs/sharding-indexed/v1.0.html), [variable chunking](https://zarr.dev/zeps/draft/ZEP0003.html), etc.),
- Provide a developer API that can be used to implement and register V3 extensions,
- Improve the performance of Zarr-Python by streamlining the interface between the Store layer and higher level APIs (e.g. Groups and Arrays),
- Clean up the internal and user-facing APIs,
- Improve code quality and robustness (e.g. achieve 100% type hint coverage), and
- Align the Zarr-Python array API with the [array API Standard](https://data-apis.org/array-api/latest/).

In late 2023, we started working on the next version of the library, iterating on core concepts and restructuring the code base. While this effort continues today, here are a few highlights that we are particularly excited about:

- New asynchronous APIs across the library, including at the `Store`, `Group`, `Array`, and `Codec` levels. The ability for Zarr-Python to leverage asynchronous computation will dramatically improve performance in the library, particularly for workloads that depend on data coming from high-latency stores. We expect most users will interact with these classes through a synchronous interface but the asynchronous alternatives will be available for users that can take advantage of them.
- Complete spec-complaint implementation supporting both V2 and V3. Zarr-Python will support reading and writing in either format. Additionally, the V2 and V3 code paths will benefit from the new asynchronous interfaces as well as other performance improvements.
- New plugin interface for codecs. Previously, codec support was required to run through [Numcodecs](https://numcodecs.readthedocs.io/en/stable/). Going forward, additional codecs may be registered with Zarr-Python using the `zarr.codecs` [Entry Point](https://packaging.python.org/en/latest/specifications/entry-points/). While Numcodecs will continue to supply the Zarr-Python project with most codecs, the plugin interface will support the integration of codecs from other libraries.

## Release plan

We are still working hard on the 3.0 development branch. You can follow our progress on our [GitHub Project Board](https://github.com/orgs/zarr-developers/projects/5). In the coming weeks, we expect to move our development to the `main` branch of the library and make a series of pre-releases. 

## Get involved

It’s not too late to get involved with the 3.0 effort. The [GitHub Project Board](https://github.com/orgs/zarr-developers/projects/5) provides an up-to-date summary of outstanding issues. If you maintain a library that depends on Zarr-Python, the 3.0.0-alpha release will be a great time to start testing against the upcoming release. Finally, we continue to hold bi-weekly developer meetings to discuss and coordinate work on Zarr-Python. This is an open meeting so please come if you are interested in getting involved. Check out the Zarr community calendar [here](https://zarr.dev/community-calls/).

~Joe Hamman

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
