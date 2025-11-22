# Contributing Guide
authored by Co-Pilot

- - - - -

1. This document describes how team members collaborate using Git and GitHub. The goal is to maintain a simple workflow, avoid conflicts, and ensure that notebooks and code remain reproducible and stable.

- - - - -

2. The main branch contains only reviewed, stable, working material. Only the project manager merges changes into main. No contributor should commit directly to main. Every contributor works in a feature branch created specifically for each task. Branch names follow the pattern <firstname>/<short-description>, such as victor/reproduce-graphics or jinwei/recompute-values.

- - - - -

3. Before beginning any task, contributors update the local main branch using git checkout main followed by git pull. After updating, a new branch is created with git checkout -b <firstname>/<short-description>. All work is done inside this dedicated branch. When the task is complete, the contributor uses git add and git commit with short descriptive messages, for example feat: reproduced main experiment graphics. The branch is pushed to GitHub with git push -u origin <branchname>.

- - - - -

4. A Pull Request must be opened from the feature branch into main. The contributor includes a short description of the work and assigns teammates as reviewers. The project manager is assigned as the person responsible for merging. Before opening the Pull Request, the contributor restarts the notebook kernel, runs all cells from top to bottom without errors, and saves a clean version.

- - - - -

5. Merge conflicts are avoided by ensuring that no two contributors work on the same notebook at the same time. The project is divided into multiple notebooks such as 1_reproduce_graphics.ipynb, 2_recompute_values.ipynb, 3_test_generated_data.ipynb, and 4_discussion.ipynb. Contributors must always update from main before starting and keep each Pull Request focused on a single task.

- - - - -

6. Commit messages follow a consistent structure. The prefixes include feat: for new analysis, fix: for corrections, plot: for figure updates, and doc: for text or documentation changes. Examples include feat: add IPe computation functions or fix: correct indexing in marker processing.

- - - - -

7. The essential workflow is: first git pull; second git checkout -b <name>/<task>; third perform the work; fourth git add and git commit; fifth git push; sixth open a Pull Request; seventh the project manager reviews and merges.

- - - - -

8. If issues arise, contributors open a GitHub Issue, describe the problem, and assign it to the project manager. This ensures clarity, transparency, and traceability throughout the project.

- - - - -

9. Thank you for contributing!