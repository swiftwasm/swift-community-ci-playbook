## Swift Community CI Playbook

This repository hosts configuration files for [Swift Community-Hosted Continuous Integration](https://github.com/apple/swift-community-hosted-continuous-integration).

## Apply playbook

```console
$ cat <<EOS > ./playbook/inventory
[buildbot]
xx.xx.xx.xx ansible_user=ubuntu
EOS
$ ansible-galaxy install -r ./playbook/requirements.yml
$ ansible-playbook -i ./playbook/inventory --private-key=path/to/ssh_key ./playbook/main.yml
```
