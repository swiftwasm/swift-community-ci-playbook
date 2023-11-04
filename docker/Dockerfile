FROM swift-ci:main-ubuntu-20.04

USER root
RUN apt-get update && apt-get install openssh-server default-jre -y
RUN ssh-keygen -A
RUN mkdir -p /run/sshd

RUN usermod -l buildbot build-user
RUN groupmod -n buildbot build-user
RUN usermod -d /home/buildbot -m buildbot
WORKDIR /home/buildbot

# Set PermitUserEnvironment to yes in /etc/ssh/sshd_config
# Set $PATH in /home/buildbot/.ssh/environment
RUN mkdir -p /home/buildbot/.ssh && \
    chmod 700 /home/buildbot/.ssh && \
    chown buildbot:buildbot /home/buildbot/.ssh && \
    touch /home/buildbot/.ssh/authorized_keys && \
    chmod 600 /home/buildbot/.ssh/authorized_keys && \
    chown buildbot:buildbot /home/buildbot/.ssh/authorized_keys && \
    echo "PATH=$PATH" > /etc/environment && \
    chown buildbot:buildbot /etc/environment

EXPOSE 22
CMD ["/usr/sbin/sshd", "-D", "-e"]
