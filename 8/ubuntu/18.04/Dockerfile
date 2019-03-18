# Dockerizing a base images with:
#
#   - Ubuntu 18.04 LTS (Bionic Beaver)
#   - Oracle JDK 8
#
# Build:    docker build -t exoplatform/jdk .
#
# Run:      docker run -ti exoplatform/jdk version

FROM  exoplatform/ubuntu:18.04
LABEL maintainer="eXo Platform <docker@exoplatform.com>"

ENV JDK_VERSION_MAJOR 8
ENV JDK_VERSION_UPDATE 171
ENV JDK_VERSION_BUILD b11
ENV JDK_VERSION_HASH 512cd62ec5174c3487ac17c61aaa89e8

ENV JDK_VERSION ${JDK_VERSION_MAJOR}u${JDK_VERSION_UPDATE}
ENV JDK_VERSION_DOT 1.${JDK_VERSION_MAJOR}.0
ENV JDK_VERSION_DOT_UPDATE ${JDK_VERSION_DOT}_${JDK_VERSION_UPDATE}
ENV JDK_DOWNLOAD http://storage.exoplatform.org/public/java/jdk/oracle/${JDK_VERSION}/jdk-${JDK_VERSION}-linux-x64.tar.gz

# Install Oracle Java 8 SDK
ENV JVM_DIR /usr/lib/jvm
RUN mkdir -p "${JVM_DIR}"

RUN wget -q --no-cookies --no-check-certificate \
  -O "${DOWNLOAD_DIR}/jdk-${JDK_VERSION}-linux-x64.tar.gz" "${JDK_DOWNLOAD}" \
  && cd "${JVM_DIR}" \
  && tar --no-same-owner -xzf "${DOWNLOAD_DIR}/jdk-${JDK_VERSION}-linux-x64.tar.gz" \
  && rm -f "${DOWNLOAD_DIR}/jdk-${JDK_VERSION}-linux-x64.tar.gz" \
  && mv "${JVM_DIR}/jdk${JDK_VERSION_DOT_UPDATE}" "${JVM_DIR}/java-${JDK_VERSION_DOT_UPDATE}-oracle-x64" \
  && ln -s "${JVM_DIR}/java-${JDK_VERSION_DOT_UPDATE}-oracle-x64" "${JVM_DIR}/java-${JDK_VERSION_DOT}-oracle-x64"

ADD java-x64.jinfo ${JVM_DIR}/.java-x64.jinfo
RUN cat "${JVM_DIR}/.java-x64.jinfo" | grep -E '^(jre|jdk|hl)' | awk '{print "/usr/bin/" $2 " " $2 " " $3 " 30 \n"}' | xargs -t -n4 gosu root update-alternatives --install
ENV JAVA_HOME ${JVM_DIR}/java-${JDK_VERSION_DOT}-oracle-x64

ENTRYPOINT ["/usr/local/bin/tini", "--", "/usr/bin/java"]
