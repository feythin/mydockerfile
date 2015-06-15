#this is a dockerfile
FROM centos:6 
MAINTAINER feythin.lau <feythin.lau@gmail.com>
RUN yum install -y openssh-server
RUN mkdir /var/run/sshd
RUN ssh-keygen -q -N "" -t dsa -f /etc/ssh/ssh_host_dsa_key
RUN ssh-keygen -q -N "" -t rsa -f /etc/ssh/ssh_host_rsa_key
RUN sed -ri 's/session    required     pam_loginuid.so/#session    required     pam_loginuid.so/g' /etc/pam.d/sshd  
RUN sed -i 's/#PermitRootLogin yes/PermitRootLogin yes/' /etc/ssh/sshd_config
RUN mkdir -p /root/.ssh && chown root.root /root && chmod 700 /root/.ssh  
RUN echo 'root:******' | chpasswd
EXPOSE 22
CMD ["/usr/sbin/sshd", "-D"]
