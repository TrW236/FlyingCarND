# Write-up Motion Planning

## 1. Explanation of the starter code

### Method `plan_path(self)` in `motion_planning.py`

1. Variable `data` is the loaded data from the file `colliders.csv`, which contains the information about the obstacles on the map.

2. The ìmported function `create_grid(...)` creates a 2d grid according to the obstacles' data.

3. The imported function `a_star(...)` performs the searching process, which tries to find a path from the start point to the end point with the provided grid.

### `planning_utils.py`

* Function `create_grid(...)` generates a 2d-grid based on the data of the obstacles, the drone altitude, and the safety distance.

* Class `Action` saves the possible actions, which the drone could take, to fly into the next cell of the grid.

* Function `valid_actions(...)` evaluates all the next possible actions, and remove the actions, which are invalid, based on the current position of the drone and the provided grid.

* Function `a_star(...)` performs a searching process, to find a path with the lowest cost according to a heuristic function from a start point to the endpoint.

* Function `heuristic(...)` calculates the heuristic value of each cell based on the distance of the current position and the goal position.

## 2. Set the home position

1. Read the global position provided in the first row in the file `colliders.csv`.

2. Set the global home position using `self.set_home_position(...)`

## 3. Calculate the local position

1. Retrieve the current global position.

2. Convert the global position to local position.

## 4. Change the start point

The start point is calculated through that the calculated current local position plus the offsets of the grid.

## 5. Change the goal position

1. Choose geodetic coordinates arbitrarily.

2. Convert this coordinates into local coordinates plus the offsets.

## 6. Searching algorithm

1. Add four additional values (north-west, northeast, south-west, south-east) to the class `Action`.

2. Add logic to the function `valid_actions(...)`, to remove the newly added values when necessary.

## 7. Cull waypoints

Perform the verification of the collinearity using the generated 2d path found from the searching algorithm.