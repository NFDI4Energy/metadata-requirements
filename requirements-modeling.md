# Modeling guidelines for the requirements

## Module entity

|Field|Type|Description|
|---|---|---|
|Title|String|A short string capturing the module's context|
|ID|GUPRI|Globally unqiue and resolveable identifier of the module|
|Description|String|Medium length text to describe the purpose of the module|
|Creation Date|Date|First insertion of the module to the requirements list|
|Scope|String|Description what cases are covered by this module and which not|
|Responsible|String|Email Address or github id of the responsible user|
|Linked terms|List of URIs|Link terms of ontologies that are relevant|
|Requirements|List of Requirements|All requirements for the module|

Think about stakeholders for the module.

### Example

|||
|---|---|
|**Title**|Time series|
|**ID**|MODULE-TIMESERIES|
|**Description**|A time series is a mapping of a point or range in time towards a value. The value at this point can be a scalar / primitive or multidimensional.|
|**Creation date**|2024-08-15|
|**Scope**|This module is focusing explicitly on any type of data set that is a mapping as described above. It does specify the characteristics of the represented data. It can link to additional modules like sensor information or database information if applicable.|
|**Responsible**|philipp.schmurr@kit.edu|
|**Linked terms**|http://purl.obolibrary.org/obo/NCIT_C181915|
|**Requirements**|see example below|


## Requirement entity

|Field|Type|Description|
|---|---|---|
|Title|String|A short string capturing the requirement's context|
|ID|GUPRI|Globally unqiue and resolveable identifier of the requirement (e.g. concat module with name part)|
|Goal|String|Description why this module is important|
|Description|String|Medium length text to describe the specification of the requirement|
|Creation Date|Date|First insertion of the requirement to the list|
|Linked terms|List of URIs|Link terms of ontologies that are relevant|
|Solution idea|Text|Describe a potential solution that satisfies the requirement|

### Example
|||
|---|---|
|**Title**|Metadata serialization formats need to be standardized|
|**ID**|REQ-METADATA-FORMATS|
|**Goal**|Make sure that metadata is stored with a standardized serialization format, so most tools and frameworks natively support parsing and serializing it|
|**Description**|To guarantee widespread compatibility it is necessary to rely on data formats that are widely accepted in the real world and most languages / frameworks and tools can handle that kind of data|
|**Creation date**|2024-08-15|
|**Linked terms**|http://purl.obolibrary.org/obo/NCIT_C171252, http://edamontology.org/format_1915, https://schema.org/encodingFormat|
|**Solution idea**|In general, metadata in an RDF format is preferred since it enables it to be stored in triple store databases. This means the preferred serialization formats are RDF/XML, JSON-LD, Turtle, N3 and Ntriples. Nevertheless, other standardized formats as XML, JSON, YAML and TOML are also valid and can be used.|


### Template
|||
|---|---|
|**Title**||
|**ID**|REQ-|
|**Goal**||
|**Description**||
|**Creation date**|2024-08-15|
|**Linked terms**||
|**Solution idea**||