FROM swift-ci:main-ubuntu-20.04

USER root
RUN apt-get update && apt-get install openssh-server default-jre -y
RUN ssh-keygen -A
RUN mkdir -p /run/sshd

RUN usermod -l buildbot build-user
RUN groupmod -n buildbot build-user
RUN usermod -d /home/buildbot -m buildbot
WORKDIR /home/buildbot

# Add PATH environment variable in profile
# to be used in ssh session
RUN echo "PATH=$PATH" >> /home/buildbot/.profile

EXPOSE 22
CMD ["/usr/sbin/sshd", "-D", "-e"]
