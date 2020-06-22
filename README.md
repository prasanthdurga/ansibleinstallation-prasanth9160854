Ansible installation.

step 1: lanuch ec2 ubuntu instance in aws

step 2 : switch to sudo group by command 
           sudo su -

step 3: adduser 
           adduser ansible  ===> command
enter the password 

step 4 : general aws will not allow password policy so 
           visudo =====> command
change the file password file 
ansible (ALL:ALL) NOPASSWD:ALL ==== ENTER THIS LINE  AND SAVE THE FILE FILE


step 5: open this file 
            vi /etc/ssh/sshd_config =====> type this command and exit the file 

restart the sshd file by command
          service sshd restart

switch to ansible user by command ( su ansible)

step 6: install anisble from below url
https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html#installing-ansible-on-ubuntu

step 7 : type the below commands

               cd /etc/ansible
               ls
               cat hosts
              sudo  vi hosts
clear the full file and add (localhost) to the file 

step 8: ssh-keygen
        ssh-copy-id ansible@localhost




example :

ubuntu@ip-172-31-52-19:~$ sudo su -
root@ip-172-31-52-19:~# adduser ansible
Adding user `ansible' ...
Adding new group `ansible' (1001) ...
Adding new user `ansible' (1001) with group `ansible' ...
Creating home directory `/home/ansible' ...
Copying files from `/etc/skel' ...
Enter new UNIX password:
Retype new UNIX password:
passwd: password updated successfully
Changing the user information for ansible
Enter the new value, or press ENTER for the default
        Full Name []:
        Room Number []:
        Work Phone []:
        Home Phone []:
        Other []:
Is the information correct? [Y/n] y
root@ip-172-31-52-19:~# su ansible
ansible@ip-172-31-52-19:/root$ exit
exit
root@ip-172-31-52-19:~# exit
logout
ubuntu@ip-172-31-52-19:~$ su ansible
Password:
ansible@ip-172-31-52-19:/home/ubuntu$ cd ~
ansible@ip-172-31-52-19:~$ pwd
/home/ansible
ansible@ip-172-31-52-19:~$ sudo ap-get update
[sudo] password for ansible:
^Csudo: 1 incorrect password attempt
ansible@ip-172-31-52-19:~$
ansible@ip-172-31-52-19:~$ exit
exit
ubuntu@ip-172-31-52-19:~$ sudo su -
root@ip-172-31-52-19:~# visudo
root@ip-172-31-52-19:~# EXIT
EXIT: command not found
root@ip-172-31-52-19:~# exit
logout
ubuntu@ip-172-31-52-19:~$ su ansible
Password:
su: Authentication failure
ubuntu@ip-172-31-52-19:~$ su ansible
Password:
ansible@ip-172-31-52-19:/home/ubuntu$ cd ~
ansible@ip-172-31-52-19:~$ sudo apt-get update
Hit:1 http://us-east-1.ec2.archive.ubuntu.com/ubuntu xenial InRelease
Hit:2 http://us-east-1.ec2.archive.ubuntu.com/ubuntu xenial-updates InRelease
Hit:3 http://us-east-1.ec2.archive.ubuntu.com/ubuntu xenial-backports InRelease
Hit:4 http://security.ubuntu.com/ubuntu xenial-security InRelease
Reading package lists... Done
ansible@ip-172-31-52-19:~$ sudo vi /etc/ssh/sshd_config
ansible@ip-172-31-52-19:~$ sudo service sshd restart
ansible@ip-172-31-52-19:~$ exit
exit
ubuntu@ip-172-31-52-19:~$ su ansible
Password:
ansible@ip-172-31-52-19:/home/ubuntu$ cd ~
ansible@ip-172-31-52-19:~$ sudo apt update
Hit:1 http://us-east-1.ec2.archive.ubuntu.com/ubuntu xenial InRelease
Hit:2 http://us-east-1.ec2.archive.ubuntu.com/ubuntu xenial-updates InRelease
Hit:3 http://us-east-1.ec2.archive.ubuntu.com/ubuntu xenial-backports InRelease
Hit:4 http://security.ubuntu.com/ubuntu xenial-security InRelease
Reading package lists... Done
Building dependency tree
Reading state information... Done
13 packages can be upgraded. Run 'apt list --upgradable' to see them.
ansible@ip-172-31-52-19:~$ sudo apt install software-properties-common
Reading package lists... Done
Building dependency tree
Reading state information... Done
software-properties-common is already the newest version (0.96.20.9).
0 upgraded, 0 newly installed, 0 to remove and 13 not upgraded.
ansible@ip-172-31-52-19:~$ sudo apt-add-repository --yes --update ppa:ansible/an                                                                                        sible
gpg: keyring `/tmp/tmp9vusb8cy/secring.gpg' created
gpg: keyring `/tmp/tmp9vusb8cy/pubring.gpg' created
gpg: requesting key 7BB9C367 from hkp server keyserver.ubuntu.com
gpg: /tmp/tmp9vusb8cy/trustdb.gpg: trustdb created
gpg: key 7BB9C367: public key "Launchpad PPA for Ansible, Inc." imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK
ansible@ip-172-31-52-19:~$  sudo apt install ansible
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following additional packages will be installed:
  libpython-stdlib libpython2.7-minimal libpython2.7-stdlib python
  python-cffi-backend python-crypto python-cryptography python-ecdsa
  python-enum34 python-httplib2 python-idna python-ipaddress python-jinja2
  python-markupsafe python-minimal python-paramiko python-pkg-resources
  python-pyasn1 python-setuptools python-six python-yaml python2.7
  python2.7-minimal sshpass
