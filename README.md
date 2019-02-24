#  JuMP Workshop at JuliaCon 2018

This site contains materials for the [JuMP](https://github.com/JuliaOpt/JuMP.jl) workshop at [JuliaCon 2018](http://juliacon.org/2018/). It is based on materials and notebooks from various sources including the [JuliaOpt notebooks](https://github.com/JuliaOpt/juliaopt-notebooks), the [2018 ISCO Spring School](https://github.com/joehuchette/ISCO-spring-school) and the [second annual JuMP-dev workshop](http://www.juliaopt.org/meetings/bordeaux2018/).

## Installation Instructions

You should use the latest version of Julia v1.1. Binaries of Julia for all platforms are available [here](http://julialang.org/downloads/).

You can download the materials by running
```
git clone https://github.com/juan-pablo-vielma/JuliaCon2018_JuMP_Workshop
```
or downloading [this zip file](https://github.com/juan-pablo-vielma/JuliaCon2018_JuMP_Workshop/archive/master.zip).

Finally, you can install [Jupyter](http://jupyter.org/) and its Julia backend [IJulia](https://github.com/JuliaLang/IJulia.jl) by running the following code in the Julia REPL.
```julia
import Pkg
ENV["JUPYTER"]=""
Pkg.add("Conda")
Pkg.add("IJulia")
import Conda
Conda.add("jupyter")
```

You can then run the following command to start Jupyter. 
```julia
using IJulia
IJulia.notebook()
```

Each notebook includes a cell with the commands
```julia
import Pkg
Pkg.activate(@__DIR__)
Pkg.instantiate()
```
that will install all required packages described by the included `Project.toml` and  `Manifest.toml` files. 	

