# Data Platforms

This repository gathers together components that take part 
in the Commons Alliance. These components describe interfaces 
and features that can be assembled to create "data platforms" useful for 
storing, and performing reproducible analyses on data and 
metadata.

This is a living document.

Note, if you are viewing this on github, the images may be cached, please visit:

https://databiosphere.github.io/data-platforms/

For more background read the [Data Biosphere post](https://medium.com/@benedictpaten/a-data-biosphere-for-biomedical-research-d212bbfae95d).

Visit the [DataBiosphere github organization](https://github.com/DataBiosphere).

## [Metadata Serialization](metadata-serialization)

Communication between data platforms requires that metadata are serialized 
in a useful and predictable manner. This document describes approaches and 
case studies in use by some components.

View the [Metadata Serialization](metadata-serialization) document.

## [Identifier Interoperability](identifier-interoperability)

When the same metadata are present in multiple locations, it is critical to 
provide guarantees of identity that are useful and portable. This document 
describes approaches to presenting and using interfaces that allow identifiers 
to be usefully exchanged.

View the [Identifier Interoperability](identifier-interoperability) document.

## Prototype

<img src="diagrams/prototype.svg" alt="The prototype components of a Commons member" />

The various components coordinate to create a platform useful for data analysis.

### Digital Object Catalog

Provides clients and services access to resources available in object stores. Digital objects
can be files and the catalog itself maintains a registry of locations to find the files, as 
well as minimal metadata.

#### GUID Resolver

Allows globally unique identifiers to be "resolved" to digital objects. For more information 
please refer to [Identifier Interoperability](identifier-interoperability).

#### Namespace Service

Identifiers can be given different namespaces or "prefixes". The namespace service allows commons 
members to easily manage GUIDs across projects and domains. For more information 
please refer to [Identifier Interoperability](identifier-interoperability).

#### Data Access

Once data have been discovered they must be localized, which requires interacting with object stores 
and performing authentication, authorization, downloading, and transfer as necessary.

### Access Control

To guarantee authority and authenticity of requests, some access control services are provided. 
These services will at least be able to identify a client and delegate authority to the access 
control system of choice.

### Analytical Engine

Software which can orchestrate and execute computational tasks in heterogeneous computing 
environments.

### Tool Repository

A resource which contains templates of reusable computational tasks that can be directed at new 
data, and then executed by the Analytical Engine.

### Workspaces

Clients accessing a commons infrastructure should be able to manage data for secondary and 
tertiary data analysis.

### Indexing and Search

Data in commons infrastructure should be findable using Search mechanisms. Indexing makes data 
available for search.

#### Ontology

A controlled vocabulary informs indexers and or querying applications to make metadata usable.

#### Metadata Indexer

Metadata made available by a platform is indexed into a store. Indexers allow data to be made 
findable using a structured document scheme.

#### Metadata Querying

Once metadata have been indexed into a platform, these indices are made available by services 
that allow queries to be formed against the metadata.

### Portal

Commons infrastructure should provide interfaces to make data easily findable. Once data has been 
found in a portal, it can be added to a workspace.

### Application

Applications combine a variety of Commons components to carry out specific tasks.

## Commons Alliance Components

### Source Code Repository Table

Links to source code repositories for implementations are provided below:

| Component                  |          [Broad][20]     |  [UChicago CDIS][21]  |       [UCSC CGP][22]          |
|----------------------------|--------------------------|-----------------------|-------------------------------|
|  *Digital Object Catalog*  |                          |                       |                               |
| GUID Resolver              |                          |  [indexd][6][*][25]   |  [dos-azul-lambda][13][*][25] |
| Namespace Service          |                          |  [indexd][6][*][25]   |                               |
| Data Access                |                          |  [fence][7]           |  [cgp-data-store][23]         |
| *Access Control*           |                          |                       |                               |
| Authorization              |   [sam][1] [bond][2]     |  [fence][7]           |                               |
| Authentication             |   [sam][1] [bond][2]     |  [fence][7]           |                               |
| Analytical Engine          |   [Cromwell][3][*][29][*][25]<br>[Leonardo][28] |       |  [toil][14]                   |
| Tool Repository            |   [Agora][4][*][24]      |                       |  [Dockstore][15][*][24]       |
| Workspaces                 |   [Rawls][26]            | [jupyterhub][8]       |                               |
| *Indexing and Search*      |   [Orchestration][27]    |                       |                               |
| Ontology                   |                          | [datadictionary][9]   |                               |
| Metadata Indexer           |   [Orchestration][27]    | [sheepdog][10]        | [azul-indexer][16]            |
| Metadata Querying          |   [Orchestration][27]    | [peregrine][11]       | [azul-webservice][17]         |
| Portal                     |   [Firecloud][5]         | [windmill][12]        | [boardwalk][18]               |
| Application                |                          |                       | [xena][19]                    |

Applications marked with a `*` implement a standard interface being developed with the GA4GH. 
Clients can interact with these applications using an open protocol

* indexd, dos-azul-lambda and Cromwell implement the [Data Object Service][25].
* Dockstore and Agora implement the [Tool Registry Service][24].
* Cromwell implememnts the [Workflow Execution Service][29]

[1]: https://github.com/broadinstitute/sam
[2]: https://github.com/DataBiosphere/bond
[3]: https://github.com/broadinstitute/cromwell
[4]: https://github.com/broadinstitute/agora
[5]: https://github.com/broadinstitute/firecloud-ui
[6]: https://github.com/uc-cdis/indexd
[7]: https://github.com/uc-cdis/fence
[8]: https://github.com/jupyterhub/jupyterhub
[9]: https://github.com/uc-cdis/datadictionary
[10]: https://github.com/uc-cdis/sheepdog
[11]: https://github.com/uc-cdis/peregrine
[12]: https://github.com/uc-cdis/data-portal
[13]: https://github.com/DataBiosphere/dos-azul-lambda
[14]: https://github.com/DataBiosphere/toil
[15]: https://github.com/ga4gh/dockstore
[16]: https://github.com/DataBiosphere/azul
[17]: https://github.com/DataBiosphere/azul
[18]: https://github.com/DataBiosphere/cgp-boardwalk
[19]: https://github.com/ucscXena/ucsc-xena-server
[20]: https://www.broadinstitute.org/
[21]: https://cdis.uchicago.edu/gen3
[22]: https://cgl.genomics.ucsc.edu/
[23]: https://github.com/DataBiosphere/cgp-data-store
[24]: https://github.com/ga4gh/tool-registry-service-schemas
[25]: https://github.com/ga4gh/data-repository-service-schemas
[26]: https://github.com/broadinstitute/rawls
[27]: https://github.com/broadinstitute/firecloud-orchestration
[28]: https://github.com/DataBiosphere/leonardo
[29]: https://github.com/ga4gh/workflow-execution-service-schemas

### UChicago CDIS

The University of Chicago, CDIS groups presents software for easily managing the submission and 
access control of bioinformatics and medical informatics data in cloud environments.

<img src="diagrams/uc-cdis.svg" alt="An image of the UC CDIS commons services" />

### UC Santa Cruz Computational Genomics Platform

<img src="diagrams/ucsc.svg" alt="An image of the UCSC commons services" />

### Broad Institute

#### This section is in progress

<img src="diagrams/broad.svg" alt="An image of the Broad commons services" />

## Development

This document is under active development. If you feel misrepresented or something has been
miscommunicated, please open an issue or make a Pull Request!

## Editing diagrams

The program used to edit the "dia" files is [dia](http://dia-installer.de/).

Github caches images when they display READMEs so be sure to check the actual file if 
it seems out of date!

