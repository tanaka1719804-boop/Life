# CLAUDE.md - Development Guide for AI Assistants

This document provides comprehensive guidance for AI assistants working on the Life project. It outlines the codebase structure, development workflows, and key conventions to follow.

---

## 1. Project Overview

**Project Name:** Life
**Repository:** tanaka1719804-boop/Life
**Status:** New project (under initial development)
**Primary Development Branch:** `claude/add-claude-documentation-*` (feature branches)

### Project Purpose
The Life project is a new initiative. As it develops, this document will be updated to reflect the actual purpose, technology stack, and architecture.

### Current State
- Empty repository with no production code yet
- Active development on feature branches
- Use this guide as a template for establishing project conventions

---

## 2. Repository Structure

```
/Life
├── CLAUDE.md                 # This file - development guide for AI assistants
├── README.md                 # Project overview and quick start (create as needed)
├── .git/                     # Git configuration
├── .gitignore                # Git ignore patterns
├── docs/                     # Documentation (create as project grows)
├── src/                      # Source code (structure depends on technology)
├── tests/                    # Test suite
├── scripts/                  # Build and utility scripts
├── .github/                  # GitHub configuration
│   └── workflows/            # CI/CD pipeline definitions
└── package.json / setup.py   # Dependency management (as appropriate)
```

### Directory Guidelines
- **`src/`**: All production source code
- **`tests/`**: Test files mirroring src structure
- **`docs/`**: Architecture decisions, guides, and documentation
- **`scripts/`**: Deployment, build, and utility scripts
- **`.github/workflows/`**: CI/CD pipeline definitions

---

## 3. Development Workflow

### Branch Strategy
- **Main branch:** Not yet established (will be created as project progresses)
- **Feature branches:** Follow naming convention `claude/feature-name-<session-id>`
- **Hotfix branches:** `hotfix/description` (if main branch exists)

### Creating & Switching Branches
```bash
# Create and switch to new feature branch
git checkout -b claude/feature-name-XfjqL

# List all branches
git branch -a

# Switch to existing branch
git checkout <branch-name>
```

### Committing Changes
- Write clear, descriptive commit messages
- Reference relevant issues/PRs when applicable
- Follow this format:
  ```
  <type>: <subject>

  <body - optional but recommended>

  Closes #<issue-number> (if applicable)
  ```

- Commit types: `feat`, `fix`, `refactor`, `docs`, `test`, `chore`
- Example:
  ```
  feat: add user authentication module

  - Implement JWT-based authentication
  - Add login and logout endpoints
  - Create user session management

  Closes #42
  ```

### Pushing Changes
```bash
# Push with tracking (required for new branches)
git push -u origin <branch-name>

# Subsequent pushes
git push

# Force push (only if necessary and coordinated)
git push --force-with-lease origin <branch-name>
```

### Pull Requests
- Always create a PR before merging to main
- Title: Clear, descriptive summary
- Description: Include context, testing done, and any breaking changes
- Request reviewers before merging
- Ensure CI/CD passes before merge

---

## 4. Key Conventions

### Code Style & Formatting
- **Language TBD:** Follow language-specific conventions once technology is selected
- **Formatting:** Use automated tools (Prettier, Black, Rustfmt, etc.)
- **Linting:** Enable linter to catch issues early
- **Type Safety:** Use type hints/annotations where available

### Naming Conventions
- **Variables & Functions:** camelCase (JavaScript) or snake_case (Python)
- **Classes/Types:** PascalCase
- **Constants:** UPPER_SNAKE_CASE
- **Files:** kebab-case for JavaScript/TypeScript, snake_case for Python
- **Directories:** lowercase, descriptive names

### File Organization
- Keep files focused on single responsibilities
- Max 500-1000 lines per file (language dependent)
- Group related functionality together
- Export public APIs clearly; mark internal utilities

### Error Handling
- Always handle errors explicitly
- Provide meaningful error messages
- Log errors with appropriate context
- Fail fast and safely

### Documentation
- Add comments for non-obvious logic only
- Maintain docstrings for public APIs
- Update documentation when code changes
- Link to architectural decision documents in code comments

---

## 5. Testing & Quality

### Testing Strategy (To Be Implemented)
- **Unit Tests:** Test individual functions/methods in isolation
- **Integration Tests:** Test module interactions
- **E2E Tests:** Test complete workflows (if applicable)
- **Coverage Goal:** Aim for 80%+ code coverage

### Test File Structure
```
tests/
├── unit/
│   └── [feature-name].test.js
├── integration/
│   └── [feature-name].integration.test.js
└── e2e/
    └── [workflow-name].e2e.test.js
```

### Running Tests Locally
```bash
# Run all tests
npm test / python -m pytest

# Run specific test file
npm test -- src/__tests__/file.test.js

# Run tests with coverage
npm run test:coverage
```

### CI/CD Pipeline
- Tests run automatically on every PR
- Coverage reports generated and checked
- Linting and type checking must pass
- All checks must pass before merging

---

## 6. Code Review & Quality Standards

### Before Submitting a PR
- [ ] Code follows project conventions
- [ ] All tests pass locally
- [ ] Code coverage is adequate
- [ ] Linting and type checking pass
- [ ] No console.log or debug code
- [ ] Documentation updated
- [ ] Commit messages are clear