Suggested packages:
  python-doc python-tk python-crypto-dbg python-crypto-doc
  python-cryptography-doc python-cryptography-vectors python-enum34-doc
  python-jinja2-doc doc-base python-setuptools-doc python2.7-doc binutils
  binfmt-support
The following NEW packages will be installed:
  ansible libpython-stdlib libpython2.7-minimal libpython2.7-stdlib python
  python-cffi-backend python-crypto python-cryptography python-ecdsa
  python-enum34 python-httplib2 python-idna python-ipaddress python-jinja2
  python-markupsafe python-minimal python-paramiko python-pkg-resources
  python-pyasn1 python-setuptools python-six python-yaml python2.7
  python2.7-minimal sshpass
0 upgraded, 25 newly installed, 0 to remove and 13 not upgraded.
Need to get 11.0 MB of archives.
After this operation, 82.0 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://us-east-1.ec2.archive.ubuntu.com/ubuntu xenial-updates/main amd64 l                                                                                        ibpython2.7-minimal amd64 2.7.12-1ubuntu0~16.04.11 [338 kB]
Get:2 http://us-east-1.ec2.archive.ubuntu.com/ubuntu xenial-updates/main amd64 p                                                                                        ython2.7-minimal amd64 2.7.12-1ubuntu0~16.04.11 [1,261 kB]
Get:3 http://us-east-1.ec2.archive.ubuntu.com/ubuntu xenial-updates/main amd64 p                                                                                        ython-minimal amd64 2.7.12-1~16.04 [28.1 kB]
Get:4 http://us-east-1.ec2.archive.ubuntu.com/ubuntu xenial-updates/main amd64 l                                                                                        ibpython2.7-stdlib amd64 2.7.12-1ubuntu0~16.04.11 [1,884 kB]
Get:5 http://us-east-1.ec2.archive.ubuntu.com/ubuntu xenial-updates/main amd64 p                                                                                        ython2.7 amd64 2.7.12-1ubuntu0~16.04.11 [224 kB]
Get:6 http://us-east-1.ec2.archive.ubuntu.com/ubuntu xenial-updates/main amd64 l                                                                                        ibpython-stdlib amd64 2.7.12-1~16.04 [7,768 B]
Get:7 http://us-east-1.ec2.archive.ubuntu.com/ubuntu xenial-updates/main amd64 p                                                                                        ython amd64 2.7.12-1~16.04 [137 kB]
Get:8 http://us-east-1.ec2.archive.ubuntu.com/ubuntu xenial/main amd64 python-ma                                                                                        rkupsafe amd64 0.23-2build2 [15.5 kB]
Get:9 http://us-east-1.ec2.archive.ubuntu.com/ubuntu xenial-updates/main amd64 p                                                                                        ython-jinja2 all 2.8-1ubuntu0.1 [106 kB]
Get:10 http://us-east-1.ec2.archive.ubuntu.com/ubuntu xenial/main amd64 python-y                                                                                        aml amd64 3.11-3build1 [105 kB]
Get:11 http://us-east-1.ec2.archive.ubuntu.com/ubuntu xenial-updates/main amd64                                                                                         python-crypto amd64 2.6.1-6ubuntu0.16.04.3 [246 kB]
Get:12 http://us-east-1.ec2.archive.ubuntu.com/ubuntu xenial/main amd64 python-s                                                                                        ix all 1.10.0-3 [10.9 kB]
Get:13 http://us-east-1.ec2.archive.ubuntu.com/ubuntu xenial-updates/main amd64                                                                                         python-ecdsa all 0.13-2ubuntu0.16.04.1 [36.2 kB]
Get:14 http://us-east-1.ec2.archive.ubuntu.com/ubuntu xenial-updates/main amd64                                                                                         python-paramiko all 1.16.0-1ubuntu0.2 [110 kB]
Get:15 http://us-east-1.ec2.archive.ubuntu.com/ubuntu xenial/main amd64 python-h                                                                                        ttplib2 all 0.9.1+dfsg-1 [34.2 kB]
Get:16 http://us-east-1.ec2.archive.ubuntu.com/ubuntu xenial/main amd64 python-p                                                                                        kg-resources all 20.7.0-1 [108 kB]
Get:17 http://us-east-1.ec2.archive.ubuntu.com/ubuntu xenial/main amd64 python-s                                                                                        etuptools all 20.7.0-1 [169 kB]
Get:18 http://us-east-1.ec2.archive.ubuntu.com/ubuntu xenial/universe amd64 sshp                                                                                        ass amd64 1.05-1 [10.5 kB]
Get:19 http://us-east-1.ec2.archive.ubuntu.com/ubuntu xenial/main amd64 python-c                                                                                        ffi-backend amd64 1.5.2-1ubuntu1 [58.1 kB]
Get:20 http://us-east-1.ec2.archive.ubuntu.com/ubuntu xenial/main amd64 python-e                                                                                        num34 all 1.1.2-1 [35.8 kB]
Get:21 http://us-east-1.ec2.archive.ubuntu.com/ubuntu xenial/main amd64 python-i                                                                                        dna all 2.0-3 [35.1 kB]
Get:22 http://us-east-1.ec2.archive.ubuntu.com/ubuntu xenial/main amd64 python-i                                                                                        paddress all 1.0.16-1 [18.0 kB]
Get:23 http://us-east-1.ec2.archive.ubuntu.com/ubuntu xenial/main amd64 python-p                                                                                        yasn1 all 0.1.9-1 [45.1 kB]
Get:24 http://us-east-1.ec2.archive.ubuntu.com/ubuntu xenial-updates/main amd64                                                                                         python-cryptography amd64 1.2.3-1ubuntu0.2 [199 kB]
Get:25 http://ppa.launchpad.net/ansible/ansible/ubuntu xenial/main amd64 ansible                                                                                         all 2.9.10-1ppa~xenial [5,787 kB]
Fetched 11.0 MB in 0s (12.1 MB/s)
Selecting previously unselected package libpython2.7-minimal:amd64.
(Reading database ... 76575 files and directories currently installed.)
Preparing to unpack .../libpython2.7-minimal_2.7.12-1ubuntu0~16.04.11_amd64.deb                                                                                         ...
Unpacking libpython2.7-minimal:amd64 (2.7.12-1ubuntu0~16.04.11) ...
Selecting previously unselected package python2.7-minimal.
Preparing to unpack .../python2.7-minimal_2.7.12-1ubuntu0~16.04.11_amd64.deb ...
Unpacking python2.7-minimal (2.7.12-1ubuntu0~16.04.11) ...
Selecting previously unselected package python-minimal.
Preparing to unpack .../python-minimal_2.7.12-1~16.04_amd64.deb ...
Unpacking python-minimal (2.7.12-1~16.04) ...
Selecting previously unselected package libpython2.7-stdlib:amd64.
Preparing to unpack .../libpython2.7-stdlib_2.7.12-1ubuntu0~16.04.11_amd64.deb .                                                                                        ..
Unpacking libpython2.7-stdlib:amd64 (2.7.12-1ubuntu0~16.04.11) ...
Selecting previously unselected package python2.7.
Preparing to unpack .../python2.7_2.7.12-1ubuntu0~16.04.11_amd64.deb ...
Unpacking python2.7 (2.7.12-1ubuntu0~16.04.11) ...
Selecting previously unselected package libpython-stdlib:amd64.
Preparing to unpack .../libpython-stdlib_2.7.12-1~16.04_amd64.deb ...
Unpacking libpython-stdlib:amd64 (2.7.12-1~16.04) ...
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for mime-support (3.59ubuntu1) ...
Setting up libpython2.7-minimal:amd64 (2.7.12-1ubuntu0~16.04.11) ...
Setting up python2.7-minimal (2.7.12-1ubuntu0~16.04.11) ...
Linking and byte-compiling packages for runtime python2.7...
Setting up python-minimal (2.7.12-1~16.04) ...
Selecting previously unselected package python.
(Reading database ... 77321 files and directories currently installed.)
Preparing to unpack .../python_2.7.12-1~16.04_amd64.deb ...
Unpacking python (2.7.12-1~16.04) ...
Selecting previously unselected package python-markupsafe.
Preparing to unpack .../python-markupsafe_0.23-2build2_amd64.deb ...
Unpacking python-markupsafe (0.23-2build2) ...
Selecting previously unselected package python-jinja2.
Preparing to unpack .../python-jinja2_2.8-1ubuntu0.1_all.deb ...
Unpacking python-jinja2 (2.8-1ubuntu0.1) ...
Selecting previously unselected package python-yaml.
Preparing to unpack .../python-yaml_3.11-3build1_amd64.deb ...
Unpacking python-yaml (3.11-3build1) ...
Selecting previously unselected package python-crypto.
Preparing to unpack .../python-crypto_2.6.1-6ubuntu0.16.04.3_amd64.deb ...
Unpacking python-crypto (2.6.1-6ubuntu0.16.04.3) ...
Selecting previously unselected package python-six.
Preparing to unpack .../python-six_1.10.0-3_all.deb ...
Unpacking python-six (1.10.0-3) ...
Selecting previously unselected package python-ecdsa.
Preparing to unpack .../python-ecdsa_0.13-2ubuntu0.16.04.1_all.deb ...
Unpacking python-ecdsa (0.13-2ubuntu0.16.04.1) ...
Selecting previously unselected package python-paramiko.
Preparing to unpack .../python-paramiko_1.16.0-1ubuntu0.2_all.deb ...
Unpacking python-paramiko (1.16.0-1ubuntu0.2) ...
Selecting previously unselected package python-httplib2.
Preparing to unpack .../python-httplib2_0.9.1+dfsg-1_all.deb ...
Unpacking python-httplib2 (0.9.1+dfsg-1) ...
Selecting previously unselected package python-pkg-resources.
Preparing to unpack .../python-pkg-resources_20.7.0-1_all.deb ...
Unpacking python-pkg-resources (20.7.0-1) ...
Selecting previously unselected package python-setuptools.
Preparing to unpack .../python-setuptools_20.7.0-1_all.deb ...
Unpacking python-setuptools (20.7.0-1) ...
Selecting previously unselected package sshpass.
Preparing to unpack .../sshpass_1.05-1_amd64.deb ...
Unpacking sshpass (1.05-1) ...
Selecting previously unselected package python-cffi-backend.
Preparing to unpack .../python-cffi-backend_1.5.2-1ubuntu1_amd64.deb ...
Unpacking python-cffi-backend (1.5.2-1ubuntu1) ...
Selecting previously unselected package python-enum34.
Preparing to unpack .../python-enum34_1.1.2-1_all.deb ...
Unpacking python-enum34 (1.1.2-1) ...
Selecting previously unselected package python-idna.
Preparing to unpack .../python-idna_2.0-3_all.deb ...
Unpacking python-idna (2.0-3) ...
Selecting previously unselected package python-ipaddress.
Preparing to unpack .../python-ipaddress_1.0.16-1_all.deb ...
Unpacking python-ipaddress (1.0.16-1) ...
Selecting previously unselected package python-pyasn1.
Preparing to unpack .../python-pyasn1_0.1.9-1_all.deb ...
Unpacking python-pyasn1 (0.1.9-1) ...
Selecting previously unselected package python-cryptography.
Preparing to unpack .../python-cryptography_1.2.3-1ubuntu0.2_amd64.deb ...
Unpacking python-cryptography (1.2.3-1ubuntu0.2) ...
Selecting previously unselected package ansible.
Preparing to unpack .../ansible_2.9.10-1ppa~xenial_all.deb ...
Unpacking ansible (2.9.10-1ppa~xenial) ...
Processing triggers for man-db (2.7.5-1) ...
Setting up libpython2.7-stdlib:amd64 (2.7.12-1ubuntu0~16.04.11) ...
Setting up python2.7 (2.7.12-1ubuntu0~16.04.11) ...
Setting up libpython-stdlib:amd64 (2.7.12-1~16.04) ...
Setting up python (2.7.12-1~16.04) ...
Setting up python-markupsafe (0.23-2build2) ...
Setting up python-jinja2 (2.8-1ubuntu0.1) ...
Setting up python-yaml (3.11-3build1) ...
Setting up python-crypto (2.6.1-6ubuntu0.16.04.3) ...
Setting up python-six (1.10.0-3) ...
Setting up python-ecdsa (0.13-2ubuntu0.16.04.1) ...
Setting up python-paramiko (1.16.0-1ubuntu0.2) ...
Setting up python-httplib2 (0.9.1+dfsg-1) ...
Setting up python-pkg-resources (20.7.0-1) ...
Setting up python-setuptools (20.7.0-1) ...
Setting up sshpass (1.05-1) ...
Setting up python-cffi-backend (1.5.2-1ubuntu1) ...
Setting up python-enum34 (1.1.2-1) ...
Setting up python-idna (2.0-3) ...
Setting up python-ipaddress (1.0.16-1) ...
Setting up python-pyasn1 (0.1.9-1) ...
Setting up python-cryptography (1.2.3-1ubuntu0.2) ...
Setting up ansible (2.9.10-1ppa~xenial) ...
ansible@ip-172-31-52-19:~$ python --version
Python 2.7.12
ansible@ip-172-31-52-19:~$ ansible --version
ansible 2.9.10
  config file = /etc/ansible/ansible.cfg
  configured module search path = [u'/home/ansible/.ansible/plugins/modules', u'                                                                                        /usr/share/ansible/plugins/modules']
  ansible python module location = /usr/lib/python2.7/dist-packages/ansible
  executable location = /usr/bin/ansible
  python version = 2.7.12 (default, Apr 15 2020, 17:07:12) [GCC 5.4.0 20160609]
