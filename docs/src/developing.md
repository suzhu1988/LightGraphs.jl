# Developing Alternate Graph Types

This section is designed to guide developers who wish to write their own graph structures.

All LightGraphs functions rely on a standard API to function. As long as your graph structure is a subtype of
[`AbstractGraph`](@ref) and implements the following API functions with the given return values, all functions
within the LightGraphs package should just work:

- [`edges`](@ref)
- [`eltype`](@ref)
- [`has_edge`](@ref)
- [`has_vertex`](@ref)
- [`in_neighbors`](@ref)
- [`is_directed`](@ref): Note that since we use traits to determine directedness, `is_directed` for a `CustomGraph` type should have the following signatures:
  - `is_directed(::Type{CustomGraph})::Bool`
  - `is_directed(g::CustomGraph)::Bool`

- [`ne`](@ref)
- [`nv`](@ref)
- [`out_neighbors`](@ref)
- [`vertices`](@ref)

If the graph structure is designed to represent weights on edges, the [`weights`](@ref) function should also be defined. Note that the output does not necessarily have to be a dense matrix, but it must be indexable via `[u, v]`.

