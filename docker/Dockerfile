FROM swift-ci:main-ubuntu-20.04

USER root
RUN apt-get update && apt-get install openssh-server default-jre -y
RUN ssh-keygen -A
RUN mkdir -p /run/sshd
RUN useradd --create-home buildbot --uid 1000 --user-group

EXPOSE 22
CMD ["/usr/sbin/sshd", "-D", "-e"]
