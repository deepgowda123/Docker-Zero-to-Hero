FROM ubuntu

WORKDIR /app

# Install necessary dependencies and clean up apt cache to save space
RUN apt-get update && apt-get install -y \
    python3 \
    python3-pip \
    python3-venv \
    && rm -rf /var/lib/apt/lists/* \
    && apt-get clean

# Copy requirements and application files
COPY requirements.txt /app/
COPY devops /app/

# Create virtual environment and install requirements
RUN python3 -m venv venv1 && \
    venv1/bin/pip install --no-cache-dir -r requirements.txt

EXPOSE 8000

CMD ["bash", "-c", "source venv1/bin/activate && python3 manage.py runserver 0.0.0.0:8000"]
`





