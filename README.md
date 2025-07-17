# Multi-Agent System Notebooks

This directory contains the production-ready, sanitized version of the multi-agent system that demonstrates the implementation using Azure AI services, Semantic Kernel, and Microsoft Fabric.

## Directory Structure

## Git Repository Setup

### Prerequisites

Before setting up Git, ensure you have:
- Git installed on your system
- A GitHub account
- A GitHub repository created (or ready to create one)

### Initial Setup

1. **Navigate to the project directory:**
   ```bash
   cd "c:\CDrive\Fabric\multifab\code\hjfabmagentsync"
   ```

2. **Initialize Git repository:**
   ```bash
   git init
   ```

3. **Configure Git (if not done globally):**
   ```bash
   git config user.name "Your Name"
   git config user.email "your.email@example.com"
   ```

4. **Set up environment variables:**
   ```bash
   # Copy the example environment file
   copy .env.example .env
   
   # Edit .env with your actual values (DO NOT commit this file)
   notepad .env
   ```

### Connect to GitHub Repository

#### Option 1: Connect to Existing Repository
```bash
# Add your GitHub repository as remote
git remote add origin https://github.com/yourusername/your-repo-name.git

# Verify remote was added
git remote -v
```

#### Option 2: Create New Repository via GitHub CLI (if installed)
```bash
# Login to GitHub
gh auth login

# Create new repository
gh repo create your-repo-name --public --description "Multi-Agent System with Azure AI and Fabric"

# Connect to the created repository
git remote add origin https://github.com/yourusername/your-repo-name.git
```

### Initial Commit and Push

```bash
# Check what files will be staged
git status

# Stage all safe files
git add .

# Create initial commit
git commit -m "Initial commit: Production-safe multi-agent system

- Add HJMultiAgent_sanitized.ipynb: Complete multi-agent orchestration
- Add README.md: Comprehensive documentation and setup guide
- Add .gitignore: Security-focused ignore rules
- Add .env.example: Environment variables template
- Add .gitattributes: Git file handling configuration
- Implement Azure AI, Fabric Data Agents, and MLFlow integration
- All sensitive information replaced with environment variables"

# Push to GitHub (creates main branch)
git push -u origin main
```

### Daily Git Workflow

```bash
# Check status of your files
git status

# Stage specific files
git add filename.ipynb

# Stage all changes
git add .

# Commit changes with descriptive message
git commit -m "Add new feature: customer segmentation agent"

# Push changes to GitHub
git push

# Pull latest changes from GitHub
git pull

# Create and switch to new branch
git checkout -b feature/new-agent

# Switch back to main branch
git checkout main

# Merge feature branch
git merge feature/new-agent
```

### Security Checklist Before Each Commit

✅ **Before committing, always verify:**
- [ ] No sensitive information in files being committed
- [ ] `.env` file is NOT staged (should be in .gitignore)
- [ ] All credentials use environment variables
- [ ] No hardcoded connection strings or API keys
- [ ] Review `git status` and `git diff --staged` output

### Troubleshooting

#### Authentication Issues
If you encounter authentication problems:

```bash
# For HTTPS: Use Personal Access Token instead of password
# Create token at: https://github.com/settings/tokens

# For SSH: Set up SSH keys
ssh-keygen -t ed25519 -C "your.email@example.com"
# Add the public key to GitHub: https://github.com/settings/keys
```

#### Large File Issues
If you have large files:

```bash
# Install Git LFS
git lfs install

# Track large files
git lfs track "*.csv"
git lfs track "*.parquet"
git lfs track "*.pkl"

# Add .gitattributes
git add .gitattributes
git commit -m "Add Git LFS tracking for large files"
```

#### Undo Last Commit (if needed)
```bash
# Undo last commit but keep changes
git reset --soft HEAD~1

# Undo last commit and discard changes (DANGEROUS)
git reset --hard HEAD~1
```

### File Safety Status

✅ **SAFE TO COMMIT:**
- `HJMultiAgent_sanitized.ipynb` - Uses environment variables only
- `README.md` - Documentation only
- `.gitignore` - Security rules
- `.env.example` - Template with placeholders
- `.gitattributes` - Git configuration

❌ **NEVER COMMIT:**
- `.env` - Contains actual secrets
- Original notebooks with hardcoded values
- Any files with actual credentials or connection strings
- Large data files without Git LFS

