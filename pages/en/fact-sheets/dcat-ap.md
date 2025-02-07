# Factsheet: DCAT-AP, the standard for Open Data Portals metadata

The DCAT-AP standard allows the reuse of metadata from open data portals in Europe. Through this standard, the main open data portals are interoperable and can exchange their metadata, synchronize them, and federate them in a fully automated manner. This standard makes it possible to describe the metadata of datasets published on open data portals.

## Data and metadata

Before we begin, we think it's interesting to recall the difference between data and metadata. Metadata is data about data, such as the name of a dataset, its publication date, or the license under which these contents are published.

On the open data portal, you will find the metadata in the “Metadata” tab of each dataset.

![](https://data.public.lu/fr/pages/fact-sheets/data-quality-metadata.png)

## Machine-readable metadata

If we want to exchange this metadata not only with humans but also with machines, it is necessary to have a common and standardized language to transmit this information.

This is what we do on data.public.lu with a specific API which implements the DCAT-AP standard.

For example, you can query the open data portal catalog at this URL:

<https://data.public.lu/catalog.rdf>

If you are viewing this URL via your browser, feel free to view the page source code (for example, by right-clicking on the page and then "view page source").

Via this web service, we can retrieve all the metadata of all the datasets available on data.public.lu. The data is not present there, only the URLs of the data are referenced there.

Here you can see that the metadata is structured in XML. DCAT-AP is based on RDF, which is an abstract model that has several serializations, that is, several concrete representations in specific computer languages, one of which is in XML. You can access the other serializations offered by the open data portal by changing the extension at the end of the URL. For example, you can use the extension .json to obtain a serialization in JSON-LD format, or .ttl or .nt for the textual formats Turtle or N-triples). For a list of available formats, you can consult the documentation of the [udata platform](https://udata.readthedocs.io/en/stable/rdf/).

This web service is paginated, it only renders the first 100 datasets by default. You can reach the other pages by using the parameters page, for the page number and page_size for the number of datasets per page. For example to display the 2nd page, you can query the following URL:

[https://data.public.lu/api/1/site/catalog.rdf?page=2 & page_size=100](https://data.public.lu/api/1/site/catalog.rdf?page=2&page_size=100)

Similarly, it is possible to obtain metadata for a particular dataset or all datasets related to a particular organization.

For the metadata of the datasets of a given organisation, the URL is of the form:

[https://data.public.lu/api/1/organizations/{id}/catalog.rdf​](https://data.public.lu/api/1/organizations/%7bid%7d/catalog.rdf)

where {id} is the identifier of an organization, which can be found in that organization's URL on the portal.

For example: <https://data.public.lu/api/1/organizations/open-data-letzebuerg/catalog.rdf>

For metadata of a single dataset, the URL is of the form:

[https://data.public.lu/api/1/datasets/{id}/rdf​](https://data.public.lu/api/1/datasets/%7bid%7d/rdf)

where {id} is the dataset identifier, which can be found in its URL on the portal.

For example: <https://data.public.lu/api/1/datasets/digital-accessibility-monitoring-report-2020-2021/rdf>

## Specific vocabulary: DCAT-AP

[DCAT-AP](https://semiceu.github.io/DCAT-AP/releases/3.0.0/) (DCAT Application Profile for data portals in Europe) is a standard defined by [SEMIC](https://interoperable-europe.ec.europa.eu/collection/semic-support-centre) (European SEMantic Interoperability Community) for metadata of open data portals. It is an extension of the [DCAT](https://www.w3.org/TR/vocab-dcat-3/) (Data Catalogue Vocabulary) standard defined by the W3C.

### The goals

If each open data portal adopted its own data schema for metadata exchange, it would be very complicated to carry out these exchanges in practice. The DCAT-AP standard was precisely defined with the aim of supporting interoperability between open data portals in Europe.

With DCAT-AP, you can:

- Retrieve metadata from an open data portal.
- Federate open data portals, for example between the Luxembourg portal and the European portal, or between the portal of a public establishment or a municipality and the national portal.
- Be able to search across multiple portals.

The Luxembourg open data portal provides an API in DCAT-AP format, its data is federated in the European portal data.europa.eu.

### The diagram

As of this writing, the latest version of DCAT-AP is version 3.0 (Feel free to refer to the [latest version of DCAT-AP](https://github.com/SEMICeu/DCAT-AP/releases).) We recommend that you familiarize yourself with the [DCAT-AP 3 data schema](https://semiceu.github.io/DCAT-AP/releases/3.0.0/#application-profile-diagram).

The main concepts are:

- **Dataset** : represents a dataset on the open data portal. A Dataset has a title, a description, an author, a license, etc.
- **Distribution** : on the open data portal we will rather talk about Resource or File. A Dataset is linked to one or more distributions, each representing a File available on the Open data portal or at a given URL. A distribution necessarily has a URL, and can have additional metadata, such as the data format, description, etc.
- **Catalog** : represents the open data portal itself, is linked to all the datasets of the portal.

DCAT-AP goes further than DCAT, as it specifies the mandatory, recommended or optional nature of the classes and properties to be implemented. This information is specified in the diagram above and is important for those responsible for implementing open data portals.

### Compatibility

The main open source platforms for creating open data portals like [CKAN](https://ckan.org/) or [udata](https://udata.readthedocs.io) support the DCAT-AP standard. The same goes for geographic data portals like GeoNetwork.

It is possible to check the compatibility of a DCAT-AP implementation using its validator:

[DCAT-AP validator](https://www.itb.ec.europa.eu/shacl/dcat-ap/upload)

The validation process and validator configuration are detailed in the DCAT-AP documentation, particularly in the [“Validation of DCAT-AP” section.](https://semiceu.github.io/DCAT-AP/releases/3.0.0/#validation-of-dcat-ap)

### DCAT-AP Extensions

DCAT-AP is an extensible format. Indeed, it is difficult to predict a priori a data schema that can meet all needs. Some extensions have been defined to complement DCAT-AP on specific use cases:

- [StatDCAT -AP](https://joinup.ec.europa.eu/collection/semic-support-centre/solution/statdcat-application-profile-data-portals-europe): for the field of statistics
- [GeoDCAT -AP](https://semiceu.github.io/GeoDCAT-AP/releases/): for geographic data

Several European countries have created their own extension of DCAT-AP such as [Belgium](http://dcat.be/) or [Germany](https://www.dcat-ap.de/), ...

## To wrap up

If you want to create a new open data portal in Luxembourg and federate it with the Luxembourg open data portal, this will most certainly happen via the DCAT-AP standard. Similarly, if you want to retrieve all the metadata from the Luxembourg open data portal, knowledge of DCAT-AP will be very useful to you.

## Learn more

- [DCAT and DCAT-AP training - Webinar 1: General introduction](https://www.youtube.com/watch?v=_JB93__aj_M)
- [DCAT and DCAT-AP training - Basic user](https://www.youtube.com/watch?v=Za1XgjisosM)
- [DCAT and DCAT-AP training Webinar 3: Advanced user](https://www.youtube.com/watch?v=etUu24hNgz4)
- [DCAT-AP API endpoints for data.public.lu](https://data.public.lu/fr/datasets/dcat-ap-api-endpoints-for-data-public-lu/)
