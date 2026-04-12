# GitHub Actions Workshop

This is a hands-on practice session. You already know the theory — let's build it.

---

## What's in this repo

| File | Description |
|------|-------------|
| `main.py` | A simple `Calculator` class with four operations |
| `test_main.py` | Unit tests for the `Calculator` class |

---

## Part 1 — Fork and clone

1. Click **Fork** at the top-right of this page.
2. Clone your fork locally:

```bash
git clone https://github.com/<your-username>/<repo-name>.git
cd <repo-name>
```

---

## Part 2 — Run the tests locally

```bash
python -m unittest test_main.py -v
```

Expected output:

```
test_add (test_main.TestCalculator) ... ok
test_divide (test_main.TestCalculator) ... ok
test_divide_by_zero (test_main.TestCalculator) ... ok
test_multiply (test_main.TestCalculator) ... ok
test_subtract (test_main.TestCalculator) ... ok

----------------------------------------------------------------------
Ran 5 tests in 0.001s

OK
```

---

## Part 3 — Break a test

In `main.py`, change `add` to subtract:

```python
def add(self, a, b):
    return a - b   # bug
```

Run the tests again and observe the failure. Then revert:

```python
def add(self, a, b):
    return a + b   # fixed
```

Confirm tests pass before moving on.

---

## Part 4 — Set up GitHub Actions (follow along with instructor)

### Step 1 — Create the workflow folder

```bash
mkdir -p .github/workflows
```

### Step 2 — Create the workflow file

Create `.github/workflows/python-tests.yml` and write it together with your instructor.

### Step 3 — Push and watch it run

```bash
git add .github/workflows/python-tests.yml
git commit -m "Add GitHub Actions workflow to run tests"
git push origin main
```

Open the **Actions** tab on your GitHub repo and watch the workflow run.

### Step 4 — Confirm it catches a bug

Push the bug from Part 3, watch the workflow go red, then fix and push again.

```bash
# introduce bug
git add main.py
git commit -m "Introduce bug"
git push origin main

# fix bug
git add main.py
git commit -m "Fix add method"
git push origin main
```
