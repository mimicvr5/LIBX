# LIBX

**Library Interface eXchange**  
File extension: `.libx`  

LIBX allows you to define libraries in a neutral format and generate code for multiple target languages.  
It now supports **cross-language imports** from Python (PyPI) and JS (npm).

---

## Importing Libraries From Other Languages

### Syntax

```libx
import <SOURCE_LANGUAGE>."<library_name>" [as <alias>] [from "<package_source_url>"]
```

- `SOURCE_LANGUAGE` must be uppercase (PYTHON, JS)
- `library_name` is the exact package name
- Optional alias with `as`
- Optional source URL with `from`

---

## Example Python -> JS

```libx
target JS
import PYTHON."pyautogui"
import JS."lodash" as _

func takeScreenshot() -> void
```
**Result**:
- Fetches `pyautogui` from [PyPI](pypi.org)
- Fetches `lodash` from [npm](npmjs.com)
- Generates JS equivalents of functions
- User only needs JS-ready output

---

## Example: Multi-language Target

```libx
target CSHARP, PYTHON
import JS."lodash" as _

func processList(data: list) -> list
```
Generates:
- C# library with mapped lodash functions
- Python library with mapped lodash functions

---

## Rules

1. Libraries must exist in their source repositories
2. Type mapping applied automatically
3. Unsupported features generate warnings
4. Recursive imports resolved automatically
5. Aliases recommended for clarity

---

## Future Features

- Support for Rust, Go, Java, Lua
- Version specifiers (`version "x.y.z"`)
- Local paths (`from "./libs/mylib"`)

---

## License

MIT License

###### See more details at [LICENSE](./LICENSE)