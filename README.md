# PkgDependency.jl

[![](https://img.shields.io/badge/docs-latest-blue.svg)](https://peng1999.github.io/PkgDependency.jl/dev/)

Print dependency tree of a project or package.

Supported features include:

- Reverse dependency tree
- Show compat info in tree
- Show repo link in tree (needs at least Julia 1.7)

## Installation

In julia REPL, type `]` to enter package manager:

```
pkg> add PkgDependency
```

## Changelog

See [CHANGELOG.md](./CHANGELOG.md).

## Usage

Call `PkgDependency.tree`. Repeated dependencies are marked as `(*)`.

```console
julia> using PkgDependency
julia> PkgDependency.tree("CSV")
 CSV v0.10.4
━━━━━━━━━━━━━
      │
      ├── InlineStrings v1.1.4
      │   └── Parsers v2.3.2
      ├── PooledArrays v1.4.2
      │   └── DataAPI v1.10.0
      ├── WeakRefStrings v1.4.2
      │   ├── DataAPI v1.10.0 (*)
      │   ├── InlineStrings v1.1.4 (*)
      │   └── Parsers v2.3.2 (*)
      ├── CodecZlib v0.7.0
      │   └── TranscodingStreams v0.9.8
      ├── Tables v1.7.0
      │   ├── DataAPI v1.10.0 (*)
      │   ├── OrderedCollections v1.4.1
      │   ├── IteratorInterfaceExtensions v1.0.0
      │   ├── DataValueInterfaces v1.0.0
      │   └── TableTraits v1.0.1
      │       └── IteratorInterfaceExtensions v1.0.0 (*)
      ├── FilePathsBase v0.9.19
      │   └── Compat v4.2.0
      ├── Parsers v2.3.2 (*)
      └── SentinelArrays v1.3.13
```

If you want to customize the display of the tree, you can pass extra keyword arguments
to `PkgDependency.tree`. These will be passed on to the `Term.Trees.Tree` constructor
and subsequently, the `AbstractTrees.print_tree` method. For example:

```console
julia> using PkgDependency
julia> PkgDependency.tree("CSV", maxdepth=1)
CSV 0.10.4                
  ├─ InlineStrings v1.4.0 
  │  ⋮                    
  │                       
  ├─ PooledArrays v1.4.3  
  │  ⋮                    
  │                       
  ├─ WeakRefStrings v1.4.2
  │  ⋮                    
  │                       
  ├─ CodecZlib v0.7.4     
  │  ⋮                    
  │                       
  ├─ Tables v1.11.1       
  │  ⋮                    
  │                       
  ├─ FilePathsBase v0.9.21
  │  ⋮                    
  │                       
  ├─ Parsers v2.8.1 (*)   
  └─ SentinelArrays v1.4.1
```

## Contribution

Feel free to create issues if you want more features!
