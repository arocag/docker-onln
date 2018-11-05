FROM oraclelinux

RUN yum -y install openssh-server

RUN useradd system && \
    echo "1234" | passwd system  --stdin && \
    mkdir /home/system/.ssh && \
    chmod 700 /home/system/.ssh

RUN yum install https://download.postgresql.org/pub/repos/yum/9.6/redhat/rhel-7-x86_64/pgdg-oraclelinux96-9.6-3.noarch.rpm -y

RUN yum install postgresql96 -y

COPY system-key.pub /home/system/.ssh/authorized_keys

RUN chown system:system -R /home/system && \
    chmod 600 /home/system/.ssh/authorized_keys

RUN /usr/sbin/sshd-keygen > /dev/null 2>&1

CMD /usr/sbin/sshd -D
