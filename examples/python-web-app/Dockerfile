FROM ubuntu

WORKDIR /app

COPY requirements.txt /app/
COPY devops /app/

# Install necessary dependencies
RUN apt-get update && apt-get install -y \
    python3 \
    python3-pip \
    python3-venv \
    && rm -rf /var/lib/apt/lists/*

# Create and activate virtual environment, then install requirements
RUN python3 -m venv venv1 && \
    venv1/bin/pip install --no-cache-dir -r requirements.txt

EXPOSE 8000

# Ensure virtual environment is activated when running the container
CMD ["bash", "-c", "source venv1/bin/activate && python3 manage.py runserver 0.0.0.0:8000"]






