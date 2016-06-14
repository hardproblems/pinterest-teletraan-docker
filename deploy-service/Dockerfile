FROM ubuntu:trusty

ENV DEBIAN_FRONTEND noninteractive
RUN \
  # Install add-apt-repository command
  apt-get install -y -qq software-properties-common python-software-properties && \
  add-apt-repository ppa:openjdk-r/ppa && \
  apt-get update && apt-get upgrade -y -qq && \

  # Install openjdk 8..." 
  apt-get install -y -qq openjdk-8-jre && \
  apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*;


ENV TELETRAAN_RELEASE_VERSION         v1.0.1
ENV TELETRAAN_DEPLOY_SERVICE_VERSION  fdd68c0
ENV INSTALL_DIR                       /opt/teletraan/deploy-service

RUN \
  mkdir -p ${INSTALL_DIR} && \
  # Download and extract teletraan service
  wget -O - https://github.com/pinterest/teletraan/releases/download/${TELETRAAN_RELEASE_VERSION}/teletraan-service-${TELETRAAN_DEPLOY_SERVICE_VERSION}.tar.gz \
  | tar zxf - -C ${INSTALL_DIR};

EXPOSE 8080

ENTRYPOINT ["/bin/bash", "${INSTALL_DIR}/bin/run.sh"]
CMD ["start"]
