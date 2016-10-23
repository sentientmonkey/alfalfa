# alfalfa

This is an experimental project for provisioning new development machines.

Alfalfa seeks a middle ground between [sprout-wrap][sprout-wrap], which relies
on Chef, and [workstation-setup][workstation-setup], which uses shell
scripting.

[sprout-wrap]: https://github.com/pivotal-sprout/sprout-wrap
[workstation-setup]: https://github.com/pivotal/workstation-setup

## Usage

### Local Provisioning

#### OSX
```
bash <(curl -s https://raw.githubusercontent.com/seattle-beach/alfalfa/master/bootstrap.sh)
cd ~/workspace/alfalfa/ansible
ansible-playbook main.yml --ask-pass --ask-become-pass
```

#### Ubuntu
```
bash <(curl -s https://raw.githubusercontent.com/seattle-beach/alfalfa/master/bootstrap_ubuntu.sh)
```

### Remote Provisioning

```
sudo -v && sudo -k
```

On the control machine:

```
brew install ansible

git clone https://github.com/seattle-beach/alfalfa
cd alfalfa/ansible
echo HOST > hosts
ansible-playbook main.yml --ask-pass --ask-become-pass
```

Since this sets up SSH keys, subsequent runs should not require `ask-pass`.

Depending on how you feel about cows, you might find it useful to `export ANSIBLE_NOCOWS=1` first.
