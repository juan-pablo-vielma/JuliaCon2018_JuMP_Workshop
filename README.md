#  JuMP Workshop at JuliaCon 2018

This site contains materials for the [JuMP](https://github.com/JuliaOpt/JuMP.jl) workshop at [JuliaCon 2018](http://juliacon.org/2018/). It is based on materials and notebooks from various sources including the [JuliaOpt notebooks](https://github.com/JuliaOpt/juliaopt-notebooks), the [2018 ISCO Spring School](https://github.com/joehuchette/ISCO-spring-school) and the [second annual JuMP-dev workshop](http://www.juliaopt.org/meetings/bordeaux2018/).

## Install Julia

You should use the latest version of Julia v0.6.2.
Binaries of Julia for all platforms are available [here](http://julialang.org/downloads/).


## Install Basic JuMP packages

To install the latest versions of [JuMP](https://github.com/JuliaOpt/JuMP.jl), [MathOptInterface](https://github.com/JuliaOpt/MathOptInterface.jl) and the open-source LP/MIP solvers [GLPK](https://www.gnu.org/software/glpk/) run the following code:
```julia
Pkg.update()
Pkg.add("JuMP")
Pkg.checkout("JuMP", "juliacon2018/0.19-dev")
Pkg.add("GLPK")
```

To test that your installation is working, run the following code (the first time you run the code you may see the message like "INFO: Precompiling stale cache ..." for a few seconds):

```julia
using JuMP, MathOptInterface, GLPK
const MOI = MathOptInterface
model = Model(with_optimizer(GLPK.GLPKOptimizerLP))
@variable(model, x >= 0)
@variable(model, y >= 0)
@objective(model, Min, x + y)
@constraint(model, x + y <= 1)
JuMP.optimize(model)
MOI.get(model, MOI.VariablePrimal(), x) == JuMP.resultvalue(x) == 0.0
```

The output should be:

```
true
```

**Note (if you have installed MOI directly):** Some notebooks may not work with MOI v0.5

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
