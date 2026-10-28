# Lab 5: Static Code Analysis

## Issues Identified and Fixed

| Issue | Type | Line(s) | Description | Fix Approach |
|---|---|---|---|---|
| Mutable default argument | Bug | 9 | The `system_logs=[]` default argument could cause the same list to be shared across function calls. | Changed the default to `None` and initialized the list inside the function. |
| Missing docstrings and naming/style issues | Code Quality | Multiple | Functions lacked docstrings, and `printSeatingSummary()` did not follow snake_case naming conventions. | Added docstrings and renamed the function to `print_seating_summary()`. |
| Broad exception handling | Code Quality / Security | 21 | A bare `except` could hide unexpected errors. | Replaced broad exception handling with a specific exception handler. |
| Weak MD5 hashing | Security | 25 | MD5 is unsuitable for security-sensitive hashing. | Replaced MD5 with SHA-256 for generating ticket identifiers. |
| Overly permissive file permissions | Security | 55 | Setting file permissions to `0o777` allowed overly broad access. | Removed the unnecessary `os.chmod()` call. |
| Unsafe file handling | Code Quality | 28, 33 | Files were opened without context managers or explicit encoding. | Used `with open()` and specified UTF-8 encoding. |
| Excess blank lines | Style | Multiple | Extra blank lines violated Flake8 formatting requirements. | Corrected blank lines between top-level functions. |
| Invalid seat numbers | Input Validation | Multiple | Negative seat numbers and nonnumeric values could be accepted as reservations. | Added validation to check seat numbers before reserving seats. |

*Note: Line numbers refer to the original code before fixes. Verify them against the saved before-analysis reports if needed.*

## Final Results

- **Pylint:** 10.00/10
- **Bandit:** No issues identified.
- **Flake8:** No errors reported.

## Reflection

### 1. What is static code analysis?

Static code analysis is the process of examining source code without executing it. It helps identify potential bugs, security vulnerabilities, and coding style violations.

### 2. What is the difference between Pylint, Bandit, and Flake8?

Pylint checks code quality, programming practices, and potential logical issues. Bandit identifies common security vulnerabilities in Python code. Flake8 checks code formatting and compliance with Python style guidelines.

### 3. What challenges did you face while fixing the issues?

Some findings required understanding the underlying problem before choosing an appropriate fix. For example, I replaced the mutable default argument with `None`, used specific exception handling, improved file handling, and corrected formatting issues. I reran the tools to verify the changes.

### 4. How does static code analysis improve code quality and maintainability?

Static analysis helps detect problems early, improves readability, reduces potential security risks, and encourages consistent coding practices. Using these tools makes code easier to maintain and helps prevent common programming mistakes.

## Conclusion

In this lab, I used Pylint, Bandit, and Flake8 to analyze and improve a Python movie seat reservation program. I fixed code quality, security, input validation, and formatting issues. After making the changes, I reran all three tools and obtained a Pylint score of 10.00/10, no Bandit findings, and no Flake8 errors.