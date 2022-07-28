---
layout: post
title: "Zarr EOSS4 Roadmap"
description: Blog Post on Zarr Accomplishments and Roadmap
date: 2022-07-26
categories: blog
permalink: /eoss4-roadmap/
---

### Hola Zarr Community! 🙋🏻‍♂️

I hope my previous blog was a good read and worth your time. Just to shed some
light on [ZEPs](https://zarr.dev/blog/zep-inception/), recently, [ZEP1](https://zarr.dev/zeps/draft/ZEP0001.html) was submitted by [Alistair Miles](https://github.com/alimanfoo) and [Jonathon Striebel](https://github.com/jstriebel) and is currently under review by the [Zarr Implementations Council](https://github.com/zarr-developers/governance/blob/main/GOVERNANCE.md#zarr-implementation-council-zic) and the Zarr community.
Feel free to leave your thoughts on ZEP1 [here](https://github.com/zarr-developers/zarr-specs/pull/149). I’m pleased to see the
ZEP process in work and hope it assists the Zarr community in systematically
achieving critical milestones.

In early 2021, we submitted a proposal to the [Chan Zuckerberg Initiative’s
(CZI) Essential Open Source Software for Science (EOSS)](https://chanzuckerberg.com/eoss/) grant program. The proposal
aimed to accelerate Zarr’s development on issues often too significant to
tackle through volunteers’ contributions. Some of the high-level goals we
focused on using the grant were API unification across open-source projects
like NumPy, Dask, Xarray, project maturity, and efficient community engagement.
The Zarr Community along with the [Zarr Steering Council](https://github.com/zarr-developers/governance/blob/main/GOVERNANCE.md#zarr-steering-council)
spent almost a year working towards these goals, and
we’re proud to say that we’ve made significant progress.

As promised in the last blog, I will talk about what we’ve accomplished so far
apart from ZEPs and what the upcoming months for the Zarr project and the
community look like. Also, I’ll shed some light on the deliverables we’ve
completed under the [CZI EOSS4](https://chanzuckerberg.com/eoss/proposals/?cycle=4) grant.

## CZI EOSS4 Accomplishments 📝

### Technical Deliverables 🧑🏻‍💻

> API Unification

The Zarr format lets you store big-size arrays into small compressed chunks,
making collaborations with various array-providing projects like NumPy and Dask
a must. API unification plays a crucial role in interoperability. This
will allow the OSS community to transparently choose between implementations
making algorithms more generalisable and scalable.

We identified several discrepancies between Zarr and related projects ([NumPy](https://github.com/numpy/numpy) and 
[Dask](https://github.com/dask/dask)) and corrected them. [Juan Nunez-Iglesias](https://github.com/jni) 
worked on adding support for fancy indexing, and [Ben Jeffrey](https://github.com/benjeffery) 
fixed indexing for scalar NumPy values. See [*zarr-python #725*](https://github.com/zarr-developers/zarr-python/pull/725) 
and [*zarr-python #974*](https://github.com/zarr-developers/zarr-python/pull/974) respectively.

[Mads R.B. Kristensen](https://github.com/madsbk) worked on adding support for
multiple array types. See [*numcodecs #305*](https://github.com/zarr-developers/numcodecs/pull/305).
If you know of other ways that we could make Zarr work more cleanly with Dask,
NumPy or other array APIs, please let us know. (How?)

> Xarray / NetCDF Interoperability

[NetCDF](https://github.com/unidata/netcdf-c/) (a long-time provider of stable
file format) and [Xarray](https://github.com/pydata/xarray/) (N-D labelled
arrays) have been updated to support each other’s project representation.
[Mattia Almansi](https://github.com/malmans2) worked on adding support from
Xarray’s side see [*xarray #6420*](https://github.com/pydata/xarray/pull/6420) and [Dennis Heimbigner](https://github.com/DennisHeimbigner) 
worked from NetCDF’s side, see
[*netcdf-c #2257*](https://github.com/unidata/netcdf-c/pull/2257). Also, both
projects have agreed to discuss a common Zarr Specification, and a proposal is
being drafted for a common standard for named dimensions.

> Multiscale array representation

The [‘datatree’ library](https://github.com/xarray-contrib/datatree) by
[Thomas Nicholas](https://github.com/TomNicholas) and supported by [B-open](https://www.bopen.eu/) can now be used to represent a pyramid of related
arrays and has been proposed as a standard data structure. Also, bioimaging
users from ITK have tested the data structure, and dimensions have begun for
integration into [Napari](https://github.com/napari/napari).


These goals were mainly focused on Zarr’s technical development, which revolves
around working collaboratively with critical open-source projects in the array
storage ecosystem. We will continue working towards strengthening the bridges
of interoperability with other projects in the upcoming months.

## Community Engagement 👨‍👩‍👧‍👦🔗👫

In this section, I’d be mainly talking about the community engagement part of
Zarr. For my part, I’ve focused on:

- The first and foremost thing I did when I started my role was to relaunch the
  Zarr Blog over at the new URL: [https://zarr.dev/blog](https://zarr.dev/blog). The newly launched blog
  post contains blog posts regarding releases, ZEPs and any further
  event/information vital for the Zarr community. I also worked on revamping
  Zarr’s webpage, which is at [https://zarr.dev/](https://zarr.dev/). Currently, I’m asynchronously
  working on a new website for Zarr and if you have any thoughts feel free to
  share them with [me](mailto:svsanketverma5@gmail.com).

- Zarr is participating in [Google Summer of Code](https://summerofcode.withgoogle.com/) for the first time this year. We made
  a list of exhaustive potential project lists, which can be seen [here](https://github.com/zarr-developers/gsoc/blob/main/2022/ideas-list.md). After
  going through several applications, we shortlisted [Shivank Chaudhary](https://github.com/alt-shivam) and [Parth Tripathi](https://github.com/parthxtripathi/) to work on [Building Codecs Registry](https://summerofcode.withgoogle.com/programs/2022/projects/g4IPN5HL) and
  [Benchmarking Zarr Implementations](https://summerofcode.withgoogle.com/programs/2022/projects/qa93Xk9L) respectively. I
  believe participating in open-source programs led by organisations is an
  excellent way to invite and collaborate with new contributors.

- We also worked on increasing participation in conferences and meet-ups. For
  example, I spoke about Zarr at [Open Geospatial Conference](https://youtu.be/KiiKvXzhyMs) along with 
  [Ryan Abernathey](https://youtu.be/unGL07trSjA). I also presented at my local [PyData chapter](https://youtu.be/EDXxytmCGqw) 
  and was elated to see the engaging interaction with the community.

- Zarr V2 is now an [OGC Standard](https://portal.ogc.org/files/100727) thanks
  to efforts led by [Ryan Abernathey](https://github.com/rabernat/).

- Apart from physically reaching out to the community, we also worked on our
  social media presence by actively tweeting and blogging about Zarr.

- The Zarr community needed a structural process to handle incoming changes to
  the Zarr Specification and accelerate the development of Zarr Specification
  V3. This led to the [inception of ZEPs](https://zarr.dev/blog/zep-inception/) and
  [ZIC](https://github.com/zarr-developers/governance/blob/main/GOVERNANCE.md#zarr-implementation-council-zic).

- We made new stickers for the project, and I was thrilled when they were
  delivered. We’ve already distributed many of them and will give them in
  future meetings.

<p align="center">
  <img src="../assets/images/zarr_sticker.jpeg" alt="zarr_sticker" width="270">
  <center> Zarr Sticker </center>
</p>


We achieved a few high-level goals that would help strengthen and bring the Zarr
community close. Apart from these, I’ve also been assisting with [Zarr-Python](https://github.com/zarr-developers/zarr-python)
releases, managing community calls, regular maintenance of Zarr repositories and working closely with
various [Zarr Implementations](https://github.com/zarr-developers/zarr_implementations).


## What does the future look like? 🔮

I’m very excited and looking forward to Zarr’s future. Having a systematic
process in place and a dedicated community manager has streamlined the
technical and community development for Zarr and its various implementations.
Since [ZEP0001](https://github.com/zarr-developers/zarr-specs/pull/149) is in
its initial review phase, we believe that the implementation of [Zarr V3](https://zarr-specs.readthedocs.io/en/latest/core/v3.0.html) 
is the next potential and upcoming change. In upcoming months, we will be focusing on:

- Implementing Zarr Specification V3 across multiple programming languages
- Implementing Sharding w/ [scalable minds GmbH](https://scalableminds.com/)
- Zarr User Survey 2022 to better understand the community needs
- Contracting with Python-based developers and organisations to add new features like IPFS and extensions like:
  - [Fsspec](https://github.com/fsspec/) Integration
  - Development of Sparse Arrays
- Improving visibility of the project by presenting at conferences and meet-ups
- Aggregating Zarr data from the community and showcasing them on our website

## Conclusion 🙌🏻

In conclusion, our first year with CZI EOSS4 grant has achieved some important
milestones. We solved some of the crucial technical and community problems
which have paved a smooth path for further development. We believe the upcoming
progress will be in streamlined and much more systematic manner.

As for me, it's been six months since I started working with the [wonderful humans](https://gitter.im/zarr-developers/community#people)
of Zarr, and every day I get to learn something new in terms of community
engagement, technical skills or as simple as talking and teaching about Zarr to
a group of humans. I believe that the future of Zarr looks promising and
there are many more exciting things yet to come!

Thanks for reading this blog post. If you’d like to contribute to Zarr in any
manner feel free to ping me or drop a 'Hi🙋🏻‍♂️' over at our [Gitter](https://gitter.im/zarr-developers/community) channel. Talk to you soon! 

~Sanket Verma
