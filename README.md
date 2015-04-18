Vagrant: Virtualbox vs Parallels 9 Performance for PHP development
===================================================================

TLDR; The vagrant parallels provider is much faster than the virtualbox provider.
Parallels scored in a `ab` benchmark **38.96 vs 17.24 requests per second** using virtualbox.
See [ab benchmark for parallels]() 
vs [ab benchmark for virtualbox]().

Using Vagrant 1.7.2:
 
| Provider      | Version           | Request/Sec  |
| ------------- |:-------------| -----:|
| virtualbox     | Virtualbox 4.3.26 | [17.24](https://github.com/adri/vagrant-virtualbox-vs-parallels/blob/comparison/ab_virtualbox.txt) |
| parallels      | Parallels Desktop 9.0.24251      |  [38.96](https://github.com/adri/vagrant-virtualbox-vs-parallels/blob/comparison/ab_parallels_9.txt) |
| parallels    | Parallels Desktop 10.2.0 (28956)     |  [44.41](https://github.com/adri/vagrant-virtualbox-vs-parallels/blob/comparison/ab_parallels_10.txt) |



## Code

The tests are using a demo installation of the Symfony2 Framework running in development mode including xdebug.
To see the code and run tests yourself use:

 1. `git clone git@github.com:adri/vagrant-virtualbox-vs-parallels.git && cd vagrant-virtualbox-vs-parallels`
 2. `git checkout virtualbox && composer install && vagrant up --provider virtualbox` and access [vagrant-symfony-virtualbox.dev](http://vagrant-symfony-virtualbox.dev)
 3. `git checkout parallels && composer install && vagrant up --provider parallels` and access [vagrant-symfony-parallels.dev](http://vagrant-symfony-parallels.dev)

[View changes between the two setups](https://github.com/adri/vagrant-virtualbox-vs-parallels/compare/virtualbox...parallels).

## VM Configuration

 - memory: 1024 Mbyte
 - cpu(s): 8
 - php 5.6 with xdebug running
 - nginx

## System

Tests were run on a Macbook Pro 15" late 2013.
