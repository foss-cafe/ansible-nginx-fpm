# Example of Packer using Ansible as provisioners

## Tools Needed

* packer
* ansible
* AWS credetials

## Usage

```bash
$ packer build -var 'aws_access_key=YOUR ACCESS KEY' \
    -var 'aws_secret_key=YOUR SECRET KEY'
    -var 'region=YOUR REGION'\
    config.json
```
**You will see somthing like:**

```bash
amazon-ebs output will be in this color.

==> amazon-ebs: Prevalidating AMI Name: packer-demo 1560510235
    amazon-ebs: Found Image ID: ami-0e63f50857fdc1f9f
==> amazon-ebs: Creating temporary keypair: packer_5d037f1b-c61b-f0e0-ed8a-f551e3f005e9
==> amazon-ebs: Creating temporary security group for this instance: packer_5d037f23-d790-b6ad-74e3-aa8f59468698
==> amazon-ebs: Authorizing access to port 22 from [0.0.0.0/0] in the temporary security groups...
==> amazon-ebs: Launching a source AWS instance...
==> amazon-ebs: Adding tags to source instance
    amazon-ebs: Adding tag: "Name": "Packer Builder"
    amazon-ebs: Instance ID: i-06c819ccf04ec02c0
==> amazon-ebs: Waiting for instance (i-06c819ccf04ec02c0) to become ready...
==> amazon-ebs: Using ssh communicator to connect: 54.214.156.144
==> amazon-ebs: Waiting for SSH to become available...
==> amazon-ebs: Connected to SSH!
==> amazon-ebs: Provisioning with Ansible...
==> amazon-ebs: Executing Ansible: ansible-playbook --extra-vars packer_build_name=amazon-ebs packer_builder_type=amazon-ebs -o IdentitiesOnly=yes -i /var/folders/l0/sczhv02x1fg67mrt1rcgzwm00000gn/T/packer-provisioner-ansible777649981 /Users/rajeev/org/oncorps/infra/ansible/site.yml -e ansible_ssh_private_key_file=/var/folders/l0/sczhv02x1fg67mrt1rcgzwm00000gn/T/ansible-key383567830
    amazon-ebs:
    amazon-ebs: PLAY [apply common configuration to all nodes] *********************************
    amazon-ebs:
    amazon-ebs: TASK [Gathering Facts] *********************************************************
    amazon-ebs: ok: [default]
    amazon-ebs:
    amazon-ebs: TASK [common : install aptititude] *********************************************
    amazon-ebs:  [WARNING]: Could not find aptitude. Using apt-get instead
    amazon-ebs: changed: [default]
    amazon-ebs:
    amazon-ebs: TASK [common : Update all packages to the latest version] **********************
    amazon-ebs:  [WARNING]: The value True (type bool) in a string field was converted to
    amazon-ebs: ok: [default]
    amazon-ebs: 'True' (type string). If this does not look like what you expect, quote the
    amazon-ebs: entire value to ensure it does not change.
    amazon-ebs:
    amazon-ebs: TASK [common : Install a list of packages] *************************************
    amazon-ebs: ok: [default]
    amazon-ebs:
    amazon-ebs: TASK [php : apt_repository] ****************************************************
    amazon-ebs: changed: [default]
    amazon-ebs:
    amazon-ebs: TASK [php : Run the equivalent of "apt-get update" as a separate step] *********
    amazon-ebs: changed: [default]
    amazon-ebs:
    amazon-ebs: TASK [php : Install a list of packages for php] ********************************
    amazon-ebs: changed: [default]
    amazon-ebs:
    amazon-ebs: TASK [php : ensure php7.1-fpm is running] **************************************
    amazon-ebs: ok: [default]
    amazon-ebs:
    amazon-ebs: TASK [php : Copy the www conf file] ********************************************
    amazon-ebs: changed: [default]
    amazon-ebs:
    amazon-ebs: TASK [php : Enable service php-fpm, and not touch the state] *******************
    amazon-ebs: ok: [default]
    amazon-ebs:
    amazon-ebs: TASK [nginx : Install a list of packages for nginx] ****************************
    amazon-ebs: changed: [default]
    amazon-ebs:
    amazon-ebs: TASK [nginx : Ansible delete file example] *************************************
    amazon-ebs: changed: [default]
    amazon-ebs:
    amazon-ebs: TASK [nginx : Copy the nginx conf file] ****************************************
    amazon-ebs: changed: [default]
    amazon-ebs:
    amazon-ebs: TASK [nginx : Enable service nginx, and not touch the state] *******************
    amazon-ebs: ok: [default]
```

Once build is completed You can find your ami image in the region you sepecified in config 

