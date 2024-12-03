# Non-functional requirements

Metadata can come in numerous flavors and therefore should allow to be used in multiple contexts.

## Design
### Metadata Schema

#### 1) 📜Links between metadata records
|||
|---|---|
|**ID**|REQ-DESIGN-SCHEMA-LINKED-METADATA|
|**Description**|Help users to traverse semantically linked metadata records that are similiar, different, related, etc. This can involve data from the same or different project, a similar purpose or an explicitly specified difference. This can be achieved using an explicit field for links in the metadata schema|
|**Creation date**|2024-08-15|
|**Linked terms**||
|**Solution idea**|Provide a generic metadata module in the schema that focuses on relations to other datasets and think about a good collection of relations between them.|
|**Priority**|Low|
|**OEMetadata**| ✔ Links between metadata records are established at different levels alrady: topics, subject, tags, context! And a seperate field is more difficult to harmonise. |

#### 2) 📜The metadata schema reuses agreed upon terms and semantics
|||
|---|---|
|**ID**|REQ-DESIGN-SCHEMA-REUSE-AGREED-SEMANTICS|
|**Description**|It is vital to not create duplicate definitions to improve interoperability. This should be done using pre-existing ontologies wherever possible|
|**Creation date**|2024-09-17|
|**Linked terms**||
|**Solution idea**|Importing / Referencing of all ontologies that provide useful terms or semantics|
|**Priority**|High|
|**OEMetadata**| ✔ Based on Datapackage and DCAT-AP |

#### 3) 📜Fields in the schema shall use controlled vocabularies as much as possible
|||
|---|---|
|**ID**|REQ-DESIGN-SCHEMA-CONTROLLED-VOCABULARIES|
|**Description**|Prevent the interoperability issues that arise with custom human input, by using controlled vocabularies for user input where possible|
|**Creation date**|2024-08-15|
|**Linked terms**||
|**Solution idea**|Use either ENUM like instances of a type in OWL or specify a base class for terms as child classes, use public identifiers of a certain pattern (e.g. purl, doi, orcid, etc.) - multiple solutions will be necessary. Consider using Terminology services or special term lookup services like the DBpedia Lookup|
|**Priority**|High|
|**OEMetadata**| ✔ OEMetadata has an LOEP feature. |

#### 4) 📜Fields need to be categorized by importance

|||
|---|---|
|**ID**|REQ-DESIGN-SCHEMA-FIELD-IMPORTANCE|
|**Description**|To allow users to quickly grasp which metadata fields are more important we need to cluster them into mandatory, optional, etc. |
|**Creation date**|2024-10-22|
|**Linked terms**||
|**Solution idea**|Additional attribute for all metadata fields (compare OEM Badges)|
|**Priority**|Medium|
|**OEMetadata**| ✔ Mandatory and Optional. Badges for additional effort. |


#### 5) 📜Modularity


|||
|---|---|
|**ID**|REQ-DESIGN-SCHEMA-MODULARITY|
|**Description**|To ensure a good quality of metadata for a given entity it is important to have specifically tailored sets of metadata fields. It makes sense to group several fields together if they always appear in a common context. Each of these modules needs to have a precise and limited scope. Smaller is often better in this context.|
|**Creation date**|2024-10-22|
|**Linked terms**||
|**Solution idea**|Cluster metadata fields in modules and allow one entity to be annotated by a set of these modules. A strategy to find the correct modules needs to be worked out|
|**Priority**|High|
|**OEMetadata**| ✔ Datapackage has basic structure, additional groups are implemented. But (JSON) nesting is annoying. |


#### 6) 📜Language

|||
|---|---|
|**ID**|REQ-DESIGN-SCHEMA-LANGUAGE|
|**Description**|Since key value maps only see a key equal if it matches 100% it is necessary to have all keys in a common language. We propose to use only English names for the keys. If a serialization format allows multiple languages also other languages can be supported, but English must have the highest priority|
|**Creation date**|2024-10-22|
|**Linked terms**||
|**Solution idea**|Just use English keys for the fields and perform translations only with annotation properties|
|**Priority**|High|
|**OEMetadata**| ✔ EN |

### Tooling

#### 12) 🔧 Metadata Schema Implementation Tools
|||
|---|---|
|**ID**|REQ-DESIGN-TOOLING-STATE-OF-THE-ART|
|**Description**|The Metadata schema shall be created and maintained using state-of-the-art tools of the semantic web domain|
|**Creation date**|2024-09-23|
|**Linked terms**||
|**Solution idea**|The core metadata schema shall be edited in Protege. The metadata schema shall be stored on github in a dedicated repository in the NFDI4Energy organization.|
|**Priority**|High|
|**OEMetadata**| ✔🛠 https://github.com/OpenEnergyPlatform/oemetadata JSON schema. Protege? |

