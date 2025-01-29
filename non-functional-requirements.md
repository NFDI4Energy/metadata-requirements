# Non-functional requirements

Metadata can come in numerous flavors and therefore should allow to be used in multiple contexts.

## Design
### Metadata Schema

#### 1) 📜Links between metadata records
|||
|---|---|
|**ID**|REQ-DESIGN-SCHEMA-LINKED-METADATA|
|**Description**|Help users to traverse semantically linked metadata records that are similar, different, related, etc. This can involve data from the same or different project, a similar purpose or an explicitly specified difference. This can be achieved using an explicit field for links in the metadata schema|
|**Creation date**|2024-08-15|
|**Linked terms**|http://purl.org/dc/elements/1.1/relation, http://purl.org/dc/terms/isReferencedBy, http://purl.org/dc/terms/isRequiredBy, http://purl.org/dc/terms/references, http://purl.org/dc/terms/requires, https://datacite-metadata-schema.readthedocs.io/en/4.6/properties/relatedidentifier/, https://datacite-metadata-schema.readthedocs.io/en/4.6/properties/relateditem/, DCAT also uses DC terms|
|**Solution idea**|Provide a generic metadata module in the schema that focuses on relations to other datasets and think about a good collection of relations between them.|
|**Priority**|Low|

#### 2) 📜The metadata schema reuses agreed upon terms and semantics
|||
|---|---|
|**ID**|REQ-DESIGN-SCHEMA-REUSE-AGREED-SEMANTICS|
|**Description**|It is vital to not create duplicate definitions to improve interoperability. This should be done using pre-existing ontologies wherever possible|
|**Creation date**|2024-09-17|
|**Linked terms**|https://schema.org/sameAs, http://www.w3.org/2004/02/skos/core#related, http://www.w3.org/2004/02/skos/core#exactMatch (and other match types)|
|**Solution idea**|Importing / Referencing of all ontologies that provide useful terms or semantics|
|**Priority**|High|

#### 3) 📜Fields in the schema shall use controlled vocabularies as much as possible
|||
|---|---|
|**ID**|REQ-DESIGN-SCHEMA-CONTROLLED-VOCABULARIES|
|**Description**|Prevent the interoperability issues that arise with custom human input, by using controlled vocabularies for user input where possible|
|**Creation date**|2024-08-15|
|**Linked terms**|https://json-schema.org/draft/2020-12/json-schema-validation#name-pattern, http://www.w3.org/ns/shacl#class, http://www.w3.org/ns/shacl#nodeKind, http://www.w3.org/ns/shacl#sparql|
|**Solution idea**|Use either ENUM like instances of a type in OWL or specify a base class for terms as child classes, use public identifiers of a certain pattern (e.g. purl, doi, orcid, etc.) - multiple solutions will be necessary. Consider using Terminology services or special term lookup services like the DBpedia Lookup|
|**Priority**|High|

#### 4) 📜Fields need to be categorized by importance

|||
|---|---|
|**ID**|REQ-DESIGN-SCHEMA-FIELD-IMPORTANCE|
|**Description**|To allow users to quickly grasp which metadata fields are more important we need to cluster them into mandatory, optional, etc. |
|**Creation date**|2024-10-22|
|**Linked terms**|https://datacite-metadata-schema.readthedocs.io/en/4.6/properties/overview/#levels-of-obligation, https://www.dcat-ap.de/def/dcatde/3.0/spec/#verbindlichkeitsstufen|
|**Solution idea**|Additional attribute for all metadata fields (compare OEM Badges)|
|**Priority**|Medium|


#### 5) 📜Modularity


|||
|---|---|
|**ID**|REQ-DESIGN-SCHEMA-MODULARITY|
|**Description**|To ensure a good quality of metadata for a given entity it is important to have specifically tailored sets of metadata fields. It makes sense to group several fields together if they always appear in a common context. Each of these modules needs to have a precise and limited scope. Smaller is often better in this context.|
|**Creation date**|2024-10-22|
|**Linked terms**|http://www.w3.org/2004/02/skos/core#ConceptScheme,http://www.w3.org/2004/02/skos/core#inScheme|
|**Solution idea**|Cluster metadata fields in modules and allow one entity to be annotated by a set of these modules. A strategy to find the correct modules needs to be worked out|
|**Priority**|High|


#### 6) 📜Language

