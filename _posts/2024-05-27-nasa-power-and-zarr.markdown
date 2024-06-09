---
layout: post
title: "NASA POWER 🤝🏻 Zarr"
description: Blog post on Zarr usage at NASA LARC's POWER project
date: 2024-06-08
categories: blog
permalink: /nasa-power-and-zarr/
---

## Hi Zarr Community! 👋🏻

Zarr's user, developer, and contributor base is growing every day across several scientific domains, including those responsible for mitigating climate change, solving complex biomedical issues, pushing the boundaries of AI development, and more.

National Aeronautics and Space Administration (NASA) is a prominent user and deeply invested in Zarr among the geospatial community. In this blog post, we'd like to highlight the NASA Prediction Of Worldwide Energy Resources (POWER) project, which has been using Zarr for its data storage needs. The POWER project is based at the NASA Langley Research Center (LaRC), which is located in Hampton, Virginia, USA.

### Introduction to POWER and Zarr 🎙

The [Prediction Of Worldwide Energy Resources (POWER)](https://power.larc.nasa.gov/) project is a cornerstone “Energy and Infrastructure” Earth Action Program project. The Project’s mission is to improve learning, decisions, and outcomes in the renewable energy, sustainable infrastructure, and agroclimatology user communities. For any location in the world, the project provides easily accessible, customized, and trusted NASA solar and meteorological data for past, current, and soon future climates. POWER improves the public and private capability for integrating these NASA Earth Observations (EO) and assimilation model data into their workflows by offering a diverse suite of tools and services to access this data. The project provides access to its Analysis Ready Data (ARD) via POWER’s Application Programming Interface (API), Data Access Viewer (DAV), geospatial services, and cloud-enabled data store. POWER offers no-cost, no-account-needed access to all of its tools, services, and data, which lowers the barrier to entry for many users across the globe. Additionally, through each of its tools and services, POWER’s multi-decadal, low-latency, high-accuracy, community-specific datasets are offered in user-customizable units and a wide variety of formats.

POWER is currently using Zarr as a backend data store for our API services that a lot of our users access to implement in their project’s needs. We have made the backend data stores directly available and freely accessible to the public with no use constraints through Amazon Web Services® (AWS®). We also plan to work with digital twins to integrate POWER data directly in for their data modelling. The POWER Project will continue leveraging the Zarr to store and serve data, which includes dynamic updates at Near Real Time (NRT) by the POWER Project’s data processing code base. Zarr enables the POWER Project to more efficiently support its user communities and impact decision-making for government agencies, non–profit organizations, universities, and private companies around the world.

🗄️ **Check POWER's Zarrs on AWS® Registry of Open Data: <https://registry.opendata.aws/nasa-power/>**

### A Brief History of Data Archives 📚

POWER’s meteorological parameters, such as temperature, humidity, precipitation, or wind are derived from the NASA’s Global Modeling and Assimilation Office (GMAO) Modern – Era Retrospective analysis for Research and Applications Version 2 (MERRA-2) assimilation model. MERRA – 2 is a version of NASA’s Goddard Earth Observing System (GEOS) Data Assimilation System. This data is available starting back in 1981.

The energy flux parameters, like solar irradiance and cloud properties, are derived from NASA’s [GWEX SRB](https://science.larc.nasa.gov/gewex-srb/) archive and NASA’s [CERES SYN1deg and FLASHFlux](https://ceres.larc.nasa.gov/data/) projects. This data is available dating back to 1984.

POWER’s ability to provide historical data allows users to access variability, make decisions, and conduct analyses based on past and current information. For more information on POWER’s history, please see our [documentation](https://power.larc.nasa.gov/docs/methodology/).

### What format did POWER use before? 🔙

Previously, POWER used a NetCDF file that was structed support temporal access by chunking along the line of dimension, in conjunction with OPeNDAP software used as middleware to support the POWER API’s temporal requests efficiently. While this system met initial requirements to provide daily data, the team had to explore new formats to meet the growing demand for hourly data.
NetCDF was no longer efficient for hourly data needs because NetCDFs is a condensed structure which prompted us to assess the use for Zarr since it is segmented.

### Why POWER switched? 🔍

The POWER Project selected the Zarr format as our Analysis Ready Data (ARD) format as we were transitioning from a monolithic server architecture to a microservice-based hybrid cloud hosted architecture environment, with the foresight of fully transitioning to a cloud environment. To support the key component of our services endpoints, the efficient and fast distribution of time-series data, we wanted to remove any middleware software, improve data access, and implement higher levels of data compression.

### Benefits after switching 💪🏻

Switching to Zarr enabled complete and direct access to the POWER data archives in an Analysis-Ready Cloud Optimized (ARCO) data store. Zarr also allows for asynchronous writing, JSON metadata, and a folder- based structure which allows us to add to the datastore faster and keep the data neatly sorted. Furthermore, POWER is able to utilize the higher level of data compression which reduces the speed for data acquisition. Lastly, being able to load small parts of the data improves efficiency, relevance and reduces costs.

For POWER’s future datastore, the Zarr’s enhanced compression was leveraged recently in initial testing which resulted in orders of magnitude smaller of total storage volume without losing any data precision. The result of this compression was saving on storage costs and increasing read/write performance of the system.

As a part of NASA’s Space Act Agreement with AWS®, this archive is hosted in S3 as part of the Open Data Registry, which provides the data freely to the public.

### Future plans for Zarr 🔮

The POWER Project plans to include both a spatial and time series based chunked data structures to better meet user demand for data and fulfill data
orders more quickly, to support more efficient access and analysis. To promote further understanding and enable effective search and discovery, the team will develop enhanced slice-based metadata.

POWER plans to use Zarr spatial data stores for ArcGIS Image Services in future data versions to cater to the needs of the GIS community.

~ [Zoe Waring](https://www.linkedin.com/in/zoe-waring/), [NASA POWER team](https://power.larc.nasa.gov/docs/team/)

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