ansible@ip-172-31-52-19:~$ cd /etc/ansibel
bash: cd: /etc/ansibel: No such file or directory
ansible@ip-172-31-52-19:~$ cd /etc/ansible/ls
bash: cd: /etc/ansible/ls: No such file or directory
ansible@ip-172-31-52-19:~$ cd /etc/ansible
ansible@ip-172-31-52-19:/etc/ansible$ ls
ansible.cfg  hosts  roles
ansible@ip-172-31-52-19:/etc/ansible$ cat hosts
# This is the default ansible 'hosts' file.
#
# It should live in /etc/ansible/hosts
#
#   - Comments begin with the '#' character
#   - Blank lines are ignored
#   - Groups of hosts are delimited by [header] elements
#   - You can enter hostnames or ip addresses
#   - A hostname/ip can be a member of multiple groups

# Ex 1: Ungrouped hosts, specify before any group headers.

## green.example.com
## blue.example.com
## 192.168.100.1
## 192.168.100.10

# Ex 2: A collection of hosts belonging to the 'webservers' group

## [webservers]
## alpha.example.org
## beta.example.org
## 192.168.1.100
## 192.168.1.110

# If you have multiple hosts following a pattern you can specify
# them like this:

## www[001:006].example.com

# Ex 3: A collection of database servers in the 'dbservers' group

