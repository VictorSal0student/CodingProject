# Circular Task Analysis - MouseReMoCo

## Project Overview
This repository contains our implementation of circular tracking task analysis using MouseReMoCo software. The project successfully replicates reference metrics with <0.5% error and includes analysis of self-generated recordings.

**Authors:** Victor Salvat, Jinwei Zhang  
**Institution:** Digital and Movement Sciences for Health, Université de Montpellier  
**Date:** December 1, 2025

## Repository Structure
```
CodingProject/
├── README.md
├── data/
│   ├── 001MoDe_R1.csv              # Reference data
│   ├── 001MoDe_R1.marker.csv       # Reference markers
│   └── record_1/                   # Self-generated data
│       ├── 001MoDe_R1.csv
│       └── 001MoDe_R1.marker.csv
├── figs/                            # Generated figures
│   ├── trajectories.png
│   ├── performance_analysis.png
│   └── trials_analysis.png
└── report.pdf                       # Technical report
└── main.ipynb                       # Jupyter notebook with implementation
```

## Key Features
- **Data Segmentation:** Automatic detection of 5 recording periods using X≈0 markers
- **Coordinate Transformation:** Screen to center-aligned coordinates with Y-axis correction
- **Angular Unwrapping:** Lap counting with ±π discontinuity correction
- **Performance Metrics:** Re, Te, Error%, MT/lap, IDe/lap, Be, IPe computation
- **Validation:** <0.5% error against reference implementation
- **Advanced Analysis:** Velocity profiles, FFT analysis, composite scoring

## Requirements
```python
numpy
matplotlib
os
```

## Usage
1. Clone the repository:
```bash
git clone https://github.com/VictorSal0student/CodingProject.git
cd CodingProject
```

2. Open and run the Jupyter notebook:
```bash
jupyter notebook notebooks/circular_task_analysis.ipynb
```

3. The notebook processes both reference and self-generated data, producing all figures and metrics.

## Team Workflow

### Roles
- **Project Manager (Victor Salvat)**  
  - Created GitHub repository and granted access
  - Sole assignee for merging pull requests
  - Resolved merge conflicts and maintained code quality
  - Implemented self-generated data analysis and advanced kinematics

- **Contributor (Jinwei Zhang)**  
  - Implemented visual reproduction (Section 1)
  - Developed metric computation and verification (Section 2)
  - Created trajectory plots and time series visualizations

### Branching Strategy
- **Main branch:** Protected, only merged via pull requests
- **Feature branches:**
  - `feature/visualization` - Trajectory and time series plots
  - `feature/metrics` - Performance metric computation
  - `feature/analysis` - Advanced kinematic analysis
  - `feature/discussion` - Report and documentation

### Workflow Process
1. Always branch from latest `main`:
```bash
git checkout main
git pull
git checkout -b feature/<description>
```

2. Commit changes with descriptive messages:
```bash
git add .
git commit -m "Implement angular unwrapping algorithm"
git push origin feature/<description>
```

3. Create pull request on GitHub:
   - Request review from team member
   - Wait for approval before merging
   - Project manager merges approved PRs

4. Keep branches updated:
```bash
git checkout main
git pull
git checkout feature/<your-branch>
git merge main
```

## Coding Standards
- **Import restrictions:** Only `numpy`, `matplotlib.pyplot`, and `os`
- **Naming conventions:** snake_case for functions and variables
- **Documentation:** Comprehensive docstrings for all functions
- **Comments:** Inline explanations for complex algorithms
- **Modularity:** Separate functions for loading, processing, visualization

## Key Implementation Details

### Coordinate Transformation
```python
x_c = x_raw - center_x
y_c = y_raw - center_y
theta = np.arctan2(-y_c, x_c)  # Negative y for screen coords
```

### Angular Unwrapping
```python
angle_diffs = np.diff(angles)
angle_diffs = np.where(angle_diffs > np.pi, angle_diffs - 2*np.pi, angle_diffs)
angle_diffs = np.where(angle_diffs < -np.pi, angle_diffs + 2*np.pi, angle_diffs)
nLaps = np.sum(angle_diffs) / (2 * np.pi)
```

## Results Summary
- **Reference data:** 5 trials processed, all metrics within 0.5% error
- **Self-generated data:** 6 trials (3 right hand, 3 left hand)
- **Key findings:** 15% higher radial deviation for left hand, rapid learning effects observed

## Citation
If using this code, please cite:
```
Salvat, V., & Zhang, J. (2025). Circular Task Analysis Using MouseReMoCo: 
Technical Implementation and Validation. Université de Montpellier.
```

## References
Fauviaux, T., Muller, C., Faity, G., Bakhti, K., Laffont, I., et al. (2021). 
Can a circular steering task quantify sensorimotor integration in persons with stroke?. 
Congrès de la Société Française de Médecine Physique et de Réadaptation 2021, Lille, France.

## License
This project is part of academic coursework at Université de Montpellier.

## Contact
- Victor Salvat: [victor.salvat@etu.umontpellier.fr]
- Jinwei Zhang: [jinwei.zhang@etu.umontpellier.fr]

Repository: https://github.com/VictorSal0student/CodingProject.git