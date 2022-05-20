---
layout: post
title: "Pre-release of Zarr Python 2.12"
date: 2022-05-16
categories: blog
permalink: /pre-release-2-12/
redirect_from:
  - /release-2-12-0-a1/
---

Pre-release versions of
[Zarr Python](https://github.com/zarr-developers/zarr-python) `2.12`
are now available! 🎉

This blog post aims to overview new features, especially newly added
experimental support for reading and writing to Zarr V3, the upcoming
format for storing N-dimensional chunked compressed data.
This blog also highlights other enhancements like
creating `FSStore` from an existing fsspec filesystem, performance
improvement for Zarr arrays when appending data to S3, bug fixes,
documentation and a maintenance fix.

## Add support for reading and writing Zarr V3

Zarr Python 2.12 provides experimental infrastructure for reading and writing
the upcoming V3 spec of the Zarr format. Users wishing to prepare for the
migration can set the environment variable `ZARR_V3_EXPERIMENTAL_API` to begin
experimenting, however data written with this API should not yet be considered
final.

The new `zarr._store.v3` package has the necessary classes and functions for
evaluating Zarr V3. Since the design is not finalised, the classes and
functions are not automatically imported into the regular Zarr namespace.

The pre-release can be installed via: `pip install —pre zarr`.

There have been significant changes to
[Zarr's Python](https://github.com/zarr-developers/zarr-python) codebase to implement
V3 functionality. Highlights of the main changes include:

- A new function is added in `store.py`, which verifies that a key conforms to
  the [V3 specification](https://zarr-specs.readthedocs.io/en/core-protocol-v3.0-dev/).
- Added function in `store.py` to ensure internally that Zarr stores are always
  a class with a specific interface derived from `Store`, which is slightly
  different from `MutableMapping`.
- Separating `metadata` files from the data (arrays). Previously metadata and
  arrays were stored together in a consolidated group known as `.zgroup`.
- Changes in `convenience.py` to use Zarr V3. The default value is `None`; it
  will attempt to infer the version from `store` if possible; otherwise, it
  will fall back to V2.
- Consolidating all metadata for groups and arrays within the given store into
  a single resource and putting it under the given key. The changes can be seen
  [here](https://github.com/zarr-developers/zarr-python/blob/b9b9bf9e0577380222f2d7871e5272d8dfff9723/zarr/convenience.py#L1163)
  in `convenience.py`.
- Modification in `creation.py`, which enables the creation of an array using
  Zarr V3. If `None`, it will be inferred from `store` or `chunk_store`;
  otherwise defaults to V2.
- Updated `meta.py` with the new V3 data types links. The V3 data types are
  listed [here](https://zarr-specs.readthedocs.io/en/core-protocol-v3.0-dev/extensions/data-types.html).
- New tests added for all the new and modified features!

If you're interested in browsing through all of the code changes, please refer
to PR [#898](https://github.com/zarr-developers/zarr-python/pull/898).

The work on V3 was done by [Gregory Lee](https://github.com/grlee77) and was
funded by the [CZI](https://chanzuckerberg.com/eoss/). The Zarr Community
extends their wholesome gratitude to Gregory for completing this! 🙌

## Appending performance improvement

The old implementation iterated through all the `old` chunks and removed those
that didn't exist in the `new` chunks. As a result, it led to significant time
delays when appending data to Zarr arrays in cloud services like S3.

The new and improved implementation will iterate through each dimension and
only find and remove the chunk slices in `old` but not in `new` data. It also
introduced a mutable list to dynamically adjust the number of chunks along the
already-processed dimensions to avoid duplicate chunk removal.

This improvement was added by [hailiangzhang](https://github.com/hailiangzhang)
with PR [#1014](https://github.com/zarr-developers/zarr-python/pull/1014).

## Other enhancements

- If you have created a fsspec filesystem outside of Zarr, you can now pass it
  as a keyword argument to `FSStore`.

This feature was added by [Ryan Abernathy](https://github.com/rabernat) with PR
[#911](https://github.com/zarr-developers/zarr-python/pull/911).

- Added number encoder for `json.dumps` to support NumPy integers in `chunks` arguments. 

This enhancement was added by [Eric Prostate](https://github.com/ericpre) with
PR [#933](https://github.com/zarr-developers/zarr-python/pull/933) and the
issue was raised by [Mark Dickinson](https://github.com/mdickinson) with
[#697](https://github.com/zarr-developers/zarr-python/issues/697).

## Bugs, Documentation and Maintenance

Fix bug that made it impossible to create an FSStore on unlistable filesystems
(e.g. some HTTP servers) by [Ryan Abernathey](https://github.com/rabernat);
[#993](https://github.com/zarr-developers/zarr-python/issues/993).

Update resize doc to clarify surprising behaviour by
[hailiangzhang](https://github.com/hailiangzhang);
[#1022](https://github.com/zarr-developers/zarr-python/pull/1022).

Pre-commit configuration now includes `YAML` check by [Shivank
Chaudhary](https://github.com/Alt-Shivam);
[#1015](https://github.com/zarr-developers/zarr-python/issues/1015) &
[#1016](https://github.com/zarr-developers/zarr-python/issues/1016).

## More information

Details on these features as well as the full list of all changes in `2.12.0a1`
are available on the release notes. Check
[here](https://zarr--1023.org.readthedocs.build/en/1023/release.html#a1).

## Appreciation 🙌🏻

Before the pre-release version `2.12.0a1` there were releases `2.11.1`,
`2.11.2`, & `2.11.3` from Zarr Python package. A special shout-out to all the
contributors who made previous releases possible:

- [Tobias Kölling](https://github.com/d70-t)
- [Ben Jeffrey](https://github.com/benjeffery)
- [Vyas Ramasubramani](https://github.com/vyasr)
- [Tom White](https://github.com/tomwhite)

Also, a huge thanks to the contributors who made the current version `2.12.0a1`
possible! 🙌🏻

If you find the above features useful and end up using them, please mention
[@zarr_dev](https://twitter.com/zarr_dev) on Twitter and tweet using #ZarrData,
and we'll make sure to get it featured! ✌🏻

~Sanket Verma
