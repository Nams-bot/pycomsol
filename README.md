# PyCOMSOL
PyCOMSOL provides a simple python interface to the template COMSOL models used by the cell simulation team, utilising the Mph library. 
A valid COMSOL licence is required to run these models. It is also useful to be familiar with the COMSOL and excel templates that are being
called in the background. The purpose of PyCOMSOL is to facilitate automation of COMSOL simulation.

## :computer: Using PyCOMSOL
A simple study can by ran in the following way:
```python
import pycomsol

param_filepath = "path/to/parameter_file.excel"
model = pycomsol.DFN(param_filepath)

my_first_study = pycomsol.Study(
    name="my_unique_study_name",
    tag="time_transient",
    input_tables={"pulse_data": "path_to_input_csv"},
    output_tables=["time_probes"],
)

sim = pycomsol.Simulation(model)
sol = sim.solve(studies=my_first_study)
```
The results of the study will be provided in the form of pandas dataframes within the `sol` object. 

## :rocket: Installing PyCOMSOL
### User Install
We recommend installing PyCOMSOL within a [virtual environment](https://www.freecodecamp.org/news/how-to-setup-virtual-environments-in-python/) or a [conda environment](https://docs.conda.io/en/latest/). To install PyCOMSOL, download the `.whl` file for the latest [release](https://github.com/northvolt/pycomsol/releases) and then call
```
pip install path\to\whl\file\pycomsol-<version-number>-py3-non-any.whl
```

### Developer Install
We manage the development of PyCOMSOL using [git](https://git-scm.com/) so you should first follow their relevant installation instructions.

First, create a clone of the PyCOMSOL repository in your desired location:
```
cd /path/to/your/folder/of/preference
git clone https://github.com/northvolt/pycomsol.git
```
Create a new conda environment to work within: 
```
conda create -n pycomsol-env python=3.11
conda activate pycomsol-env
```
Then enter the PyCOMSOL directory and install the package and all required dependencies :
```
cd pycomsol
python -m pip install -e .
```

## :email: Get in Touch
If this tool is something that might also be useful to you or your team, feel free to reach out to us at: 
- manik.mayur@northvolt.com
- scott.marquis@northvolt.com
