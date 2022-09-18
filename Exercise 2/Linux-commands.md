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

* Running `du *` will calculate the size of each file individually.

## Command 5: netstat
* The `netstat` is a command-line tool that presents an overview of the network connections.

### Example

![netstat](https://user-images.githubusercontent.com/101622646/190912696-43e83583-d42f-494a-88df-805b197d96bb.png)

## Command 6: free
* Running the `free` command provides us with a summary of the total available free space on the computer.
* More so, it also displays the total amount of memory of the Random Access Memory (RAM) and the swap memory on the computer.

## Example

![free](https://user-images.githubusercontent.com/101622646/190912894-b8daf6ab-e9bd-4fa0-b8d5-db989317a0aa.png)


## Command 7: ssh
* The `ssh` command allow users to connect to remote Linux machines.
* You can even log into your account on the remote computer using the command

## Example

![ssh](https://user-images.githubusercontent.com/101622646/190913711-bcc3cd7f-8aba-4409-93c9-8f36fb7d79b0.png)



## Command 8: exit
* The `exit` command does the following: exits the shell in which it is active, close the terminal and even logs out of an ssh remote session.

## Example

![exit](https://user-images.githubusercontent.com/101622646/190913723-1e6775b0-7796-4061-98d7-3a9d037d4f65.png)


## Command 9: date
* The `date` command is used to display the system date and time.
* The`date` command is also used to set date and time of the system. By default the date command displays the date in the time zone on which unix/linux operating system is configured.


## Example


![date](https://user-images.githubusercontent.com/101622646/190913954-298c25f2-ad7e-4bd2-9f0b-7ec6e172361f.png)

- [ ] other ways to format the date and time
* %D – Display date as mm/dd/yy.
* %Y – Year (e.g., 2020)
* %m – Month (01-12)
* %B – Long month name (e.g., November)
* %b – Short month name (e.g., Nov)
* %d – Day of month (e.g., 01)
* %j – Day of year (001-366)
* %u – Day of week (1-7)

## Command 10: whatis
* `whatis` prints a single-line description of any other command, making it a helpful reference


## Example

![whatis](https://user-images.githubusercontent.com/101622646/190915702-46323aa8-a1c8-456a-9ab1-d191a64c5580.png)




