FROM tomcat8:jdk1.8
LABEL maintainer "qiangqiang.zhou@changhong.com"
COPY JDBCTest.war tomcat/webapps/ROOT/ROOT.war
RUN cd tomcat/webapps/ROOT && \
jar -xf ROOT.war && \
rm -rf ROOT.war
