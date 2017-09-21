FROM centos:node

LABEL maintainer "qiangqiang.zhou@changhong.com"

#添加用户，UID、GID为4001,home的路径为/srv/ssc
RUN groupadd user_grp -g 4001 && \
useradd -u 4001 --home-dir /srv/ssc --create-home --system --no-user-group ssc && \
usermod -g user_grp ssc && \
ln -s /srv/ssc /var/lib/ssc && \
chown -R ssc:user_grp /var/lib/ssc

#建议修改为其他非root目录
WORKDIR /srv/ssc

#设置一个Dockerfile内部使用的变量
ARG JAVA=/srv/ssc/jdk1.8.0_144

ADD jdk-8u144-linux-x64.tar.gz .
RUN chown -R ssc:user_grp $JAVA

#同时设置多个环境变量，相互不可见，使用上面的变量
ENV JAVA_VERSION=8 \
JAVA_HOME=$JAVA  \
JRE_HOME=$JAVA/jre \
CLASSPATH=.:$JAVA/lib:$JAVA/jre/lib \
PATH=$PATH:$JAVA/bin

USER ssc

CMD ["/bin/bash"]
