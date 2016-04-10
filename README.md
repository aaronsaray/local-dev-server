# Local Development Server

This repo will help you bootstrap a local development server.  It's pretty swell. 

## Installation

Todo.

## Configuration

To make the configuration of this local dev server easier, all configuration options have been included in a YAML
file in the root of this project.  There you'll find the following configuration options (with comments - of course!)

**hostname** This is the host name for your virtual machine.  It is also added to your /etc/hosts file.  Finally, this
is also used in the VirtualBox registry (which isn't really that exciting until you were to look at something like the 
VirtualBox GUI and see very nicely labeled vagrant boxes - wow!)

**private_network_ip** Currently this box only allows a NAT + private network configuration.  Here you must specify 
an IP address that is private and available.  This is used when the hosts file is edited as well.

**available_ram_mb** This is the RAM amount that is specified for the VirtualBox virtual machine.  I've picked 2G of RAM
for a base box.  You may want to raise or lower this depending on your needs.

## Usage

` cd directory-of-project && vagrant up`

It's that easy!  Now you have a nice local dev server.  There was much rejoicing.

## Requirements

- Vagrant 1.8+
- vagrant-hostsupdater vagrant plugin
- VirtualBox 4.x+
- Ansible 1.9+

## Contributors

- [Aaron Saray](https://github.com/aaronsaray)
