# Non-functional requirements

Metadata can come in many different flavors and therefore should allow to be used in multiple contexts.

## 1) Supported serialization formats

In general, metadata in a RDF format is preferred since it enables it to be stored in triple store databases.
This means the preferred serialization formats are RDF/XML, JSON-LD, Turtle, N3 and Ntriples.


Nevertheless, other standardized formats as XML, JSON, YAML and TOML are also valid and can be used.

## 2) Provided schema files

Schema files shall be provided as Turtle/Notation3 and as JSON schema. Both for standard JSON and JSON-LD?!
