# Repolex Knowledge Graph of twisted/hyperbola

RDF knowledge graph data for [twisted/hyperbola](https://github.com/twisted/hyperbola), parsed by [repolex](https://repolex.ai).

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
rlex download twisted/hyperbola
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── acadb1f2e36b251947689eb83c98d1e0471037b0
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── acadb1f2e36b251947689eb83c98d1e0471037b0
│           └── chunk-001.nq.gz
├── blob
│   ├── 0ac576c1aa0ffdee40d4dffafd981129128a6334.nq.gz
│   ├── 14b65eb353313d722ee74054dcad9414284c940f.nq.gz
│   ├── 18bd8b050fc479593471dc2112879dead886e598.nq.gz
│   ├── 1c7000d4474d8b1bc029f68354bb8825382722c9.nq.gz
│   ├── 1f8b2de703085f0d6d5f8bcdbc6641fb89c58708.nq.gz
│   ├── 2789f850ab1178d7e58567b6344b1b6ef57d3b33.nq.gz
│   ├── 320b002d5a436057781366c55bbc9782e10fb362.nq.gz
│   ├── 33eac4f793a76b71eead3a6cde311fc34ea7717a.nq.gz
│   ├── 48ff3f9ed296edb553ec52b0e9abc00f23780013.nq.gz
│   ├── 50b565e2754275cab112f0a5807c3d7cdd12e961.nq.gz
│   ├── 554a2cf1816eefe117fb2f1946f32adaf03fbade.nq.gz
│   ├── 56a0158ceb13e32d7cb73bfe385bee0ced1e1bab.nq.gz
│   ├── 58049960ccb7eb34b51e2d4210b5927b8aace33e.nq.gz
│   ├── 59df026c0d94e9e87467002fa087b05e91bdf882.nq.gz
│   ├── 5d430bb5cb33629523ce235a74e6f30139a4a42d.nq.gz
│   ├── 69399df37133270a0a379936179aa121a97ae0ef.nq.gz
│   ├── 6c72c41044931c046b7aeb3a3bb6af4449db14b5.nq.gz
│   ├── 6cef434b4681ae6f8543bf30ca561b1884b29a86.nq.gz
│   ├── 77e24b4d9e8c3349fc968e37b681b8727e5f6e71.nq.gz
│   ├── 7f2c02724db6a08c6e41f0e853ecb95e9a4e8ebb.nq.gz
│   ├── 8457bac2c42e33138c6ec600a55302f48bd22cff.nq.gz
│   ├── 88d36bcafe8b16428c503c0b12ac563391521cf4.nq.gz
│   ├── 89dd1007f34f8fa6ad212b3fbbc68a3c9a9c91de.nq.gz
│   ├── 9942012673db1895cc2a535a4cac15478e7c8702.nq.gz
│   ├── 9d7c00e6918e4e8ed5b3d585779482f34d65b9c5.nq.gz
│   ├── 9f904e02975c829f6d909f0e3a98c8da71694c4f.nq.gz
│   ├── ac803655e2037040444bf4b1835c3267910d7560.nq.gz
│   ├── b4d6d9e4727e3067048f028f9247c16526b0e21c.nq.gz
│   ├── bbc12718a67c53e640d6faedcb6f3eaf7829fa38.nq.gz
│   ├── bd7e4c0f3d59b255b9c862bedd13b2f8b9dd860d.nq.gz
│   ├── cdbb516d94be73e7bdfb20124ccde7788519094b.nq.gz
│   ├── d8016c8b26e0959fab588ca8a4b2dde3ba543cfb.nq.gz
│   ├── de977ead995ce6d86200c7f33fe58278bf7a08c3.nq.gz
│   ├── e69de29bb2d1d6434b8b29ae775ad8c2e48c5391.nq.gz
│   ├── ef16a42d6519729cc96542a8b4f430725990464f.nq.gz
│   └── ff5c471315d959e6412f792df374d2af8641dabe.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── acadb1f2e36b251947689eb83c98d1e0471037b0.nq.gz
└── tag
    └── tag.nq.gz

11 directories, 42 files
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

[twisted/hyperbola](https://github.com/twisted/hyperbola)

---
*Parsed on 2026-10-15 by [repolex](https://repolex.ai)*
