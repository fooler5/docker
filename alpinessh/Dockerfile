FROM alpine:latest
RUN apk add --update openssh
RUN ssh-keygen -f /etc/ssh/ssh_host_rsa_key -N '' -t rsa &&\  
    ssh-keygen -f /etc/ssh/ssh_host_dsa_key -N '' -t dsa &&\
    ssh-keygen -f /etc/ssh/ssh_host_ecdsa_key -N '' -t ecdsa &&\
    ssh-keygen -f /etc/ssh/ssh_host_ed25519_key -N '' -t ed25519
RUN sed -i "s/UsePrivilegeSeparation.*/UsePrivilegeSeparation no/g" /etc/ssh/sshd_config && sed -i "s/UsePAM.*/UsePAM no/g" /etc/ssh/sshd_config && sed -i "s/PermitRootLogin.*/PermitRootLogin yes/g" /etc/ssh/sshd_config && sed -i "s/#AuthorizedKeysFile/AuthorizedKeysFile/g" /etc/ssh/sshd_config

RUN adduser  -D  www &&\
    mkdir -p /home/www/.ssh &&\   
    echo "www:123456" | chpasswd

RUN chown www:www  -R /home/www/ &&\
    chmod 755 -R /home/www/ &&\
    echo "/usr/sbin/sshd -D" >>/etc/start.sh
EXPOSE 22

CMD ["/bin/sh","/etc/start.sh"]