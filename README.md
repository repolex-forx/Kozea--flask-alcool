# Repolex Knowledge Graph of Kozea/flask-alcool

RDF knowledge graph data for [Kozea/flask-alcool](https://github.com/Kozea/flask-alcool), parsed by [repolex](https://repolex.ai).

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
rlex download Kozea/flask-alcool
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 507a7556f54a9d7c84e6bab6ccb4689757ca0132
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 507a7556f54a9d7c84e6bab6ccb4689757ca0132
│           └── chunk-001.nq.gz
├── blob
│   ├── 71a11e8ab1a11e3d01daa90964e699d55358c495.nq.gz
│   ├── 783a605eeb821996d3e0f0f0a462ccf40ef3c4bd.nq.gz
│   ├── 85fec3a4b02653e178718189e9bbc8bb42b13f17.nq.gz
│   ├── af2c23f1db095c075a646a5213f217e7e61eb66e.nq.gz
│   ├── c07bc349d4470a84e0be3cdc58f12b2c11115a43.nq.gz
│   └── f5197ae7c00e927028120e248ccd08fabaacc6b1.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 507a7556f54a9d7c84e6bab6ccb4689757ca0132.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 14 files
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

[Kozea/flask-alcool](https://github.com/Kozea/flask-alcool)

---
*Parsed on 2026-10-28 by [repolex](https://repolex.ai)*
