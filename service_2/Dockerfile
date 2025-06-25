FROM python:3.10-slim

# Install system dependencies
RUN apt-get update && apt-get install -y build-essential curl \
    && apt-get clean

# Install uv globally
RUN pip install --no-cache-dir uv

# Set working directory
WORKDIR /app

# Copy all app files
COPY . .

# Create a virtual environment
RUN uv venv .venv

# Compile and install dependencies using global uv
RUN uv pip compile pyproject.toml -o requirements.txt && \
    uv pip install -r requirements.txt

# Run the app using uv from the global install (still respects .venv)
CMD ["uv", "run", "app.py"]

EXPOSE 8002
