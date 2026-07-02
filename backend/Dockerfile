FROM python:3.11-slim

WORKDIR /app

# Install build tools, if required for some packages (like SQLite extensions or compilers)
RUN apt-get update && apt-get install -y \
    build-essential \
    && rm -rf /var/lib/apt/lists/*

COPY requirements.txt .

RUN pip install --no-cache-dir -r requirements.txt

COPY . .

# Expose the port
EXPOSE 8000

# Run uvicorn on port 8000 and bind to all interfaces
CMD ["uvicorn", "app.main:app", "--host", "0.0.0.0", "--port", "8000"]