|||
|---|---|
|**ID**|REQ-DESIGN-SCHEMA-LANGUAGE|
|**Description**|Since key value maps only see a key equal if it matches 100% it is necessary to have all keys in a common language. We propose to use only English names for the keys. If a serialization format allows multiple languages also other languages can be supported, but English must have the highest priority|
|**Creation date**|2024-10-22|
|**Linked terms**|http://purl.org/dc/elements/1.1/language, https://datacite-metadata-schema.readthedocs.io/en/4.6/properties/language/, Note that these links are focusing on a language of a resource while this requirement focuses more on the design of the metadata schema|
|**Solution idea**|Just use English keys for the fields and perform translations only with annotation properties|
|**Priority**|High|

### Tooling

#### 12) 🔧 Metadata Schema Implementation Tools
|||
|---|---|
|**ID**|REQ-DESIGN-TOOLING-STATE-OF-THE-ART|
|**Description**|The Metadata schema shall be created and maintained using state-of-the-art tools of the semantic web domain|
|**Creation date**|2024-09-23|
|**Linked terms**|https://protege.stanford.edu/, https://github.com|
|**Solution idea**|The core metadata schema shall be edited in Protege. The metadata schema shall be stored on github in a dedicated repository in the NFDI4Energy organization.|
|**Priority**|High|

#### 7) 🔧 Metadata Schema Improvement Tools

|||
|---|---|
|**ID**|REQ-DESIGN-TOOLING-IMPROVEMENT|
|**Description**|To enhance the interoperability of the metadata schema with other metadata schemas and improve the overall quality of metadata, it is important to try to reuse existing terms. Finding these can be aided with the use of terminology search and cross-walks between metadata standards. The used design tools shall assist the developer in applying these mechanisms.|
|**Creation date**|2024-09-23|
|**Linked terms**|It seems existing plugins are too old to work|
|**Solution idea**|Protege can be used to edit the metadata schema. Protege could have useful plugins for terminology search from important other metadata standards. Otherwise a plugin might be configurable against a DBPedia Lookup that was initialized with common metadata standards.|
|**Priority**|Medium|


## Implementation

### Metadata Schema

#### 8) 📜Provided schema files

|||
|---|---|
|**ID**|REQ-IMPL-SCHEMA-PROVIDED-FILES|
|**Description**|A formalized specification of the schema is necessary. The preferred format is in a semantic format like Turtle/Notation3. Additionally the schema files shall be provided as JSON schema (both plain JSON and JSON-ld) as a convenience for external use cases. Only the semantic format can be considered the root schema and the others most be updated on every change respectively. These types of formats are prioritized because of their validation and form generation capabilities|
|**Creation date**|2024-09-23|
|**Linked terms**|N/A|
|**Solution idea**|JSON-Schema files can be generated from an OWL/SHACL specification of the root schema|
|**Priority**|High|

### Metadata Record

#### 9) 📝Metadata serialization formats shall be storable in a way that supports SPARQL federation

|||
|---|---|
|**ID**|REQ-IMPL-RECORD-STORAGE-FEDERATION|
|**Description**|Metadata shall be easily queriable among federated SPARQL endpoints, to improve findability. Queries should function with either native or virtual endpoints.|
|**Creation date**|2024-09-19|
|**Linked terms**|https://schema.org/SearchAction, https://schema.org/EntryPoint, https://schema.org/query, https://schema.org/includedInDataCatalog, http://edamontology.org/data_2080, http://edamontology.org/format_3748, http://edamontology.org/format_2195|
|**Solution idea**|Triplestore databases easily provide SPARQL endpoints and therefore federation capabilities. Alternatively metadata can be stored in a way that allows for virtual SPARQL endpoints to achieve the same effect.|
|**Priority**|high|

#### 10) 📝Metadata serialization formats need to be standardized

|||
|---|---|
|**ID**|REQ-IMPL-RECORD-FORMAT-STANDARDS|
|**Description**|Make sure that metadata is stored with a standardized serialization format, so most tools and frameworks natively support parsing and serializing it|
|**Creation date**|2024-08-15|
|**Linked terms**|http://purl.obolibrary.org/obo/NCIT_C171252, http://edamontology.org/format_1915, https://schema.org/encodingFormat|
|**Solution idea**|This means the preferred serialization formats are RDF/XML, JSON-LD, Turtle, N3 and Ntriples. Nevertheless, other standardized formats as XML, JSON, YAML and TOML are also valid and can be used.|
|**Priority**|high|

