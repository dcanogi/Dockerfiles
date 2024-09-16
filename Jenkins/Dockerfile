# Use a base image with Alpine Linux
FROM openjdk:11-jre-slim

# Install necessary dependencies
RUN apt-get update && apt-get install -y \
    wget \
    gnupg \
    && rm -rf /var/lib/apt/lists/*

# Install Jenkins
RUN wget -q -O - https://pkg.jenkins.io/debian/jenkins.io.key | apt-key add - \
    && sh -c 'echo deb http://pkg.jenkins.io/debian-stable binary' > /etc/apt/sources.list.d/jenkins.list \
    && apt-get update \
    && apt-get install -y jenkins \
    && rm -rf /var/lib/apt/lists/*

# Expose Jenkins port
EXPOSE 8080

# Start Jenkins
ENTRYPOINT ["/usr/bin/java", "-jar", "/usr/share/jenkins/jenkins.war"]