#### 7) 🔧 Metadata Schema Improvement Tools

|||
|---|---|
|**ID**|REQ-DESIGN-TOOLING-IMPROVEMENT|
|**Description**|To enhance the interoperability of the metadata schema with other metadata schemas and improve the overall quality of metadata, it is important to try to reuse existing terms. Finding these can be aided with the use of terminology search and cross-walks between metadata standards. The used design tools shall assist the developer in applying these mechanisms.|
|**Creation date**|2024-09-23|
|**Linked terms**||
|**Solution idea**|Protege can be used to edit the metadata schema. Protege could have useful plugins for terminology search from important other metadata standards. Otherwise a plugin might be configurable against a DBPedia Lookup that was initialized with common metadata standards.|
|**Priority**|Medium|
|**OEMetadata**| ? |


## Implementation

### Metadata Schema

#### 8) 📜Provided schema files

|||
|---|---|
|**ID**|REQ-IMPL-SCHEMA-PROVIDED-FILES|
|**Description**|A formalized specification of the schema is necessary. The preferred format is in a semantic format like Turtle/Notation3. Additionally the schema files shall be provided as JSON schema (both plain JSON and JSON-ld) as a convenience for external use cases. Only the semantic format can be considered the root schema and the others most be updated on every change respectively. These types of formats are prioritized because of their validation and form generation capabilities|
|**Creation date**|2024-09-23|
|**Linked terms**||
|**Solution idea**|JSON-Schema files can be generated from an OWL/SHACL specification of the root schema|
|**Priority**|High|
|**OEMetadata**| 🛠 JSON schema modules forbetter maintenance. No turtle yet. |

### Metadata Record

#### 9) 📝Metadata serialization formats shall be storable in a way that supports SPARQL federation

|||
|---|---|
|**ID**|REQ-METADATA-FORMAT-FEDERATION|
|**Goal**|Metadata shall be easily queriable among federated endpoints|
|**Description**|Finding metadata works best in a federated environment. So we want to make sure that the metadata records used for any NFDI4Energy service are stored in a way that allows for SPARQL federation. Either with native or virtual SPARQL endpoints|
|**Creation date**|2024-09-19|
|**Linked terms**||
|**Solution idea**|Triplestore databases easily provide SPARQL endpoints and therefore federation capabilities. Alternatively metadata can be stored in a way that allows for virtual SPARQL endpoints to achieve the same effect.|
|**OEMetadata**| ✔ OEMetadata is part of the Databus / MOSS: https://moss.openenergyplatform.org/ |


#### 10) 📝Metadata serialization formats need to be standardized

|||
|---|---|
|**ID**|REQ-METADATA-FORMAT-STANDARDS|
|**Goal**|Make sure that metadata is stored with a standardized serialization format, so most tools and frameworks natively support parsing and serializing it|
|**Description**||
|**Creation date**|2024-08-15|
|**Linked terms**|http://purl.obolibrary.org/obo/NCIT_C171252, http://edamontology.org/format_1915, https://schema.org/encodingFormat|
|**Solution idea**|This means the preferred serialization formats are RDF/XML, JSON-LD, Turtle, N3 and Ntriples. Nevertheless, other standardized formats as XML, JSON, YAML and TOML are also valid and can be used.|
|**OEMetadata**| ✔🛠 Used JSON schema. Add RDF. |

#### 11) 📝 Metadata record submodules storage structure
|||
|---|---|
|**ID**|REQ-METADATA-SUBMODULE-STORAGE-STRUCTURE|
|**Description**|Submodules will need to reference each other and a flat way of storage is superior if multiple submodules might reference the same submodule|
|**Creation date**|2024-10-22|
|**Linked terms**||
|**Solution idea**|Use JSON $ref in JSON and the respective URIs in RDF based file formats|
|**Priority**|5|
|**OEMetadata**| ✔ Implemented JSOn schema submodules and script to generate. |


### Tooling

#### 13) 🔧 Metadata record Implementation Tools

