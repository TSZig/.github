# TSZig

**TypeScript-like syntax → Memory-safe Zig code**

TSZig is a transpiler that enables JavaScript/TypeScript developers to write systems-level code using familiar syntax while generating memory-safe, high-performance Zig code.

## 🚀 Features

- **Familiar Syntax**: Write TypeScript-like code with types, interfaces, and modern ES6/ES12 features
- **Memory Safety**: Automatic resource cleanup with `@defer` annotation system
- **Zero Memory Leaks**: Smart detection of file handles, allocations, and resources
- **Native Performance**: Generates optimized Zig code that compiles to native executables
- **C-Style Extensions**: Support for `printf()`, compound operators, ternary expressions

## 📦 Packages

| Package | Description | Status |
|---------|-------------|--------|
| [tszig](https://github.com/TSZig/tszig) | Main CLI transpiler | 🔶 Active |
| [tszig-core](https://github.com/TSZig/tszig-core) | Core transpilation engine | 🔶 Active |
| [tszig-runtime](https://github.com/TSZig/tszig-runtime) | Runtime support library | 📋 Planned |
| [tszig-stdlib](https://github.com/TSZig/tszig-stdlib) | Standard library mappings | 📋 Planned |
| [tszig-inspector](https://github.com/TSZig/tszig-inspector) | Package analyzer & stub generator | 📋 Planned |
| [tszig-types](https://github.com/TSZig/tszig-types) | TypeScript definitions for IDEs | 📋 Planned |
| [tszig-examples](https://github.com/TSZig/tszig-examples) | Examples and tutorials | 📋 Planned |
| [tszig-vscode](https://github.com/TSZig/tszig-vscode) | VS Code extension | 📋 Future |
| [tszig-zed](https://github.com/TSZig/tszig-zed) | Zed editor extension | 📋 Future |

## 🎯 Quick Example

```typescript
// input.ts
function processFile(path: string): string {
    // @defer automatically injects cleanup
    const file = fs.openSync(path, "r");
    const content = fs.readFileSync(file, "utf8");
    return content;
}

function main(): void {
    const data = processFile("config.json");
    printf("Config: %s\n", data);
}
```

Generated Zig:
```zig
pub fn processFile(path: []const u8) []const u8 {
    const file = std.fs.cwd().openFile(path, .{}) catch unreachable;
    defer file.close();  // ✅ Auto-injected
    
    const content = file.readToEndAlloc(allocator, 1024 * 1024) catch unreachable;
    return content;
}

pub fn main() void {
    const data = processFile("config.json");
    defer allocator.free(data);  // ✅ Auto-injected
    
    std.debug.print("Config: {s}\n", .{data});
}
```

## 📚 Documentation

- [Getting Started](https://github.com/TSZig/tszig#readme)
- [Examples](https://github.com/TSZig/tszig-examples)
- [API Reference](https://github.com/TSZig/tszig-core#readme)

## 🤝 Contributing

We welcome contributions! See our [Contributing Guide](https://github.com/TSZig/.github/blob/main/CONTRIBUTING.md).

## 📄 License

MIT License - see individual repositories for details.

---

<p align="center">
  <b>TSZig</b> = <b>T</b>ranspiled <b>S</b>yntax + <b>Zig</b>
</p>
