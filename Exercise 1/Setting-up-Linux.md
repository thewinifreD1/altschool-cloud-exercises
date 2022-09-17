Exercise 1
Task:
Setup Ubuntu 20.04 LTS on your local machine using Vagrant
Instruction: 
 Customize your Vagrant file as necessary with private_network set to DHCP.
 Once the machine is up, run ifconfig and share the output in your submission along with your Vagrant file in a folder for this exercise.

STEPS
Download and install a virtual box according to your operating systems
create a new machine in the virtual box (vagrant default)
Download and install Vagrant.
create a vagrant folder inside the documents folder
proceed to run vagrant init on your terminal to initialize the current directory to be a vagrant environment by creating an initial vagrantfile.
Create a vagrant machine ny running the command vagrant up.
A box will be downloaded at this point if you do not already have any.
with the virtual machine running in the background, we run the vagrant ssh command to login or gain entry into the system.
