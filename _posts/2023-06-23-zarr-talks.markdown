---
layout: post
title: "Zarr, as seen in the public 📣"
description: Blog Post on Zarr talks
date: 2023-06-23
categories: blog
permalink: /zarr-talks/
---

## Hi Zarr Community! 👋🏻

Recently, I and several community members have been speaking at various conferences and events. There has been an exciting development in the Zarr ecosystem, like finalising V3 specification, submitting new ZEPs, initiating new implementations, etc.

While I’m mostly giving beginner talks on Zarr, which answers how, why, and what, the enthusiastic community members have been talking about other exciting stuff!

In this blog post, I highlight a few talks which were delivered in the past two months. Also, we’re maintaining a playlist on YouTube, which has a more extensive collection of talks from various domains and diverse speakers. Check the playlists: [Zarr: Introductory Talks](https://youtube.com/playlist?list=PLvkeNUPrCU04Xvcph4ErxsRkZq28Oucr7) and [Zarr: Projects, Uses, Research and Workflows](https://youtube.com/playlist?list=PLvkeNUPrCU05qHkZso_T74yoayqLFHzkI).

## PyCon DE and PyData Berlin 2023 🇩🇪

I went to Berlin, Germany, in April to speak at [PyCon DE and PyData Berlin 2023](https://2023.pycon.de/). My talk was titled “[The Beauty of Zarr](https://2023.pycon.de/program/JY3R3Z/)”, where I emphasised the inner workings using some near illustrations by [Trevor Manz](https://github.com/manzt). I highlighted how simple, convenient and hackable it is to use Zarr. After going through various explanations, I focused on some critical issues that Zarr eradicates because of its design and workings, i.e. chunking, compression, cloud-enabled etc. 

Towards the end, I prepared a [Jupyter notebook](https://github.com/MSanKeys963/presentations/blob/main/pycon_de_pydata_berlin_2023/notebook.ipynb) where I walked through Zarr 101 code to create, read, write and manipulate arrays. I also converted the Zarr pixelated logo from `.png` to `.zarr` format, which was a neat closing for my talk.

> The slides and notebook can be accessed [here](https://github.com/MSanKeys963/presentations/tree/main/pycon_de_pydata_berlin_2023).

Please watch the video here: 👇🏻

<iframe
    width="800"
    height="500"
    src="https://www.youtube.com/embed/OYaMi9WnQpA"
    frameborder="0"
    allow="autoplay; encrypted-media"
    allowfullscreen
>
</iframe>

## ESIP Meetings 🌏

[Earth Science Information Partners (ESIP)](https://www.esipfed.org/) is a community of data and information technology practitioners working together to coordinate earth science interoperability efforts. ESIP has various [collaboration areas](https://www.esipfed.org/get-involved/collaborate). ESIP Collaboration areas are made up of administrative committees and small working groups that are called clusters. Some of them are:

- Agriculture & Climate
- Open Science
- Cloud Computing
- Soli Ontology and Informatics
- Data Management Training Clearinghouse
- Council of Data Facilities

And many more.

The ESIP [Cloud Computing Cluster](https://wiki.esipfed.org/Cloud_Computing) organised a three-part series on Zarr titled “[Zarr: The Next Generation](https://discourse.pangeo.io/t/join-the-esip-cloud-computing-cluster-session-april-24-for-zarr-the-next-generation-part-2-3/3354)” In every part, the Zarr Community members talked about several things ranging from V3 to conventions to ZEPs.

> The first part took place on March 27th where:

- [Ryan Abernathey](https://github.com/rabernat/) presented on the [Zarr V3 Specification](https://zarr-specs.readthedocs.io/en/latest/v3/core/v3.0.html), i.e. [ZEP0001](https://zarr.dev/zeps/draft/ZEP0001.html)
- [Martin Durant](https://github.com/martindurant/) presented on the variable chunking, i.e. [ZEP0003](https://zarr.dev/zeps/draft/ZEP0003.html)

The video recording of the session can be seen here: 👇🏻

<iframe
    width="800"
    height="500"
    src="https://www.youtube.com/embed/50_LwbIUXi0"
    frameborder="0"
    allow="autoplay; encrypted-media"
    allowfullscreen
>
</iframe>


> The second part took place on April 24th where:

- [Briana Pagán](https://github.com/briannapagan) spoke about the current state of [GeoZarr specification](https://github.com/zarr-developers/geozarr-spec) and working group
- [Norman Rzepka](https://github.com/normanrz) spoke about the Sharding specification, i.e. [ZEP0002](https://zarr.dev/zeps/draft/ZEP0002.html)

The video recording of the session can be seen here:

<iframe
    width="800"
    height="500"
    src="https://www.youtube.com/embed/a4-vmJRQcrg"
    frameborder="0"
    allow="autoplay; encrypted-media"
    allowfullscreen
>
</iframe>


> The third part took place on May 22nd where:

- [Hailiang Zhang](https://github.com/hailiangzhang/) presented the accumulation proposal, i.e. [ZEP0005](https://zarr.dev/zeps/draft/ZEP0005.html)
- [Max Jones](https://github.com/maxrjones) spoke about [Kerchunk](https://github.com/fsspec/kerchunk) and [Pangeo-Forge](https://pangeo-forge.org/) recipes developments

The video recording of the session can be seen here:

<iframe
    width="800"
    height="500"
    src="https://www.youtube.com/embed/ROsHdJI3-yw"
    frameborder="0"
    allow="autoplay; encrypted-media"
    allowfullscreen
>
</iframe>


These meetings covered a great deal of recent developments in the Zarr ecosystem. The ZEPs mentioned above explained the V3 specification, sharding, and a couple of new exciting features the community is working on. The interesting thing to note here is that the ZEP0003 and ZEP0005 are something the community members wrote to support their use-case in their domain. This shows the openness and flexibility of the Zarr open-source community and how we support everyone. Though these ZEPs are still in the draft state, they’ll be finalised soon for adoption.

I will discuss about V3 specification in a separate blog post, so I’d not go into the details here. But it’s worth noticing GeoZarr specification and what Briana presented. GeoZarr is one of the conventions on top of Zarr specification, which support various use cases of the geospatial community on how they store their data and metadata. The GeoZarr SWG (Steering Working Group) has been working quickly despite the roadblocks (as mentioned by Briana). The progress and specification can be seen [here](https://github.com/zarr-developers/geozarr-spec).

## Conclusion

These are some of the public engagements done by the Zarr Community members in the past months. If you spoke on Zarr recently or in the past and would like me to highlight your talk, please don’t hesitate to contact [me](mailto:svsanketverma5@gmail.com). If you’re working on something interesting which involves Zarr and want to share it with the community, please say ‘Hi’ to me!

I’ll be talking to you all soon.

Until next time, peace! ✌🏻

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