|||
|---|---|
|**ID**|REQ-IMPL-TOOLING-RECORD-CREATION-SERVICE|
|**Description**|To ensure that the creation of metadata records can be done easily from different application contexts a service solution for the creation can be beneficial. So this service could be embedded via an application plugin. Such a service can therefore support multiple programming languages.|
|**Creation date**|2024-09-23|
|**Linked terms**||
|**Solution idea**|metadata record creation and editing as a web service.|
|**Priority**|Medium|
|**OEMetadata**| ✔ OEMetadataBuilder https://openenergyplatform.org/dataedit/oemetabuilder/ |

## Integration
### Metadata Schema

#### 14) 📜Allow interoperability between existing metadata standards
|||
|---|---|
|**ID**|REQ-INTEGRATION-SCHEMA-STANDARD-INTEROPERABILITY|
|**Description**|Metadata records for our schema should be easily interoperable with other platforms that use different schemas, as it prevents re-annotation of metadata in other formats and supports data access to and from other platforms|
|**Creation date**|2024-08-15|
|**Linked terms**||
|**Solution idea**|Schema crosswalks to the most relevant standards are helpful for federated searches and form a foundation of format conversions. Scripts shall be provided to convert from and to our schema for a selected set of standards. Evaluate formalized (semantic) formats for crosswalks and recommend one that can be integrated into existing knowledge graphs / ontologies.|
|**Priority**|Medium|
|**OEMetadata**| 🛠 Implement mappings and crosswalks in OMI (ongoing development)|

#### 15) 📜Requirements for applications using the metadata schema
|||
|---|---|
|**ID**|REQ-INTEGRATION-SCHEMA-APPLICATION-REQUIREMENTS|
|**Description**|Allow developers to get going with the schema quickly with a clear set of requirements on how to integrate and work with the metadata schema and records. All applications that want to work with the standard are obliged to follow these guidelines.|
|**Creation date**|2024-08-15|
|**Linked terms**||
|**Solution idea**|Extrapolate a subset of the requirements on this page and format them on some kind of online documentation.|
|**Priority**|Low|
|**OEMetadata**| 🛠 Add to documentation |


### Tooling
#### 16) 🔧 Metadata Integration Tools

|||
|---|---|
|**ID**|REQ-METADATA-TOOLING-INTEGRATION|
|**Goal**|Create a unified metadata schema that ensures all relevant metadata is included, but can also be customized to specific needs and use cases.|
|**Description**|The metadata integration tools should define explicit rules for what metadata fields are necessary and which are optional. These tools should allow users to select from domain-specific metadata schemas/modules, ensuring that relevant metadata is captured.|
|**Creation date**|2024-09-23|
|**Linked terms**||
|**Solution idea**|The input forms for metadata should be somehow generated. This might require inputs from the developer on what metadata modules are relevant and if certain fields should have a non-standard mandatory state.|
|**OEMetadata**| 🛠 Badges to priotise metadata keys. Develop templates for different ressources: timeseries, geodata, parameter...  |

#### 17) 🔧 Provide export capabilities
|||
|---|---|
|**ID**|REQ-STANDARD-EXPORTS|
|**Description**|To boost compatibility and interoperability it is necessary to provide exports in a selection of well established metadata standards|
|**Creation date**|2024-10-22|
|**Linked terms**||
|**Solution idea**|Use formalized crosswalks to perform a conversion to classic standards like DCT, Datacite, ...|
|**Priority**|4|
|**OEMetadata**| ✔🛠 Mappings to DCAT-AP, Dublin Core, INSPIRE, Data Cite, Zenodo. Implement crosswalks in OMI. |


## Use 
### Metadata Schema

#### 18) 📜Online documentation

Each metadata module / profile and each individual metadata field shall have a definition and description text that is available online.

#### 19) 📜Usage guide

The metadata schema needs to be accompanied by an online documentation or guide on how to use it properly.
This shall include different user perspectives including but not limited to data owners, application developers and data registry maintainers. Also it needs to motiviate why the usage of metadata and respective standards is important.

#### 20) 📜Visualize different use of terminology among reused / mapped schemas and ontologies
|||
|---|---|
|**ID**|REQ-DOCUMENTATION-TERMINOLOGY-DIFFERENCES|
|**Goal**|Help users understand the differences of similar terms in other standards|
|**Description**|Some terms are used differently between different standards or use different names for the same thing. The documentation shall provide a way to recognize those cases.|
|**Creation date**|2024-08-15|
|**Linked terms**||
|**Solution idea**|Use terminology from thesauri or SKOS to express "similarTerms", "similarButDifferent" and "notToBeConfusedWith" relations.|
|**OEMetadata**| ✔🛠 Include SKOS in the metadata crosswalks in OMI. |

