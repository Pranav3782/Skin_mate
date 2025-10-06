# Use an official Python runtime as a parent image
FROM python:3.11-slim

# Set the working directory in the container
WORKDIR /app

# Update package lists and install tesseract-ocr
# This runs with root privileges inside the Docker build
RUN apt-get update && apt-get install -y tesseract-ocr

# Copy the requirements file into the container
COPY requirements.txt .

# Install any needed packages specified in requirements.txt
RUN pip install --no-cache-dir -r requirements.txt

# Copy the rest of the application code into the container
COPY . .

# Run uvicorn when the container launches
# Render will automatically use the correct port
CMD ["uvicorn", "main:app", "--host", "0.0.0.0", "--port", "10000"]
