
## Exercise 2
### Task:
* Research online for 10 more linux commands aside the ones already mentioned in this module. Submit using your altschool-cloud-exercises project, explaining what each command is used for with examples of how to use each and example screenshots of using each of them.
## Instruction:
- [ ] Submit your work in a folder for this exercise in your altschool-cloud-exercises project. You will need to learn how to embed images in markdown files.


## Command 1: History
* Everytime a command is run, it is memorized in the history
* you can display all the history using: `history`


### Example

![history](https://user-images.githubusercontent.com/101622646/190896218-1feea214-71d0-477c-b1fb-64155ef8a989.png)


## Command 2: Ping
* this command pings a specific network host, on the local network or on the internet.
* you use it with the syntax `ping <host>` where `<host>` could be a domain name, or an ip address.
* Example: `ping` `altschoolafrica.com`


## Example

![ping](https://user-images.githubusercontent.com/101622646/190896297-84612165-8876-41d2-8699-cc15e8d6fc61.png)

* this command sends a request to the server and the server returns a response.
* `ping` keep sending a request every second, by default and will keep running until you stop it with `ctrl-C`


## Command 3: who
* The `who` command displays the users logged into the system
* Unless you are using a server multiple people have access to, chances are you will be the only user logged in, multiple time


## Example

![who](https://user-images.githubusercontent.com/101622646/190896556-20e57306-81f5-4c61-9262-8cdaa8276bbd.png)

* Why multiple times? Because each shell opened will count as an access


## Command 4: du
* The `du` command will calculate the size of a directory as a whole
* The number displayed is a value expressed in bytes.

## Example

![du](https://user-images.githubusercontent.com/101622646/190896697-410cfe38-e8a3-4199-ba40-5b48eb0e4337.png)

* Running `du *` will calculate the size of each file individually

