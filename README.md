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
