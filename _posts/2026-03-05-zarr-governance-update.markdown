---
layout: post
title: Evolving Zarr Governance
description: Updates to Zarr governance to streamline and simplify operations.
date: 2026-03-05
categories: blog
permalink: /governance-update/
---

# Evolving Zarr’s Governance

Authors: Ryan Abernathey, Alistair Miles, Josh Moore, Norman Rzepka,

In the ten years since its inception, Zarr has transformed the landscape of scientific data management. What started as a side project for a single genomics researcher frustrated with existing storage options has blossomed into critical scientific infrastructure for bioinformatics, bioimaging, geospatial, and Earth-system science. Zarr is in use in production at organizations such as NASA, NOAA, ESA, EMBL-EBI, Allen Institutes, Bi\[o\]hub, RIKEN, NVIDIA, Google, and Microsoft. Zarr was recently chosen as the next-generation format for the Copernicus Sentinel missions, which produce 40 Petabytes of data per year.

The reasons for this widespread adoption fall into two broad categories:

* **Technical** \- Zarr’s design offers superior performance, scalability, and extensibility than alternatives, especially in the cloud. The data model can accommodate a wide range of domain-specific scientific data schemas.  
* **Social** \- Compared to data formats controlled by a single vendor, Zarr’s open-source, community-based governance model appeals to organizations who care about long-term data sovereignty and stewardship.

The social reasons are not to be discounted; for many organizations, these are just as important as the technical ones. So as the Zarr community evolves and grows, so must its governance. Learning, evolving, and growing is essential to any well-functioning organization, and we have learned many lessons from the past few years. Today we are proposing updates to Zarr’s governance aimed at streamlining the development process and encouraging new contributors to get involved while recognizing the importance of maintaining stability and continuity.

**Current Challenges**