## [dbservers]
##
## db01.intranet.mydomain.net
## db02.intranet.mydomain.net
## 10.25.1.56
## 10.25.1.57

# Here's another example of host ranges, this time there are no
# leading 0s:

## db-[99:101]-node.example.com

ansible@ip-172-31-52-19:/etc/ansible$ ls
ansible.cfg  hosts  roles
ansible@ip-172-31-52-19:/etc/ansible$ vi hosts
ansible@ip-172-31-52-19:/etc/ansible$ sudo vi hosts
ansible@ip-172-31-52-19:/etc/ansible$ sudo vi hosts
ansible@ip-172-31-52-19:/etc/ansible$ ansible -m ping all
The authenticity of host 'localhost (127.0.0.1)' can't be established.
ECDSA key fingerprint is SHA256:cmco0wavlkaBr3QbDpaySaf1Yl3FhEBGFoxAu0MZUvE.
Are you sure you want to continue connecting (yes/no)? y
Please type 'yes' or 'no': yes
localhost | UNREACHABLE! => {
    "changed": false,
    "msg": "Failed to connect to the host via ssh: Warning: Permanently added 'localhost' (ECDSA) to the list of known hosts.\r\nPermission denied (publickey,password).",
    "unreachable": true
}
ansible@ip-172-31-52-19:/etc/ansible$ ssh-keygen
Generating public/private rsa key pair.
Enter file in which to save the key (/home/ansible/.ssh/id_rsa):
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
Your identification has been saved in /home/ansible/.ssh/id_rsa.
Your public key has been saved in /home/ansible/.ssh/id_rsa.pub.
The key fingerprint is:
SHA256:yseSjrQlW7G7mk3mxkwXsj/LcVOd5gwxJM2+tj/4Lfs ansible@ip-172-31-52-19
The key's randomart image is:
+---[RSA 2048]----+
|          .o.    |
|           oo    |
|           .o    |
|      . .   .+ . |
|      .oS.  o.+  |
|     .o*.  .o=   |
|    o+@o+ o. oo  |
|   . #+=oo .o o. |
|    *o*.oo   o+=E|
+----[SHA256]-----+
ansible@ip-172-31-52-19:/etc/ansible$ ls /home/ansible/.ssh/
id_rsa  id_rsa.pub  known_hosts
ansible@ip-172-31-52-19:/etc/ansible$ ssh-copy-id ansible@localhost
/usr/bin/ssh-copy-id: INFO: Source of key(s) to be installed: "/home/ansible/.ssh/id_rsa.pub"
/usr/bin/ssh-copy-id: INFO: attempting to log in with the new key(s), to filter out any that are already installed
/usr/bin/ssh-copy-id: INFO: 1 key(s) remain to be installed -- if you are prompted now it is to install the new keys
ansible@localhost's password:

