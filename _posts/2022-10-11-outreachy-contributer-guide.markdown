---
layout: post
title: "Outreachy Contributer Guide 2022"
description: Blog Post on Outreachy Contributer Guide
date: 2022-10-11
categories: blog
permalink: /outreachy-contributer-guide/
---

### Hi Outreachies! 🙋🏻‍♂️

We’re elated to see the initial participation from interns in the contribution period for the [Outreachy](https://www.outreachy.org/) December 2022 cohort. This blog post aims to briefly explain how you can contribute to Zarr open-source project and prepare yourself for the listed projects [here](https://www.outreachy.org/apply/project-selection/#zarr).

Zarr has submitted three projects for Outreachy this time, and every project requires a fundamental understanding of Zarr along with some additional skills for every project. So though the initial steps for all three projects remain the same, I’d explain the contribution steps for every project separately, emphasising some of the essential skills required for each. Before we start, here are some of the important links:

- Website: [https://zarr.dev/](https://zarr.dev/)
- Documentation: [https://zarr.readthedocs.io/en/stable/](https://zarr.readthedocs.io/en/stable/)
- Gitter Chat: [https://gitter.im/zarr-developers/outreachy-contributors-dec-2022](https://gitter.im/zarr-developers/outreachy-contributors-dec-2022)
- Outreachy projects: [https://www.outreachy.org/apply/project-selection/#zarr](https://www.outreachy.org/apply/project-selection/#zarr)

## Create tutorials for Zarr

Outreachy project link: [https://www.outreachy.org/outreachy-december-2022-internship-round/communities/zarr/#create-tutorials-for-zarr](https://www.outreachy.org/outreachy-december-2022-internship-round/communities/zarr/#create-tutorials-for-zarr)

> Please go through the complete project details. You may need to sign in/sign-up to see them. 👀

- Set up Zarr on your local/cloud system. Zarr is available via [pip](https://pypi.org/project/zarr/) and [conda](https://anaconda.org/conda-forge/zarr).
- We’d prefer virtual environments as they’d enable you to keep Zarr separate from other packages. This can be done using Python virtual environment or a conda virtual environment. We prefer conda virtual environments as you’ll be using [Jupyter notebooks](https://jupyter.org/) heavily for this project.
- If you’re not familiar with Python or conda virtual environments, please refer [here](https://packaging.python.org/en/latest/guides/installing-using-pip-and-virtual-environments/#creating-a-virtual-environment) for Python and [here](https://docs.conda.io/projects/conda/en/latest/user-guide/getting-started.html#managing-environments) for conda.

> Feel free to ask questions related to setting-up Zarr in the Gitter chat. 🙋🏻‍♂️

Once you’re done setting up Zarr:

- Make yourself familiar with Zarr by going through the existing [tutorials](https://zarr.readthedocs.io/en/stable/tutorial.html). These tutorials provide a smooth entry point for understanding Zarr and how to use it. We’d encourage you to try the code yourself using Jupyter notebooks!
- Additionally, there are great introductory and hands-on videos on Zarr over here: [https://www.youtube.com/channel/UChjAUriJ18ksReZhoWHdcHw/playlists](https://www.youtube.com/channel/UChjAUriJ18ksReZhoWHdcHw/playlists).
- After you’re done with the tutorials, please head over to the open issues in the zarr-python repository having tags [help wanted](https://github.com/zarr-developers/zarr-python/labels/help%20wanted), [low-hanging fruit](https://github.com/zarr-developers/zarr-python/labels/low-hanging-fruit), [good first issue](https://github.com/zarr-developers/zarr-python/labels/good-first-issue), [documentation](https://github.com/zarr-developers/zarr-python/labels/documentation) and comment on an issue you’d like to start working on.
- If you cannot find a specific issue to work on and need some help, please head to our [Outreachy Gitter chat](https://gitter.im/zarr-developers/outreachy-contributors-dec-2022), and the mentors will assist you.

> PS. We’d strongly encourage you to go through the list of open issues first and then ask for help in the Gitter chat.

## Managing Zarr Releases with Rever

Outreachy project link: [https://www.outreachy.org/outreachy-december-2022-internship-round/communities/zarr/#managing-zarr-releases-with-rever](https://www.outreachy.org/outreachy-december-2022-internship-round/communities/zarr/#managing-zarr-releases-with-rever)

> Please go through the complete project details. You may need to sign in/sign-up to see them. 👀

- You can follow the same steps for setting up Zarr on your local/cloud system as mentioned above. Of course, we’d prefer you to use [Python virtual environments](https://packaging.python.org/en/latest/guides/installing-using-pip-and-virtual-environments/#creating-a-virtual-environment) for this project, but both are fine.

Once you’re done setting up Zarr:

- Follow the [docs](https://zarr.readthedocs.io/en/stable/), [tutorials](https://zarr.readthedocs.io/en/stable/tutorial.html) and [videos](https://www.youtube.com/channel/UChjAUriJ18ksReZhoWHdcHw/playlists) to familiarise yourself with Zarr.
- Now, please head over to the Rever [documentation](https://regro.github.io/rever-docs/). Rever has [tutorials](https://regro.github.io/rever-docs/tutorial.html), [workflows](https://regro.github.io/rever-docs/news.html), and [contributor and authorship tracking](https://regro.github.io/rever-docs/authorship.html) in their documentation which are super helpful.

Once you’re done with Rever’s documentation, try to create [rever.xsh](https://regro.github.io/rever-docs/#initializing-rever) in the [zarr-python](https://github.com/zarr-developers/zarr-python) repository.

- After you’re done with the tutorials, please head over to the open issues in the zarr-python repository having tags [help wanted](https://github.com/zarr-developers/zarr-python/labels/help%20wanted), [low-hanging fruit](https://github.com/zarr-developers/zarr-python/labels/low-hanging-fruit), [good first issue](https://github.com/zarr-developers/zarr-python/labels/good-first-issue), [documentation](https://github.com/zarr-developers/zarr-python/labels/documentation) and comment on an issue you’d like to start working on.
- If you cannot find a specific issue to work on and need some help, please head to our [Outreachy Gitter chat](https://gitter.im/zarr-developers/outreachy-contributors-dec-2022), and the mentors will assist you.

> PS. We’d strongly encourage you to go through the list of open issues first and then ask for help in the Gitter chat.

## Testing the support and interoperability of Zarr Zip Stores

Outreachy project link: [https://www.outreachy.org/outreachy-december-2022-internship-round/communities/zarr/#testing-the-support-and-interoperability-of-zarr-z](https://www.outreachy.org/outreachy-december-2022-internship-round/communities/zarr/#testing-the-support-and-interoperability-of-zarr-z)

> Please go through the complete project details. You may need to sign in/sign-up to see them. 👀

- You can follow the same steps for setting up Zarr on your local/cloud system as mentioned above. Of course, we’d prefer you to use [Python virtual environments](https://packaging.python.org/en/latest/guides/installing-using-pip-and-virtual-environments/#creating-a-virtual-environment) for this project, but both are fine.

Once you’re done setting up Zarr:

- Follow the [tutorials](https://zarr.readthedocs.io/en/stable/tutorial.html) and [videos](https://www.youtube.com/channel/UChjAUriJ18ksReZhoWHdcHw/playlists) to make yourself familiar with Zarr. This specific project at least requires an understanding of Zarr fundamentals.
- Now, please head over to the [storage classes](https://zarr.readthedocs.io/en/stable/api/storage.html) in Zarr [documentation](https://zarr.readthedocs.io/en/stable/). One of the methods inside [zarr.storage](https://zarr.readthedocs.io/en/stable/api/storage.html) is [ZipStore](https://zarr.readthedocs.io/en/stable/api/storage.html#zarr.storage.ZipStore), which essentially stores Zarr arrays and groups using a Zip file. For this project, we would like to test the support and interoperability of ZipStores among various [Zarr implementations](https://github.com/zarr-developers/zarr_implementations).
- After you’re through with the ZipStore documentation and running the code, please head over to the zarr-python [codebase](https://github.com/zarr-developers/zarr-python/tree/main/zarr), especially [storage.py](https://github.com/zarr-developers/zarr-python/blob/main/zarr/storage.py) and go through them.

Once you’re done with the above steps, create a [ZipStore](https://zarr.readthedocs.io/en/stable/api/storage.html#zarr.storage.ZipStore) using [zarr-python](https://github.com/zarr-developers/zarr-python/tree/main/zarr) and test the support across various [Zarr implementations](https://github.com/zarr-developers/zarr_implementations).

- Next, please head over to the open issues in the zarr-python repository having tags [help wanted](https://github.com/zarr-developers/zarr-python/labels/help%20wanted), [low-hanging fruit](https://github.com/zarr-developers/zarr-python/labels/low-hanging-fruit), [good first issue](https://github.com/zarr-developers/zarr-python/labels/good-first-issue), [documentation](https://github.com/zarr-developers/zarr-python/labels/documentation) and comment on an issue you’d like to start working on.
- If you cannot find a specific issue to work on and need some help, please head to our [Outreachy Gitter chat](https://gitter.im/zarr-developers/outreachy-contributors-dec-2022), and the mentors will assist you.


> PS. We’d strongly encourage you to go through the list of open issues first and then ask for help in the Gitter chat.

- Once you’re assigned an issue, you can start working on it and send a [GitHub pull request](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/creating-a-pull-request) for the same.

→ Once your PR is accepted and merged, you’ve successfully passed the Outreachy contribution phase. 🎉

Now you have to wait for the final results, or you can start working on additional issues to increase your chances of selection. 🤞🏻


If you have any queries during the contribution phase, don't hesitate to ask them in the Gitter. We're here to help you!

Happy Contributing! ✌🏻

~Sanket Verma