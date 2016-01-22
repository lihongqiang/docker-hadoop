FROM hadoop-base:latest

MAINTAINER Lihongqiang <415200973@qq.com>

# move all confugration files into container
ADD files/* /tmp/

ENV HADOOP_INSTALL /usr/local/hadoop

# mk hdfs logs
RUN mkdir -p ~/hdfs/namenode && \ 
mkdir -p ~/hdfs/datanode && \
mkdir $HADOOP_INSTALL/logs

# update etc files
RUN mv /tmp/hdfs-site.xml $HADOOP_INSTALL/etc/hadoop/hdfs-site.xml && \ 
mv /tmp/core-site.xml $HADOOP_INSTALL/etc/hadoop/core-site.xml && \
mv /tmp/mapred-site.xml $HADOOP_INSTALL/etc/hadoop/mapred-site.xml && \
mv /tmp/yarn-site.xml $HADOOP_INSTALL/etc/hadoop/yarn-site.xml && \
mv /tmp/slaves $HADOOP_INSTALL/etc/hadoop/slaves && \

# add exec files
mv /tmp/start-hadoop.sh ~/start-hadoop.sh && \
mv /tmp/run-wordcount.sh ~/run-wordcount.sh && \ 

# chmod exec files
RUN chmod +x ~/start-hadoop.sh && \
chmod +x ~/run-wordcount.sh && \
chmod 1777 tmp

# format namenode
RUN /usr/local/hadoop/bin/hdfs namenode -format

# expose port
EXPOSE 22 7373 7946 9000 50010 50020 50070 50075 50090 50475 8030 8031 8032 8033 8040 8042 8060 8088 50060

CMD 'bash'