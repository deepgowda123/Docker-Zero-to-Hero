FROM ubuntu

# Set the working directory to /app
WORKDIR /app

# Copy requirements.txt and app code into the container
COPY requirements.txt /app
COPY devops /app

# Install necessary dependencies and create a virtual environment
RUN apt-get update && \
    apt-get install -y python3 python3-pip python3-venv && \
    python3 -m venv /app/venv && \
    /app/venv/bin/pip install --no-cache-dir -r requirements.txt

# Expose port 8000 for the application
EXPOSE 8000

# Set the entry point to use the virtual environment and run the Django app
ENTRYPOINT ["/bin/bash", "-c"]
CMD ["source /app/venv/bin/activate && python3 manage.py runserver 0.0.0.0:8000"]

