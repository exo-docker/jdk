# Dockerizing a base images with:
#
#   - Ubuntu 20.04 LTS (Focal Fossa)
#   - OpenJDK 14
#
# Build:    docker build -t exoplatform/jdk:openjdk-14 .
#
# Run:      docker run -ti exoplatform/jdk:openjdk-14 -version

FROM  exoplatform/ubuntu:20.04
LABEL maintainer="eXo Platform <docker@exoplatform.com>"

# Install OpenJdk Java 14 SDK
RUN apt-get update && apt-get -y install openjdk-14-jdk-headless && rm -rf /var/lib/apt

ENTRYPOINT ["/usr/local/bin/tini", "--", "/usr/bin/java"]
