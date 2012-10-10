OpenStackInstaller
==================

Now with added Folsom! Bring out the gimp! :)

GETTING READY
=============
Create a VM or have available a server with specs similar to below:

        * 2vCPU
        * 2048 Mb Ram
        * 20Gb Hard Disk (/dev/sda)
	* 20Gb Hard Disk (/dev/sdb) for Cinder
        * 2 Nics - eth0 Public, eth1 Private

Experimental: Check out the 'virtualbox' directory for scripts for use with Vagrant and shell scripts for creating VirtualBox instances. TODO: All hard coded IPs, etc - will make more flexible.


HOW TO DO IT
============
1. Clone the OpenStackInstaller

        * $ git clone https://github.com/uksysadmin/OpenStackInstaller.git

2. Check out the 'folsom' branch

        * $ cd OpenStackInstaller
        * $ git checkout folsom

3. Edit 'openstack.conf' file that describes your environment. By default this is defined as follows:

        * eth0 has been defined as 192.168.1.12/16
        * eth1 will be your private interface
        * VLAN Manager will be used (Quantum soon!)
        * Private range defined: 10.0.0.0/24
        * Floating range is 192.168.2.0/24
        * Hardware virtualization is defined (kvm)
	* Installation will partition /dev/sdb and create LVM volume by default

	Note: To disable Cinder creating a partition on /dev/sdb comment out:

	# CINDER_DEVICE=/dev/sdb

	WARNING! Do NOT set this to be your boot disk, e.g. /dev/sda

4. Run the installer:

        * $ ./install-folsom.sh

   This will ask you for the password of the current user to gain sudo privileges

5. Once complete:

        * $ sudo nova-manage service list

        * http://192.168.1.12/horizon


Kevin Jackson http://about.me/kevjackson
