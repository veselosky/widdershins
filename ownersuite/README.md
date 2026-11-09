# Widdershins Owner's Suite

The owner's suite is a Django project that provides tools for building your own personal web environment. It's the "members only" area of Widdershins, where you can manage your own content, relationships, and activities.

## How to use it

After creating your project, set up your development environment:

1. Install [uv](https://docs.astral.sh/uv/):
   ```bash
   # On macOS/Linux:
   curl -LsSf https://astral.sh/uv/install.sh | sh
   # Or with pip:
   pip install uv
   ```

2. Create a virtual environment and install dependencies:
   ```bash
   uv sync
   ```

3. Copy `example.env` to `.env` and configure your environment variables.

4. Run migrations:
   ```bash
   uv run python manage.py migrate
   ```

5. (Optional) Install pre-commit hooks:
   ```bash
   uv run pre-commit install
   ```

## Dependency Management

This project uses [uv](https://docs.astral.sh/uv/) for fast, reliable dependency
management. Dependencies are defined in `pyproject.toml`.

### Adding Dependencies

To add a new dependency:

```bash
uv add <package-name>
```

### Updating Dependencies

To update all dependencies in your environment to their latest compatible versions:

```bash
uv sync --upgrade
```

To update a specific package:

```bash
uv sync --upgrade-package django
```

### Production Deployment

For production, install only the core dependencies:

```bash
uv sync --locked
```
