# Ansible Playbook for nginx-fpm

## Tools Needed
* Ansible 
**Note**: If you are testing on local install **Vagrant** and add ubnuntu box (16.x).

## usage

* Add hosts file(This is your inventory file for Ansible)
* Add ansible.cfg file
**Note**: You need add your ssh key to server to run this 
or 
```bash
$ git checkout 5357d07f27ce386d65d1d3ece88e5b03055b5de0
```
and Run
```bash
$ ansible-playbook site.yml
```
You see out put like 
```
ok: [192.168.33.110]

TASK [for-pdf-parser : Install (Bottle) python package.] ***************************************************************************
changed: [192.168.33.110]

PLAY RECAP *************************************************************************************************************************
192.168.33.110             : ok=16   changed=1    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0

```