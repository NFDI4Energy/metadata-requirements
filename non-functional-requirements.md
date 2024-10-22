# Non-functional requirements

Metadata can come in numerous flavors and therefore should allow to be used in multiple contexts.

## Metadata serialization formats need to be standardized

|||
|---|---|
|**Title**|Metadata serialization formats need to be standardized|
|**ID**|REQ-METADATA-FORMAT-STANDARDS|
|**Goal**|Make sure that metadata is stored with a standardized serialization format, so most tools and frameworks natively support parsing and serializing it|
|**Description**||
|**Creation date**|2024-08-15|
|**Linked terms**|http://purl.obolibrary.org/obo/NCIT_C171252, http://edamontology.org/format_1915, https://schema.org/encodingFormat|
|**Solution idea**|This means the preferred serialization formats are RDF/XML, JSON-LD, Turtle, N3 and Ntriples. Nevertheless, other standardized formats as XML, JSON, YAML and TOML are also valid and can be used.|

## Metadata serialization formats shall be storable in triple store databases

|||
|---|---|
|**Title**|Metadata serialization formats shall be storable in a way that supports SPARQL federation|
|**ID**|REQ-METADATA-FORMAT-FEDERATION|
|**Goal**|Metadata shall be easily queriable among federated endpoints|
|**Description**|Finding metadata works best in a federated environment. So we want to make sure that the metadata records used for any NFDI4Energy service are stored in a way that allows for SPARQL federation. Either with native or virtual SPARQL endpoints|
|**Creation date**|2024-09-19|
|**Linked terms**||
|**Solution idea**|Triplestore databases easily provide SPARQL endpoints and therefore federation capabilities. Alternatively metadata can be stored in a way that allows for virtual SPARQL endpoints to achieve the same effect.|

## Metadata serialization format validation

|||
|---|---|
|**Title**|Metadata serialization format validation|
|**ID**|REQ-METADATA-FORMAT-VALIDATION|
|**Goal**|Validation of metadata records improves the quality of metadata|
|**Description**|Validation techniques need to be available for the used serialization formats that are used for metadata records|
|**Creation date**|2024-08-15|
|**Linked terms**||
|**Solution idea**|JSON schema and JSONld can be used in conjunction to validate input metadata records. If using other semantic formats the superior validation of SHACL can be applied.|

|||
|---|---|
|**Title**|The metadata schema reuses agreed upon terms and semantics|
|**ID**|REQ-SCHEMA-REUSE-AGREED-SEMANTICS|
|**Goal**|Do not create duplicate definitions to have improved interoperability|
|**Description**|The terms and semantics used for the schema should be from pre-existing ontologies as much as possible.|
|**Creation date**|2024-09-17|
|**Linked terms**||
|**Solution idea**|Importing / Referencing of all ontologies that provide useful terms or semantics|

|||
|---|---|
|**Title**|Allow interoperability between existing metadata standards|
|**ID**|REQ-STANDARD-INTEROPERABILITY|
|**Goal**|Metadata records for our schema should be easily interoperable with other platforms that use different schemas|
|**Description**|Interoperability of different metadata standards is important for our application this allows to prevent re-annotation of metadata in other formats and supports other platforms to access our artifacts more easily|
|**Creation date**|2024-08-15|
|**Linked terms**||
|**Solution idea**|Schema crosswalks to the most relevant standards are helpful for federated searches and form a foundation of format conversions. Scripts shall be provided to convert from and to our schema for a selected set of standards.|

|||
|---|---|
|**Title**|Metadata schema / standard needs to have a clear versioning scheme|
|**ID**|REQ-SCHEMA-VERSIONING|
|**Goal**|Versioning allows to clearly identify the correct schema for each dataset|
|**Description**|Clearly distinguish newer versions from the old ones and make sure that all versions are available online|
|**Creation date**|2024-08-15|
|**Linked terms**||
|**Solution idea**|Semantic versioning for the schema and reference the versioned URL of the schema in each metadata record|

