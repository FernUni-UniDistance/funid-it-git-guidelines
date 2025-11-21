# Welcome

This repo contains our naming rules and best practices for repositories at UniDistance.
Please check these guidelines before creating a new repository.

## 1. Repository Naming Structure
Use lowercase, hyphens, and a clear scope.
### General pattern
```
funid-<department>-<project>[-<specification>]
```
Department prefixes:
- `it`
- `it-odoo`
- `edudl`
- `mkt`
- `fac-psy`

Project name: Choose a short, meaningful project name.
### Examples
- `funid-it-odoo-addons`
- `funid-mkt-web-typo3`
- `funid-fac-psy-translation-labjs`

## 2. Repository Creation Workflow
1. Create a new repository on GitHub following the naming conventions above.  
   Include:
   - a README.md
   - a .gitignore
   - no license, unless required
2. Clone the repository to your local machine
3. Create a Python virtual environment, e.g. with `pyenv` or `venv`: 
``` bash
pyenv virtualenv 3.11
```
4. Activate the environment: 
``` bash
pyenv activate your-project-name
```
5. Define your dependencies in `requirements.txt`.
6. Install dependencies:
```bash 
pip install -r requirements.txt
```
7. Commit and push
8. Set the correct team permissions on GitHub.
9. Apply branch protection rules, e.g. require at least one reviewer before merging.

## 3. Branching strategy
### Main Branch
- `main` – always stable, deployable, production-ready
- No direct commits to `main` are allowed.
- All changes must go through a Pull Request.
- The main branch may be versioned, e.g. `17.0`, `18.0`
### Additional branches
These are branches you actually work on.
Use one of the follow prefixes.
release/<description>
bugfix/[<ticketnr>-]<short-description>
feature/[<ticketnr>-]<short-description>

## 4. Commit messages
### Types
- `feat:` new feature
- `fix:` bug fix
- `docs:` documentation changes
- `style:` formatting only
- `refactor:` code restructuring (no behavior changes)
- `test:` test-related changes
- `chore:` maintenance tasks
### Examples
- `docs: improve markdown formatting`
- `feat: add gpu monitoring script`
- `fix: correct ssh permissions`
- `chore: update dependencies`
### Best Practices
- Use imperative form ("add" not "added")
- Keep the subject under 50 chars
- Use the body for context if needed