# ------------------------------------------------------------------------
#
# Copyright 2017 WSO2, Inc. (http://wso2.com)
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
# http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License
#
# ------------------------------------------------------------------------

# set to Centos 7.3
# Vendor, License and Build date are for the Centos Base Image
FROM centos:7.3.1611
LABEL name="CentOS WSO2 EI" \
    vendor="CentOS" \
    license="GPLv2" \
    build-date="20161214"
MAINTAINER MDG DevOps HMRC "messaging-devops@hmrc.gsi.gov.uk"

# set user configurations
ARG USER=wso2
ARG USER_ID=802
ARG USER_GROUP=wso2
ARG USER_GROUP_ID=802
ARG USER_HOME=/home/${USER}

# set dependant files directory
#ARG FILES=./files

# set wso2 product configurations
ARG WSO2_SERVER=wso2ei
ARG WSO2_SERVER_VERSION=6.1.1
ARG WSO2_FOLDER=enterprise-integrator
ARG WSO2_SERVER_DIST=${WSO2_SERVER}-${WSO2_SERVER_VERSION}
ARG WSO2_SERVER_HOME=/opt/${WSO2_SERVER_DIST}
# set jdk configurations
ARG JDK_DIST=jdk1.8.0_161
ARG JAVA_HOME=/usr/local/${JDK_DIST}

# install required packages
RUN yum -y update && yum clean all
RUN yum -y install zip unzip telnet iproute2 tar curl wget vim && yum clean all

# create a user group and a user
RUN groupadd --system -g ${USER_GROUP_ID} ${USER_GROUP} && \
    useradd --system --create-home --home-dir ${USER_HOME} --no-log-init -g ${USER_GROUP_ID} -u ${USER_ID} ${USER}

# Download jdk and wso2 distribution zip

RUN wget --tries=3 \
        --header "Cookie: oraclelicense=accept-securebackup-cookie" \
        --no-check-certificate \
        http://download.oracle.com/otn-pub/java/jdk/8u161-b12/2f38c3b165be4555a1fa6e98c45e0808/jdk-8u161-linux-x64.tar.gz \
        -O /tmp/jdk.tar.gz \
    && tar -zxf /tmp/jdk.tar.gz -C /usr/local \
    && rm -f /tmp/jdk.tar.gz ${JAVA_HOME}/src.zip ${JAVA_HOME}/javafx-src.zip \
    && chown -R wso2:wso2 ${JAVA_HOME} \
    && echo 'Downloaded and Installed JDK 1.8.0_161'

RUN cd /tmp && \
    wget \
        -q \
        --referer=https://wso2.com/integration/download-thank-you/ \
        --no-check-certificate \
        https://product-dist.wso2.com/products/${WSO2_FOLDER}/${WSO2_SERVER_VERSION}/${WSO2_SERVER}-${WSO2_SERVER_VERSION}.zip && \
    cd /opt && \
    unzip -q /tmp/${WSO2_SERVER}-${WSO2_SERVER_VERSION}.zip && \
    rm -f /tmp/${WSO2_SERVER}-${WSO2_SERVER_VERSION}.zip && \
    chown -R wso2:wso2 ${WSO2_SERVER}-${WSO2_SERVER_VERSION} && \
    echo 'Downloaded and Installed WSO2 EI 6.1.1'

RUN (cd /lib/systemd/system/sysinit.target.wants/; for i in *; do [ $i == \
systemd-tmpfiles-setup.service ] || rm -f $i; done); \
rm -f /lib/systemd/system/multi-user.target.wants/*;\
rm -f /etc/systemd/system/*.wants/*;\
rm -f /lib/systemd/system/local-fs.target.wants/*; \
rm -f /lib/systemd/system/sockets.target.wants/*udev*; \
rm -f /lib/systemd/system/sockets.target.wants/*initctl*; \
rm -f /lib/systemd/system/basic.target.wants/*;\
rm -f /lib/systemd/system/anaconda.target.wants/*;
VOLUME [ "/sys/fs/cgroup" ]


# set the wso2 user and work directory
USER ${USER}

# set environment variables
ENV JAVA_HOME=${JAVA_HOME} \
    PATH=$JAVA_HOME/bin:$PATH \
    WSO2_SERVER_HOME=${WSO2_SERVER_HOME}
