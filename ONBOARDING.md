# Developer Onboarding Guide

This guide helps new developers quickly get set up with the AI Coding Standards and start contributing to the project.

## Quick Start (5 minutes)

### Step 1: Install the Standards Package

```bash
pip install git+https://github.com/peterhallen/AI-coding-standards.git
```

Or if you have the repository cloned:

```bash
cd AI-coding-standards
pip install -e .
```

### Step 2: Install Standards in Your Project

Navigate to your project directory:

```bash
cd your-project
ai-coding-standards install --cursor --docs --pre-commit
```

This installs:
- ✅ Configuration files (`.editorconfig`, `.flake8`, `.pylintrc`, `pyproject.toml`)
- ✅ Cursor IDE rules (`.cursorrules` and `.cursor/rules/`)
- ✅ Documentation files (`docs/standards/`)
- ✅ Pre-commit hooks

### Step 3: Install Development Dependencies

```bash
pip install -r requirements-dev.txt
```

Or install individually:

```bash
pip install black isort mypy flake8 pylint pytest pytest-cov pre-commit
```

### Step 4: Set Up Your IDE

#### Cursor IDE (Recommended)

1. Open your project in Cursor
2. Cursor will automatically read `.cursorrules` and `.cursor/rules/`
3. The AI assistant will now follow your coding standards

#### VS Code

1. Install extensions:
   - Python
   - Black Formatter
   - Pylint
   - MyPy Type Checker
2. Settings will be picked up from `.editorconfig` and `pyproject.toml`

#### PyCharm

1. Go to Settings → Editor → Code Style
2. Import from `.editorconfig`
3. Configure Black as external tool

### Step 5: Verify Setup

Run these commands to verify everything is working:

```bash
# Check formatters
black --version
isort --version

# Check linters
flake8 --version
pylint --version

# Check type checker
mypy --version

# Test the setup
black --check .
isort --check-only .
```

## Understanding the Standards

### Read the Documentation

1. **Start with Quick Reference**: `CODING_STANDARDS_QUICK_REF.md`
   - One-page summary of key rules
   - Keep it handy while coding

2. **Read Full Standards**: `CODING_STANDARDS.md`
   - Comprehensive guide
   - Examples of good and bad code

3. **AI Prompt Standards**: `AI_PROMPT_STANDARDS.md`
   - How to write effective prompts for AI assistants
   - Especially useful with Cursor IDE

### Key Rules to Remember

**Function Limits:**
- Max 50 lines per function (prefer 30)
- Max 5 parameters (prefer 3)
- Max complexity of 10 (prefer 5)
- Max 3 levels of nesting (prefer 2)

**Documentation:**
- All public functions need docstrings
- All functions need type hints
- Use Google-style docstrings

**Naming:**
- Functions/variables: `snake_case`
- Classes: `PascalCase`
- Constants: `UPPER_SNAKE_CASE`

## Daily Workflow

### Before Writing Code

1. **Pull latest standards** (if updated):
   ```bash
   pip install --upgrade git+https://github.com/peterhallen/AI-coding-standards.git
   ```

2. **Check existing code style**:
   ```bash
   black --check .
   isort --check-only .
   flake8 .
   ```

### While Writing Code

1. **Use Cursor IDE** (if available):
   - AI assistant automatically follows standards
   - Ask for code generation with standards in mind

2. **Run formatters frequently**:
   ```bash
   black .
   isort .
   ```

3. **Check as you go**:
   ```bash
   mypy your_file.py
   flake8 your_file.py
   ```

### Before Committing

1. **Format code**:
   ```bash
   black .
   isort .
   ```

2. **Run linters**:
   ```bash
   flake8 .
   pylint your_module/
   ```

3. **Type check**:
   ```bash
   mypy .
   ```

4. **Run tests**:
   ```bash
   pytest --cov
   ```

5. **Pre-commit hooks** (if installed) will run automatically

## Common Tasks

### Adding a New Function

1. Write function with type hints
2. Add Google-style docstring
3. Keep under 50 lines
4. Add error handling
5. Write tests

**Example:**
```python
def process_user_data(
    user_id: str,
    data: Dict[str, Any]
) -> Dict[str, Any]:
    """Process user data and return results.
    
    Args:
        user_id: Unique identifier for the user
        data: Dictionary containing user data
    
    Returns:
        Dictionary with processed user data
    
    Raises:
        ValueError: If user_id is empty or data is invalid
    """
    if not user_id:
        raise ValueError("user_id cannot be empty")
    
    # Process data...
    return processed_data
```

### Refactoring Existing Code

1. **Check current state**:
   ```bash
   pylint your_file.py
   ```

2. **Identify issues**:
   - Functions too long? Extract helpers
   - Too complex? Simplify logic
   - Missing docs? Add docstrings
   - No type hints? Add them

3. **Refactor incrementally**:
   - One function at a time
   - Run tests after each change
   - Format as you go

### Working with Legacy Code

See [CODE_COMPLIANCE.md](CODE_COMPLIANCE.md) for detailed guide on bringing legacy code into compliance.

## Getting Help

### Resources

- **Quick Reference**: `CODING_STANDARDS_QUICK_REF.md`
- **Full Standards**: `CODING_STANDARDS.md`
- **Examples**: `examples/good_example.py`
- **Setup Guide**: `INSTALLATION.md`
- **Cursor Setup**: `CURSOR_SETUP.md`

### Common Questions

**Q: My function is 55 lines, what should I do?**
A: Extract helper functions. Look for logical sections that can be separate functions.

**Q: I need 6 parameters, what's the best approach?**
A: Use a dataclass or TypedDict to group related parameters.

**Q: How do I handle exceptions?**
A: Catch specific exceptions, provide context, and use custom exceptions for domain errors.

**Q: Do private functions need docstrings?**
A: They should have docstrings if the logic is non-obvious, but it's less critical than public functions.

## Checklist for New Developers

- [ ] Installed standards package
- [ ] Installed standards in project (`ai-coding-standards install`)
- [ ] Installed development dependencies
- [ ] Set up IDE (Cursor/VS Code/PyCharm)
- [ ] Read quick reference guide
- [ ] Read full standards (at least skimmed)
- [ ] Verified setup works (ran formatters/linters)
- [ ] Set up pre-commit hooks
- [ ] Understand key rules (function limits, docs, naming)
- [ ] Know where to find help/resources

## Next Steps

1. **Start coding**: Use the standards from day one
2. **Ask questions**: Don't hesitate to ask team members
3. **Review examples**: Check `examples/good_example.py`
4. **Use Cursor**: If available, leverage AI assistance
5. **Iterate**: Standards improve over time, contribute feedback

## Team Integration

### Code Reviews

When reviewing code, check:
- [ ] Functions ≤ 50 lines
- [ ] Type hints present
- [ ] Docstrings present
- [ ] Error handling appropriate
- [ ] Tests included
- [ ] Follows naming conventions

### Pair Programming

- Use Cursor IDE for real-time AI assistance
- Run formatters frequently
- Check standards as you code

### Team Meetings

- Discuss standards regularly
- Share best practices
- Update standards based on team feedback

---

**Welcome to the team!** 🎉

For questions or issues, see the resources above or reach out to your team lead.

