# Blockchain

### 개발환경 설정
* Vagrant 
* Ubuntu
* Intelij
* node.js (8.10)
* golang (1.10.2)

### Vagrant 설정
1. 적당한 폴더 생성 
```sh
>vagrant box list
There are no installed boxes! Use `vagrant box add` to add some.

>vagrant init ubuntu/xenial64
A `Vagrantfile` has been placed in this directory. You are now
ready to `vagrant up` your first virtual environment! Please read
the comments in the Vagrantfile as well as documentation on
`vagrantup.com` for more information on using Vagrant.

>vagrant plugin install vagrant-vbguest
Installing the 'vagrant-vbguest' plugin. This can take a few minutes...
Fetching: micromachine-2.0.0.gem (100%)
Fetching: vagrant-vbguest-0.15.2.gem (100%)
Installed the plugin 'vagrant-vbguest (0.15.2)'!

>vagrant plugin install vagrant-disksize
Installing the 'vagrant-disksize' plugin. This can take a few minutes...
Fetching: vagrant-disksize-0.1.2.gem (100%)
Installed the plugin 'vagrant-disksize (0.1.2)'!
>
```
2. Vagrantfile 수정
```sh
>tree
VM2 볼륨에 대한 폴더 경로의 목록입니다.
볼륨 일련 번호는 5C5C-F673입니다.
G:.
└─exchange
```

3. 구동
```sh
>vagrant up
Bringing machine 'default' up with 'virtualbox' provider...
==> default: Checking if box 'ubuntu/xenial64' is up to date...
==> default: Clearing any previously set forwarded ports...
==> default: Clearing any previously set network interfaces...
==> default: Preparing network interfaces based on configuration...
    default: Adapter 1: nat
==> default: Forwarding ports...
    default: 22 (guest) => 2222 (host) (adapter 1)
==> default: Running 'pre-boot' VM customizations...
==> default: Resized disk: old 10240 MB, req 51200 MB, new 51200 MB
==> default: You may need to resize the filesystem from within the guest.
==> default: Booting VM...
==> default: Waiting for machine to boot. This may take a few minutes...
    default: SSH address: 127.0.0.1:2222
    default: SSH username: vagrant
    default: SSH auth method: private key
    default: Warning: Remote connection disconnect. Retrying...
    default: Warning: Connection aborted. Retrying...
    default: Warning: Connection reset. Retrying...
    default: Warning: Connection aborted. Retrying...
    default: Warning: Connection reset. Retrying...
    default: Warning: Connection aborted. Retrying...
    default:
    default: Vagrant insecure key detected. Vagrant will automatically replace
    default: this with a newly generated keypair for better security.
    default:
    default: Inserting generated public key within guest...
    default: Removing insecure key from the guest if its present...
    default: Key inserted! Disconnecting and reconnecting using new SSH key...
==> default: Machine booted and ready!
Installing Virtualbox Guest Additions 5.2.12 - guest version is 5.1.34
Verifying archive integrity... All good.
Uncompressing VirtualBox 5.2.12 Guest Additions for Linux........
VirtualBox Guest Additions installer
Copying additional installer modules ...
Installing additional modules ...
VirtualBox Guest Additions: Building the VirtualBox Guest Additions kernel modules.
VirtualBox Guest Additions: Starting.
Unmounting Virtualbox Guest Additions ISO from: /mnt
==> default: Checking for guest additions in VM...
==> default: Mounting shared folders...
    default: /vagrant => D:/blockchain/dev
    default: /home/vagrant/exchange => D:/blockchain/dev/exchange

>vagrant ssh
Welcome to Ubuntu 16.04.4 LTS (GNU/Linux 4.4.0-127-generic x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/advantage

  Get cloud support with Ubuntu Advantage Cloud Guest:
    http://www.ubuntu.com/business/services/cloud

0 packages can be updated.
0 updates are security updates.

vagrant@ubuntu-xenial:~$
vagrant@ubuntu-xenial:~$
```
