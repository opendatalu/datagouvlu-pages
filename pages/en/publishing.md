---
title: Guidelines for the publication of open data in Luxembourg
keywords:
description: Guidelines for the publication of open data in Luxembourg
reuses:
datasets:
---

Guidelines for the publication of open data in Luxembourg
=========================================================

The following guidelines for the publication of datasets as open data in Luxembourg are adapted from sections of the [Open Data Handbook](http://opendatahandbook.org/) by the Open Knowledge Foundation.

What is Open Data?
------------------

The [Open Definition](http://opendefinition.org/) defines open data as data that can be freely used, re-used and redistributed by anyone - subject only, at most, to the requirement to attribute and share alike. Important aspects are:

*   **Availability and access:**the data must be available as a whole and at no more than a reasonable reproduction cost, preferably as internet downloads. The data must also be available in a convenient and modifiable form.
*   **Re-use and redistribution:**the data must be provided under terms that permit re-use and redistribution including the intermixing with other datasets.
*   **Universal participation:**everyone must be able to use, re-use and redistribute - there should be no discrimination against fields of endeavor or against persons or groups. For example, restrictions that would prevent commercial use, or certain purposes (e.g. only in education), are not allowed.

The principal goal of this openness of datasets is their interoperability, i.e. the ability to intermix with other datasets. The combination of different datasets together potentially leads to more and better products and services.

What Data can be opened up?
---------------------------

Data that is not subject to legal publication restrictions, like for example in case of personal data, intellectual property, national security aspects ... can principally be taken into consideration to be made available as open data. In case of public sector bodies, the publication of data is ruled by the [Law on open data - Loi du 29 novembre 2021 sur les données ouvertes et la réutilisation des informations du secteur public](https://legilux.public.lu/eli/etat/leg/loi/2021/11/29/a836/jo). The focus is on non-personal data, which does not contain information about specific individuals.

What strategy should be adopted for opening up data?
----------------------------------------------------

Three general principles are recommended when opening up data:

*   **Keep it simple.** Start out small, simple and fast. There is no requirement that every dataset must be made open immediately - it is better to quickly start out by opening a first one and to continuously add more later on, because one can build momentum and learn from experience.
*   **Engage early and engage often.** Engage with actual and potential users and re-users of the data as early and as often as possible, be they citizens, businesses or developers. This will ensure that the next iteration of the service is as relevant as it can be. It is essential to bear in mind that much of the data will not reach end-users directly, but rather via people who initially take the data and transform or remix it to be presented for others.
*   **Address common fears and misunderstandings.** Opening up data will generate plenty of questions and fears. It is important to identify the most important ones and address them at as early a stage as possible. Be aware that not necessarily every dataset will be useful, and that a dataset's potential usefulness will reveal itself only if the data is available.

How to proceed to open up data ?
--------------------------------

There are four main steps in making data open:

### Choose Dataset(s)

Although it is no legal requirement, it is a useful step to make a list of your datasets. Public sector bodies should bear in mind that the PSI directive and the [corresponding national law](https://legilux.public.lu/eli/etat/leg/loi/2021/11/29/a836/jo) obliges them to open up their data. It is recommended to _ask the community_, who will be accessing and using the data, as it is likely to have a good understanding of which data could be valuable.

The more public sector agencies spend on the collection and maintenance of data sets, the more interesting they might well be for third parties to access (_Cost factor_). Small and easy releases can act as a catalyst for larger behavioural change within an organisation.

### Apply an Open License (Legal Openness)

Open data should be accompanied by a license which is important for the sake of legal clarity. It is important to determine what intellectual property rights exist in the data and to apply a suitable open license that licenses all of these rights and supports the definition of openness discussed in these guidelines.

For Luxembourg, the application of the Creative Commons family of licenses is strongly advocated, with a clear preference for the Creative Commons Zero CC0 license: this is the "no copyright reserved" option in the Creative Commons toolkit and effectively means relinquishing all copyright and similar rights that you hold in a work and dedicating those rights to the [public domain](https://wiki.creativecommons.org/wiki/Public_domain).

### Make Data Available (Technical Openness)

Open data needs to be available in bulk in a [machine-readable](http://opendatahandbook.org/glossary/en/terms/machine-readable/) format.

Available: Data should be priced at no more than a reasonable cost of reproduction, preferably as a free download from the Internet.

In bulk: The data should be available as a complete set. A web API or similar service may also be very useful, but they are not a substitute for bulk access.

Open, machine-readable format: Re-use of data should not be subject to patent restrictions. Machine-readable formats allow simple re-use. For example, PDF files are less than ideal as a proprietary format targeted at preserving page layout for print, making it very hard to extract data, information, text and pictures for analysis and reuse.

### Make data discoverable

It is crucial for the open data principle, to make sure that potential users can find the source material. There exist a number of live tools on the web to publish data and to make the material discoverable, and some are especially designed for different sectors (e.g. science). Luxembourg's government has also created a national open data portal and catalog at [https://data.public.lu](https://data.public.lu), where anyone can publish his datasets and re-uses. It is important to make datasets searchable by adding as many tags as possible and by providing good metadata in general.

Online methods
--------------

Keep it simple - move fast - be pragmatic: better give out raw data now than perfect data in six months’ time. There are many different ways to make data available to others. The most natural in the Internet age is online publication. At its most basic, public sector actors make their data available via their websites and the central catalog ([https://data.public.lu](https://data.public.lu)) directs visitors to the appropriate online source.

### Via your existing website

You easily can provide access to data files via your website, but in general it may become difficult for an outsider to discover where to find updated information, which is a burden to people creating tools with your data. That is why you always also should add your data at the national data portal (see below), with link to the resources on your website.

### Via the national data portal

Make sure to register at Luxembourg's national open data portal at [https://data.public.lu](https://data.public.lu), where you can create your organisation's account and publish your datasets or re-uses. This platform offers the necessary infrastructure, provides analytics and usage information, and pools together a local community of interested people as well as other sets of data.

### As an API

Data can be published via an [Application Programming Interface](http://opendatahandbook.org/glossary/en/terms/application-programming-interface/) (API). These interfaces allow programmers to select specific portions of the data, rather than providing all of the data in bulk as a large file. APIs are typically connected to a database which is being updated in real-time. This means that making information available via an API can ensure that it is up to date.

Bulk data
---------

Publishing raw data in bulk should be the primary concern of all open data initiatives, as there are considerable costs to providing an API. Access to bulk data ensures that:

*   There is no dependency on the original provider of the data, meaning that in case of a situation change, the data are still available.
*   Anyone else can obtain a copy and redistribute it. This reduces the cost of distribution away from the source agency and means that there is no single point of failure.
*   Others can develop their own services using the data, because they have certainty that the data will not be taken away from them.

Providing data in bulk allows others to use the data beyond its original purposes. For example, it allows it to be converted into a new format, linked with other resources, or versioned and archived in multiple places. While the latest version of the data may be made available via an API, raw data should be made available in bulk at regular intervals.
