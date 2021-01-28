# PyLKH
This is a super simple Python wrapper for the constrained traveling salesman and vehicle routing problem solver called [LKH-3](http://akira.ruc.dk/~keld/research/LKH-3/).

If you want to use this wrapper, you should [install](http://akira.ruc.dk/~keld/research/LKH-3/) LKH-3 first.

LKH-3 expects problems in the TSPLIB95 format. Using PyLKH you can solve problems represented as Python objects (via [tsplib95](https://tsplib95.readthedocs.io/)) or files.

## Example
```
import requests
import tsplib95
import lkh

problem_str = requests.get('http://vrp.galgos.inf.puc-rio.br/media/com_vrp/instances/A/A-n32-k5.vrp').text
problem = tsplib95.parse(problem_str)

solver_path = '../LKH-3.0.6/LKH'
lkh.solve(solver_path, problem=problem, runs=10)
```

## API
`lkh.solve(solver='LKH', problem=None, **kwargs)`
Solve a problem.
#### Parameters
**solver** (str, optional): Path to LKH-3 executable.
**problem** ([tsplib95.model.StandardProblem](https://tsplib95.readthedocs.io/en/stable/pages/modules.html#tsplib95.models.StandardProblem), optional): Problem object. `problem` or `problem_file` is required.
**kwargs** (optional): Any LKH-3 parameter described here. For example: `max_trials=10000`.
#### Returns
**routes** (list): List of lists of nodes.