# Some vagrant basebox definitions

These are some variations on the initial baseboxes provided by vagrant basebox

## Available boxes

### 1. debian6

Debian6 with the debian6 backports repo added and some packages removed:

 - there's no chef
 - there's no gem from source
 - puppet is installed from debian/backports (v 2.7.x)

### 2. debian6-puppet3x

Debian6 with the debian6 backports and puppetlabs repo added, some packages removed:

 - there's no chef
 - there's no gem from source
 - puppet is installed from the puppetlabs repository (v. 3.0.1)

## How to use

### Pre-requirements

 - vagrant: https://github.com/mitchellh/vagrant
 - veewee: https://github.com/jedi4ever/veewee

### Steps

 1. Build the basebox:
  
  `vagrant basebox build [basebox-name]`

 2. Export the basebox.

  `vagrant basebox export [basebox-name]`
    
 3. Import the basbox to your vagrant catalog.

  `vagrant box add '[basebox-name]' '[basebox-name].box'`

 4. (optional) remove any .box file leftover.

   `rm [basebox-name].box`
   
 5. Include your basebox in your Vagrantfile:


    Vagrant::Config.run do |config|
        config.vm.define :blogserver do |blogserver_config|
        blogserver_config.vm.box = "[basebox-name]"
        blogserver_config.vm.provision :puppet do |puppet|`
        .
        .
        .
        

## Notes 

 - vagrant basebox validate won't be successfull as the boxes don't include the chef packages.
 - The basebox are usually based on the default templates included in veewee
