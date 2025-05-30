# Tutorial: neon

Neon is a serverless, open-source alternative to AWS Aurora Postgres. It **separates storage and compute**, enabling independent scaling and branching of data. The system uses *Pageservers* for scalable storage and *Safekeepers* for durable WAL management, allowing stateless *Compute Nodes* to efficiently execute queries.


**Source Repository:** [https://github.com/neondatabase/neon.git](https://github.com/neondatabase/neon.git)

```mermaid
flowchart TD
    A0["Pageserver
"]
    A1["Safekeeper
"]
    A2["Compute Node
"]
    A3["Timeline
"]
    A4["Local File Cache (LFC)
"]
    A5["WAL Proposer
"]
    A6["Connection Strings (pageserver_connstring, safekeepers_list)
"]
    A7["Neon Request LSNs (request_lsn, not_modified_since, effective_request_lsn)
"]
    A2 -- "Requests pages from" --> A0
    A2 -- "Sends WAL to" --> A1
    A5 -- "Replicates WAL to" --> A1
    A2 -- "Relies on" --> A5
    A0 -- "Cached by" --> A4
    A0 -- "Stores data versions" --> A3
    A2 -- "Uses for requests" --> A7
    A0 -- "Handles using" --> A7
    A2 -- "Configured by" --> A6
    A0 -- "Needs for communication" --> A6
    A5 -- "Configured with" --> A6
    A4 -- "Retrieves data from" --> A0
    A5 -- "Replicates WAL for" --> A3
```

## Chapters

1. [Compute Node
](01_compute_node_.md)
2. [Connection Strings (pageserver_connstring, safekeepers_list)
](02_connection_strings__pageserver_connstring__safekeepers_list__.md)
3. [Timeline
](03_timeline_.md)
4. [Pageserver
](04_pageserver_.md)
5. [Safekeeper
](05_safekeeper_.md)
6. [WAL Proposer
](06_wal_proposer_.md)
7. [Neon Request LSNs (request_lsn, not_modified_since, effective_request_lsn)
](07_neon_request_lsns__request_lsn__not_modified_since__effective_request_lsn__.md)
8. [Local File Cache (LFC)
](08_local_file_cache__lfc__.md)


---

Generated by [AI Codebase Knowledge Builder](https://github.com/The-Pocket/Tutorial-Codebase-Knowledge)