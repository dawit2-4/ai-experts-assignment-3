Here is your content properly formatted as a **`README.md` Markdown file**.

You can copy this directly into **README.md**.

```markdown
# OAuth2 Client Assignment

## Project Structure
```

.
├── app/
│ ├── http_client.py
│ └── tokens.py
│
├── tests/
│ └── test_http_client.py
│
├── Dockerfile
├── requirements.txt
├── README.md
├── Explanation.md
└── .gitignore

````

## Description

### app/

Contains the application logic.

- **tokens.py** – Handles OAuth2 token representation and parsing.
- **http_client.py** – Implements a simple HTTP client that attaches OAuth2 authentication headers.

### tests/

Contains the **pytest test suite** that validates the behavior of the client and token handling.

---

# Running Tests Locally

### 1. Clone the repository

```bash
git clone <your-repo-url>
cd <repo-name>
````

### 2. Create a virtual environment (optional but recommended)

```bash
python -m venv venv
source venv/bin/activate
```

For **Windows**:

```bash
venv\Scripts\activate
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

### 4. Run the test suite

```bash
pytest -v
```

### Expected Output

```
================= test session starts =================

tests/test_http_client.py::test_client_uses_requests_session PASSED
tests/test_http_client.py::test_token_from_iso_uses_dateutil PASSED
tests/test_http_client.py::test_api_request_sets_auth_header_when_token_is_valid PASSED
tests/test_http_client.py::test_api_request_refreshes_when_token_is_missing PASSED
tests/test_http_client.py::test_api_request_refreshes_when_token_is_dict PASSED

================= 5 passed =================
```

---

# Running Tests with Docker

The repository includes a **Dockerfile** to ensure the tests run in a clean environment similar to CI.

### 1. Build the Docker image

```bash
docker build -t oauth2-client-assignment .
```

### 2. Run the tests inside the container

```bash
docker run oauth2-client-assignment
```

Docker will automatically execute:

```bash
pytest -v
```

---

# Assignment Tasks Completed

This repository includes the following required components:

- Dockerfile for containerized test execution
- Pinned dependencies in `requirements.txt`
- Tests that reproduce the identified bug
- A minimal fix applied to the codebase
- `Explanation.md` describing the bug, root cause, and fix
- Instructions for running the project locally and with Docker
