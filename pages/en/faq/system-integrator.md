---
title: Discover OpenData as a system integrator
keywords:
description: Discover OpenData as a system integrator
reuses:
datasets:
---

Discover OpenData as a system integrator
==========================================

The "data.public.lu" platform offers you several more or less advanced ways to integrate the data available in open data on your own sites:

1. in a unitary way if you want to display only one or a few particular dataset(s);
2. more generally if you want to display all the datasets relating to a territory or an organization;
3. for detailed management of the skin and the data displayed, we recommend the API;
4. to have your own portal based on the platform engine.

These different cases of integration generally correspond to different profiles:

1. a journalist dealing with a given issue will be interested in including datasets directly in his article;
2. a town hall will be interested in integrating data sets relating to its territory on its website;
3. an association might be interested in creating a personalized page compiled from data from multiple sources;
4. a country embarking on open data will seek to create its own portal.

Whatever your needs or your profile, we are here to support you in your process of disseminating open data. Below, the technical documentation corresponding to each of the cases mentioned:

1\. Ad hoc integration of datasets
----------------------------------------------

Each dataset can be integrated on any page by adding two lines of HTML:

    <div data-udata-dataset-id="DATASET ID"></div>
    <script src="https://data.public.lu/static/widgets.js" id="udata" async defer onload="udataScript.loadDatasets()"></script>
    

By replacing the `DATASET IDENTIFIER` with the identifier available on its dedicated page, you should see a box appear on your site containing the information relating to this dataset as follows:

It is possible to integrate several datasets at the same time by duplicating the line corresponding to the `<div>` element with a new identifier. You can customize the appearance of the title block rendering with the `dataset-card` CSS class.

2\. Integration for an organization or territory
-------------------------------------------------- ----

Please note: this type of integration is currently under development and the API is subject to change. Please contact us if you would like to participate in the preliminary tests.

The mechanism for displaying all the datasets relating to an organization or territory is the same as that for the integration of a single dataset described above.

This usage is recommended if you are responsible for this organization or territory and want to promote related datasets.

### 2.1 Integration of an organization

    <div data-udata-organization="ORGANIZATION IDENTIFIER"></div>
    <script src="https://www.data.public.lu/static/widgets.js" id="udata" async defer onload="udataScript.loadOrganization()"></script>
    

By replacing the `ORGANIZATION IDENTIFIER` with the identifier available on its dedicated page, you should see a box appear on your site containing the information relating to the datasets of this organization as follows:

Optionally, it is possible to display a search bar to allow the visitor to filter the list of datasets displayed. This is enabled by passing the `{withSearch: true}` option to the `loadOrganization()` method above.

3\. Integration of a complete open data portal
----------------------------------------------

The tools we develop are available in open-source. They are the result of an international effort to create synergies around open data and pool our development efforts. The governance is inclusive and the license is permissive. We participate in the animation around the development of the platform because we want to produce a common good reusable by all.

The integration of a complete open data portal requires skills in system administration, Python and JavaScript development as well as a significant time to get to grips with the platform. This is a choice that must be carefully considered and we recommend that you go directly through "data.public.lu" if you have data from French-speaking territories.

If you still want to embark on this adventure, you can start by analyzing the [source code](https://github.com/opendatateam/udata) as well as the [dedicated documentation](http://udata.readthedocs.io /en/latest/). You can also come to [chat with the community](https://gitter.im/opendatateam/udata).


[← Back to FAQ home](/en/pages/faq/)
