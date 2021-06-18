# Dockerizing a base images with:
#
#   - Ubuntu 20.04 LTS (Focal Fossa)
#   - OpenJDK 11
#
# Build:    docker build -t exoplatform/jdk:openjdk-11 .
#
# Run:      docker run -ti exoplatform/jdk:openjdk-11 -version

FROM  exoplatform/ubuntu:20.04
LABEL maintainer="eXo Platform <docker@exoplatform.com>"

# Install OpenJdk Java 11 SDK
RUN apt-get update && apt-get -y install openjdk-11-jdk-headless=11.0.7+10-3ubuntu1 && rm -rf /var/lib/apt

ENTRYPOINT ["/usr/local/bin/tini", "--", "/usr/bin/java"]
