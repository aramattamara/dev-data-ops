# Build stage
FROM python:3.8-slim AS build

# Set the working directory in the container
WORKDIR /app

# Copy the current directory contents into the container at /app
COPY server/ .

# Install necessary dependencies specified in requirements.txt
RUN pip install --no-cache-dir -r requirments.txt

# Base stage
FROM python:3.8-slim AS base

# Set the working directory to /app
WORKDIR /app

# Copy the application code from the build stage
COPY --from=build /app /app

# Make port 5000 available to the world outside this container
EXPOSE 8050

# Define environment variable
ENV FLASK_APP=app.py

# Run app.py when the container launches
CMD ["flask", "run", "--host=0.0.0.0", "--port=5000"]
