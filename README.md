Performance Virtualbox vs Parallels 9 for PHP dev
=================================================

TLDR; The vagrant parallels provider is much faster than the virtualbox provider.
Parallels scored in a `ab` benchmark **38.96 vs 17.24 requests per second** using virtualbox.
See [ab benchmark for parallels](https://github.com/adri/vagrant-virtualbox-vs-parallels/blob/comparison/ab_parallels.txt) 
vs [ab benchmark for virtualbox](https://github.com/adri/vagrant-virtualbox-vs-parallels/blob/comparison/ab_virtualbox.txt).

 * Vagrant 1.7.2
 * Virtualbox 4.3.26
 * Parallels Desktop 9.0.24251

## Code

The tests are using a demo installation of the Symfony2 Framework running in development mode including xdebug.
To see the code and run tests yourself use:

 1. `git clone git@github.com:adri/vagrant-virtualbox-vs-parallels.git && cd vagrant-virtualbox-vs-parallels`
 2. `git checkout virtualbox && composer install && vagrant up` and access [vagrant-symfony-virtualbox.dev](http://vagrant-symfony-virtualbox.dev)
 3. `git checkout parallels && composer install && vagrant up` and access [vagrant-symfony-parallels.dev](http://vagrant-symfony-parallels.dev)

## VM Configuration

 - memory: 1024 Mbyte
 - cpu(s): 8
 - php 5.6 with xdebug running
 - nginx

## System

Tests were run on a Macbook Pro 15" late 2013.
