# Local Development Server

This repo will help you bootstrap a local development server.  It's pretty swell. 

## What do I get?

I've loaded this machine with the most common tools that I've found that I need for most of my web projects.  You might
find that you don't use all of them - and that's ok.  Just keep in mind, if you're going to be developing something for
a production website as well, you really should trim down your development box to be identical to what's going to be
in production.  This box is *not recommended for production* deployments.

So, in here, in no particular order, are the highlights of what you get.

- After you ssh to the box, you're put directly in the `/vagrant` folder and not left in your home directory 
- Git is installed
- Apache is installed, default site is removed, your site is added as a vhost, and mod_rewrite is enabled.  (Your folder
location is `/vagrant/web/your-site` with your docroot being `/vagrant/web/your-site/public`
- MySQL is installed, root password is still blank - this installation is pretty insecure
- PHP is installed to the latest version supported by Apt and Ubuntu at time of installation (may not be bleeding edge)
- PHP modules including imagick, gd, sqlite, curl and more
- NodeJS / NPM

In the `config.yml` file, there are other conditionals that will allow you to customize the following items:

- Swap file for Ubuntu (disabled by default)
- Composer for managing PHP dependencies is installed (enabled by default)
- API Doc for documenting APIs (enabled by default)
- JS Doc for documenting Javascript (enabled by default)
- WordPress Latest Version (and wp-cli) (disabled by default)
- Drupal 8 (and drupal console) (disabled by default)
- Joomla 3.5 (disabled by default)

## Installation

There are two ways to use this box.  

### Just for local development

First, clone this to a location you desire.

`git clone git@github.com:aaronsaray/local-dev-server.git`

Then, check out or create your own repo in the `web/public` folder (or you may want to delete the public folder first, and create it later)

`cd web/public && git init`

### Use as part of your project.

You can use this as a basis or launch pad for your own project.  Remember, this is *not recommended* for production boxes. 
However, if you want to distribute your project with a virtual machine, you can download this an integrate it into your project.

First, clone this to your project directory.

`mkdir my-project && cd my-project && git clone git@github.com:aaronsaray/local-dev-server.git .`

Now, the easiest way to take care of this is to just git rid of my git history and create your own git project to begin with.

`rm -rf .git && git init`

`git add . && git commit -a -m "First commit using github.com/aaronsaray/local-dev-server for a local server."`

Then you may want to add your own remote (yeah you probably want to do this).

## Configuration

To make the configuration of this local dev server easier, all configuration options have been included in a YAML
file in the root of this project.  There you'll find the following configuration options (with comments - of course!)

`hostname` This is the host name for your virtual machine.  It is also added to your /etc/hosts file.  Finally, this
is also used in the VirtualBox registry (which isn't really that exciting until you were to look at something like the 
VirtualBox GUI and see very nicely labeled vagrant boxes - wow!)

`private_network_ip` Currently this box only allows a NAT + private network configuration.  Here you must specify 
an IP address that is private and available.  This is used when the hosts file is edited as well.

`available_ram_mb` This is the RAM amount that is specified for the VirtualBox virtual machine.  I've picked 2G of RAM
for a base box.  You may want to raise or lower this depending on your needs.

## Usage

`cd directory-of-project && vagrant up`

It's that easy!  Now you have a nice local dev server.  There was much rejoicing.

## Requirements

- Vagrant 1.8+
- vagrant-hostsupdater vagrant plugin
- VirtualBox 4.x+
- Ansible 1.9+

## Todo

- Outgoing email using your SMTP authentication
- XDebug for PHP

## Contributors

- [Aaron Saray](https://github.com/aaronsaray)
