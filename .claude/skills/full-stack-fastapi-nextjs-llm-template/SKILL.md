# full-stack-fastapi-nextjs-llm-template Development Patterns

> Auto-generated skill from repository analysis

## Overview

This skill teaches development patterns for a full-stack cookiecutter template that generates FastAPI backends with Next.js frontends, specifically designed for LLM/AI agent applications. The codebase combines Python backend services with TypeScript frontend components, using a template-driven approach to generate customizable project structures.

## Coding Conventions

### File Naming
- Use **camelCase** for file names
- Template files follow cookiecutter pattern: `{{cookiecutter.variable_name}}`
- Test files use pattern: `*.spec.ts`

### Import Style
```python
# Use aliases for imports
import pandas as pd
import numpy as np
from fastapi import FastAPI as FastAPIApp
```

### Export Style
```typescript
// Use default exports
export default function Component() {
  return <div>Content</div>;
}
```

### Commit Messages
- Use conventional commit prefixes: `fix:`, `feat:`, `docs:`, `build:`, `test:`
- Keep messages around 45 characters
- Examples:
  - `fix: resolve user schema type mismatch`
  - `feat: add CrewAI agent integration`
  - `docs: update installation instructions`

## Workflows

### Version Release
**Trigger:** When preparing a new version release
**Command:** `/release`

1. Update version number in `pyproject.toml`
2. Add new features and fixes to `CHANGELOG.md`
3. Update `docs/CHANGELOG.md` if documentation changes exist
4. Ensure all changes are properly documented and tested
5. Tag the release and update version metadata

**Files involved:**
- `pyproject.toml`
- `CHANGELOG.md`
- `docs/CHANGELOG.md`

### User Model Schema Sync
**Trigger:** When updating user data structures or fixing type issues
**Command:** `/sync-user-types`

1. Update the user database model in `backend/app/db/models/user.py`
2. Update corresponding user schema in `backend/app/schemas/user.py`
3. Ensure type consistency between model and schema definitions
4. Run tests to verify compatibility
5. Update any dependent API endpoints

**Example:**
```python
# models/user.py
class User(Base):
    id: int
    email: str
    full_name: str | None = None

# schemas/user.py
class UserBase(BaseModel):
    email: str
    full_name: str | None = None
```

### Add AI Agent Framework
**Trigger:** When adding support for a new AI agent framework
**Command:** `/add-agent-framework`

1. Update `fastapi_gen/config.py` with new framework configuration options
2. Add user prompts in `fastapi_gen/prompts.py` for framework selection
3. Create agent implementation file in `template/.../backend/app/agents/`
4. Update API routes in `backend/app/api/routes/v1/agent.py`
5. Add framework variables to `template/cookiecutter.json`
6. Update backend dependencies in `backend/pyproject.toml`
7. Add comprehensive tests in `tests/test_config.py`
8. Update documentation with framework usage examples

**Example config addition:**
```python
# config.py
AGENT_FRAMEWORKS = {
    "crewai": "CrewAI multi-agent framework",
    "langgraph": "LangGraph workflow framework", 
    "deepagents": "DeepAgents autonomous framework"
}
```

### Dependency Updates
**Trigger:** When dependabot or manual dependency updates are needed
**Command:** `/update-deps`

1. Review and update GitHub workflow files in `.github/workflows/`
2. Update `uv.lock` file with new package versions
3. Update `pyproject.toml` if major version changes are needed
4. Test all workflows to ensure compatibility
5. Update any breaking changes in dependent code

### Template Feature Integration
**Trigger:** When adding new optional features to the template
**Command:** `/add-template-feature`

1. Add configuration options to `fastapi_gen/config.py`
2. Create user prompts for feature selection in `fastapi_gen/prompts.py`
3. Add variables to `template/cookiecutter.json`
4. Create template files for the new feature
5. Update post-generation hooks in `template/hooks/post_gen_project.py`
6. Add comprehensive tests covering the new feature
7. Update documentation with usage examples
8. Test template generation with feature enabled/disabled

**Example cookiecutter variable:**
```json
{
  "enable_redis_cache": ["yes", "no"],
  "database_type": ["postgresql", "sqlite", "mysql"]
}
```

### Documentation Update
**Trigger:** When project documentation needs updates or corrections
**Command:** `/update-docs`

1. Update main `README.md` with current project status
2. Update specific documentation files in `docs/` directory
3. Update template `README.md` files if generated projects change
4. Add entries to `CHANGELOG.md` documenting the changes
5. Ensure all code examples in docs are current and working
6. Update any architectural diagrams or workflow descriptions

## Testing Patterns

### Test Framework
- Uses **vitest** for TypeScript/JavaScript testing
- Test files follow `*.spec.ts` pattern
- Python tests likely use pytest (standard for FastAPI projects)

### Test Structure
```typescript
// example.spec.ts
import { describe, it, expect } from 'vitest';

describe('Component functionality', () => {
  it('should handle user input correctly', () => {
    // Test implementation
    expect(result).toBe(expected);
  });
});
```

## Commands

| Command | Purpose |
|---------|---------|
| `/release` | Update version and changelog for new release |
| `/sync-user-types` | Synchronize user model and schema definitions |
| `/add-agent-framework` | Integrate new AI agent framework support |
| `/update-deps` | Update GitHub Actions and package dependencies |
| `/add-template-feature` | Add new configurable feature to cookiecutter template |
| `/update-docs` | Update project documentation and README files |