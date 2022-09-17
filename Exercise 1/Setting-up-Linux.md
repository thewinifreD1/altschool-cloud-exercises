## Exercise 1
### Task:
* Setup Ubuntu 20.04 LTS on your local machine using Vagrant
### Instruction: 
- [ ] Customize your Vagrant file as necessary with private_network set to DHCP.
 - [ ] Once the machine is up, run ifconfig and share the output in your submission along with your Vagrant file in a folder for this exercise.

## STEPS
* I downloaded and installed a virtualbox according to my operating system

* I created a new machine in the virtualbox (vagrant default)

* I downloaded and installed the Vagrant version right for system

* I created a vagrant folder/directory.

* I proceeded to run `vagrant init` on my terminal to initialize the current directory to be a vagrant environment by creating an initial vagrantfile.

* I created a vagrant machine by running the command `vagrant up`.

* A box will be downloaded at this point if you do not already have any 'ubuntu/focal64'.

* With the virtual machine running in the background, i run the `vagrant ssh` command to login or gain entry into the system.

* Inorder to run `ifconfig` to be able to view my ip address, i install net-tools

* finally, i input the `ifconfig` command, run it and view my machine's ip address.


## ifconfig

![ifconfig](https://user-images.githubusercontent.com/101622646/190879497-9ab8ba32-a40e-4647-9913-8e17a18ea4fa.png)