#### 21) 📜Schema documentation shall be understandable for users that need to fill or read metadata

|||
|---|---|
|**ID**|REQ-USE-SCHEMA-DOCUMENTATION-STAKEHOLDER-USERS|
|**Description**|The schema documentation must provide helpful information to users without semantics or metadata background, so it should not just be focused around developers|
|**Creation date**|2024-08-15|
|**Linked terms**||
|**Solution idea**|This is hard to measure, so for now just involve end users in the design of the documentation.|
|**Priority**|Medium|
|**OEMetadata**| ✔🛠 Documentation in MkDocs. |

#### 22) 📜Allow for a curated way to extend controlled vocabularies

|||
|---|---|
|**ID**|REQ-CURATED-CONTROLLED-VOCABS|
|**Goal**|The predifined vocabularies are sometimes not enough - by introducing a mechanism to extend them in a curated way it prevents frustrations for users|
|**Description**|Free text can sometimes describe better what a certain artefact / dataset is about if there are no matching values in a controlled vocabulary. So it would be nice if there would be a simple process to add new items to a controlled vocabulary in a curated way, that does not hinder the workflow of the user|
|**Creation date**|2024-08-15|
|**Linked terms**||
|**Solution idea**|Embedding a terminology search into a metadata input form when there can be no proper choice made to find a reference in an ontology for a term. If the term from the other ontology fulfills yet to be determined characteristics it might be possible to extend the vocabulary with that term (initially for the time the form is active) and on a long run the added "external" terms could be curated and either accepted or revoked centrally for the schema.|
|**OEMetadata**| ✔🛠 Terminology is part of the OEO. A link to OEO-X has been added to the OEMetadataBuilder.Improve workflow! |


### Metadata Record

#### 23) 📝Metadata UI needs to be simple and streamlined
|||
|---|---|
|**ID**|REQ-USE-RECORD-SIMPLE-UI|
|**Description**|Don't annoy or scare users with complex forms or workflows as this will prevent them from entering data alltogether. Simple and streamlined processes and UIs are key.|
|**Creation date**|2024-08-15|
|**Linked terms**||
|**Solution idea**|Provide either a wizard/survey like form with multiple small pages or a dialog with a chatbot rather than a form and use modern web frameworks to build the UI.|
|**Priority**|High|
|**OEMetadata**| ✔🛠 OEMetadataBuilder has been updated with tabs. Contains LOEP for OEO annotations. Feedback wanted. |

#### 24) 📝Simplify linking between metadata records
|||
|---|---|
|**ID**|REQ-USE-RECORD-SIMPLIFY-LINKING|
|**Description**|For easier navigation and understanding relations between multiple (data) artifacts - it is necessary to allow to link between metadata records easily. Users are not likely to manually look up relations themselves. As a result any user interface should assist the user in finding appropriate potentially related metadata records automatically.|
|**Creation date**|2024-08-15|
|**Linked terms**||
|**Solution idea**|Search for strategies how to identify metadata records with a certain degree of similarties, such that a service can propose them to be added as a related metadata record. (Use the OEP scenario comparision as a foundation)|
|**Priority**|Low|
|**OEMetadata**| ✔ Links are done with tags. Datapackage (Datase) can contain multiple resources (distributions). |

#### XX) 📝Metadata record value languages
|||
|---|---|
|**ID**|REQ-USE-RECORD-LANGUAGES|
|**Description**|Ontologies do support annotation in multiple languages so any user interface shall be allowed to present metadata in any given language as long as the formal serialization is again in the standard language. Controlled vocabularies might also provide translations for a given item.|
|**Creation date**|2024-11-07|
|**Linked terms**||
|**Solution idea**|User interface code can use the respective language annotations for labels when displaying both fieldnames and selected (controlled) values|
|**Priority**|Low|
|**OEMetadata**| ? |

#### XX) 📝Metadata usage documentation shall be understandable for users that need to fill or read metadata

|||
|---|---|
|**ID**|REQ-USE-RECORD-DOCUMENTATION-STAKEHOLDER-USERS|
|**Description**|The workflow documentation must provide helpful information to users without data management background and shall allow everybody to get started with metadata annotation.|
|**Creation date**|2024-11-07|
|**Linked terms**||
|**Solution idea**|This is hard to measure, so for now just involve end users in the design of the documentation.|
|**Priority**|Medium|
|**OEMetadata**| ✔🛠 Existing Academy Course: https://openenergyplatform.github.io/academy/courses/07_metadata/ Update to 2.0|

