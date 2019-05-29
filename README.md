# protoToOpenAPISchema
A python3 script for the generation of openAPI schemas from protocol buffers.
The script currently only works with openAPI definitions as yaml and thus requires the installation of:
<pre>
  sudo apt-get install python3-yaml
</pre>

# Features
* Take a proto file or a directory which is recursively searched for proto files and creates openAPI schemas
* Schemas are written to a yaml file or if an existing openAPI definition in yaml is provided the schemas will be added
* Does not overwrite existing schemas unless specified
* Allows adding a prefix to the names of schemas (E.g. the proto message Timestamp combined with the prefix Openbase results in the schema OpenbaseTimestamp.)
* Referenced messages result in references to their generated schemas

# Limits
* Only the first message in a proto file is processed (it can contain an arbitrary amount of internal messages and enums)

# Usage
<pre>
protoToOpenAPISchema.py [-h] [-p PROTO] [--openAPI OPENAPI]
                               [--overwrite] [--schemaPrefix SCHEMAPREFIX]

Tool for generating openAPI schemas definitions from protocol buffers.

optional arguments:
  -h, --help            show this help message and exit
  -p PROTO, --proto PROTO
                        proto file or directory. If a directory, it is
                        recursively searched for proto files. (default: .)
  --openAPI OPENAPI     openAPI definition file in yaml format to which the
                        generated schemas will be added. If it does not exist
                        it will be created. (default: openAPI.yaml)
  --overwrite           flag determining if schemas should be overwritten if
                        defined multiple times. (default: False)
  --schemaPrefix SCHEMAPREFIX
                        prefix used for every schema name. (default: )
</pre>

For a usage example, refer to the https://github.com/openbase/bco.openapi project.
