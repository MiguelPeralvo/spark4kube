FROM centos:latest
MAINTAINER 2dmitrypavlov@gmail.com
USER root
WORKDIR /usr/share/
ADD master.sh /usr/share/
ADD slaves.sh /usr/share/
ADD master_dns.sh /usr/share/
ADD slaves_dns.sh /usr/share/
ADD .bashrc /root/
ADD RedshiftJDBC4-1.1.17.1017.jar /root/jars/
ADD RedshiftJDBC4-1.1.17.1017.jar /usr/share/
RUN yum install -y libaio.x86_64
ADD oracle-instantclient12.1-basic-12.1.0.2.0-1.x86_64.rpm /usr/share/
ADD oracle-instantclient12.1-sqlplus-12.1.0.2.0-1.x86_64.rpm /usr/share/
ADD ojdbc7.jar /usr/share/
ADD ojdbc7.jar /root/jars/
ADD slaves_local.sh /usr/share/
ADD zeppelin.sh /usr/share/
ADD mykey.key /usr/share/
ADD mycert.pem /usr/share/
ADD jupyter.sh /usr/share/
RUN mkdir /root/.jupyter
ADD jupyter_notebook_config.py /root/.jupyter
RUN cd /usr/share/
RUN chmod 600 mykey.key mycert.pem
RUN export TERM=xterm
RUN yum clean all -y
RUN yum update -y
RUN yum install -y vim
RUN yum install -y bind-utils 
RUN yum install -y yum-utils
RUN yum install -y zsh
RUN yum install -y wget bzip2 git
RUN yum install openssl.x86_64 -y
RUN wget https://github.com/s3tools/s3cmd/archive/master.zip
RUN wget https://s3.amazonaws.com/cxa-redshift-dev/spark_jars/sandbox-all.jar
RUN wget http://central.maven.org/maven2/com/amazonaws/aws-java-sdk/1.7.4/aws-java-sdk-1.7.4.jar
RUN wget http://central.maven.org/maven2/org/apache/hadoop/hadoop-aws/2.7.1/hadoop-aws-2.7.1.jar
RUN wget http://central.maven.org/maven2/org/apache/hadoop/hadoop-aws/2.6.0/hadoop-aws-2.6.0.jar
RUN wget http://central.maven.org/maven2/mysql/mysql-connector-java/5.1.39/mysql-connector-java-5.1.39.jar
RUN wget http://central.maven.org/maven2/com/databricks/spark-redshift_2.11/2.0.1/spark-redshift_2.11-2.0.1.jar
RUN wget http://central.maven.org/maven2/org/postgresql/postgresql/9.4-1201-jdbc41/postgresql-9.4-1201-jdbc41.jar
RUN wget http://central.maven.org/maven2/com/eclipsesource/minimal-json/minimal-json/0.9.4/minimal-json-0.9.4.jar
#RUN openssl req -x509 -nodes -days 365 -newkey rsa:1024 -keyout mykey.key -out mycert.pem
RUN wget --quiet https://repo.continuum.io/archive/Anaconda2-4.1.1-Linux-x86_64.sh -O ~/anaconda.sh
RUN /bin/bash ~/anaconda.sh -b -p /opt/conda && \
    rm ~/anaconda.sh
RUN cd /usr/share/
RUN rpm -ivh oracle-instantclient12.1-basic-12.1.0.2.0-1.x86_64.rpm
RUN rpm -ivh oracle-instantclient12.1-sqlplus-12.1.0.2.0-1.x86_64.rpm
RUN wget http://d3kbcqa49mib13.cloudfront.net/spark-2.0.2-bin-hadoop2.7.tgz
RUN tar -zxvf spark-2.0.2-bin-hadoop2.7.tgz
RUN mv spark-2.0.2-bin-hadoop2.7 spark
RUN yum install -y java-1.8.0-openjdk-devel.x86_64
RUN yum install net-tools -y
ENV PATH $PATH:/usr/share/spark/bin:/opt/conda/bin/
ADD log4j.properties /usr/share/spark/conf/
RUN cd /root/jars/
RUN wget http://central.maven.org/maven2/org/postgresql/postgresql/9.4-1201-jdbc41/postgresql-9.4-1201-jdbc41.jar
ADD spark-defaults.conf /usr/share/spark/conf/
RUN curl "https://bootstrap.pypa.io/get-pip.py" -o "get-pip.py"
RUN python get-pip.py
RUN pip install numpy
RUN pip install scipy
RUN pip install scikit-learn
RUN pip install pandas
