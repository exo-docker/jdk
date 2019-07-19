# Dockerizing a base images with:
#
#   - Ubuntu 18.04 LTS (Bionic Beaver)
#   - OpenJDK 11
#
# Build:    docker build -t exoplatform/jdk:openjdk-11 .
#
# Run:      docker run -ti exoplatform/jdk:openjdk-11 -version

FROM  exoplatform/ubuntu:18.04
LABEL maintainer="eXo Platform <docker@exoplatform.com>"

ENV JDK_VERSION_MAJOR 11
ENV JDK_VERSION 11.0.2

ENV JDK_DOWNLOAD http://storage.exoplatform.org/public/java/jdk/openjdk/${JDK_VERSION}/openjdk-${JDK_VERSION}_linux-x64_bin.tar.gz

# Install OpenJdk Java 11 SDK
ENV JVM_DIR /usr/lib/jvm
RUN mkdir -p "${JVM_DIR}"

RUN wget -q --no-cookies --no-check-certificate \
  -O "${DOWNLOAD_DIR}/openjdk-${JDK_VERSION}_linux-x64_bin.tar.gz" "${JDK_DOWNLOAD}" \
  && cd "${JVM_DIR}" \
  && tar --no-same-owner -xzf "${DOWNLOAD_DIR}/openjdk-${JDK_VERSION}_linux-x64_bin.tar.gz" \
  && rm -f "${DOWNLOAD_DIR}/openjdk-${JDK_VERSION}_linux-x64_bin.tar.gz" \
  && mv "${JVM_DIR}/jdk-${JDK_VERSION}" "${JVM_DIR}/java-${JDK_VERSION}-openjdk-x64" \
  && ln -s "${JVM_DIR}/java-${JDK_VERSION}-openjdk-x64" "${JVM_DIR}/java-${JDK_VERSION_MAJOR}-openjdk-x64"

ADD java-x64.jinfo ${JVM_DIR}/.java-x64.jinfo
RUN cat "${JVM_DIR}/.java-x64.jinfo" | grep -E '^(jre|jdk|hl)' | awk '{print "/usr/bin/" $2 " " $2 " " $3 " 30 \n"}' | xargs -t -n4 gosu root update-alternatives --install
ENV JAVA_HOME ${JVM_DIR}/java-${JDK_VERSION_MAJOR}-openjdk-x64

ENTRYPOINT ["/usr/local/bin/tini", "--", "/usr/bin/java"]
