# CodingProject

# GitHub Collaboration Guidelines

## Roles & workflow
- **Team manager (one person per team)**  
  - Creates the GitHub repository and grants access.  
  - Is the only person who merges pull requests (the assignee).  
  - Resolves merge conflicts and enforces repo policies.

- **Contributors (everyone else)**  
  - Create a feature branch for every task.  
  - Open a Pull Request (PR) to merge into `main` when ready.  
  - Request review from 1–2 teammates (not the manager necessarily).

## Branching & naming
- Always branch from the latest `main`:
  ```bash
  git checkout main
  git pull
  git checkout -b <initials>/<short-description>