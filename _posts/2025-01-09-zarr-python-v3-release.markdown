---
layout: post
title: "Zarr-Python 3.0 is here!"
description: Zarr-Python 3.0 is here! This release brings support for Zarr's v3 specification and major performance improvements.
date: 2025-01-09
categories: blog
permalink: /zarr-python-v3-release/
---

After more than a year of development, we’re thrilled to announce the release of Zarr-Python 3.0! This major release brings full support for the Zarr v3 specification, including the new chunk-sharding extension, major performance enhancements, and a thoroughly modernized codebase. Whether you use Zarr to managing large multi-dimensional datasets in the cloud or for high-performance machine learning applications, Zarr-Python 3 has something for you. Let’s dive into some of the details of this release!

Zarr-Python is available today on [PyPI](https://pypi.org/project/zarr/) and [Conda-Forge](https://anaconda.org/conda-forge/zarr). It is compatible with Python 3.11 and above.

```bash
pip install --upgrade zarr
# or
conda install --channel conda-forge zarr
```

### Support for Zarr's v3 specification

The most notable addition in Zarr-Python 3.0 is complete support for Zarr's [v3 specification](https://zarr-specs.readthedocs.io/en/latest/v3/core/v3.0.html). The v3 specification brought greater multi-language interoperability and new extension points for customizing Zarr (codecs, chunk grids, data types, and stores).

Beyond supporting the core v3 specification, Zarr-Python 3.0 also includes support for the [chunk-sharding](https://zarr.dev/zeps/accepted/ZEP0002.html) extension. This feature allows for multiple chunks to be stored in a single file (or object), allowing users to utilize much smaller chunks without increasing the total number of objects in a dataset. Without chunk sharding, users optimizing for read-heavy applications had a difficult choice: either use a small chunk size, but create a huge number of stored objects, or use a large chunk size, but suffer poor IO for random reads into the data. With chunk-sharding, the number of stored objects is decoupled from the chunk size. Users can safely create very large Zarr arrays with very small chunks without generating a glut of stored objects. For more on how sharding works, see the [sharding documentation page](https://zarr.readthedocs.io/en/latest/user-guide/arrays.html#sharding).

```python
import numpy as np
import zarr

arr = zarr.create_array(
    "data/example-1.zarr",
    dtype="int32",
    zarr_format=3,
    shape=(1000, 1000),
    shards=(100, 100),
    chunks=(10, 10),
)
arr[:] = np.random.randint(0, 100, size=(1000, 1000))
```

Note that Zarr-Python 3.0 maintains read and write support for data stored according to Zarr’s v2 specification. Some features (e.g. sharding) are not available for v2 data. Users can set `zarr_format=2` in the top level API to continue using Zarr v2’s specification.

### Major performance improvements

Zarr-Python 3.0 delivers significant performance improvements across the board. A large part of the refactor focused on making the library fully asynchronous, using Python’s [asyncio](https://docs.python.org/3/library/asyncio.html) library. The new asynchronous core enables efficient I/O operations and better utilization of system resources. This means that multiple I/O operations can be performed concurrently, leading to faster data access and reduced latency, especially when data is stored on high-latency storage backends (like cloud object storage).

For compute bound operations (like compression), Zarr now dispatches to a managed thread pool. Combined with asynchronous IO, this threaded parallelization allows for Zarr to take full advantage of the compute resources available when reading and writing data.

<p align="center">
  <img src="../assets/images/zarr3-performance.png" alt="zarr3perf">
  <center> Performance analysis of Zarr-Python 3 relative to Zarr-Python 2.18.4. Test wrote and read a 1GB array (shape=(512, 512, 512), chunks=(512, 512, 8), dtype='float64') to and from AWS S3 from a _m6i.4xlarge_ VM in the same region. </center>
</p>

While we've made significant strides in performance optimization in the 3.0 release, we've done little performance tuning and expect to share more optimizations in future releases. We are actively working on identifying and addressing performance bottlenecks to further enhance the library's speed and efficiency.

### Built with extensions in mind

Zarr-Python 3.0 is [designed to be highly extensible](https://zarr.readthedocs.io/en/latest/user-guide/extending.html). Key features include:

- **New `Store` ABC:** A new abstract base class for defining custom storage backends, making it easier to integrate Zarr with various storage systems. This allows for seamless integration with cloud storage solutions, distributed file systems, and other data storage technologies.

    Zarr-Python 3.0 ships with support for the following stores:

    - `LocalStore` - for reading/writing to a [local file system](https://zarr-specs.readthedocs.io/en/latest/v3/stores/filesystem/v1.0.html)
    - `FsspecStore` - for reading/writing to remote/cloud storage (based on [fsspec](https://filesystem-spec.readthedocs.io/))
    - `ZipStore` - for reading/writing to a ZipFile (experimental)

    Additional stores are also in development (like [Earthmover’s](https://earthmover.io/) [Icechunk](https://icechunk.io/icechunk-python/quickstart/) store).

- **`Codec` and `CodecPipeline` Entrypoints:** Zarr-Python 3.0 provides [Python entry points](https://packaging.python.org/en/latest/specifications/entry-points/) for defining custom codecs and codec pipelines, enabling flexible data compression and encoding strategies. This empowers users to tailor data compression and encoding to specific use cases and optimize storage and performance.

    [Numcodecs](https://numcodecs.readthedocs.io/en/stable/zarr3.html) has been adapted to use Zarr’s `Codec` entrypoint system. And [`Zarrs-python`](https://zarrs-python.readthedocs.io/en/latest/) has already developed an experimental Rust-based `CodecPipeline`.


### Modernized Codebase

The Zarr-Python 3.0 codebase has been significantly modernized:

- **100% Type Hint Coverage:** Comprehensive type hints improve code readability, maintainability, and IDE support. This makes the code easier to understand, debug, and refactor, leading to higher code quality and reduced development time.
- **Cleanly Defined Public/Private API:** A clear distinction between public and private APIs enhances code organization and stability. This ensures that the public API remains stable and consistent, while allowing for flexibility and future development in the private API.
- **Improved Development Environment, CI/CD, and Testing:** A streamlined development workflow, robust CI/CD pipelines, and comprehensive testing ensure high-quality releases. This rigorous development process helps to identify and fix bugs early, leading to more reliable and robust software.

### Migration from Zarr-Python 2 to 3

We have done everything possible to make the migration from Zarr-Python 2 to 3 as easy as possible. The [3.0 migration guide](https://zarr.readthedocs.io/en/latest/user-guide/v3_migration.html) provides details the parts of the Zarr-Python API that have changed and provides suggested actions for migration. Additionally, libraries such as [Xarray](https://xarray.dev/), [Dask](https://www.dask.org/), have already added support for Zarr-Python 3.

### Conclusion

Zarr-Python 3.0 marks the beginning of a new chapter for the Zarr project. We encourage you to try out this new version and provide feedback. We're also excited to see the development of new extensions built on top of this solid foundation, such as Icechunk and Zarrs-Python.

The development of Zarr-Python 3 was a huge effort, spanning over 12 months and including contributions from over 30 contributors. Special thanks to [Davis Bennett](https://github.com/d-v-b) and [Norman Rzepka](https://github.com/normanrz) who helped me kick off the 3.0 refactor in Potsdam, Germany in December 2024.

**Further reading**

- [Zarr-Python 3 documentation](https://zarr.readthedocs.io/)
- [Zarr-Python 3 design doc](https://zarr.readthedocs.io/en/latest/developers/roadmap.html)
- [Zarr V3 Specification](https://zarr-specs.readthedocs.io/en/latest/v3/core/v3.0.html)

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
