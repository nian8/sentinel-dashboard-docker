# 使用 alpine 镜像才能执行 apk 命令
FROM openjdk:8-jre-alpine3.9
#
ARG SENTINEL_DASHBOARD_VERSION=1.8.3
# set environment
ENV BASE_DIR="/home/sentinel" \
    SERVER_PORT="8858" \
    DASHBOARD_SERVER="localhost:8858" \
    PROJECT_NAME="sentinel-dashboard" \
    JAVA_OPTS="" \
    TIME_ZONE="Asia/Shanghai"

WORKDIR $BASE_DIR

RUN set -x \
    && apk update \
    && apk --no-cache add ca-certificates wget \
    && update-ca-certificates \
    && wget https://github.com/alibaba/Sentinel/releases/download/${SENTINEL_DASHBOARD_VERSION}/sentinel-dashboard-${SENTINEL_DASHBOARD_VERSION}.jar -O $BASE_DIR/sentinel-dashboard.jar \
    && ln -snf /usr/share/zoneinfo/$TIME_ZONE /etc/localtime && echo '$TIME_ZONE' > /etc/timezone

ADD bin/docker-entrypoint.sh bin/docker-entrypoint.sh

# set startup log dir
RUN mkdir -p logs \
	&& cd logs \
	&& touch start.out \
	&& ln -sf /dev/stdout start.out \
	&& ln -sf /dev/stderr start.out
#
RUN chmod +x bin/docker-entrypoint.sh

EXPOSE 8858
ENTRYPOINT ["bin/docker-entrypoint.sh"]