|||
|---|---|
|**Title**|Version control shall be applied for documentation|
|**ID**|REQ-DOCUMENTATION-VERSION-CONTROL|
|**Goal**|Make changes to documentation traceable|
|**Description**|Version control needs to be applied to improve documentation quality and prevent losses through editing from different people|
|**Creation date**|2024-09-19|
|**Linked terms**||
|**Solution idea**|Github is a good foundation for the documentation source files and can also host the actual online documentation|

|||
|---|---|
|**Title**|Documentation shall clearly show the terms used from other ontologies / schemas|
|**ID**|REQ-DOCUMENTATION-CLEAR-REFERENCES|
|**Goal**|Express the amount of terminology reuse to express high level of interoperability|
|**Description**|The terms used to express things shall provide a reference to the original documentation and formal specification|
|**Creation date**|2024-08-15|
|**Linked terms**||
|**Solution idea**|Markdown and HTML both support named links to external sources|

|||
|---|---|
|**Title**|Visualize different use of terminology among reused / mapped schemas and ontologies|
|**ID**|REQ-DOCUMENTATION-TERMINOLOGY-DIFFERENCES|
|**Goal**|Help users understand the differences of similar terms in other standards|
|**Description**|Some terms are used differently between different standards or use different names for the same thing. The documentation shall provide a way to recognize those cases.|
|**Creation date**|2024-08-15|
|**Linked terms**||
|**Solution idea**|Use terminology from thesauri or SKOS to express "similarTerms", "similarButDifferent" and "notToBeConfusedWith" relations.|

|||
|---|---|
|**Title**|Fields in the schema shall use controlled vocabularies as much as possible|
|**ID**|REQ-CONTROLLED-VOCABULARIES|
|**Goal**|Prevent the interoperability issues that arise with custom human input|
|**Description**|Controlled vocabularies are a good way to allow proper linking and interoperability between different datasets|
|**Creation date**|2024-08-15|
|**Linked terms**||
|**Solution idea**|Use either ENUM like instances of a type in OWL or specify a base class for terms as child classes, use public identifiers of a certain pattern (e.g. purl, doi, orcid, etc.) - multiple solutions will be necessary.|

|||
|---|---|
|**Title**|Links between metadata records|
|**ID**|REQ-LINKED-METADATA|
|**Goal**|Help users to traverse semantically linked metadata records that are similiar, different, related, etc.|
|**Description**|When metadata records allow to link to other metadata records it is easier to navigate through a collection of artifacts to find out which are related in any way. This can either mean a similar project, similar purpose, explicit difference to another metadata record, etc.|
|**Creation date**|2024-08-15|
|**Linked terms**||
|**Solution idea**|Provide a generic metadata module in the schema that focuses on relations to other datasets and think about a good collection of relations between them.|

|||
|---|---|
|**Title**|Documentation shall be understandable for users that need to fill or read metadata records|
|**ID**|REQ-DOCUMENTATION-STAKEHOLDER-USERS|
|**Goal**|The documentation must provide helpful information to users without semantics or metadata background|
|**Description**|Oftentimes documentation focuses on developers or assumes some kind of background on side of the users. This shall not be the case with the metadata schema documentation. Everybody that needs to fill or look at a metadata record should be able to understand the documentation.|
|**Creation date**|2024-08-15|
|**Linked terms**||
|**Solution idea**|This is hard to measure, so for now just involve end users in the design of the documentation.|

|||
|---|---|
|**Title**|Allow for a curated way to extend controlled vocabularies|
|**ID**|REQ-CURATED-CONTROLLED-VOCABS|
|**Goal**|The predifined vocabularies are sometimes not enough - by introducing a mechanism to extend them in a curated way it prevents frustrations for users|
|**Description**|Free text can sometimes describe better what a certain artefact / dataset is about if there are no matching values in a controlled vocabulary. So it would be nice if there would be a simple process to add new items to a controlled vocabulary in a curated way, that does not hinder the workflow of the user|
|**Creation date**|2024-08-15|
|**Linked terms**||
|**Solution idea**|Embedding a terminology search into a metadata input form when there can be no proper choice made to find a reference in an ontology for a term. If the term from the other ontology fulfills yet to be determined characteristics it might be possible to extend the vocabulary with that term (initially for the time the form is active) and on a long run the added "external" terms could be curated and either accepted or revoked centrally for the schema.|

