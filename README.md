# Basis-Template Projekt

Getting Started
---
new base development stack for frontend projects

Vagrant
---
Vagrant is optional. Using Vagrant you can checkout and setup the project with a few steps and all requirements are 
installed scoped for the project

If you are not using Vagrant, you need to manually install all requirements from the requirements list further down 
this doc.



Requirements
---
- (optional) Vagrant by HashiCorp - https://www.vagrantup.com/
- (optional) VirtualBox by Oracle - https://www.virtualbox.org/
- node -> nodejs / npm
- yarn (preferred over the default npm installer but not necessary)

If you want to run the project in a virtual box and provision it with vagrant, those two requirements are mandatory.



# initializing the project
clone the project via git

using Vagrant
-
0) make sure, Vagrant and VirtualBox are installed
1) Go to the root of the project and run
    * $ vagrant up
2) Once that task is through, connect via ssh to the VM and navigate to the vagrant directory
    * $ vagrant ssh
    * $ cd /vagrant
3) Run the yarn installer () to build the project by installing all dependencies from the package.json
    * $ yarn install

without Vagrant
-
If you are not using Vagrant, you can skip the first 3 steps and directly run the "yarn install" command from the 
projects root directory.

# running the project for development
To start the project for development, all you need to to is running "yarn start". If you need to run the project 
without an internet connection, you can run "yarn start_offline" to skip the nps security check.