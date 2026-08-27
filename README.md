# Quarzum for Visual Studio Code

Syntax highlighting, file icons and code snippets for the **Quarzum**
programming language (`.qz` and `.quarzum` files), based on the official
language reference in [`docs/language-reference.md`](../docs/language-reference.md).

## Features

- Syntax highlighting for keywords, data types, literals, operators, comments
  and identifiers.
- Quarzum logo as the file icon for `.qz` / `.quarzum` files.
- Code snippets for the most common constructs (functions, loops, classes,
  enums, traits, memory management, I/O, etc.).
- Comment toggling (`//`, `/* */`), bracket pairing, auto-closing pairs and
  folding markers.

## File icons

The Quarzum logo is contributed as a **language default icon**
(`contributes.languages[].icon`). It is **not** a file icon theme, so it works
on top of whichever icon theme is active (e.g. Seti, Material Icon Theme):

- The icon is shown for `.qz` / `.quarzum` files automatically.
- It applies to the whole `quarzum` language (any file whose language mode is
  Quarzum), even for files with other extensions.
- The active icon theme still provides all the other icons; VS Code only falls
  back to the language icon when the theme has no icon of its own for the file
  type.

Two variants are provided: `quarzum-language.png` (dark color themes) and
`quarzum-language-light.png` (light color themes).

## Installation (development)

1. Open this folder (`vscode-quarzum`) in VS Code.
2. Press `F5` (Run Extension) to launch an Extension Development Host.
3. Open any `.qz` file to see the highlighting and snippets in action.

## Installing the `.vsix`

```sh
npm install -g @vscode/vsce
vsce package
code --install-extension vscode-quarzum-0.2.0.vsix
```

## Language reference

The grammar and snippets are generated from the lexical and syntactic elements
that the Quarzum C compiler implements today:

- **57 keywords** (declaration, control flow, types, operators, access
  modifiers).
- **Primitive types**: `void`, `bool`, `char`, `int8`–`int64`, `uint8`–`uint64`,
  `float32`/`float64` (with aliases `int`, `uint`, `float`), plus `string`
  (alias of `char[]`), `ptr<T>` and the slice type `T[]`.
- **Literals**: decimal and hexadecimal integers, floats, characters and strings
  with escapes, `true`/`false`, `null`.
- **Operators**: arithmetic, comparison, logical keywords (`and`/`or`/`xor`/
  `not`), bitwise (`&&`/`||`/`^^`/`!!`/`&`), and assignment (`=` plus compound).

`T[]` is the only array type in Quarzum: there are no static (fixed-size) arrays
nor variable-length arrays (VLAs) as types. `alloc T[n]` allocates
`sizeof(T) * n` bytes on the heap and returns a `ptr<T>`.

## Snippets

Prefix | Description
-------|------------
`import` | Import a module (`import "@std/io.qz"`)
`importio` | Import `@std/io.qz`
`main` | Program entry point
`function`, `functype`, `funcexpr` | Function declarations
`class`, `classgen` | Class declarations (generic + `implements`)
`struct` | Struct declaration
`enum`, `enumgen` | Enum declarations
`trait` | Trait declaration
`var`, `vartype`, `const` | Variable and constant declarations
`if`, `ifelse`, `for`, `foreach`, `while`, `do` | Control flow
`switch`, `case`, `match` | Multi-branch selection and pattern matching
`new`, `alloc`, `free` | Memory management
`sizeof`, `as`, `tern` | Operators
`println`, `print`, `eprintln` | Standard output
`exit`, `return` | Control transfer

## Icon

The extension icon is the Quarzum logo (`images/quarzum_logo.svg`).
