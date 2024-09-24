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

### Metadata Implementation Tools

|||
|---|---|
|**Title**|Metadata Implementation Tools|
|**ID**|REQ-METADATA-TOOLING-IMPLEMENT|
|**Goal**|Ensure that the implementation of the metadata schema is both comprehensive and user-friendly.|
|**Description**|The metadata implementation tools need to support both web services and software plugins, tailored to the specific needs of energy-related software. Thses tools should support multiple programming languages and are able to capture all the relevant metadata.|
|**Creation date**|2024-09-23|
|**Linked terms**||
|**Solution idea**|The core metadata schema shall be edited in Protege. The metadata schema shall be stored on github in a dedicated repository in the NFDI4Energy organization.|


### Metadata Integration Tools

|||
|---|---|
|**Title**|Metadata Integration Tools|
|**ID**|REQ-METADATA-TOOLING-INTEGRATION|
|**Goal**|Create a unified metadata schema that ensures all relevant metadata is included, but can also be customized to specific needs and use cases.|
|**Description**|The metadata integration tools should define explicit rules for what metadata fields are necessary and which are optional. These tools should allow users to select from a predefined families of metadata, ensuring that relevant metadata is captured.|
|**Creation date**|2024-09-23|
|**Linked terms**||
|**Solution idea**|Some existing ontoloy matching tools can be used for metadata integration|



### Metadata Validation Tools

|||
|---|---|
|**Title**|Metadata Validation Tools|
|**ID**|REQ-METADATA-TOOLING-VALIDATION|
|**Goal**|Make sure that metadata schema is accurate, complete, and compliant with predefined standards.|
|**Description**|Metadata validation tools can display and compare metadata, standardize mandatory fields for meaningful comparisons, and balance user experience with data comparability.|
|**Creation date**|2024-09-23|
|**Linked terms**||
|**Solution idea**||

### Metadata Improvement Tools

|||
|---|---|
|**Title**|Metadata Improvement Tools|
|**ID**|REQ-METADATA-TOOLING-IMPROVEMENT|
|**Goal**|Enhance the interoperability of the metadata schema with other metadata schems and improve the quality of metadata.|
|**Description**|The metadata improvement tools should provide functionality to edit existing metadata records and integrate the metadata standards from different sources together.|
|**Creation date**|2024-09-23|
|**Linked terms**||
|**Solution idea**|Protege can be used to improve metadata schema.|

Only one formal specification of the metadata schema can be considered to root schema.
Any other potential schema serialization must be generated from this root specification.
An example for this would be the generation of JSON schema files from an OWL formalization.

## 9) Metadata Versionalization Tools

|||
|---|---|
|**Title**|Metadata Versionalization Tools|
|**ID**|REQ-METADATA-TOOLING-VERSIONING|
|**Goal**|Implement version control for metadata schema.|
|**Description**|A new version shall come with a migration script to convert existing entries to a newer version of the schema.|
|**Creation date**|2024-09-23|
|**Linked terms**||
|**Solution idea**|The metadata schema can be versioned using git tags, in this way, the persistent URLs of the metadata schema files will contain the respective version number. Each new release of the schema must be checked with analysis tools to avoid design flaws and other smells.|



## 10) Usage guide

The metadata schema needs to be accompanied by an online documentation or guide on how to use it properly.
This shall include different user perspectives including but not limited to data owners, application developers and data registry maintainers.
