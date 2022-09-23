## Swift Community CI Playbook

This repository hosts configuration files for [Swift Community-Hosted Continuous Integration](https://github.com/apple/swift-community-hosted-continuous-integration).

## Apply playbook

```console
$ cat <<EOS > ./playbook/inventory
[buildbot]
xx.xx.xx.xx ansible_user=ubuntu
EOS
# Put Apple CI public key, which is usually shared by the CI manager
$ echo $APPLE_JENKINS_PUBKEY > playbook/public-keys/apple-jenkins.pub
$ ansible-galaxy install -r ./playbook/requirements.yml
$ ansible-playbook -i ./playbook/inventory --private-key=path/to/ssh_key ./playbook/main.yml
```
