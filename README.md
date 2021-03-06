Vagrant LAMP
============

Want to test a new web app but don't want to affect your current Apache / MySQL / PHP system?
Applications like MAMP are great, but they don't make it easy to maintain multiple, separate
web roots.

If you find yourself needing quick to configure web stack, but also one that is customizable try this Vagrant project

Vagrant allows for Virtual Machines to be quickly setup, and easy to use.

And this project aims to make it very easy to spinup a complete LAMP stack in a matter of minutes.

Requirements
------------
* VirtualBox <http://www.virtualbox.com>
* Vagrant <http://www.vagrantup.com>
* Git <http://git-scm.com/>

Usage
-----

### Startup
	$ git clone http://www.github.com/bullgare/vagrant-lamp
	$ cd vagrant-lamp
	$ vagrant up

That is pretty simple.

### Connecting

#### Apache
The Apache server is available at <http://localhost:8888>

#### MySQL
Externally the MySQL server is available at port 8889, and when running on the VM it is available as a socket or at port 3306 as usual.
Username: root
Password: root

Technical Details
-----------------
* Ubuntu 14.04 64-bit
* Apache 2
* PHP 5.5
* MySQL 5.5

We are using the base Ubuntu 14.04 box from Vagrant. If you don't already have it downloaded
the Vagrantfile has been configured to do it for you. This only has to be done once
for each account on your host computer.

The web root is located in the project directory at `htdocs` and you can install your files there

And like any other vagrant file you have SSH access with

	$ vagrant ssh
	
### Changing sync directory to custom one
#### Vagrantfile
Append this to file

	config.vm.synced_folder "/Users/bullgare/projects/[your_path_on_host_machine]/","/[dir_name_on_vagrant]"

#### provision.sh
Change apache's settings with this

	DocumentRoot /[dir_name_on_vagrant_from_Vagrantfile]
	<Directory /[dir_name_on_vagrant_from_Vagrantfile]>

