# Repolex Knowledge Graph of explosion/wikid

RDF knowledge graph data for [explosion/wikid](https://github.com/explosion/wikid), parsed by [repolex](https://repolex.ai).

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
rlex download explosion/wikid
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 72d702cb6bec41d1901ccb3857e698eb4fb5c166
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 72d702cb6bec41d1901ccb3857e698eb4fb5c166
│           └── chunk-001.nq.gz
├── blob
│   ├── 02bed4a6e6548410df59e529a1489cef7ac3288a.nq.gz
│   ├── 0aa555ceb849fbcc73ac3e61d34baa0ff2991d64.nq.gz
│   ├── 148de8d29cc18bf5809919a08ba25347650bf5fe.nq.gz
│   ├── 1703a3b138127438a9f295dd5fa7cc4ba4b7e810.nq.gz
│   ├── 1c114c8d8cf8b863f8408cfeef86914a3d91dfb7.nq.gz
│   ├── 211238c7b5a24d68ce540329ca4a2b62f73c4081.nq.gz
│   ├── 284908a140fb1d6d9667539f4a4823b6422b0491.nq.gz
│   ├── 33c1e57678e33c43f332e196edf84f33da988b6e.nq.gz
│   ├── 52ae4f4ef8bd0b9642dfce2daed762d5e71ac3c0.nq.gz
│   ├── 55f7a920de5cde2ecf712c92a22657d1af9d293a.nq.gz
│   ├── 622440153fdf040561aca30224f0bdd706d7f58e.nq.gz
│   ├── 6ed5b998ef4bb6fc5fdf7abc62d8a29849951161.nq.gz
│   ├── 7aadd26b21677354d17cf299f708933196721526.nq.gz
│   ├── 835a49f3e08b673ece152dba3846d5375a3ca06d.nq.gz
│   ├── 84bbe6e978fffbc44e4d4bc32d1ffaa1b3c0c392.nq.gz
│   ├── 94548af5beba7825284af746324c8dc5b2f1ea31.nq.gz
│   ├── 9616597262107f5dd278eae46a41ae3193f2aa2b.nq.gz
│   ├── a049000665d486a2405642f005c803342720281a.nq.gz
│   ├── aca355600bd932fa6e5ee3e75aa78e5eb860f02b.nq.gz
│   ├── b2fd09d33f009b45b9ba102c635151386a2712a6.nq.gz
│   ├── bfa6e9a8bfef275a8b63e5329c7602e543473b68.nq.gz
│   ├── c1389f8e3de126fd75dea1e01f1c27a6b8d8fa66.nq.gz
│   ├── ce637ef8e254e9fa41edfc0fc46db7907f77d0e5.nq.gz
│   ├── da75a3196cdf089a25ecf5af162139adabba0852.nq.gz
│   ├── df59697b129765f7446eb8ae129ee7e21ed7195e.nq.gz
│   ├── e911b270fb9aeabe8a62f710a50382df01a875c1.nq.gz
│   ├── edfac194e1cbbabe1a2cfc0e30b350d8264b6394.nq.gz
│   └── f3d90d367550cb9e88c939a125a054e486c5510f.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 72d702cb6bec41d1901ccb3857e698eb4fb5c166.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 36 files
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

[explosion/wikid](https://github.com/explosion/wikid)

---
*Parsed on 2026-10-28 by [repolex](https://repolex.ai)*
