# Dockerizing a base images with:
#
#   - Ubuntu 20.04 LTS (Focal Fossa)
#   - OpenJDK 8
#
# Build:    docker build -t exoplatform/jdk:openjdk-8 .
#
# Run:      docker run -ti exoplatform/jdk:openjdk-8 -version

FROM  exoplatform/ubuntu:20.04
LABEL maintainer="eXo Platform <docker@exoplatform.com>"

# Install OpenJdk Java 8 SDK
RUN apt-get update && apt-get -y install openjdk-8-jdk-headless && rm -rf /var/lib/apt

ENTRYPOINT ["/usr/local/bin/tini", "--", "/usr/bin/java"]
