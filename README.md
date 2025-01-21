# VeTRA-Instances
Instances to test the Vehicle and Tool Routing Assignment (VeTRA-Instances)

## Dependecies
Works with Python 3.8+ and only depends on pandas.

## Example usage

To read the instances you must import pandas libary for python and following the next procedure:

```python
import pandas as pd

# Read Static benchmark instance and solution
tasks_dataset       = pd.read_csv(os.path.join(instance_dir, 'tasks.csv'))
depots_dataset      = pd.read_csv(os.path.join(instance_dir, 'depots.csv'))
vehicles_dataset    = pd.read_csv(os.path.join(instance_dir, 'vehicles.csv'))
tools_dataset       = pd.read_csv(os.path.join(instance_dir, 'tools.csv'))
compatibilities_tasks_tools_dataset     = pd.read_csv(os.path.join(instance_dir, 'compatibilities_tasks_tools.csv'))
compatibilities_vehicles_tools_dataset  = pd.read_csv(os.path.join(instance_dir, 'compatibilities_vehicles_tools.csv'))
```

The `instance` is compose of the set of tasks, depots, vehicles, tools and their compatibilities.

```python
>>> tasks_dataset.columns.tolist()
['name', 'x', 'y', 'start_time', 'end_time', 'service_time', 'revenue']

>>> depots_dataset.columns.tolist()
['name', 'x', 'y', 'start_time', 'end_time']

>>> vehicles_dataset.columns.tolist()
['name', 'max_distance', 'source_ref', 'sink_ref', 'speed', 'distance_cost']

>>> tools_dataset.columns.tolist()
['name', 'source_ref', 'sink_ref', 'use_cost']
```


The `solution` of each `instance` is a json with the whole information about vehicle and tools routes.

```python
import json

# Open and read the JSON file
with open(file_solution, 'r') as file:
    solution_json = json.load(file)

>>> solution_json.keys()
dict_keys(['instance', 'algorithm', 'objective_value', 'run_time', 'best_bound', 'overall_profit', 'solution', 'first_overall_profit', 'first_solution_time', 'max_run_time', 'vehicles_solved', 'steps', 'column_generated', 'rmp_run_time', 'warm_columns_added', 'all_times'])

>>> solution_json['solution'].keys()
dict_keys(['instance_name', 'objective_value', 'vehicle_routes', 'tool_routes'])
```