### Common Issues to Avoid
- **Performance:** Don't ignore algorithmic complexity
- **Security:** Validate all inputs, avoid injection vulnerabilities
- **Accessibility:** Ensure UI features are accessible
- **Memory Leaks:** Clean up resources, avoid circular references
- **Over-engineering:** KISS principle - keep it simple

---

## 7. Deployment (To Be Configured)

### Deployment Environments
- **Development:** Local development environment
- **Staging:** Pre-production testing environment
- **Production:** Live environment for users

### Deployment Checklist
- [ ] All tests pass
- [ ] Code reviewed and approved
- [ ] Documentation updated
- [ ] Version bumped appropriately
- [ ] Changelog updated
- [ ] No environment secrets in code
- [ ] Database migrations prepared (if applicable)

---

## 8. AI Assistant Guidelines

### When Working on This Project

#### Do's
- ✅ Read existing code thoroughly before making changes
- ✅ Maintain consistency with established patterns
- ✅ Write clear commit messages
- ✅ Test changes before committing
- ✅ Document complex logic
- ✅ Follow the principle of least change - only modify what's necessary
- ✅ Ask for clarification on ambiguous requirements
- ✅ Refactor code responsibly with test coverage

#### Don'ts
- ❌ Commit without understanding the impact
- ❌ Introduce dependencies without discussion
- ❌ Break existing functionality
- ❌ Commit commented-out code
- ❌ Add unnecessary complexity or premature optimization
- ❌ Ignore test failures
- ❌ Force-push to main/master branch

### Decision Making
- **Ambiguity:** Ask for clarification before proceeding
- **Trade-offs:** Discuss performance vs. maintainability concerns
- **Architecture:** Propose designs for larger features, don't implement in isolation
- **Dependencies:** Minimize external dependencies; justify new ones

### Common Tasks

#### Adding a New Feature
1. Create a feature branch from main
2. Plan the implementation with clear, testable components
3. Implement incrementally with tests
4. Commit with clear messages
5. Create a PR with detailed description
6. Address review feedback
7. Merge once approved

#### Fixing a Bug
1. Reproduce the bug with a test case
2. Fix the underlying cause
3. Verify the fix with the test
4. Add regression test if not covered
5. Commit with clear explanation
6. Create a PR referencing the issue

#### Refactoring Code
1. Ensure comprehensive test coverage exists
2. Make small, incremental changes
3. Run tests after each change
4. Maintain functionality and API
5. Document any behavior changes
6. Keep commits focused on specific improvements

---

## 9. Development Setup (To Be Completed)

### Prerequisites
- Git configured with name and email
- Required language runtime/compiler installed
- Package manager appropriate to the stack

### Initial Setup
```bash
# Clone the repository
git clone http://local_proxy@127.0.0.1:17461/git/tanaka1719804-boop/Life
cd Life

# Install dependencies
# npm install / pip install -r requirements.txt / cargo build / etc.

# Create .env file if needed
# cp .env.example .env

# Run tests to verify setup
# npm test / python -m pytest / cargo test
```

### IDE/Editor Configuration
- Install relevant linting extensions
- Enable auto-formatting on save
- Install language support extensions
- Configure debug settings

---

## 10. Resources & Documentation (To Be Updated)

### To Be Created
- `README.md` - Project overview and quick start
- `ARCHITECTURE.md` - System design and architecture decisions
- `CONTRIBUTING.md` - Contribution guidelines (can reference this file)
- `API.md` - API documentation (if applicable)
- `.github/ISSUE_TEMPLATE/` - Issue templates
- `.github/PULL_REQUEST_TEMPLATE.md` - PR template

### External References
- (Add relevant documentation links as project develops)

---

## 11. Troubleshooting

### Git Issues

**"Push rejected - branch doesn't exist on remote"**
```bash
# Make sure to use -u flag when pushing new branch
git push -u origin <branch-name>
```

**"Merge conflicts when pulling"**
```bash
# Resolve conflicts in your editor, then:
git add <resolved-files>
git commit -m "Resolve merge conflicts"
git push
```

**"Need to undo recent commits"**
```bash
# Undo last commit but keep changes
git reset --soft HEAD~1

# Undo last commit and discard changes
git reset --hard HEAD~1
```

---

## 12. Maintenance & Updates

This document should be updated:
- When new technologies are adopted
- When development processes change
- When new conventions are established
- When major architectural decisions are made
- Regularly to reflect project maturity

**Last Updated:** 2026-02-24
**Last Updated By:** AI Assistant
**Status:** Template - To be expanded with actual project details

---

## Next Steps

1. **Define Project Purpose:** Clearly state what this project does
2. **Choose Technology Stack:** Select languages, frameworks, and tools
3. **Establish CI/CD:** Set up GitHub Actions or similar
4. **Create Baseline Documentation:** README, API docs, architecture decisions
5. **Initialize Project Structure:** Create directories and starter files
6. **Set Team Standards:** Establish code review criteria and quality gates

For AI assistants: This template is ready to be expanded. As the project develops, update sections with concrete details about the actual technology stack, architecture, and workflows being used.
