#  JuMP Workshop at JuliaCon 2018

This site contains materials for the [JuMP](https://github.com/JuliaOpt/JuMP.jl) workshop at [JuliaCon 2018](http://juliacon.org/2018/)

## Install Julia

You should use the latest version of Julia v0.6.2.
Binaries of Julia for all platforms are available [here](http://julialang.org/downloads/).


## Install Basic JuMP packages

To install the latest versions of [JuMP](https://github.com/JuliaOpt/JuMP.jl), [MathOptInterface](https://github.com/JuliaOpt/MathOptInterface.jl) and the open-source LP/MIP solvers [GLPK](https://www.gnu.org/software/glpk/) run the following code:
```julia
Pkg
Pkg.add("JuMP")
Pkg.checkout("JuMP")
Pkg.add("MathOptInterface")
Pkg.checkout("MathOptInterface")
Pkg.add("GLPK")
Pkg.checkout("GLPK")

```

To test that your installation is working, run the following code (the first time you run the code you may see the message like "INFO: Precompiling stale cache ..." for a few seconds):

```julia
using JuMP, MathOptInterface, GLPK
const MOI = MathOptInterface
m = Model(optimizer = GLPK.GLPKOptimizerLP())
@variable(m, x >= 0)
@variable(m, y >= 0)
@objective(m, Min, x + y)
@constraint(m, x + y <= 1)
JuMP.optimize(m)
println(MOI.get(m.moibackend, MOI.VariableName(), MOI.get(m.moibackend, MOI.VariableIndex, "x"))," = ",JuMP.resultvalue(x))
```

The output should be:

```
x = 0.0
```

## Install IJulia and Jupyter

[Jupyter](http://jupyter.org) is a convenient notebook-based interface to present documents which interleave code, text, and equations. Example code will be available in notebook format, but you should also be able to copy the notebook code to run from the REPL.

To install Jupyter and the Julia backend [IJulia](https://github.com/JuliaLang/IJulia.jl) run the following code:
```julia
ENV["JUPYTER"]=""
Pkg.add("IJulia")
```

To start Jupyter run the following code:
```julia
using IJulia
notebook()
```
