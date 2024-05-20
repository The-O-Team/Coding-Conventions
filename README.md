# Coding Conventions
## Introduction

This page introduces the coding guidelines for the team. These guidelines aim to improve:

- The quality of the code
- The readability
- The maintainability
- General project stability
- Fewer regressions

They are loosely based on the OCA guidelines, but with some changes to fit the company's own needs.

# Focus Points During Code Reviews

## Coding Style

- Importance of following the coding guidelines
- Common issues observed in previous reviews
- Tools and linters used to enforce style (pre-commit)
  - eslint
  - black
  - pylint (Odoo flavour)
  - flake8
  - isort

## Documentation

- Necessity of clear and concise comments
- Documenting complex logic and APIs
- Ensuring code is understandable for future developers
- Importance of keeping documentation up-to-date

## Automated Testing

- Should be added to test business logic, not odoo's core logic
- Do not only test the happy path
- Write basic setups and then test individual scenarios (No method testing, only scenario testing)

## Writing modular and reusable code

- Identifying opportunities for code abstraction
- Encouraging the use of existing libraries and components. Avoid adding new libraries unless necessary.

## The Best Code You Write is the One You Never Wrote

- Emphasizing simplicity and minimalism in coding
- Avoiding unnecessary complexity and over-engineering
- Leveraging existing solutions and avoiding reinventing the wheel
