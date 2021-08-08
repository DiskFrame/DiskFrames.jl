## Not possible to use DataFrames.jl directly

After studying the `groupby` code for `DataFrames.jl` for example, it's clear that we can't just define a disk-based vector type and rely on dataframes to make things work. Because in the group by code they have things like `groups = Vector{Int}(undef, nrow(df))` which is an IN-MEMORY vector to keep track the groups. This will not be acceptable as it can just break. 

So it seems like we need a new type of Tables. Let's call it DiskFrames.jl.

I think the DiskArrays.jl is still usable.
