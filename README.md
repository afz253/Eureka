Here’s a README file for the provided PRM implementation code:

---

# PRM Algorithm for 2D Motion Planning

## Overview

This Python script implements the Probabilistic Roadmap (PRM) algorithm to solve a 2D motion planning problem in an environment containing triangular obstacles. The script generates a roadmap of valid paths, searches for a path from a start to a goal configuration, and applies path shortcutting for optimization.

## Dependencies

- `numpy`
- `pylab` (part of `matplotlib`)
- `networkx`
- `sklearn` (for `KDTree`)

Make sure to install these packages if you haven’t already:
```bash
pip install numpy matplotlib networkx scikit-learn
```

## Usage

1. **Setup Environment**: 
   - Create an instance of the `Environment` class with specified dimensions and obstacles.

2. **Generate Nodes**:
   - Randomly sample points in the environment that are not colliding with obstacles.

3. **Build Roadmap**:
   - Connect nodes within a certain radius if the path between them is collision-free.

4. **Add Start and Goal**:
   - Add the start and goal points to the roadmap and connect them to nearby nodes if the paths are collision-free.

5. **Path Search**:
   - Use the A* algorithm to find the shortest path from the start to the goal, with a heuristic that penalizes paths close to obstacles and boundaries.

6. **Path Shortcutting**:
   - Apply path shortcutting to optimize the path by removing unnecessary waypoints while ensuring the new path is collision-free.

## Code Details

### Key Functions

- **`is_line_segment_intersecting(x1, y1, x2, y2, x3, y3, x4, y4)`**:
  - Checks if two line segments intersect.

- **`is_point_near_boundary(x, y)`**:
  - Checks if a point is within a specified safe distance from the environment boundary.

- **`is_path_collision_free(node1, node2)`**:
  - Checks if the path between two nodes is collision-free.

- **`heuristic(node1, node2)`**:
  - Computes a heuristic for A* search, including penalties for proximity to obstacles and boundaries.

- **`is_segment_collision_free(x1, y1, x2, y2)`**:
  - Checks if a segment between two points is collision-free.

- **`path_shortcutting(path, max_rep)`**:
  - Applies shortcutting to the path to reduce its length while maintaining collision-free constraints.

### Parameters

- `num_samples`: Number of random nodes to sample in the environment.
- `connection_radius`: Maximum distance to connect nodes in the roadmap.
- `step_size`: Step size for finer collision checking.
- `safe_distance`: Threshold distance from obstacles and boundaries to maintain safety.
- `max_rep`: Number of repetitions for path shortcutting.

## Running the Code

To run the script, simply execute it in a Python environment with the necessary dependencies installed. The script will generate a 2D environment, compute the roadmap, search for a path, and visualize the results using `matplotlib`.

```bash
python prm_2d_motion_planning.py
```

## Visualization

The script uses `matplotlib` to display the environment, obstacles, start and goal configurations, and the computed path. The path is shown in green after shortcutting, indicating the optimized route from start to goal.

## License

This code is provided under the [MIT License](LICENSE), which allows for modification and distribution under certain conditions.

## Acknowledgements

This implementation is based on the PRM algorithm and the example code provided in the OSR robotics path planning documentation.

---

Feel free to adjust or add any additional information relevant to your specific use case or environment.