#### 11) 📝 Metadata record submodules storage structure
|||
|---|---|
|**ID**|REQ-IMPL-RECORD-METADATA-SUBMODULE-STORAGE-STRUCTURE|
|**Description**|Submodules will need to reference each other and a flat way of storage is superior if multiple submodules might reference the same submodule|
|**Creation date**|2024-10-22|
|**Linked terms**|https://schema.org/DefinedTermSet (A submodule is a Defined Term Set that contains metadata fields relevant to the topic of the submodule), https://schema.org/inDefinedTermSet (could use this to note if a term belongs to more than one submodule), https://schema.org/citation (could use this property of a Defined Term Set to track other sets that it references)|
|**Solution idea**|Use JSON $ref in JSON and the respective URIs in RDF based file formats|
|**Priority**|high|


### Tooling

#### 13) 🔧 Metadata record creation service

|||
|---|---|
|**ID**|REQ-IMPL-TOOLING-RECORD-CREATION-SERVICE|
|**Description**|To ensure that the creation of metadata records can be done easily from different application contexts a service solution for the creation can be beneficial. So this service could be embedded via an application plugin. Such a service can therefore support multiple programming languages.|
|**Creation date**|2024-09-23|
|**Linked terms**|N/A|
|**Solution idea**|Metadata record creation and editing as a web service.|
|**Priority**|Medium|

## Integration
### Metadata Schema

#### 14) 📜Allow interoperability between existing metadata standards
|||
|---|---|
|**ID**|REQ-INTEGRATION-SCHEMA-STANDARD-INTEROPERABILITY|
|**Description**|Metadata records for our schema should be easily interoperable with other platforms that use different schemas, as it prevents re-annotation of metadata in other formats and supports data access to and from other platforms|
|**Creation date**|2024-08-15|
|**Linked terms**|https://www.getty.edu/publications/categories-description-works-art/metadata-standards-crosswalk/, https://www.ukoln.ac.uk/metadata/interoperability/, http://www.w3.org/2004/02/skos/core#, http://ns.inria.org/edoal/1.0/, https://faircore4eosc.eu/eosc-core-components/metadata-schema-and-crosswalk-registry-mscr|
|**Solution idea**|Schema crosswalks to the most relevant standards are helpful for federated searches and form a foundation of format conversions. Scripts shall be provided to convert from and to our schema for a selected set of standards. Evaluate formalized (semantic) formats for crosswalks and recommend one that can be integrated into existing knowledge graphs / ontologies.|
|**Priority**|Medium|

#### 15) 📜Guidelines for applications using the metadata schema
|||
|---|---|
|**ID**|REQ-INTEGRATION-SCHEMA-APPLICATION-GUIDELINES|
|**Description**|Allow developers to get going with the schema quickly with a clear set of requirements or guidelines on how to integrate and work with the metadata schema and records. All applications that want to work with the standard are obliged to follow these guidelines.|
|**Creation date**|2024-08-15|
|**Linked terms**|N/A|
|**Solution idea**|Extrapolate a subset of the requirements on this page and format them on some kind of online documentation.|
|**Priority**|Low|


### Tooling
#### 16) 🔧 Metadata Integration Tools

|||
|---|---|
|**ID**|REQ-INTEGRATION-TOOLING-METADATA-FLEXIBILITY-FOR-APPLICATIONS|
|**Description**|A unified metadata schema used by the tools shall provide capabilities that allows each tool to customize the schema in certain limits to be best suited for the given use case of the tool. For example tools should be able to define explicit rules for what metadata fields are necessary and which are optional. Also the use of certain domain-specific metadata schemas/modules should be controllable, ensuring that relevant metadata is captured.|
|**Creation date**|2024-09-23|
|**Linked terms**|https://w3id.org/squap/SoftwareQuality/FlexibilityInUse, https://w3id.org/dco#FlexibilityService|
|**Solution idea**|The input forms for metadata should be somehow generated. This might require inputs from the developer on what metadata modules are relevant and if certain fields should have a non-standard mandatory state. This could work best with a service that produces metadata forms that can be configured via the parameters to the endpoint|
|**Priority**|Medium|

#### 17) 🔧 Provide export capabilities

|||
|---|---|
|**ID**|REQ-INTEGRATION-TOOLING-STANDARD-EXPORTS|
|**Description**|To boost compatibility and interoperability it is necessary to provide exports in a selection of well established metadata standards|
|**Creation date**|2024-10-22|
|**Linked terms**|https://w3id.org/squap/SoftwareQuality/Compatibility, https://w3id.org/squap/SoftwareQuality/Interoperability|
|**Solution idea**|Use formalized crosswalks to perform a conversion to classic standards like DCT, Datacite, ...|
|**Priority**|Medium|


