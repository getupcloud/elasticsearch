FROM centos:centos7

MAINTAINER Mateus Caruccio <mateus.caruccio@getupcoud.com.br>

ENV HOME=/opt/app-root/src \
  JAVA_VER=1.8.0 \
  ES_VER=1.1.0 \
  ES_CONF=/usr/share/elasticsearch/config/elasticsearch.yml \
  CLUSTER_NAME=default-cluster \
  INSTANCE_RAM=1G \
  LOGLEVEL=INFO

LABEL io.k8s.description="Elasticsearch container for allowing indexing and searching of aggregated logs" \
  io.k8s.display-name="Elasticsearch 1.1" \
  io.openshift.expose-services="9200:https, 9300:https" \
  io.openshift.tags="elasticsearch,search"

COPY elasticsearch.repo /etc/yum.repos.d/elasticsearch.repo
RUN rpm --import https://packages.elastic.co/GPG-KEY-elasticsearch && \
    yum install -y --setopt=tsflags=nodocs elasticsearch java-1.8.0-openjdk && \
    yum clean all && \
    mkdir -p /elasticsearch/persistent && \
    chown -R 1001 /elasticsearch && \
    chmod -R 755 /elasticsearch

COPY container-entrypoint /usr/bin/
COPY elasticsearch.yml logging.yml /etc/elasticsearch/

EXPOSE 9200
EXPOSE 9300
USER 1001

ENTRYPOINT ["container-entrypoint"]

CMD ["/usr/share/elasticsearch/bin/elasticsearch"]
