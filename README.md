# Repolex Knowledge Graph of scrapy/booksbot

RDF knowledge graph data for [scrapy/booksbot](https://github.com/scrapy/booksbot), parsed by [repolex](https://repolex.ai).

> **Note**: This data is experimental and subject to change without notice.

## How to use this data

The easiest way to get started is to install the [rlex](https://github.com/repolex-ai/rlex) query tool:

```bash
cargo install --git https://github.com/repolex-ai/rlex
```

Verify the install:

```bash
rlex --help
```

**rlex is designed to be used primarily by LLMs in a terminal.** Start up your favorite AI assistant and ask it to use rlex. It handles the SPARQL — you just ask questions in plain English.

To load this repo's data:

```bash
rlex download scrapy/booksbot
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 959a7dcdcf34c12f446a20e6e7bbecf97697f0fd
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 959a7dcdcf34c12f446a20e6e7bbecf97697f0fd
│           └── chunk-001.nq.gz
├── blob
│   ├── 08518a2ac28696dee3fa854b9e24113e329b179e.nq.gz
│   ├── 72364f99fe4bf8d5262df3b19b33102aeaa791e5.nq.gz
│   ├── 99ab43461fa4ad4144201f8dc513e7843df43797.nq.gz
│   ├── c5c46986f2b7232f850532ab8b04e53ca4a3781c.nq.gz
│   ├── e2c03f843de1122c06351f1a491dab1ed79b99db.nq.gz
│   ├── e69de29bb2d1d6434b8b29ae775ad8c2e48c5391.nq.gz
│   ├── ebd689ac51d69c5e1dbbe80083c2b20a39f8bb79.nq.gz
│   └── ed6286abcc0646c0f115a90423ab3e8be37f9ec4.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 959a7dcdcf34c12f446a20e6e7bbecf97697f0fd.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

12 directories, 15 files
```

| Directory | What it contains |
|-----------|-----------------|
| `blob/` | Per-file AST graphs, content-addressed by git blob SHA. Each file in the source repo gets its own graph. |
| `aggregate/ast/` | Combined AST graph per parsed commit. Merges all blob graphs for a snapshot of the entire codebase at that point. |
| `aggregate/lsp/` | Language Server Protocol enrichment: resolved symbols, definitions, references, and type information. |
| `aggregate/dataflow/` | Interprocedural data flow edges between functions and modules. |
| `aggregate/repolex/` | Combined graph (AST + LSP + dataflow) per commit. |
| `commit/` | Git commit metadata (author, date, message, parent links). |
| `branch/` | Branch metadata. |
| `tag/` | Tag metadata. |
| `filetree/` | File tree snapshots per commit (which files existed and their blob SHAs). |
| `audit/` | Code architecture and graph audit reports per commit. |

## Source repository

[scrapy/booksbot](https://github.com/scrapy/booksbot)

---
*Parsed on 2026-10-21 by [repolex](https://repolex.ai)*
