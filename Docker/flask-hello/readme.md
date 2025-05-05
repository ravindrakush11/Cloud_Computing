# Docker Flask Hello World

## ✅ Goal
Run a simple Flask web server inside Docker and access it at http://localhost:5000/

---

## 📁 Files

**app.py**
```python
from flask import Flask

app = Flask(__name__)

@app.route("/")
def hello():
    return "Hello from Flask inside Docker!"

if __name__ == "__main__":
    app.run(host="0.0.0.0", port=5000)
```

**requirements.txt**
```
flask
```

**Dockerfile**
```Dockerfile
FROM python:3.10-slim

WORKDIR /app

COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

COPY app.py .

EXPOSE 5000

CMD ["python", "app.py"]
```

---

## 🛠 Build and Run

### Build Image
```bash
docker build -t flask-hello .
```

### Run Container with Port Mapping
```bash
docker run -p 5000:5000 flask-hello
```

Visit: [http://localhost:5000](http://localhost:5000)

---

## ⚠️ Common Mistakes & Fixes

### ❌ Mistake: Missing host in `app.run()`
```python
app.run()
```

**Problem:** Flask only listens inside the container (`127.0.0.1`).

✅ **Fix:**
```python
app.run(host="0.0.0.0", port=5000)
```
