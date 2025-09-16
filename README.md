# scrap

A Python project managed with UV for fast and reliable dependency management.

## Prerequisites

This project uses [UV](https://github.com/astral-sh/uv) for Python package management. UV is a fast Python package installer and resolver, written in Rust.

## Installation

### Install UV

If you don't have UV installed, you can install it using:

```bash
curl -LsSf https://astral.sh/uv/install.sh | sh
```

Or using pip:

```bash
pip install uv
```

### Install Project Dependencies

Once UV is installed, you can install all project dependencies:

```bash
uv sync
```

This will:
- Create a virtual environment (`.venv/`)
- Install all dependencies from `pyproject.toml`
- Lock the exact versions in `uv.lock`

## Usage

### Running Commands

To run commands in the UV-managed environment:

```bash
# Run a Python script
uv run python script.py

# Run any command in the virtual environment
uv run <command>

# Activate the virtual environment manually
source .venv/bin/activate
```

### Managing Dependencies

```bash
# Add a new dependency
uv add package-name

# Add a development dependency
uv add --dev package-name

# Add a specific version
uv add "package-name>=1.0.0"

# Remove a dependency
uv remove package-name

# Update all dependencies
uv sync --upgrade

# Show installed packages
uv pip list
```

### Project Structure

- `pyproject.toml` - Project configuration and dependencies
- `uv.lock` - Locked dependency versions (auto-generated)
- `.venv/` - Virtual environment (auto-generated)
- `requirement.txt` - Original requirements file (kept for reference)

## Dependencies

This project includes the following main dependencies:

**Core Dependencies:**
- `jinja2~=3.0` - Template engine
- `markdown~=3.2` - Markdown processor
- `mkdocs~=1.6` - Static site generator
- `mkdocs-material~=9.5` - Material theme for MkDocs
- `mkdocs-get-deps~=0.2` - Dependency management for MkDocs
- `mkdocs-material-extensions~=1.3` - Extensions for Material theme
- `pygments~=2.16` - Syntax highlighting
- `pymdown-extensions~=10.2` - Markdown extensions

**Plugin Dependencies:**
- `babel~=2.10` - Internationalization
- `colorama~=0.4` - Cross-platform colored terminal text
- `paginate~=0.5` - Pagination utilities
- `regex>=2022.4` - Regular expressions
- `requests~=2.26` - HTTP library

## Development

### Adding New Dependencies

When adding new dependencies, use UV instead of pip:

```bash
# Instead of: pip install package-name
uv add package-name

# For development dependencies
uv add --dev package-name
```

### Updating Dependencies

```bash
# Update all dependencies to latest compatible versions
uv sync --upgrade

# Update a specific package
uv add "package-name@latest"
```

## GitHub Actions

This project includes automated CI/CD workflows:

### Continuous Integration (`ci.yml`)
- Runs on every push and pull request
- Tests MkDocs build process
- Validates Python syntax
- Ensures dependencies are properly installed

### Build and Deploy (`build-and-deploy.yml`)
- Automatically builds documentation on main branch pushes
- Deploys to GitHub Pages
- Includes both production deployment and PR testing

### Setup GitHub Pages

To enable automatic deployment:

1. Go to your repository Settings
2. Navigate to Pages section
3. Set Source to "GitHub Actions"
4. The workflow will automatically deploy on every push to main

## Benefits of Using UV

- **Speed**: 10-100x faster than pip
- **Reliability**: Better dependency resolution
- **Reproducibility**: Lock file ensures consistent installs
- **Modern**: Built with Rust, follows modern Python packaging standards
- **Compatibility**: Works with existing pip/requirements.txt workflows
