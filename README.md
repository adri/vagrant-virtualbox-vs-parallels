Vagrant: Virtualbox vs Parallels Performance for PHP development
===================================================================

> I've tried to compare the providers fairly. Of course these benchmarks are specific to my [machine and environment](#system). So please don't take them as set in stone. 

TLDR; The vagrant parallels provider is much faster than the virtualbox provider.

Using Vagrant 1.7.2:
 
| Provider      | Version           | Request/Sec  | Notes |
| ------------- |:------------------| ------------:|:------|
| virtualbox     | Virtualbox 4.3.26 | [17.24](https://github.com/adri/vagrant-virtualbox-vs-parallels/blob/comparison/ab_virtualbox.txt) |nginx 1.6.2 |
| parallels      | Parallels Desktop 9.0.24251      |  [38.96](https://github.com/adri/vagrant-virtualbox-vs-parallels/blob/comparison/ab_parallels_9.txt) |nginx 1.6.2 |
| parallels    | Parallels Desktop 10.2.0 (28956)     |  [44.41](https://github.com/adri/vagrant-virtualbox-vs-parallels/blob/comparison/ab_parallels_10.txt) | nginx 1.6.2 |
| parallels    | Parallels Desktop 11.0.1 (31277)     |  [47.65](https://github.com/adri/vagrant-virtualbox-vs-parallels/blob/comparison/ab_parallels_11.txt) | nginx 1.8.0 (*) |

(*) coudn't get nginx 1.6.2 installed on a current ubuntu trusty, can't find the package anymore.

## Code

The tests are using a demo installation of the Symfony2 Framework running in development mode including xdebug.
To see the code and run tests yourself use:

 1. `git clone git@github.com:adri/vagrant-virtualbox-vs-parallels.git && cd vagrant-virtualbox-vs-parallels`
 2. `git checkout virtualbox && composer install && vagrant up --provider virtualbox` and access [vagrant-symfony-virtualbox.dev](http://vagrant-symfony-virtualbox.dev)
 3. `git checkout parallels && composer install && vagrant up --provider parallels` and access [vagrant-symfony-parallels.dev](http://vagrant-symfony-parallels.dev)

[View changes between the two setups](https://github.com/adri/vagrant-virtualbox-vs-parallels/compare/virtualbox...parallels).

## What is benchmarked

The login page in the Symfony2 demo installation is benchmarked with Apache benchmark. 

<img width="600" alt="sf-demo-page" src="https://cloud.githubusercontent.com/assets/133832/10116866/1e0f8488-6443-11e5-81b4-9919ffe0a068.png">


## VM Configuration

 - memory: 1024 Mbyte
 - cpu(s): 8
 - php 5.6 with xdebug and opcode cache
 - php fpm
 - nginx

## System

Tests were run on a **Macbook Pro 15" late 2013** 

 * 2.0GHz
 * 16 GB memory
 * 250 GB SSD
 * OSX 10.10
