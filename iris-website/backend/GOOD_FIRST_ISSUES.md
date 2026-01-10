# Good First Issues (Backend)

Welcome to the IRis Backend! We have identified several areas where new contributors can make a significant impact. These tasks are designed to get you familiar with the codebase.

## 1. Create Proper Unit Tests
**Difficulty:** Medium
**Description:**
Currently, `test_api.py` is an integration script that requires a running server. We need a proper unit test suite using `pytest`.
**Tasks:**
- Create `tests/` directory.
- Add `conftest.py` with Flask app fixtures.
- Write tests for `routes/llvm_api.py` using `unittest.mock` to mock `LLVMOptimizationService`.
- Ensure tests run fast without performing actual compilation/inference.

## 2. Add API Documentation (Swagger/OpenAPI)
**Difficulty:** Easy
**Description:**
The API lacks interactive documentation.
**Tasks:**
- Install `flasgger` or `flask-restx`.
- Decorate route functions in `routes/llvm_api.py` with Swagger docstrings.
- Enable the `/apidocs` endpoint to view the UI.

## 3. Improve Type Hinting and Validation
**Difficulty:** Easy/Medium
**Description:**
While some type hints exist, they are not consistent.
**Tasks:**
- Add return type hints to all route functions in `routes/llvm_api.py`.
- Run `mypy` and fix reported errors.
- Refactor `utils/validators.py` to ensure it's strictly used in all endpoints.

## 4. Refactor `run_ml_passes`
**Difficulty:** Medium
**Description:**
The `run_ml_passes` function in `services/llvm_optimization_service.py` is too large (~200 lines).
**Tasks:**
- Break it down into smaller helper functions:
  - `_compile_to_bc()`
  - `_apply_ir_passes()`
  - `_generate_assembly()`
  - `_compile_executable()`
  - `_measure_performance()`
- Ensure each helper handles its own error states and cleanup.

## 5. Standardize Configuration
**Difficulty:** Easy
**Description:**
`config.py` uses simple class attributes.
**Tasks:**
- Switch to using `pydantic-settings` or Flask's `config.from_object` pattern more robustly.
- Ensure all paths are essentially relative to `PROJECT_ROOT` and verified on startup.