## Use
### Metadata Schema

#### 18) 📜Online documentation

|||
|---|---|
|**ID**|REQ-USE-SCHEMA-DOCUMENTATION|
|**Description**|Each metadata module / profile, and each individual metadata field shall have a definition and description text that is available online.|
|**Creation date**|2024-08-15|
|**Linked terms**|https://w3id.org/arco/ontology/context-description/Documentation, http://dev.poderopedia.com/vocab/Documentation, https://w3id.org/loin#Documentation, https://w3id.org/semsys/ns/swemls#hasDocumentation, https://w3id.org/vair#TechnicalDocumentation, http://meta.icos-cp.eu/ontologies/cpmeta/hasDocumentationUri|
|**Solution idea**|Generated documentation on GitHub pages|
|**Priority**|high|

#### 19) 📜Usage guide

|||
|---|---|
|**ID**|REQ-USE-SCHEMA-USAGE-GUIDE|
|**Description**|The metadata schema needs to be accompanied by an online documentation or guide on how to use it properly. This shall include different user perspectives including but not limited to data owners, application developers and data registry maintainers. Also, it needs to motivate why the usage of metadata and respective standards is important.|
|**Creation date**|2024-08-15|
|**Linked terms**|http://www.w3.org/ns/lemon/ontolex#usage, http://rdvocab.info/RDARelationshipsWEMI/guide, http://def.seegrid.csiro.au/isotc211/iso19115/2003/metadata#Usage, http://purl.org/olia/ubyCat.owl#usage|
|**Solution idea**|Additional Markdown based documentation that can accompany the generated GitHub pages.|
|**Priority**|medium|

#### 20) 📜Visualize different use of terminology among reused / mapped schemas and ontologies
|||
|---|---|
|**ID**|REQ-USE-SCHEMA-DOCUMENTATION-TERMINOLOGY-DIFFERENCES|
|**Description**|Some terms are used differently between different standards or use different names for the same thing. The documentation shall provide a way to recognize those cases, to help users understand the differences of similar terms|
|**Creation date**|2024-08-15|
|**Linked terms**|http://open.vocab.org/terms/similarTo, http://vocab.deri.ie/cogs#TerminologicalMapping, http://www.w3.org/ns/lemon/vartrans#TerminologicalRelation|
|**Solution idea**|Use terminology from thesauri or SKOS to express "similarTerms", "similarButDifferent" and "notToBeConfusedWith" relations.|
|**Priority**|medium|

#### 21) 📜Schema documentation shall be understandable for users that need to fill or read metadata

|||
|---|---|
|**ID**|REQ-USE-SCHEMA-DOCUMENTATION-STAKEHOLDER-USERS|
|**Description**|The schema documentation must provide helpful information to users without semantics or metadata background, so it should not just be focused around developers|
|**Creation date**|2024-08-15|
|**Linked terms**|http://dev.poderopedia.com/vocab/hasOtherDocumentation, https://w3id.org/arco/ontology/context-description/DocumentationType (not sure)|
|**Solution idea**|This is hard to measure, so for now just involve end users in the design of the documentation.|
|**Priority**|Medium|

#### 22) 📜Allow for a curated way to extend controlled vocabularies

|||
|---|---|
|**ID**|REQ-USE-SCHEMA-CURATED-CONTROLLED-VOCABS|
|**Description**|Strict controlled vocabularies can cause frustration for users, if they are unable to correctly express the meta information that would be best suited. Free text can sometimes describe better what a certain artifact / dataset is about, if there are no matching values in the controlled vocabulary. However, free text causes interoperability issues, so it is necessary to provide a process that allows to add new items to a controlled vocabulary in a curated way, that does not hinder the workflow of the user|
|**Creation date**|2024-08-15|
|**Linked terms**|https://w3id.org/BCI-ontology#extends, (not sure)|
|**Solution idea**|Embedding a terminology search into a metadata input form when there can be no proper choice made to find a reference in an ontology for a term. If the term from the other ontology fulfills yet to be determined characteristics it might be possible to extend the vocabulary with that term (initially for the time the form is active) and on a long run the added "external" terms could be curated and either accepted or revoked centrally for the schema.|
|**Priority**|Medium|


