# Lab 5: Static Code Analysis

## Issues Identified and Fixed

| Issue | Tool | Fix Applied |
|---|---|---|
| Mutable default argument in `reserve_seat()` | Pylint | Replaced the list default with `None` and initialized it inside the function. |
| Missing docstrings and naming/style issues | Pylint | Added docstrings and renamed `printSeatingSummary()` to `print_seating_summary()`. |
| Broad exception handling | Pylint / Bandit | Replaced broad exception handling with specific exceptions. |
| Weak MD5 hashing | Bandit | Replaced MD5 with SHA-256 for ticket identifiers. |
| Overly permissive file permissions | Bandit | Removed the unnecessary `os.chmod(..., 0o777)` call. |
| Files not managed with context managers | Pylint | Used `with open(...)` and specified UTF-8 encoding. |
| Excess blank lines | Flake8 | Corrected blank lines between top-level functions. |
| Invalid seat numbers | Manual code review | Added validation for seat numbers before reservation. |

## Final Results

- Pylint score: 10.00/10
- Bandit: No issues identified.
- Flake8: No errors reported.

## Conclusion

Static analysis helped identify code quality, security, and formatting problems. Fixing these issues improved readability, reliability, and maintainability. The program was tested after the changes and all three analysis tools were rerun.