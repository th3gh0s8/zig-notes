# zig-notes

[![license](https://img.shields.io/github/license/th3gh0s8/zig-notes?style=flat-square)](./LICENSE)
[![zig version](https://img.shields.io/badge/zig-%3E%3D0.11-brightgreen?style=flat-square)](https://ziglang.org)

Personal notes, examples, and small experiments for the Zig programming language — a concise, runnable reference for common patterns, language quirks, and quick demos.

---

## Table of contents

- [About](#about)
- [Quickstart](#quickstart)
  - [Prerequisites](#prerequisites)
  - [Run an example](#run-an-example)
  - [Build an executable](#build-an-executable)
  - [Run tests](#run-tests)
  - [Format code](#format-code)
- [Recommended layout](#recommended-layout)
- [How to contribute](#how-to-contribute)
- [License](#license)
- [Contact](#contact)

---

## About

This repository collects short notes, focused examples, and tiny projects used to learn Zig and preserve small, reusable snippets. Each example is intended to be simple and runnable so you can quickly reproduce behavior and adapt code for your own experiments.

## Quickstart

### Prerequisites

- Install Zig (stable recommended): https://ziglang.org
- Basic command-line knowledge.

Verify Zig:

```sh
zig version
```

### Run an example

Create a file `hello.zig`:

```zig
const std = @import("std");

pub fn main() !void {
    const stdout = std.io.getStdOut().writer();
    try stdout.print("Hello, Zig!\n", .{});
}
```

Run it:

```sh
zig run hello.zig
```

### Build an executable

```sh
zig build-exe hello.zig -O ReleaseSafe -target native
./hello
```

For smaller binary:

```sh
zig build-exe hello.zig -O ReleaseSmall
```

### Run tests

Zig includes a test runner. Example test:

```zig
const std = @import("std");

test "addition" {
    try std.testing.expectEqual(1 + 1, 2);
}
```

Run tests:

```sh
zig test
# or
zig test tests/example_test.zig
```

### Format code

Format the repo or files:

```sh
zig fmt .
```

---

## Recommended layout

Organize the repository so examples and notes are easy to find:

- notes/        — written notes and explanations (Markdown)
- examples/     — runnable example projects (one directory per example)
- snippets/     — single-file .zig snippets
- projects/     — small multi-file projects or experiments
- tests/        — test cases or reproducible scenarios

Example tree:

```
.
├─ README.md
├─ LICENSE
├─ notes/
├─ examples/
│  └─ http_server/
│     └─ src/main.zig
├─ snippets/
└─ projects/
```

When adding an example, include a small README in the example directory explaining how to run it.

---

## How to contribute

Contributions are welcome — fixes, new examples, improved notes.

Suggested workflow:

1. Fork the repo.
2. Create a branch named for your change: `git checkout -b feat/add-comptime-notes`
3. Add your files and run `zig fmt .`
4. Commit and open a Pull Request with a clear description of what you added and why.

Guidelines:
- Keep examples small and focused.
- Add tests when demonstrating behaviors that can break.
- Use descriptive commit messages.

If you want, I can add a CONTRIBUTING.md and PR template.

---

## License

This repository includes a LICENSE file at the project root. See the [LICENSE](./LICENSE) file for details.

(If you want the README to show a specific license badge or short license summary, tell me which license you added and I will update the header/badge text.)

---

## Contact

Repository owner: th3gh0s8

<!-- Bordered avatar with link -->
<div align="center" style="margin-top:12px">
  <a href="https://github.com/th3gh0s8" target="_blank">
    <img src="https://github.com/th3gh0s8.png?size=120"
         alt="th3gh0s8 avatar"
         width="120"
         height="120"
         style="border:4px solid #e1e4e8; border-radius:12px; padding:6px; background:#fff;">
  </a>
</div>
