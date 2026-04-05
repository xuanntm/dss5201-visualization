# Document for new course


## Project structure
```
Throughout the semester, we will store our
- source files (.py, .ipynb) in the src sub-folder;
- data files in the data sub-folder.
- ensure we are using at least Python 3.12
Using virtual environment: venv for project
Additional Packages
- numpy, matplotlib, pandas,...
```


## Create environment and install necessary libraries
```shell
cd src
python3.12 -m venv venv-dss5201
source venv-dss5201/bin/activate
pip install -r requirements.txt
pip freeze > requirements_2026April.txt
```

## Group project
- Load data from `data/plastics.csv`
- Cleanup data
- Visualize data
  - Visualization 1 : Over all top 10 companies in Asia 
  - Visualization 2 : focus companies tag to the respective countries but not present in global countries (not part of viz 1) 
  - Visualization 3 : compare the trend between 2019 and 2020