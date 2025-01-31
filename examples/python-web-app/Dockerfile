# Start with an official Ubuntu image
FROM ubuntu:20.04

# Set working directory to /app
WORKDIR /app

# Install system dependencies for Python and virtual environment
RUN apt-get update && apt-get install -y \
    python3 python3-pip python3-venv \
    && apt-get clean

# Copy the requirements.txt and app files into the container
COPY requirements.txt /app/
COPY devops /app/

# Create and activate a virtual environment
RUN python3 -m venv /app/venv && \
    /app/venv/bin/pip install --upgrade pip

# Install Python dependencies inside the virtual environment
RUN /app/venv/bin/pip install --no-cache-dir -r requirements.txt

# Expose port 8000 for the application
EXPOSE 8000

# Set the entry point to activate the virtual environment and run the Django app
CMD ["/bin/bash", "-c", "source /app/venv/bin/activate && python3 manage.py runserver 0.0.0.0:8000"]





