# Repolex Knowledge Graph of canonical/boltd-snap

RDF knowledge graph data for [canonical/boltd-snap](https://github.com/canonical/boltd-snap), parsed by [repolex](https://repolex.ai).

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
rlex download canonical/boltd-snap
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 733c91ba71e0e15f68340b27b6d5442a6f5b3d18
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 733c91ba71e0e15f68340b27b6d5442a6f5b3d18
│           └── chunk-001.nq.gz
├── blob
│   ├── 0869d473d353d8cb153f614c004cb314cc27c5a9.nq.gz
│   ├── 2051c072ac41adc0af5ca2e4de138e337d407737.nq.gz
│   ├── 287097bed5b2ffbbc691b5c0a48f73a43b600a72.nq.gz
│   ├── 2fa89653c99a162e283c32618a5ea3ca207ebcd1.nq.gz
│   └── 94d7b0724f63e1c207a05e74b2be603de8b3bded.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 733c91ba71e0e15f68340b27b6d5442a6f5b3d18.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

12 directories, 12 files
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

[canonical/boltd-snap](https://github.com/canonical/boltd-snap)

---
*Parsed on 2026-11-08 by [repolex](https://repolex.ai)*
