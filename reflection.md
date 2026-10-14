# Lab 5 : Static Code Analysis Reflection

## 1. Which issues were the easiest to fix, and which were the hardest? Why?

The easiest issues to fix were unused imports, long lines, missing docstrings, naming conventions, and formatting problems. The hardest issues were security-related problems such as `eval()`, shell command execution, and weak hashing because they required changing the implementation while preserving the program's functionality.

## 2. Did the static analysis tools report any false positives? If so, describe one example.

The tools identified potential security risks that needed to be evaluated in context. For example, Bandit flagged MD5 hashing. Although the program used it to generate a digest of a patient identifier rather than to store passwords, MD5 is not suitable for security-sensitive cryptographic purposes. Therefore, this finding was addressed rather than dismissed as a false positive.

## 3. How would you integrate static analysis tools into your actual software development workflow?

I would run Pylint, Flake8, and Bandit regularly during development and before committing code. Pylint would check code quality, Flake8 would identify style violations, and Bandit would detect common security risks. I would also integrate these tools into GitHub Actions to automate checks before code is merged.

## 4. What tangible improvements did you observe in code quality, readability, or potential robustness after applying the fixes?

The Pylint score improved from 5.19/10 to 10.00/10. Bandit initially reported five potential security issues and reported none after the fixes. Flake8 initially reported 11 violations and reported none after the fixes. The code became more readable and maintainable, with safer calculation handling, stronger hashing, secure token generation, and improved file handling.