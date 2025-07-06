# Shuup Template Subproject

This is a template subproject for Shuup e-commerce platform that uses the modern hatchling build system and uv package manager.

## Build Process Integration

This template syncs with the main Shuup build stack using:

### Modern Build System
- **Build Backend**: `hatchling.build`
- **Package Manager**: `uv` for fast dependency resolution
- **Configuration**: `pyproject.toml` (no setup.py or requirements.txt needed)

### Development Commands
```bash
# Install project for development
uv pip install -e .

# Install with optional dependencies
uv pip install -e ".[postgresql,production]"

# Run tests
uv run pytest

# Code quality checks
uv run black .
uv run isort .
uv run flake8 .
uv run ruff check .

# Type checking
uv run mypy .
```

### Dependencies
- **Core**: Latest compatible versions (no pinning)
- **Optional**: Database drivers, caching, production tools via `project.optional-dependencies`
- **Development**: Code quality tools via `dependency-groups.dev`

### Template Setup Process
1. **Clone Template**: Start with this modern template structure
2. **Install Dependencies**: `uv pip install -e .`
3. **Environment Setup**: Copy `.env.template` to `.env` if needed
4. **Database Setup**: `python manage.py migrate`
5. **Initialize Shuup**: `python manage.py shuup_init`
6. **Create Superuser**: `python manage.py createsuperuser`
7. **Run Server**: `python manage.py runserver`

### Key Files
- `pyproject.toml` - Modern build configuration with all dependencies
- `manage.py` - Django management commands
- `project/settings.py` - Django settings with environment support
- `business_logic/` - Custom business logic package

### Build Stack Synchronization
The template maintains compatibility with the main Shuup build system by:
- Using hatchling build backend (same as main project)
- Following same code quality standards (black, isort, flake8, ruff)
- Using uv for dependency management
- Implementing same testing framework (pytest)
- Following same project structure conventions

### Optional Dependencies
Install additional features as needed:
```bash
# Database drivers
uv pip install -e ".[postgresql]"  # PostgreSQL
uv pip install -e ".[mysql]"       # MySQL
uv pip install -e ".[oracle]"      # Oracle

# Caching
uv pip install -e ".[redis]"       # Redis
uv pip install -e ".[memcached]"   # Memcached

# Production deployment
uv pip install -e ".[production]"  # Gunicorn + WhiteNoise

# Error monitoring
uv pip install -e ".[monitoring]"  # Sentry SDK
```

### Development Environment
```bash
# Install all development tools
uv pip install -e ".[dev]"

# Run full development setup
uv run pre-commit install
uv run black .
uv run isort .
uv run flake8 .
uv run pytest
```

This template provides a modern, maintainable foundation for Shuup projects with automated build processes and quality checks.