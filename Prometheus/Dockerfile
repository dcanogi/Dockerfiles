# Use a lightweight base image
FROM python:3.11-slim

# Metadata as described above
LABEL Name="Project Manager Monitoring Dashboard" \
      Version="1.0" \
      Description="Dockerfile for a container with monitoring and project management tools."

# Set the working directory
WORKDIR /app

# Install system dependencies
RUN apt-get update && apt-get install -y \
    curl \
    gnupg \
    && rm -rf /var/lib/apt/lists/*

# Install monitoring tools (e.g., Prometheus and Grafana)
RUN curl -LO https://github.com/prometheus/prometheus/releases/download/v2.41.0/prometheus-2.41.0.linux-amd64.tar.gz \
    && tar xvf prometheus-2.41.0.linux-amd64.tar.gz \
    && mv prometheus-2.41.0.linux-amd64/prometheus /usr/local/bin/ \
    && mv prometheus-2.41.0.linux-amd64/promtool /usr/local/bin/ \
    && rm -rf prometheus-2.41.0.linux-amd64.tar.gz prometheus-2.41.0.linux-amd64

# Copy configuration files if needed
COPY prometheus.yml /etc/prometheus/prometheus.yml

# Expose necessary ports
EXPOSE 9090

# Set the entry point
ENTRYPOINT ["/usr/local/bin/prometheus"]

# Default command
CMD ["--config.file=/etc/prometheus/prometheus.yml"]
