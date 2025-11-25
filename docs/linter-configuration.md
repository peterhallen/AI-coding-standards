# Linter Configuration Guidelines

This document provides guidelines for configuring linters to ensure consistent code quality across AI-assisted development projects.

## 1. Why Linters Matter

Linters help maintain code quality by:
- Enforcing consistent code style
- Catching common errors before runtime
- Improving code readability
- Reducing cognitive load during code reviews

## 2. Language-Specific Linter Recommendations

### 2.1 JavaScript/TypeScript

**Recommended Tools:**
- ESLint (primary linter)
- Prettier (code formatting)
- TypeScript compiler (type checking)

**Sample ESLint Configuration (.eslintrc.json):**
```json
{
  "extends": [
    "eslint:recommended"
  ],
  "parserOptions": {
    "ecmaVersion": 2022,
    "sourceType": "module"
  },
  "env": {
    "node": true,
    "es2022": true
  },
  "rules": {
    "no-unused-vars": "error",
    "no-console": "warn",
    "eqeqeq": "error",
    "curly": "error",
    "prefer-const": "error"
  }
}
```

### 2.2 Python

**Recommended Tools:**
- Ruff (fast all-in-one linter)
- Black (code formatting)
- mypy (type checking)

**Sample Ruff Configuration (pyproject.toml):**
```toml
[tool.ruff]
line-length = 88
target-version = "py311"

[tool.ruff.lint]
select = [
    "E",  # pycodestyle errors
    "W",  # pycodestyle warnings
    "F",  # Pyflakes
    "I",  # isort
    "B",  # flake8-bugbear
    "S",  # flake8-bandit (security)
]
```

### 2.3 Go

**Recommended Tools:**
- golangci-lint (comprehensive linting)
- gofmt (formatting)
- go vet (static analysis)

**Sample golangci-lint Configuration (.golangci.yml):**
```yaml
linters:
  enable:
    - errcheck
    - gosimple
    - govet
    - ineffassign
    - staticcheck
    - unused
    - gofmt
    - goimports
```

### 2.4 Java/Kotlin

**Recommended Tools:**
- Checkstyle (Java)
- SpotBugs (bug detection)
- ktlint (Kotlin)

### 2.5 C#/.NET

**Recommended Tools:**
- Roslyn analyzers
- StyleCop.Analyzers
- dotnet format

## 3. General Configuration Principles

### 3.1 Start with Recommended Configurations
- Begin with established "recommended" rule sets
- Customize based on team preferences and project needs
- Document any deviations from defaults

### 3.2 Consistency Over Perfection
- Choose a style and stick with it
- Avoid frequent rule changes that create unnecessary churn
- Prioritize rules that catch bugs over stylistic preferences

### 3.3 Integration with Development Workflow

**IDE Integration:**
- Configure linters to run on save
- Show inline warnings and errors
- Enable auto-fix where available

**CI/CD Integration:**
- Run linters in continuous integration pipelines
- Fail builds on linter errors
- Generate reports for tracking improvements

### 3.4 Gradual Adoption
- When adding linters to existing projects, start with warnings
- Fix issues incrementally
- Use baseline files to track new violations separately

## 4. AI-Specific Linting Considerations

### 4.1 Validate AI-Generated Code
- Run linters immediately after AI generates code
- Use strict rules for security-related patterns
- Check for common AI-generated code issues

### 4.2 Common AI Code Issues to Watch
- Unused imports or variables
- Inconsistent naming conventions
- Missing error handling
- Hardcoded values that should be configurable
- Overly complex or inefficient solutions

## 5. Sharing Linter Configurations

### 5.1 Team Sharing
- Store configurations in version control
- Use shareable config packages where available
- Document any custom rules or plugins

### 5.2 Cross-Project Consistency
- Create organization-wide base configurations
- Allow project-specific overrides
- Maintain a changelog of configuration changes
