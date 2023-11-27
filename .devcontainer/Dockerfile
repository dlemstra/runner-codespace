FROM alpine:3

RUN apk update && \
    apk add curl git openssh openrc sshfs vim

COPY codespace/. /

RUN chmod 700 /usr/bin/runner-connect && \
    chmod 700 /usr/bin/shell && \
    chmod 700 /usr/bin/start-linux && \
    chmod 700 /usr/bin/start-macos && \
    chmod 700 /usr/bin/start-runner && \
    chmod 700 /usr/bin/stop-runner && \
    chmod 700 /root && \
    chmod 700 /postStartCommand

RUN rm -rf /etc/ssh/ssh_host_rsa_key /etc/ssh/ssh_host_dsa_key && \
    ssh-keygen -f /etc/ssh/ssh_host_rsa_key -N '' -t rsa && \
    ssh-keygen -f /etc/ssh/ssh_host_dsa_key -N '' -t dsa && \
    sed -i 's/AllowTcpForwarding no/AllowTcpForwarding yes/g' /etc/ssh/sshd_config && \
    mkdir /root/.ssh && \
    chmod 700 /root/.ssh && \
    touch /root/.ssh/authorized_keys && \
    chmod 600 /root/.ssh/authorized_keys

ENV ENV=/root/.rc
