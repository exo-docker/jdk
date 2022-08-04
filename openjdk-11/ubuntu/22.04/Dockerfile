# Dockerizing a base images with:
#
#   - Ubuntu 22.04 LTS (Jammy Jellyfish)
#   - OpenJDK 11
#
# Build:    docker build -t exoplatform/jdk:openjdk-11 .
#
# Run:      docker run -ti exoplatform/jdk:openjdk-11 -version

FROM  exoplatform/ubuntu:22.04
LABEL maintainer="eXo Platform <docker@exoplatform.com>"

# Install OpenJdk Java 11 SDK
RUN apt-get update && apt-get -y install openjdk-11-jdk-headless && rm -rf /var/lib/apt

ENTRYPOINT ["/usr/local/bin/tini", "--", "/usr/bin/java"]
