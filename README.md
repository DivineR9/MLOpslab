# MLOps Lab 5 — Configuration, Refactoring and Testing

## Student Details

- **Name:** Hardik Rakwal
- **Roll Number:** S24CSEU0753
- **Batch:** 79
- **Course:** MLOps
- **Assignment:** Practical 05

## Repository

GitHub Repository: https://github.com/DivineR9/MLOpslab5

## Overview

This assignment focuses on improving the reliability, maintainability, and reproducibility of a Python project using MLOps practices.

The main objectives are:

1. Managing project settings through a `config.yaml` file.
2. Refactoring Python code into a cleaner and more maintainable structure.
3. Writing automated unit tests using `pytest`.
4. Identifying and fixing errors in program logic.
5. Verifying the correctness of the code through automated testing.

## Technologies Used

- Python
- YAML
- PyYAML
- pytest
- Git
- GitHub
- VS Code

## Project Structure

```text
MLOpslab5/
│
├── config.yaml
├── orders.py
├── test_orders.py
├── README.md
└── P05_S24CSEU0753.ipynb
```

The exact file structure may vary depending on how the assignment files are organized.

## 1. Configuration Management

The `config.yaml` file stores project settings separately from the Python source code.

This approach makes it easier to modify configuration values without changing the application logic.

Python can load the configuration using PyYAML:

```python
import yaml

with open("config.yaml", "r") as file:
    config = yaml.safe_load(file)
```

Using a configuration file improves maintainability and makes experiments easier to reproduce.

## 2. Code Refactoring

Refactoring improves the internal structure of code without changing its intended behaviour.

The assignment focuses on organizing the code, improving readability, and reducing unnecessary complexity.

A well-structured project is easier to test, debug, maintain, and extend.

## 3. Automated Testing with pytest

The `test_orders.py` file contains automated tests for the functions implemented in `orders.py`.

The tests help verify that:

- Functions return the expected results.
- Calculations follow the intended logic.
- Invalid inputs are handled appropriately.
- Errors introduced during development or refactoring can be detected.

The `pytest` framework is used to execute the tests and report their results.

### Run the Tests

Install the required dependencies:

```bash
python -m pip install pytest pyyaml
```

Run the test suite from the directory containing the test file:

```bash
python -m pytest -v
```

Pytest reports which tests passed and identifies any failures.

## 4. Bug Detection and Correction

Automated tests help identify incorrect calculations and unexpected behaviour.

For example, a test can verify that a function calculates a delivery-time-related value correctly and raises an appropriate exception for invalid input.

When a test fails, the implementation can be examined and corrected before the code is used elsewhere.

## 5. Benefits of This Practical

- Better code organization.
- Separation of configuration and application logic.
- Improved code readability and maintainability.
- Automated verification of program behaviour.
- Earlier detection of programming errors.
- A more reliable and reproducible development workflow.

## 6. Conclusion

This practical demonstrates important MLOps principles through configuration management, code refactoring, and automated testing.

Using YAML for configuration and pytest for testing helps make Python projects easier to maintain and validate.

These practices provide a foundation for developing reliable and reproducible machine learning and software pipelines.

## AI Use Disclosure

AI assistance was used to help understand the assignment requirements and prepare explanations and documentation. The submitted implementation and test results should be reviewed and understood by the student.