|||
|---|---|
|**Title**|Requirements for applications using the metadata schema|
|**ID**|REQ-TOOL-REQUIREMENTS|
|**Goal**|Allow developers to get going with the schema quickly with a clear set of requirements|
|**Description**|The documentation shall provide requirements that each application using the metadata schema and its records needs to fulfil. This makes sure developers can get started more quickly and have a clear set of rules a new application can be checked to be compatible.|
|**Creation date**|2024-08-15|
|**Linked terms**||
|**Solution idea**|Extrapolate a subset of theses requirements on this page and format them on some kind of online documentation.|

|||
|---|---|
|**Title**|Metadata UI needs to be simple and streamlined|
|**ID**|REQ-SIMPLE-UI|
|**Goal**|Don't annoy or scare users with complex forms or workflows|
|**Description**|Any UI that is used to create metadata forms needs to be simple and streamlined because users are easily scared off and do not enter metadata at all. Make the hurdle to do it as simple as possible|
|**Creation date**|2024-08-15|
|**Linked terms**||
|**Solution idea**|Provide more like a dialog with a chatbot than a form and use modern web frameworks to build the UI.|


- Process descriptions (describe data flows, provenance, reproducability of data)
- Two kinds of documentation:
    - how does this work?
    - the storyline that tells me what all of this is good for
- Additional information on what other users could do with the content of a metadata field (e.g. with a tooltip / popover?)

- Always provide exports of commonly available metadata schemas (integrate conversions in tools or as a service).


## 2) Provided schema files

Schema files shall be provided as Turtle/Notation3 and as JSON schema.
Both for standard JSON and JSON-LD?!

## 3) Modularity

Metadata should be tailored specifically for the type of data being annotated.
Many metadata fields are not relevant to a slightly different data set.
As a result, each metadata module / profile must have a precise and limited scope.
Smaller is often better in this context.
This means each data set is likely to require multiple metadata modules / profiles to be properly annotated.
A strategy to find relevant will eventually be published by our working group.

## 4) Standard reuse

There are many metadata standards around focusing on different use cases.
Whenever possible a metadata field or even profile should be reused from existing standards.
This can be done by using the respective GUPRIs (Globally Unique Persistent Resolvable Identifier) of the existing terms.

## 5) Online documentation

Each metadata module / profile and each individual metadata field shall have a definition and description text that is available online.

## 6) Formalized specification

The metadata schema needs to be available in a formalized way such that it can be used for validation and form generation purposes.

## 7) Language

The language used to specify metadata modules / profiles and metadata fields must be English.
If the formalization supports multiple languages other languages can be added as well, but English needs to be the one with the highest priority.

## 8) Tooling

### 8.1) Schema Editing

The metadata schema shall be stored on github in a dedicated repository in the NFDI4Energy organization.

The core schema shall be edited in Protege.

### 8.2) Analysis and Validation

Each new release of the schema must be checked with analysis tools to avoid design flaws and other smells.

At this point a list of recommended tools will be added in the future.

### 8.3) Conversion

Only one formal specification of the metadata schema can be considered to root schema.
Any other potential schema serialization must be generated from this root specification.
An example for this would be the generation of JSON schema files from an OWL formalization.

## 9) Versioning

The metadata schema must be versioned using git tags.
This way, the persistent URLs for the schema files include the respective version number.
A new version shall come with a migration script to convert existing entries to a newer version of the schema.

## 10) Usage guide

The metadata schema needs to be accompanied by an online documentation or guide on how to use it properly.
This shall include different user perspectives including but not limited to data owners, application developers and data registry maintainers.
