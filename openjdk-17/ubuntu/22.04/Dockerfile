# Dockerizing a base images with:
#
#   - Ubuntu 22.04 LTS (Jammy Jellyfish)
#   - OpenJDK 17
#
# Build:    docker build -t exoplatform/jdk:openjdk-17 .
#
# Run:      docker run -ti exoplatform/jdk:openjdk-17 -version

FROM  exoplatform/ubuntu:22.04
LABEL maintainer="eXo Platform <docker@exoplatform.com>"

ENV JDK_VERSION 17.0.9
ENV JDK_MAJOR_VERSION 17
ENV TEMURIN_SUFFIX 9

ENV JDK_DOWNLOAD http://storage.exoplatform.org/public/java/jdk/openjdk/${JDK_VERSION}/openjdk-${JDK_VERSION}_linux-x64_bin.tar.gz


# Install OpenJDK Java 17 SDK
ENV JVM_DIR /usr/lib/jvm
RUN mkdir -p "${JVM_DIR}"

RUN wget -q --no-cookies --no-check-certificate \
  -O "${DOWNLOAD_DIR}/openjdk-${JDK_VERSION}-linux-x64.tar.gz" "${JDK_DOWNLOAD}" \
  && cd "${JVM_DIR}" \
  && tar --no-same-owner -xzf "${DOWNLOAD_DIR}/openjdk-${JDK_VERSION}-linux-x64.tar.gz" \
  && rm -f "${DOWNLOAD_DIR}/openjdk-${JDK_VERSION}-linux-x64.tar.gz" \
  && mv "${JVM_DIR}/jdk-${JDK_VERSION}+${TEMURIN_SUFFIX}" "${JVM_DIR}/java-${JDK_VERSION}-openjdk-x64" \
  && ln -s "${JVM_DIR}/java-${JDK_VERSION}-openjdk-x64" "${JVM_DIR}/java-${JDK_MAJOR_VERSION}-openjdk-x64"

ADD java-x64.jinfo ${JVM_DIR}/.java-x64.jinfo
RUN cat "${JVM_DIR}/.java-x64.jinfo" | grep -E '^(jre|jdk|hl)' | awk '{print "/usr/bin/" $2 " " $2 " " $3 " 30 \n"}' | xargs -t -n4 gosu root update-alternatives --install
ENV JAVA_HOME ${JVM_DIR}/java-${JDK_MAJOR_VERSION}-openjdk-x64

ENTRYPOINT ["/usr/local/bin/tini", "--", "/usr/bin/java"]
