# Contributing to TSZig

Thank you for your interest in contributing to TSZig! This document provides guidelines and instructions for contributing.

## 📋 Table of Contents

- [Code of Conduct](#code-of-conduct)
- [Getting Started](#getting-started)
- [Development Setup](#development-setup)
- [Making Changes](#making-changes)
- [Commit Guidelines](#commit-guidelines)
- [Pull Request Process](#pull-request-process)
- [Coding Standards](#coding-standards)

## Code of Conduct

By participating in this project, you agree to maintain a respectful and inclusive environment. Be kind, constructive, and professional in all interactions.

## Getting Started

1. **Fork** the repository you want to contribute to
2. **Clone** your fork locally
3. **Create a branch** for your changes
4. **Make your changes** following our guidelines
5. **Submit a Pull Request**

## Development Setup

### Prerequisites

- **Zig 0.15.1** or later
- **Git**
- A code editor (VS Code, Zed, or similar)

### Building from Source

```bash
# Clone the repository
git clone https://github.com/TSZig/<repo-name>
cd <repo-name>

# Build
zig build

# Run tests
zig build test
```

## Making Changes

### Branch Naming

Use descriptive branch names:
- `feat/arrow-functions` - New features
- `fix/parser-destructuring` - Bug fixes
- `docs/api-reference` - Documentation
- `refactor/lexer-optimization` - Refactoring

### Before You Start

1. Check existing issues and PRs to avoid duplicates
2. For large changes, open an issue first to discuss
3. Keep changes focused and atomic

## Commit Guidelines

We use [Conventional Commits](https://www.conventionalcommits.org/):

```
<type>: <description>

[optional body]

[optional footer]
```

### Types

| Type | Description |
|------|-------------|
| `feat` | New feature |
| `fix` | Bug fix |
| `docs` | Documentation only |
| `style` | Formatting, no code change |
| `refactor` | Code restructuring |
| `test` | Adding tests |
| `perf` | Performance improvement |
| `chore` | Maintenance tasks |
| `ci` | CI/CD changes |

### Examples

```
feat: add arrow function support to parser

fix: resolve memory leak in codegen output buffer

docs: update API reference for transpile function

refactor: optimize keyword lookup with ComptimeStringMap
```

### Rules

- **Max 70 characters** for the first line
- Use **imperative mood** ("add" not "added")
- **No period** at the end of the subject line
- **English only** for all commits

## Pull Request Process

1. **Update documentation** if needed
2. **Add tests** for new functionality
3. **Ensure all tests pass**: `zig build test`
4. **Follow coding standards** (see below)
5. **Request review** from maintainers

### PR Title Format

Same as commit messages:
```
feat: add template literal support
fix: correct array destructuring codegen
```

### PR Description Template

```markdown
## Summary
Brief description of changes.

## Changes
- Change 1
- Change 2

## Testing
How was this tested?

## Related Issues
Fixes #123
```

## Coding Standards

### Language

- **ALL code, comments, and documentation must be in English**
- No Portuguese, Spanish, or other languages in the codebase
- Variable and function names must be English words

### Zig Style

```zig
// ✅ CORRECT
pub fn parseExpression(self: *Parser) !*ast.Node {
    // Parse primary expression first
    const primary = try self.parsePrimary();
    return primary;
}

// ❌ WRONG - Portuguese comments
pub fn parseExpression(self: *Parser) !*ast.Node {
    // Analisa a expressão primária primeiro
    const primary = try self.parsePrimary();
    return primary;
}
```

### TypeScript Style (for examples)

```typescript
// ✅ CORRECT - Use const/let, never var
function processData(items: string[]): number {
    const count: number = items.length;
    let total: number = 0;
    
    for (const item of items) {
        total += item.length;
    }
    
    return total;
}

// ❌ WRONG - Using var
function processData(items: string[]): number {
    var count = items.length;  // Never use var
    return count;
}
```

### Testing Requirements

- All new features must have tests
- All bug fixes should include a regression test
- Tests must pass before merging

## Questions?

- Open an issue for questions
- Join discussions in the repository

---

Thank you for contributing to TSZig! 🚀
