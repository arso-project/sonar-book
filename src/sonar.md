# Sonar

Now what is Sonar? It's our interpretation of the Dat stack, aimed at making it easy to archive, share and discover digitial media files. It's part of a larger (and early-stage) project towards a toolset for community media and the preservation of emancipatory parts of history.

Sonar is a set of modules and a user interface to manage records in a database built on top of hypercores and kappa-core. Sonar also is the integration of that database with tantivy, a fast full-text search engine written in Rust. Finally, Sonar is a sort of a runtime for services and interfaces that interact with these records-stored-in-hypercores. 

What follows is a description of the different parts of sonar, their interaction and status.

- hyper-content-db: v1 uses hyperdrives to store records in json files. v2 will use hypercores as append-only logs of records. A record has a unique id, a schema, and a value. The value usually is any JSON object, the schema describes all records of the same type. The ID is a unique string that is usually assigned by the database when creating new records. The database includes a few basic views to find records by type, id and modification date, to track relationships between records. It also will include ways to deal with schema modification and migration.

    > rename to sonar-db?

    > dependencies: hypercore, (hyperdrive? should be optional), kappa-core, leveldb

- [sonar-tantiy] is a binary for the tantivy search engine that includes a few modifications and additions around the managment of schema and indexes. It is written in Rust.

- [sonar-dat]: Connect a database with tantivy, plus a way to manage many of these databases. Currently based on hyper-content-db v1. Also connects the databases/hypercores to hyperswarm and simple-local-swarm.

- [sonar-server]: HTTP API to sonar-db and hyperdrives (/ sonar-fs?). Currently this is what "runs all the things".

- [sonar-ui]: A react single-page application that talks to sonar-server through sonar-client.

- [sonar-runtime]: A process runner that connects different clients through simple-rpc-protocol. Also will manage access and scopes?

- sonar-server: 
