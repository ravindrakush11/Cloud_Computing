# 🐳 Docker + 🐍 Python Hello World

> A beginner-friendly guide to running a simple **Python "Hello World"** script inside a **Docker** container.

---

## 🎯 Goal

Run a Python script using Docker to print `Hello World` from inside a container.

---

## 📁 Project Structure

```
python-hello/
├── Dockerfile
└── app.py
```

### `app.py`

```python
print("Hello from your custom Python Docker container!")
```

### `Dockerfile`

```Dockerfile
FROM python:3.10-slim

WORKDIR /app

COPY app.py .

CMD ["python", "app.py"]
```

---

## 🛠️ Build and Run

### 🔧 Build the Docker Image

```bash
docker build -t python-hello .
```

### ▶️ Run the Container

```bash
docker run python-hello
```

### ✅ Expected Output

```
Hello from your custom Python Docker container!
```

---

## ⚠️ Common Mistakes & Fixes

### ❌ Mistake 1: Incomplete COPY command

```Dockerfile
COPY app.py
```

**Error:**

```
COPY requires at least two arguments
```

✅ **Fix:**

```Dockerfile
COPY app.py .
```

---

### ❌ Mistake 2: Escaped quotes in echo command

```bash
echo print(\"Hello from your custom Python Docker container!\") > app.py
```

**Result:** Adds unwanted backslashes.

✅ **Fix (Windows CMD):**

```bash
echo print("Hello from your custom Python Docker container!") > app.py
```

---

### ❌ Mistake 3: Incorrect Dockerfile syntax

```Dockerfile
from python:3.10-slim
```

**Lint Warning:** Dockerfile instructions must be uppercase.

✅ **Fix:**

```Dockerfile
FROM python:3.10-slim
```

---

## 🧼 Tips

* Always **capitalize Dockerfile instructions** (`FROM`, `COPY`, `CMD`, etc.).
* Prefer lightweight base images like `python:3.10-slim` for faster builds.
* Use `.dockerignore` to speed up builds (optional enhancement).

---
