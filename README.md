# Welcome

This repo contains our naming rules and best practices for repositories at UniDistance.
Please check these guidelines before creating a new repository.

## 1. Repository Naming Convention
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
- `funid-it-web-typo3`
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

## 3. Repository access
Repository access is managed through GitHub teams within the UniDistance organization.
- UniDistance members should receive access via their team, not as direct collaborators.
- Direct access is reserved only for external collaborators who are not part of the organization.
This ensures consistent rights management and easier onboarding/offboarding.

## 4. Branching strategy
### Main Branch
- `main` – always stable, deployable, production-ready
- No direct commits to `main` are allowed.
- All changes must go through a Pull Request.
- The main branch may be versioned, e.g. `17.0`, `18.0`
### Additional branches
These are branches you actually work on.
Use one of the follow prefixes.
- `release/<description>`
- `bugfix/[<ticketnr>-]<short-description>`
- `feature/[<ticketnr>-]<short-description>`

## 5. Commit messages
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

## 6. Secrets and sensitive data
**Do not commit secrets to Git repositories.**
Secrets include, but are not limited to:
- Private keys (`.pem`, `.key`, `.p12`, `.pfx`)
- API keys and tokens
- Passwords or credentials
- Certificates containing private keys
- Environment files (`.env`) with sensitive values
### Rules
- **Never commit private keys** (e.g. files containing  
  `BEGIN PRIVATE KEY`, `BEGIN RSA PRIVATE KEY`, `BEGIN EC PRIVATE KEY`).
- Only **public certificates** (`BEGIN CERTIFICATE`) or **public keys**
  may be committed.
- Secrets must be stored using:
  - Environment variables
  - A secret manager (GitHub Secrets, Vault, etc.)
  - Secure deployment tooling
### If a secret was committed by mistake
1. **Remove it immediately** from the repository.
2. **Rotate / regenerate** the compromised secret.
3. Rewrite Git history if necessary.
4. Notify the team if the secret may have been exposed.
### Best practices
- Add sensitive file patterns to `.gitignore`
- Use example files (e.g. `.env.example`) instead of real secrets
- Review commits carefully before pushing