### Tooling

#### 25) 🔧 Metadata Integration Tools

|||
|---|---|
|**ID**|REQ-METADATA-TOOLING-INTEGRATION|
|**Goal**|Make it easy for tool developers to integrate with our schema, even if it has been using a different metadata schema before|
|**Description**|We need to provide a service that allows metadata record conversion from one schema to another|
|**Creation date**|2024-09-23|
|**Linked terms**||
|**Solution idea**|Some existing ontoloy matching tools can be used for metadata schema matching which then form the foundation for automated metadata record conversion.|
|**OEMetadata**| 🛠 Implement mappings in OMI (ongoing development) |


## Review
### Metadata Schema

#### 26) 📜Documentation shall clearly show the terms used from other ontologies / schemas
|||
|---|---|
|**Title**||
|**ID**|REQ-DOCUMENTATION-CLEAR-REFERENCES|
|**Goal**|Express the amount of terminology reuse to express high level of interoperability|
|**Description**|The terms used to express things shall provide a reference to the original documentation and formal specification|
|**Creation date**|2024-08-15|
|**Linked terms**||
|**Solution idea**|Markdown and HTML both support named links to external sources|
|**OEMetadata**| ? |

#### 27) 📜Metadata schema / standard needs to have a clear versioning scheme
|||
|---|---|
|**ID**|REQ-SCHEMA-VERSIONING|
|**Goal**|Versioning allows to clearly identify the correct schema for each dataset|
|**Description**|Clearly distinguish newer versions from the old ones and make sure that all versions are available online|
|**Creation date**|2024-08-15|
|**Linked terms**||
|**Solution idea**|Semantic versioning for the schema and reference the versioned URL of the schema in each metadata record|
|**OEMetadata**| ✔ Implemented versions for standard + latest |

### Metadata Record

#### 28) 📝Metadata serialization format validation

|||
|---|---|
|**ID**|REQ-REVIEW-RECORD-FORMAT-VALIDATION|
|**Description**|Validation of metadata records improves the quality of metadata. Therefore used record serializations must allow for standardized validation mechanisms. Validation needs to be done in two stages (client and server) to first improve UX and second guarantee record conformance|
|**Creation date**|2024-08-15|
|**Linked terms**||
|**Solution idea**|JSON schema and JSONld can be used in conjunction to validate input metadata records. If using other semantic formats the superior validation of SHACL can be applied. Web user interfaces often support client side validation this should be applied whenever possible.|
|**Priority**|High|
|**OEMetadata**| ✔🛠 Implemented validations in OMI: Check datapackage, check JSON schema. |


### Tooling

#### 29) 🔧Version control shall be applied for documentation
|||
|---|---|
|**ID**|REQ-DOCUMENTATION-VERSION-CONTROL|
|**Goal**|Make changes to documentation traceable|
|**Description**|Version control needs to be applied to improve documentation quality and prevent losses through editing from different people|
|**Creation date**|2024-09-19|
|**Linked terms**||
|**Solution idea**|Github is a good foundation for the documentation source files and can also host the actual online documentation|
|**OEMetadata**| ✔🛠 Use mkdocs and mike for documentation versioning |


#### 30) 🔧 Metadata Versioning Tools
|||
|---|---|
|**ID**|REQ-METADATA-TOOLING-VERSIONING|
|**Goal**|Implement version control for metadata schema.|
|**Description**|A new version shall come with a migration script to convert existing entries to a newer version of the schema.|
|**Creation date**|2024-09-23|
|**Linked terms**||
|**Solution idea**|The metadata schema can be versioned using git tags, in this way, the persistent URLs of the metadata schema files will contain the respective version number. Each new release of the schema must be checked with analysis tools to avoid design flaws and other smells.|
|**OEMetadata**| ✔ Version control implemented |



#### 31) 🔧 Metadata Validation Tools
|||
|---|---|
|**ID**|REQ-METADATA-TOOLING-VALIDATION|
|**Goal**|Make sure that metadata schema is accurate, complete, and compliant with predefined standards.|
|**Description**|Metadata schema validation tools ensure that data registries can display and compare metadata, standardize mandatory fields for meaningful comparisons, and balance user experience with data comparability.|
|**Creation date**|2024-09-23|
|**Linked terms**||
|**Solution idea**|OBO-Foundry, OOPS!, ...|
|**OEMetadata**| ✔🛠 Implemented validations in OMI: Check datapackage, check JSON schema. Misses check linceses, etc.|






