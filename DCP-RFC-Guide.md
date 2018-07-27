# DCP RFC Guide

This document is meant to serve as an introduction to the current status of NIH Data Commons Pilot Requests For Comment. In the future, we hopefully won't have so many to comment on at one time!

The RFCs came out of the Key Capability (KC) coordinating groups, which have been managing meetings around various sides of building up a Commons infrastructure. Each RFC receives a number depending on the order it was presented to the DCPPC.

This document will try to make clear when opinions versus summarization are provided, and is dated 
7/26/18 10:47 AM.

1. [Draft 1: KC6 Security, Ethics, and Privacy Use Cases](#1) [doc](https://docs.google.com/document/d/1Eizi5W7oV45gmQ-QO3AqXwZOPQdhWGDPX_qecroR3xI/edit?usp=sharing)
2. [Draft 2: KC1 Phase 1 Overview for Full Stacks](#2) [doc](https://docs.google.com/document/d/19-0NtTutSoe6T9XkDAFcIdH7fEDMGVW69OIqCUh0D-M/edit?usp=sharing)
3. [Draft 3: KC2 Phase 1 Overview for Full Stacks](#3) [doc](https://docs.google.com/document/d/1lx3uakz4foYN8vw8E5U6NM2F7RcBjyIGA4ZE2zvE9_g/edit?usp=sharing)
4. [Draft 4: KC3 Phase 1 Overview for Full Stacks](#4) [doc](https://docs.google.com/document/d/1jh9rF9gNjxIBHm3wCQTBBUZHNJ4-xRUPFsb8z1m4qBI/edit?usp=sharing)
5. [Draft 5: KC6 OAuth/OIDC Registry for the Data Commons](#5) [doc](https://docs.google.com/document/d/1VsGmO17gwu8lGV-8V-TqjyVjmxTBIRRlYq3-jjKAPOw/edit?usp=sharing)
6. [Draft 6: KC7 Initial Products (Crosscut Metadata Model, Stage 1 Metadata Instance, and Exchange Format)](#6) [doc](https://docs.google.com/document/d/1Qf5L4PNBb7zN9H7yqJpTfZCOGO6CfqzyB2V7FpFBqPw/edit?usp=sharing)

<a name="1"></a>

## [Draft 1: KC6 Security, Ethics, and Privacy Use Cases](#1) [doc](https://docs.google.com/document/d/1Eizi5W7oV45gmQ-QO3AqXwZOPQdhWGDPX_qecroR3xI/edit?usp=sharing)

### Summary

A list of Use Cases, numbered UC-* detail various interactions that are expected to be necessary for creating a Commons Infrastructure that is appropriate for sensitive data. This includes things like controlled access, logging, auditing, and other compliance and authorization schemes. Each UC is given a "timing" of "Pilot" or "Post-pilot", which addresses the 180-day phase, and after.

The Use Cases do not prescribe what software or standards are needed to support the various interactions. Instead, they provide a high-level narrative of what one is expected to be able. For example, it doesn't say "use LDAP" under "UC-3 Authenticate User with Trusted Identity Provider," instead it simply states "the user must be guided through the process of satisfying the criteria through further authentication actions".

Of the now 43 Use Cases there are:

* 12 in Authentication and Identity Management, 7 during the Pilot
* 12 in Authorization and Data Access, 2 during the Pilot
* 14 in Auditing and Logging and, 3 during the Pilot
* 5 in Interoperability, 0 during the Pilot

To roughly summarize the amalgamated Use Cases during the Pilot:

#### Authentication and Identity Management

* UC-1: Maria is provisioned an identity from a Full Stack.
* UC-2: This identity can be used to authenticate using Single Sign On to another Full stack.
* UC-3: A Trusted Identity Provider is used to authenticate Maria's identity.
* UC-5: Maria can choose a single Identity Authority to manage her identity.
* UC-6: Maria can use a digital identity provided by eRA Commons, Google, AWS, or her institutional account.
* UC-7: Maria can provide her identity to a workspace provisioner that can request resources and bill on her behalf.
* UC-10: Maria should be able to login to the web portal, if the login attempt fails, the portal should not provide the reason.

#### Authorization and Data Access

* UC-16: Maria should be able to use an existing dbGap Access Request to access data.
* UC-20: If Maria is a a PI, she should be able to ensure that redistribution restrictions are being upheld.

#### Auditing and Logging

* UC-25: If Maria forgets her password or performs a password reset request, these logs will be available for auditing.
* UC-26: Maria's request to access a dataset is logged so that an Authorizer can approve her.
* UC-27: If Maria asks for an analysis to be run by a system, it should log the steps of the analysis.

The Post-Pilot Use Cases build deeper authorization integrations, logging facilities, data use restrictions, and interoperability between stacks.

### Response

The document is generally instructive about the type of Full Stack that will be useful for creating a system that can work with public Institutions, private data, public clouds, and private clouds. Most of the Use Cases are clear and when taken in concert provide a model of a "Trusted Full Stack". By mixing the Post and Pilot Use Cases, it becomes less clear.

#### We can build a system that can be trusted like dbGap

The high level nature of this document allows some interpretability on details. These Use Cases are largely what one would expect from a system that could safely serve the same utility as dbGap. There are some noted additions around running analyses over data, and how to manage identity across multiple Full Stacks.

Because of the flexibility of interpreting the Use Cases during the pilot, we can see that the various Commons entrants are largely expected to expose existing mechanisms with some specific requirements. These mechanisms are meant to respect the existing Data Access Requests for data in dbGap and identity management spanning private and public authentication mechanisms.

#### SSO or Federated Identity Management

This document should be a preview of DRAFT-5, also from KC6, which specifies the actual mechanisms for carrying out some of the authentication interactions. It may be possible to satisfy the Use Cases in this document without deeply addressing interoperability, but Single-Sign-On as a Use Case during the Pilot would require a large degree of coordination.

Reading the description of Draft 5, and UC-2 here, One might change the wording to "Federated Identity Management." Single Sign On suggests using a single username and password to access connected systems. I believe the intent is rather to create a federated system of Identity providers and authorization systems so that I can authorize as my institutional identity to access both public authorization providers and private authentication and authorization systems.  

#### Switch SSO Use Case to Post-Pilot

I would expect interoperating with dbGap, eraCommons, and a cloud or on-premises system with some measure of safety should be the target for the Pilot. In that spirit, I might suggest switching this Use Case to be Post-Pilot to unencumber Full Stacks from addressing the issues that will hinder developing necessary features in their own stacks.

Given DRAFT-5 (KC6 SSO solution) is still requesting comment, it seems like it would be a challenge to practically review, publish, DRAFT-5, and then implement it to satisfy this Use Case within the Pilot.

#### Move Post-Pilot Use Cases to a Separate Document

It would improve the document to simply provide the Use Cases for the Pilot and save the Post-Pilot Use Cases for a separate document. This would allow the draft to move forward more quickly and allow the community time to arrive at the expected Use Cases that should be fulfilled Post-Pilot with more meaningful milestones or dates.

#### Define terms and Acronyms

Some terms and jargon need to be described in a separate section. The usage of abbreviations should be consistent.

#### Strike/reword Workspace Authentication UC-7

It seems like the features here would be supported by interoperability features (UC-41, UC-22) and shouldn't be a part of this document. UC-7 makes very specific requirements and uses terminology not present in the rest of the document. It seems out of step with the rest of the document to make specific requirements and technology suggestions. If UC-22 is not sufficient, what should be added to it?

<a name="2"></a>

## [Draft 2: KC1 Phase 1 Overview for Full Stacks](#2) [doc](https://docs.google.com/document/d/19-0NtTutSoe6T9XkDAFcIdH7fEDMGVW69OIqCUh0D-M/edit?usp=sharing)


### Summary

KC1 intends to create a service for evaluating the FAIRness of Full Stacks. This is done by making public metadata available for testing. This document provides specific instruction on how Full Stacks can interoperate with the FAIR assessment service to generate rubrics, that will track FAIR metrics.

The document is made up of a Use Case pattern for FAIR assessment, a list of APIs, and pledges from Full Stacks to implement a FAIR assessment.

FAIR assessment projects are made up of rubrics. Rubrics track digital objects in a stack and are captured in versioned assessments, wherein various metrics are derived from metadata found when attempting to access the object. These assessments can be later retrieved using a service listed on SmartAPI and which is compatible with [FAIRshake](http://fairshake.cloud).

The specific implementation plans from the Full Stacks for Calcium, Xenon, and Helium are in this document. They describe various scenarios where digital objects will be registered and evaluated.

There are 8 APIs described: FAIR Assessment Project API, FAIR Digital Object Store API, FAIR Associate Digital Objects and Rubrics API, FAIR Request Assessment API, FAIR Assessment API, Metric API, Rubric API, and FAIR Assessment Visualization API.

### Response

Interoperability and accessibility can not be accidentally achieved, but instead require a degree of testing and oversight. This document describes a very abstract way of creating accountability for the types of metadata Full Stacks are providing. A hand curated process will be made to evaluate FAIRness, but its unclear how it overlaps with access control.

#### API Specification or Compliance Walkthrough

The patterns for accessing the various APIs are addressed through a series of numbered actions. However, they do not specifically address the numbered APIs in the next section. The high-level description of the process might be better linked by addressing the specific API interaction to carry out each step.

In addition, the API specification areas are incomplete and optional HTTP operations' behavior is left unspecified in places. It might be better to simply state the high level process of assessment and then provide further guidelines with links to machine readable API specifications.

#### Specific Team Calcium Plan

Team Calcium has signed on to list items via TRS and DOS that are Open Access so that a FAIR assessment can be made on them. This should improve the quality of our metadata and could perhaps be a way to assist clients when interfaces change.

Creating rubrics will require hand curation of Workflows (from TRS) and Data Objects (from DOS). This agreement states that when a Commons DCAF instance is available this will be done. It does not state what, if anything will happen with those assessments.

#### Open Access versus Controlled Access for FAIR Commons

Much of the Data Commons infrastructure is centered around working with controlled access data. The redistribution restrictions are very clear and satisfying these capabilities is a large part of the effort of interoperating with existing NIH data use and restrictions. How does FAIR and the redistribution requirements interrelate?

Will the FAIR services be storing controlled access data? Metadata about controlled access data? Will the service controllers have active DARs?

<a name="3"></a>

## [Draft 3: KC2 Phase 1 Overview for Full Stacks](#3) [doc](https://docs.google.com/document/d/1lx3uakz4foYN8vw8E5U6NM2F7RcBjyIGA4ZE2zvE9_g/edit?usp=sharing)

### Summary

This RFC is informational and does not present design guidelines, but instead a variety of solutions. It begins with two dozen definitions that are meant to provide information about how data in the Commons will be identified.  These definitions provide links to more information in places.

The definitions are largely concerned with characterizing the types of services needed to support identification, and the definitions for given identifiers.

### Response

The variety of services on this document should not be troubling, but a testament to the ingenuity of their designers. Since this is an informational RFC, it makes no specific requirements on Full Stacks. This is a good opportunity for us to demonstrate how our API-based resolution networks can work independently and interoperate with existing systems.

#### Definitions Outside of Scope

Why is Data Catalog defined here by the W3C and how does it relate to NIH DCPPC?

#### Repeated Definitions

Items like "minid", "DataCite DOI" are repeated in the definitions and in the Data GUIDs in use. Is this intended?

#### Landing/Brokerage are not Required for Object Resolution

Details of the implementation of various identifier services is important, however, for Object Resolution these seem extraneous or misinterpreted in this document. This document aims to be an informational list of ways to identify data. To that end I suggest removing section 5 as it points to a "landing page" model, which is not tied to specific Use Cases.

#### Coordinating with specific Use Cases

Most of the Use Cases in DRAFT-1 have interoperability between stacks for Data Access beyond the portion of the pilot. To make this information truly valuable, it should be tied to specific Use Cases and shown how vendor-agnostic implementations can be provided. It is unclear the extent to which metadata for the Commons are expected to be centralized. 

#### Centralization versus Federation

It is of concern that in approaching this document, it is unclear the extent to which it relies on centralized services for handling Commons metadata. For protected access data, especially, the requirements to make metadata as well as data inaccessible unauthorized access is largely ignored. Although the document is informational, I believe it is light on the information describing what the technical merits are behind ARK and minid.

#### Add Definitions

We ought to define Data Object Service and link to it. Added to doc 7/26/18 4:59 PM

#### identifiers.org usage

One of the great values we've gained from Team Sodium is via the identifiers.org team. Being able to quickly and easily register a namespace to identifiers.org is very useful and could be better described in the informational document KC2 provides. Additionally link to their work on making it API driven.

#### zenodo DOI versus DataCite DOI

If we already have software or data registered to a zenodo DOI, do we need to issue a DataCite DOI? Would it be more correct to say that DOI in general are used, or another section for zenodo?

<a name="4"></a>

## [Draft 4: KC3 Phase 1 Overview for Full Stacks](#4) [doc](https://docs.google.com/document/d/1jh9rF9gNjxIBHm3wCQTBBUZHNJ4-xRUPFsb8z1m4qBI/edit?usp=sharing)

### Summary

Another Informational RFC, it provides a directory of APIs that have registered with the DCP. It provides a quick overview of APIs meant to be advertised as part of the Data Commons, but not meant to be exhaustive or exclusive. Many APIs overlap and perform similar tasks, yet are specified in different ways or implemented over different providers.

In general, to respond one must provide information about the development status of their API, an implementation if is available, contact information, and a link to any further documentation.

### Response

Team Calcium takes an API specification driven approach to developing interoperable software, so this is an opportunity to demonstrate the repeatability of our approach. Having easy to implement APIs that can interoperate with existing systems is one of our strengths, and working in the Open Source towards standards lends our efforts some authority.

Since this document is a registry of APIs, it will likely stay in draft forever, being updated with details as they are made available.

#### Sandboxes

Since some of Team Calcium's Common's Entrants host private, controlled access data in a production environment, we cannot provide separate instances for this effort. To that end, we can simply list our production services where they are available.

#### API Advertising

It would be good to come back to this document to treat it as the onboarding to various systems. Most demos are UI or platform centric, however, as development becomes more API driven this is an easy way to advertise your API. This might also be a good place to link to portals (which may be necessary for generating API keys).

<a name="5"></a>

## [Draft 5: KC6 OAuth/OIDC Registry for the Data Commons](#5) [doc](https://docs.google.com/document/d/1VsGmO17gwu8lGV-8V-TqjyVjmxTBIRRlYq3-jjKAPOw/edit?usp=sharing)

### Summary


### Response



<a name="6"></a>

## [Draft 6: KC7 Initial Products (Crosscut Metadata Model, Stage 1 Metadata Instance, and Exchange Format)](#6) [doc](https://docs.google.com/document/d/1Qf5L4PNBb7zN9H7yqJpTfZCOGO6CfqzyB2V7FpFBqPw/edit?usp=sharing)

### Summary

This document arrives as a Design Principle, which has more entailments than informational. From https://github.com/dcppc/internal/tree/master/RFC/#design-principle , it means that this RFC can be accepted or rejected as a "new feature or implementation" as a part of the Commons.

It describes three parts, which are the Crosscut Metadata Model, Stage 1 Metadata Instance, and Exchange Format.

DATS is presented as a metadata model useful for describing datasets by capturing their metadata in a specific JSON schema. Links to examples are provided.

The Stage 1 Metadata Instance describes a metadata resource for a few Commons datasets. Some of the metadata across these datasets will be harmonized by the KC7 group. 

The Exchange Format section addresses BDBags and minids. BDBags format is used for archivally storing named data with its checksums. minid is used to identify a dataset or its elements.

### Response

For a document to arrive as a design principle, this lacks a great deal of the rigor and specification needed. The RFC process provides for a way to arrive at consensus around Design Principles, but this is offered as something further evaluated. DATS as a metadata format makes opinionated decisions and can be interpreted in a variety of ways.

The actual problems of presenting useful metadata indexing, querying, and metadata harmonization are not provided by the offered designs. Bagit as a specification is not evaluated against other standards, including JSON serialization.

#### Make RFC type Informational

To demonstrate that viable possible alternatives were evaluated, this RFC should be made informational. This will help make sure KC7 arrives at solutions based on technical merit.

#### Metadata Instance

A centralized metadata instance may be useful for bootstrapping the Commons, but it implies a centralization of services that goes against the spirit of a Commons. Our aim is to provide interfaces and applications that can communicate with other Full Stacks to reason about datasets. A centralized metadata instance implies the presence of controlled access data (which is addressed briefly in the document).

This appears more like a Full Stack describing its metadata ingestion methods than a Key Capability providing a utility to the community. If it is necessary to create a centralized metadata service to bootstrap the Commons, we might encourage that it isn't maintained in the future.

#### Centralization and minids

A Commons infrastructure is made up of many decoupled services. A centralized identifier registration service seems out of the scope of a Data Commons itself, individual Commons entrants may use a centralized metadata registry like minid/EZID, however, this is impractical for a variety of reasons that we address by using Data GUIDs.

These solutions are not exclusive, however, we suggest that KC7 first collects more information and then later put forward a design principle for the Commons that does not promote a decentralized and federated exchange of data (as opposed to centralization).

Minids are already addressed in the informational DRAFT-3 document as one of the ways items may be identified in the Commons. If minids are in this document as a design principle, then we have assumed that a solution should be a part of the Commons before Full Stack entrants have been able to respond to the Informational work from KC2.

#### Bagit, BDBags

As internet services have built up, files are rarely transferred between services. Instead of receiving a file, your Web browser interprets data models describe in JSON, XML, RDF, etc. and interacts with services to exchange the metadata. Bagit, as is stated in the document, grew up around archival Use Cases. Making this step away from representing files using files is precisely what enabled the proliferation of cloud object stores. You can reason about data using a simple HTTP interface.

To adopt the incidental complexity of using files means the Bagit tooling must present some feature over a more modern, lightweight approach. It is unclear whether a BDBag could itself be entirely represented in a DATS and whether JSON parsing a DATS for a key would carry out the same functions as the bdbag tooling, calling into question the technical merit of the approach.

Commons Entrants should work to automate the exchange of metadata between them. We would suggest a service-oriented as opposed to a file-oriented approach.