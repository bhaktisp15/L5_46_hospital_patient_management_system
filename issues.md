# Lab 5 : Static Code Analysis Issues

## 1. Security Issues

| Issue | Tool | Severity | Description | Proposed Fix |
|---|---|---|---|---|
| Use of `eval()` | Bandit, Pylint | Medium | Evaluates a string as Python code, which can execute unintended expressions. | Replace it with a safe calculation method. |
| Shell command execution | Bandit | High | `os.system()` executes a shell command and may introduce command-injection risks. | Remove unnecessary shell execution and use safe file operations. |
| Weak MD5 hash | Bandit | High | MD5 is unsuitable for security-sensitive cryptographic hashing. | Use a stronger algorithm if cryptographic hashing is required. |
| Pseudo-random ward token | Bandit | Low | `random.randint()` is not intended for security-sensitive tokens. | Use Python's `secrets` module if the token must be unpredictable. |

## 2. Code Quality Issues

| Issue | Tool | Description | Proposed Fix |
|---|---|---|---|
| Mutable default argument | Pylint | A default list can be shared between function calls. | Use `None` and create a new list inside the function. |
| Bare exception | Pylint, Flake8 | Broad exception handling can hide unexpected errors. | Catch specific exceptions and handle missing patient records explicitly. |
| Unused import and variables | Pylint, Flake8 | Unused declarations make the code less clear. | Remove unused imports and variables. |
| Missing docstrings | Pylint | The module and functions lack documentation. | Add meaningful docstrings. |
| File handling | Pylint | File encoding is unspecified and the file is not managed using a context manager. | Use `with open(..., encoding="utf-8")`. |
| Naming and formatting | Pylint, Flake8 | Naming conventions, long lines, and the missing final newline reduce consistency. | Follow Python naming and formatting conventions. |
| Comparison with `None` | Pylint, Flake8 | Comparing a value to `None` using `==` is discouraged. | Use `is None` or `is not None`. |

## Conclusion

Static analysis identified security concerns, code-quality problems, and formatting inconsistencies in the original hospital patient management program. These findings provide a checklist for improving the code and comparing tool reports before and after the fixes.