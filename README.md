# Commons Alliance Components

This repository will try to explain the components that take part 
in the Team Calcium NIH DCPPC Pilot (and beyond).

Read the [Data Biosphere post](https://medium.com/@benedictpaten/a-data-biosphere-for-biomedical-research-d212bbfae95d).

## Prototype

<img src="diagrams/prototype.svg" alt="The prototype components of a Commons member" />

The various components coordinate to create a platform useful for data analysis.

### Digital Object Catalog

Provides clients and services access to resources available in object stores. Digital objects
can be files and the catalog itself maintains a registry of locations to find the files, as 
well as minimal metadata.

#### GUID Resolver

Allows globally unique identifiers to be "resolved" to digital objects. 

#### Namespace Service

Identifiers can be given different namespaces or "prefixes". The namespace service allows commons 
members to easily manage GUIDs across projects and domains.

### Access Control

To guarantee authority and authenticity of requests, some access control services are provided. 
These services will at least be able to identify a client and delegate authority to the access 
control system of choice.

### Analytical Engine

Software which can orchestrate and execute computational tasks in heterogeneous computing 
environments

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

| Component              |     Broad      |   UChicago CDIS    |           UCSC          |   |
|------------------------|----------------|--------------------|-------------------------|---|
| Digital Object Catalog |                |                    |     dos-azul-lambda     |   |
| GUID Resolver          |                |  indexd            |                         |   |
| Namespace Service      |                |  indexd            |                         |   |
| Access Control         |   SAM bond     |   fence            |                         |   |
| Analytical Engine      |   Cromwell     |                    |  toil                   |   |
| Tool Repository        |   Agora        |                    |  Dockstore              |   |
| Workspaces             |   Firecloud    |   jupyterhub       |                         |   |
| Indexing and Search    |                |                    |                         |   |
| Ontology               |                | datadictionary     |                         |   |
| Metadata Indexer       |                | sheepdog           | dss-azul-indexer        |   |
| Metadata Querying      |                | peregrine          | cgp-dashboard-service   |   |
| Portal                 |                | windmill           | boardwalk               |   |
| Application            |                |                    | xena                    |   |

### UChicago CDIS

<img src="diagrams/uc-cdis.svg" alt="An image of the UC CDIS commons services" />



### UCSC Genomics Institute

<img src="diagrams/ucsc.svg" alt="An image of the UCSC commons services" />

### Broad Institute

<img src="diagrams/broad.svg" alt="An image of the Broad commons services" />

## Development

This document is under active development. If you feel misrepresented or something has been
miscommunicated, please open an issue or make a Pull Request!

## Editing diagrams

The program used to edit the "dia" files is [dia](http://dia-installer.de/).

Github caches images when they display READMEs so be sure to check the actual file if 
it seems out of date!

