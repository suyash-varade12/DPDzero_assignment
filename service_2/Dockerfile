# # Use an official lightweight Python image as base
# FROM python:3.10-slim

# # Update package list, install curl, install PDM (Python Development Master), and clean up
# RUN apt-get update && apt-get install -y curl \
#   && curl -sSL https://pdm.fming.dev/install-pdm.py | python3 - \
#   && apt-get clean

# # Set working directory inside the container
# WORKDIR /app

# # Copy project files from the host to the container
# COPY . .

# ENV PATH="/root/.local/bin:$PATH"

# # Install only production dependencies using PDM
# RUN pdm install --prod

# # Expose port 8002 for external access
# EXPOSE 8002

# CMD ["pdm", "run", "python", "app.py"]

# Use official Python image
FROM python:3.10-slim

# Install system dependencies
RUN apt-get update && apt-get install -y curl \
  && apt-get clean

# Install uv (Python process manager like uvicorn + virtualenv)
RUN curl -LsSf https://astral.sh/uv/install.sh | sh

# Set working directory
WORKDIR /app

# Copy application files
COPY . .

# Expose the service port
EXPOSE 8002

# Run the service using uv
CMD ["uv", "run", "app.py"]
