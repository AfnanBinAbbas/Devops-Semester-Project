FROM python:3.10-slim-bullseye

# Install system packages
RUN apt-get update && \
    apt-get install -y --no-install-recommends --no-install-suggests \
    build-essential \
    libpq-dev \
    python3-dev \
    && rm -rf /var/lib/apt/lists/*

# Upgrade pip
RUN pip install --no-cache-dir --upgrade pip

# Set working directory
WORKDIR /app

# Copy and install Python dependencies
COPY ./requirements.txt /app
RUN pip install --no-cache-dir --requirement /app/requirements.txt

# Copy the rest of the app
COPY . /app

# Expose port
EXPOSE 5000

# Command to run the app
CMD ["python", "server.py"]
