---
layout: post
title: 'Versioning Zarr with EffVer'
description: We are updating the versioning policy for the Zarr python library.
date: 2025-01-09
categories: blog
permalink: /versioning-with-effver/
---

Back in January we released [Zarr-Python 3](https://zarr.readthedocs.io/en/v3.0.0/), the first new version of the library since 2016. While working on this release, we found that Zarr-Python's versioning policy didn't quite fit the needs of the project as it stands today. So we are modifying that versioning policy to make it better suited to the needs of Zarr-Python developers and users.

This post will explain what our old versioning policy was, why it wasn't working well for us, and why we are switching to ["Intended Effort Versioning"](https://jacobtomlinson.dev/effver/), or "EffVer".

### Our old versioning policy

The old Zarr-Python versioning policy was effectively [Semantic Versioning](https://semver.org/), or "SemVer". In this scheme, backwards-incompatible API changes may only be released in major versions, backwards-compatible API changes (i.e., adding new APIs) may only be released in minor or major versions, and bug fixes can be released in major, minor, or patch versions.

#### Friction with SemVer

The impetus for releasing Zarr-Python 3 was to support a new version of the Zarr format. So Zarr-Python 3 was released with a lot of new APIs; some of these APIs have bugs or warts. 

For example, we released some functions that *should* have consistent default values, but due to developer error (this author's error, in fact) those functions are inconsistent. [The fix](https://github.com/zarr-developers/zarr-python/pull/2819) is simple, in terms of code changes, but it requires breaking changes to our public API. According to SemVer, fixing this would require releasing Zarr-Python 4, only a few months after we released 3.

Besides fixing bugs in new APIs, we released Zarr-Python 3 with deprecation notices for many old APIs. We would like to eventually remove these routines from Zarr-Python, but we don't think it would match user expectations if we released a new major version of the library just to signify removing code. Again, this is contrary to SemVer.

Our users assume that major releases Zarr-Python will contain sweeping changes, not tiny adjustments to public APIs. So releasing version 4 of Zarr-Python because we changed the default values of a few functions would likely confuse people.

We learned that SemVer does not actually fit our project very well, so we decided to update the versioning policy accordingly. If you are interested in the developer discussion about this topic, see this [Github issue](https://github.com/zarr-developers/zarr-python/issues/2889).

### Our new versioning policy

We were accustomed to thinking about major releases of Zarr-Python as epochal events that offer lots of new functionality to users (like a brand new version of the underlying Zarr format), but also require substantial changes to existing code. In other words, while major releases likely contain backwards-incompatible changes, backwards-incompatible changes on their own don't really warrany a major release.

[Jacob Tomlinson](https://jacobtomlinson.dev/) extended this framing to a full versioning scheme, which he calls [Intended Effort Versioning](https://jacobtomlinson.dev/effver/), or "EffVer" for short. The basic idea of EffVer is that you version your project according to the expected effort a user will spend in upgrading to that version. 

- Major releases should contain changes have the most impact on users, and thus require the most effort to adopt.
- Minor releases can require some adoption effort from some users.
- Patch releases should require no adoption effort from users.

While SemVer indexes code changes by whether they are backwards compatible or not, EffVer indexes changes on how much effort is required for users to adapt to them. Thus EffVer allows us to ship small-but-breaking changes -- like changing default values of some recently-added functions -- in a minor release, so long as we think these changes will be easy for users to integrate.

### Conclusion

We think switching to EffVer is right for Zarr-Python development. It lets us refine newly-added APIs while reserving major releases for epochal changes, like the Zarr-Python 2 -> 3 transition. 

If you have any thoughts or concerns about this decision, we would love to hear from you. The best way to reach us is to open an [issue](https://github.com/zarr-developers/zarr-python/issues) or [discussion](https://github.com/zarr-developers/zarr-python/discussions) on our [Github page](https://github.com/zarr-developers/zarr-python). Thanks for your time!
