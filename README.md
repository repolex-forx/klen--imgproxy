# Repolex Knowledge Graph of klen/imgproxy

RDF knowledge graph data for [klen/imgproxy](https://github.com/klen/imgproxy), parsed by [repolex](https://repolex.ai).

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
rlex download klen/imgproxy
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 593191e936d653aaee36cdf84e514c29937458cc
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 593191e936d653aaee36cdf84e514c29937458cc
│           └── chunk-001.nq.gz
├── blob
│   ├── 00972793f953fcd71db62a15fff308892b06ff41.nq.gz
│   ├── 078ee803019030802caa7a3f24eb3d3de73e9287.nq.gz
│   ├── 18eff644215a6655fcf2724538e0d0f25ec46ea7.nq.gz
│   ├── 3ac1bb9c5b7aca06ed951b2f163e81a8cab45feb.nq.gz
│   ├── 5e7050c7a5e002102d5566dd56b9357ed2cabca7.nq.gz
│   ├── 66296b9fbe5c8ed758b0e0529a72bdc1f5bf994b.nq.gz
│   ├── 8c3b0f6523dc722b5d69c3fdaff16976267d52f1.nq.gz
│   ├── 97be70f2b88a778f950d830262920e2b63a029fc.nq.gz
│   ├── c5b55bcf627ada24f28caaedd438ab1f55ddf928.nq.gz
│   └── ed24943d06ae02837b0d2b5acb1d531984114c2e.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 593191e936d653aaee36cdf84e514c29937458cc.nq.gz
├── issue
│   └── issue.nq.gz
└── tag
    └── tag.nq.gz

12 directories, 17 files
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

[klen/imgproxy](https://github.com/klen/imgproxy)

---
*Parsed on 2026-10-20 by [repolex](https://repolex.ai)*