Zarr governance started as a “[BDFL model](https://en.wikipedia.org/wiki/Benevolent_dictator_for_life)”; the creator of Zarr, Alistair Miles, wrote the initial spec, built the first implementation (zarr-python), and was the sole owner of these things. Recognizing the value of empowering the community, in 2020 the Zarr Steering Council and current governance framework was established while moving the project under the umbrella of NumFocus as a fiscal sponsor. During this period, a significant number of new Zarr implementations emerged.

Building and maintaining a data format in a decentralized and community-driven way, without one organization or individual ultimately calling the shots, is not without its challenges. Today the Zarr community is feeling growing pains around governance in several ways:

* Development of extensions and conventions has been somewhat slow moving due to an ambiguous approval process  
* The agency of some individual projects within the zarr-developers GitHub org (e.g. zarr-python) is constrained by permissions limitations.  
* Ambiguity around the process for membership on Zarr’s various committees and groups.  
* Fragmentation of Zarr-related projects across many different GitHub organizations and repositories.

Our diagnosis of the root cause of these challenges is that Zarr governance has not fully evolved its single-project, single-repo structure to the multi-project reality of today. Additionally, project administrative issues have become intermingled with the constraints of GitHub’s IAM system, conflating governance with technical capabilities of this specific platform.

Going forward, our new proposed framework aims to clarify the roles and responsibilities of different stakeholders via more precise definitions.

**What is Zarr?**

The Zarr ecosystem today consists of the following entities.

* **The Zarr Project** \- The umbrella entity which is fiscally sponsored by NumFocus. NumFocus sponsored projects are required to have a formal governance process and may receive financial donations via the NumFocus 501c3.   
* **The Zarr Specification** \- A collection of documents defining the on-disk Zarr format.  
* **Affiliated Software Projects** \- Specific individual software projects (including the specification but typically Zarr implementations) which are considered *part of the Zarr Project*. These projects are eligible to receive funds via NumFocus and are therefore subject to the overarching Project governance framework.  
* **Non-Affiliated Software Projects** \- Other software projects which implement Zarr or interact with it in some way, but are not under the umbrella of the Zarr Project.

Our current governance challenges mostly stem from incomplete disambiguation between these different entities, and the resulting overloading of the authority of the ZSC. This ambiguity is exemplified by the current [governance doc](https://github.com/zarr-developers/governance/blob/main/GOVERNANCE.md), which lives at the zarr-developers org level. It’s unclear whether this applies to all repos within the zarr-developers org, and whether it applies to zarr-affiliated projects under other orgs. We aim to resolve this through the following resolutions.

1. The Zarr Project as a whole will remain governed by the Zarr Steering Council ZSC. Going forward, the Steering Council’s responsibilities include:  
   1. Interface between The Project and its fiscal sponsor  
   2. Manage the copyrights and trademarks associated with the Project  
   3. Manage the list of affiliated projects  
   4. Manage responsibilities which don’t belong to a specific affiliated project (e.g. Zarr website, GitHub org) in order to ensure smooth operations and effective collaboration.  
2. The Zarr Specification will be governed by a separate Spec Committee. The Spec Committee’s responsibilities are to  
   1. Manage changes to the Zarr core Specification  
   2. Maintain the list of Zarr Extensions  
3. Each Affiliated Software Project will be governed independently by a Core Developers Group (GDC) and will adhere to a simple governance process defined in a standardized document (below for more detail), without oversight from the ZSC.  
4. We are introducing a simple and transparent process for welcoming new Affiliated Software Projects.  
5. Non-affiliated Software Projects can of course continue to do their own thing however they wish, outside the boundaries of this framework, with whatever governance (or lack thereof) they choose. Non-affiliated projects are not eligible for direct funding via NumFocus. We welcome and encourage all Zarr-related projects to become affiliated.

These changes are formalized as a Zarr Enhancement Proposal ([ZEP-11](https://github.com/zarr-developers/zeps/blob/main/draft/ZEP0011.md)), which will now go through an approval process and receive feedback from the community.
Feedback should be shared via the [dedicated discussion issue](https://github.com/zarr-developers/zeps/issues/69) in the `zeps` repo.

**The Spec Committee**

The Zarr Spec is the focal point that brings together all of the different Zarr implementations. Because it addresses the on-disk format, decisions about the spec will persist for decades. Ensuring responsible and careful evolution of the spec, and balancing the need for innovation with the need for stability, is the challenge of the Spec Committee.

The evolution of the spec is currently governed by the ZEP process (see [ZEP0](https://zarr.dev/zeps/active/ZEP0000.html)). Changes to the spec currently require unanimous approval of the ZSC and majority approval of the Zarr Implementation Council (ZIC). In practice, the ZIC didn’t take shape in the way we had hoped. As implementations appeared and became inactive, the council’s membership adapted too slowly. Members frequently didn’t have the time needed to follow the ongoing GitHub conversations. The steering council also never set expectations around meetings or time limits on when decisions would be made. Looking back, the lack of clear time commitments and processes made it difficult for the ZIC to function effectively.

Instead, we propose moving to a single Spec Committee. This is what other successful, widely adopted file formats (like Apache Parquet) do. To provide continuity with the current system, initial membership of the Spec Committee will include the current members of both the ZSC and the ZIC; however, these members are encouraged to resign if they don’t plan to actively participate. It is expected that the Spec Committee will contain members of the most active Zarr implementations, including both Affiliated and Non-affiliated Software Projects.

The Spec Committee's primary mandate is to manage the core specification and to review and approve Zarr Extensions. To streamline decision-making and ensure agility, the first task of the newly formed Spec Committee will be to establish and document its own operational governance model, including decision-making procedures (e.g., voting mechanisms and quorum requirements) and membership review. This new process will supersede the unanimous ZSC/majority ZIC approval process currently defined in ZEP0 for all future core specification changes.

**Governance for Affiliated Software Projects**

Affiliated Software Projects will now follow a simple, standard, merit-based governance process akin to the Apache model. The default governance for Affiliated Software Projects is spelled out in an accompanying governance document: [Draft: Governance for Zarr Affiliated Software Projects](https://docs.google.com/document/d/1WDl25LgYEcqJZK8qd1AL0qVcXo9O9F8D4jSY13gzCXA/edit?tab=t.0).

This governance initially consists of the following key elements:

* Each project has a group called the Core Developers Group (CDG) which makes decisions, e.g. about accepting PRs. (A group of one is fine for small projects.)  
* Projects aim for consensus, falling back on majority vote of Core Developers when necessary.  
* Any contributor is eligible to join the CDG. Existing Core Developers can nominate new members. Nominations should be based on evidence of sustained, quality contribution to the project. Nominations are accepted by majority vote of existing Core Developers.  
* Core Developers who become inactive can and should be removed, via a majority vote.  
* Larger groups should have a chair, who acts as a facilitator / coordinator.  
* Projects must adhere to the Zarr code of conduct, which is a requirement for NumFocus fiscal sponsorship.

Projects are free to evolve and change their governance as they see fit, provided it remains within the accepted norms of community open-source projects. If an affiliated project abandons open and transparent governance, the ZSC reserves the right to remove its affiliation.

Current affiliated projects are:

- The Zarr Specification  
- Zarr-Python (incl. Numcodecs)  
- Zarr-java  
- jzarr  
- GeoZarr  
- VirtualiZarr

Going forward, we welcome new affiliated projects to join. To be considered for affiliation, a project must be open source, be directly related to Zarr, and demonstrate a critical mass of sustained development activity. The ZSC will make decisions about affiliation based on these criteria and the overall strategic direction of The Project.

**Non-Affiliated Software Projects**

The Zarr ecosystem contains several important implementations that are not formally affiliated with the numfocus-sponsored Zarr Project. These include Tensorstore, Zarrs, and Zarr.jl. This is great and speaks to the vitality of the Zarr ecosystem. 

For projects which do wish to be formally affiliated with the Zarr Project, and thereby benefit from the NumFocus fiscal sponsorship, we extend an open invitation to join. We hope the governance changes introduced here make this appealing and clarify the light-weight governance expectations around affiliated projects. Conversely, non-affiliated projects are totally fine as-is and are under zero pressure to change their approach to governance.

**The Role of GitHub**

The use of GitHub by the Zarr Project is purely an implementation detail. GitHub is a tool which helps us manage code. GitHub roles, groups, and repos do not have any formal status within the Zarr governance framework.

That said, in practice, we are heavily reliant on GitHub for day-to-day operations, and clarity is needed about how to map various roles and responsibilities to specific capabilities and functions within GitHub. Zarr is mission critical code for hundreds of organizations, and security must be taken seriously. Because privileges in GitHub map to ability to commit and release code, we aim to adhere to a “principle of least privilege” model, wherein different actors have only the minimal privileges required to perform their function. This minimizes the blast radius for any potential threat. For example, a compromised GitHub account for a maintainer in one affiliated project should not be able to impact a different affiliated project.  
Consistent with existing practice, we make the choice that all affiliated software projects will live within the same GitHub organization: `zarr-developers`. The reasons for this are:

* It provides a central entry point into all outputs of of the NumFocus-sponsored Zarr Project, aiding discoverability  
* It allows affiliated projects to share resources, including paid capabilities of the GitHub platform

Each Affiliated Software Project, including the Zarr Spec itself, will have responsibility for one or more repos under this parent organization. Each affiliated project will manage its own committee membership via a GitHub group. Ownership of the GitHub org as a whole will be managed by the ZSC, including creation of new repos and the creation of groups.

There is one technical limitation of GitHub which must be addressed: new members to the organization can only be added to existing groups by organization owners. This makes the ZSC a bottleneck on the autonomous operation of each affiliated project. As a workaround, we will set up a github bot which automatically updates group membership based on a list of committee members within each repo. This will effectively allow each affiliated project to manage its own membership independently.

**What’s Next?**

It’s an exciting time for Zarr. The recent creation of the extensions and conventions frameworks are motivating lots of creative new directions for development. Our goal with these governance updates is to cast off the last vestiges of Zarr’s early governance and replace it with a model that is appropriate to the multifaceted character of the Zarr Project today. This model is based on proven, established best practices for multi-stakeholder, community-developed open-source software projects. Once fully implemented, these governance updates will empower developers to work more effectively and eliminate unnecessary centralization of authority within the ZSC.