### Metadata Record

#### 23) 📝Metadata UI needs to be simple and streamlined
|||
|---|---|
|**ID**|REQ-USE-RECORD-SIMPLE-UI|
|**Description**|Don't annoy or scare users with complex forms or workflows as this will prevent them from entering data alltogether. Simple and streamlined processes and UIs are key.|
|**Creation date**|2024-08-15|
|**Linked terms**|https://w3id.org/mod#browsingUI, http://www.w3.org/ns/ui#style|
|**Solution idea**|Provide either a wizard/survey like form with multiple small pages or a dialog with a chatbot rather than a form and use modern web frameworks to build the UI.|
|**Priority**|High|

#### 24) 📝Simplify linking between metadata records
|||
|---|---|
|**ID**|REQ-USE-RECORD-SIMPLIFY-LINKING|
|**Description**|For easier navigation and understanding relations between multiple (data) artifacts - it is necessary to allow to link between metadata records easily. Users are not likely to manually look up relations themselves. As a result any user interface should assist the user in finding appropriate potentially related metadata records automatically.|
|**Creation date**|2024-08-15|
|**Linked terms**|http://purl.obolibrary.org/obo/OBI_0000800|
|**Solution idea**|Search for strategies how to identify metadata records with a certain degree of similarties, such that a service can propose them to be added as a related metadata record. (Use the OEP scenario comparision as a foundation)|
|**Priority**|Low|

#### XX) 📝Metadata record value languages
|||
|---|---|
|**ID**|REQ-USE-RECORD-LANGUAGES|
|**Description**|Ontologies do support annotation in multiple languages so any user interface shall be allowed to present metadata in any given language as long as the formal serialization is again in the standard language. Controlled vocabularies might also provide translations for a given item.|
|**Creation date**|2024-11-07|
|**Linked terms**|http://purl.org/linguistics/gold/Language, http://purl.org/dc/terms/language, http://schema.org/Language|
|**Solution idea**|User interface code can use the respective language annotations for labels when displaying both fieldnames and selected (controlled) values|
|**Priority**|Low|

#### XX) 📝Metadata usage documentation shall be understandable for users that need to fill or read metadata

|||
|---|---|
|**ID**|REQ-USE-RECORD-DOCUMENTATION-STAKEHOLDER-USERS|
|**Description**|The workflow documentation must provide helpful information to users without data management background and shall allow everybody to get started with metadata annotation.|
|**Creation date**|2024-11-07|
|**Linked terms**||
|**Solution idea**|This is hard to measure, so for now just involve end users in the design of the documentation.|
|**Priority**|Medium|

### Tooling

#### 25) 🔧 Metadata Integration Tools

|||
|---|---|
|**ID**|REQ-USE-TOOLING-CONVERSION-SERVICE|
|**Description**|Provide a tool that supports metadata record conversion from one schema to another, enabling easy integration for tool developers, even if their existing tools are built around a different metadata schema. This tool should facilitate interoperability across multiple schemas, reducing the burden on developers to manually map terms or fields.|
|**Creation date**|2024-09-23|
|**Linked terms**|https://schema.org/Thing, https://schema.org/convertTo, https://schema.org/targetFormat, http://purl.org/dc/terms/conformsTo, http://purl.org/dc/terms/format, http://purl.org/dc/terms/relation, https://www.w3.org/TR/prov-o/#wasDerivedFrom, https://www.w3.org/TR/prov-o/#hadPrimarySource, https://www.w3.org/ns/dcat#mediaType, https://www.w3.org/TR/vocab-dcat-2/#Class, http://edamontology.org/format_1915, http://edamontology.org/operation_0335, http://www.w3.org/2004/02/skos/core#exactMatch, http://www.w3.org/2004/02/skos/core#closeMatch|
|**Solution idea**|Consider using existing ontology matching tools to perform schema mapping, which can be used as foundation to automate much of the metadata record conversion process.|
|**Priority**|Medium|


## Review
### Metadata Schema

