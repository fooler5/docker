# AlpineLinux open jre 8
FROM  registry.cn-hangzhou.aliyuncs.com/zhulei-cywx/alpine-ssh

RUN apk --update add curl bash openjdk8-jre-base && \
      rm -rf /var/cache/apk/*

# Set environment
ENV JAVA_HOME /usr/lib/jvm/default-jvm
ENV PATH ${PATH}:${JAVA_HOME}/bin