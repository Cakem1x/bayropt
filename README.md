Bayropt
=======
Bayropt (Bayesian Robot Optimization) aims to provide an easily usable framework for blackbox parameter-optimization, using Bayesian optimization.
The framework is developed with robot perception algorithms as its focus.
Its first version was created as part of [my master's thesis](http://elib.dlr.de/119013/) on how to optimize feature-based map matcher algorithms.

Dependencies:
* python3
* numpy
* scipy
* matplotlib
* scikit-learn
* bayesian-optimization (https://github.com/fmfn/BayesianOptimization)
* pyyaml

Installation
------------
In case you don't already have python3 installed, you should be able to install it with your system's package manager.
The following code assumes that python and pip reference to python3.
Otherwise, replace python by python3 and pip by pip3.
All other depedencies are python-dependencies and they'll get installed automatically by using a python package manager like pip.
While this package isn't registered somewhere at the moment, but you can still install it after cloning this repo.
```bash
git clone git@github.com:Cakem1x/bayropt.git
cd bayropt
pip install .
```
Note that you may need to call pip install with sudo or tell pip to install it for your user only by providing the --user flag: `pip install --user .`
(Optional) Execute the provided tests to see whether things work on your system (let me know if they don't!).
```bash
python setup.py test
```

How to Use
----------
The etc directory contains an example experiment setup that should be ready for execution.
You can run it after installing the bayropt package:
```bash
./examples/wrapper.sh etc/example_experiment/experiment.yaml
```
The main script is experiment\_coordinator.py, but please use wrapper.sh to run it.
It's a simple wrapper script which sets PYTHONHASHSEED to a fixed value.
Without it, the SampleDatabase won't be able to recognize previously generated Samples.

This will generate MapMatcherSamples with fake data (lists of match-errors and the number of total matches) per tested parameter-set.
You can have look at the results in `etc/example_experiment/results`.
For productive use, those samples shouldn't be fake of course.
Instead, they should get generated by the perception algorithm you want to optimize.
