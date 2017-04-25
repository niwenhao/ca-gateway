from centos:6
add rootca.crt /etc/.
env CURL_CA_BUNDLE /etc/rootca.crt
env HTTP_PROXY ${HTTP_PROXY}
env http_proxy ${http_proxy}
env HTTPS_PROXY ${HTTPS_PROXY}
env https_proxy ${https_proxy}

run yum update -y
run yum install -y openssh-server rsyslog crontabs xinetd zip unzip openssh-clients mysql-server
add jdk-8u121-linux-x64.tar.gz /tmp/.
run cd /opt && mv /tmp/jdk1.8.0_121 . && ln -s jdk1.8.0_121 java
run echo password | passwd --stdin root
run sed -i 's/^#Port 22/Port 2022/g' /etc/ssh/sshd_config
run groupadd gateway && useradd -g gateway -m gateway && echo password | passwd --stdin gateway
run groupadd layer7 && useradd -g layer7 -m layer7 && echo password | passwd --stdin layer7
add jce_policy-8.zip /tmp/.
run cd /tmp && unzip jce_policy-8.zip && cp -f UnlimitedJCEPolicyJDK8/* /opt/java/jre/lib/security/. && rm -rf jce_policy-8.zip UnlimitedJCEPolicyJDK8
add ssg-9.1.00-6342.noarch.rpm /tmp/.
run cd /tmp && rpm -Uvh ssg-9.1.00-6342.noarch.rpm
run sed -i '$s|^|export JAVA_HOME=/opt/java\n|'  /etc/bashrc
run sed -i '$s|^|export PATH=$JAVA_HOME/bin:$PATH\n|'  /etc/bashrc
run sed -i '$s|$|\nexport PATH=/opt/SecureSpan/Gateway/runtime/bin:$PATH|' /home/gateway/.bashrc
run sed -i /etc/my.cnf -e '/\[mysqld\]/amax_allowed_packet=16M'
run yum install -y vim-enhanced sudo
add my.cnf /etc/my.cnf
add input.txt /tmp/.
workdir /opt/SecureSpan/Gateway/runtime/bin
