# Non-functional requirements

Metadata can come in numerous flavors and therefore should allow to be used in multiple contexts.

## 1) Supported serialization formats

In general, metadata in an RDF format is preferred since it enables it to be stored in triple store databases.
This means the preferred serialization formats are RDF/XML, JSON-LD, Turtle, N3 and Ntriples.


Nevertheless, other standardized formats as XML, JSON, YAML and TOML are also valid and can be used.

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