#### 26) 📜Documentation shall clearly show the terms used from other ontologies / schemas
|||
|---|---|
|**ID**|REQ-REVIEW-SCHEMA-DOCUMENTATION-CLEAR-REFERENCES|
|**Description**|Documentation should reference terms from other ontologies and schemas to maximize interoperability, providing clear links to the original sources and formal specifications. This approach ensures consistent terminology and enables seamless integration with external systems, enhancing the metadata’s usability across diverse platforms. It also increases the awareness of users about the origins of each metadata field.|
|**Creation date**|2024-08-15|
|**Linked terms**|https://schema.org/about, https://schema.org/itemReviewed, https://schema.org/reviewAspect, https://schema.org/author, https://schema.org/reviewBody, https://schema.org/mentions, https://schema.org/citation|
|**Solution idea**|Use Markdown and HTML to incorporate named links to external sources. Schema terms can be embedded as metadata tags or structured annotations where applicable.|
|**Priority**|High|

#### 27) 📜Metadata schema / standard needs to have a clear versioning scheme
|||
|---|---|
|**ID**|REQ-REVIEW-SCHEMA-VERSIONING|
|**Description**|Implement a clear versioning scheme to ensure that each dataset is accurately linked to the correct schema version. This enables consistency, traceability, and compatibility across systems. The versioning system should include identifiers for major, minor, and patch updates. Each version should also link to release notes and modification dates where applicable. The current and all older versions must be accessible via a GUPRI.|
|**Creation date**|2024-08-15|
|**Linked terms**|https://schema.org/version, https://schema.org/releaseNotes, https://schema.org/dateModified|
|**Solution idea**|Use semantic versioning (e.g., MAJOR.MINOR.PATCH) and reference the used version in the metadata schema, so each record can be clearly referenced to the used version.|
|**Priority**|High|

### Metadata Record

#### 28) 📝Metadata serialization format validation

|||
|---|---|
|**ID**|REQ-REVIEW-RECORD-FORMAT-VALIDATION|
|**Description**|Validation of metadata records improves the quality of metadata. Therefore used record serializations must allow for standardized validation mechanisms. Validation needs to be done in two stages (client and server) to first improve UX and second guarantee record conformance|
|**Creation date**|2024-08-15|
|**Linked terms**|http://vocab.deri.ie/cogs#Validation, http://def.seegrid.csiro.au/isotc211/iso19115/2003/metadata#Format, http://simile.mit.edu/2003/10/ontologies/vraCore3#measurementsFormat, http://open.vocab.org/terms/json|
|**Solution idea**|JSON schema and JSONld can be used in conjunction to validate input metadata records. If using other semantic formats the superior validation of SHACL can be applied. Web user interfaces often support client side validation this should be applied whenever possible.|
|**Priority**|High|


### Tooling

#### 29) 🔧Version control shall be applied for documentation
|||
|---|---|
|**ID**|REQ-REVIEW-TOOLING-DOCUMENTATION-VERSION-CONTROL|
|**Description**|Apply version control to the metadata schema documentation. This will improve documentation quality, make changes to documentation traceable, and prevent losses when edits are made by multiple people.|
|**Creation date**|2024-09-19|
|**Linked terms**|https://schema.org/version, https://schema.org/UpdateAction|
|**Solution idea**|GitHub is a good foundation for the documentation source files and can also host the actual online documentation|
|**Priority**|medium|

#### 30) 🔧 Metadata Versioning Tools
|||
|---|---|
|**ID**|REQ-REVIEW-TOOLING-VERSIONING|
|**Description**|Apply version control to the metadata schema. This will improve schema quality, make changes to the schema traceable, and prevent losses when edits are made by multiple people. New versions shall come with migration scripts to convert existing entries to the new version of the schema.|
|**Creation date**|2024-09-23|
|**Linked terms**|https://schema.org/version, https://schema.org/schemaVersion, https://schema.org/UpdateAction|
|**Solution idea**|The metadata schema can be versioned using git tags, in this way, the persistent URLs of the metadata schema files will contain the respective version number. Each new release of the schema must be checked with analysis tools to avoid design flaws.|
|**Priority**|high|


#### 31) 🔧 Metadata Validation Tools
|||
|---|---|
|**ID**|REQ-REVIEW-TOOLING-VALIDATION|
|**Description**|Ensure that the metadata schema is accurate, complete, and compliant with predefined standards. This can be done, for example, through metadata schema validation tools which check that data registries can display and compare metadata, standardize mandatory fields for meaningful comparisons, and balance user experience with data comparability.|
|**Creation date**|2024-09-23|
|**Linked terms**|http://vocab.deri.ie/cogs#Validation, https://w3id.org/vair#Validation, http://data.businessgraph.io/ontology#validationRule|
|**Solution idea**|OBO-Foundry, OOPS!, ...|
|**Priority**|medium|