Number of key(s) added: 1

Now try logging into the machine, with:   "ssh 'ansible@localhost'"
and check to make sure that only the key(s) you wanted were added.

ansible@ip-172-31-52-19:/etc/ansible$ ssh localhost
Welcome to Ubuntu 16.04.6 LTS (GNU/Linux 4.4.0-1105-aws x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/advantage


13 packages can be updated.
0 updates are security updates.

New release '18.04.4 LTS' available.
Run 'do-release-upgrade' to upgrade to it.


*** System restart required ***
ansible@ip-172-31-52-19:~$ ansible -m ping all
[DEPRECATION WARNING]: Distribution Ubuntu 16.04 on host localhost should use /usr/bin/python3, but is using /usr/bin/python for backward compatibility with prior
Ansible releases. A future Ansible release will default to using the discovered platform python for this host. See
https://docs.ansible.com/ansible/2.9/reference_appendices/interpreter_discovery.html for more information. This feature will be removed in version 2.12. Deprecation
warnings can be disabled by setting deprecation_warnings=False in ansible.cfg.
localhost | SUCCESS => {
    "ansible_facts": {
        "discovered_interpreter_python": "/usr/bin/python"
    },
    "changed": false,
    "ping": "pong"
}
ansible@ip-172-31-52-19:~$
