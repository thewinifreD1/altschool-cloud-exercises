## Exercise 7

### Task:

* Create a bash script to run at every hour, saving system memory (RAM) usage to a specified file and at midnight it sends the content of the file to a specified email address, then starts over for the new day.

### Instruction:

- [ ] Submit the content of your script, cronjob and a sample of the email sent, all in the folder for this exercise.



## Creating the bash script
* I used the command `nano name-of-script` to create a new bash script
* I wrote inside the file i created variables for, location of the log files, the email the log files would be sent to and a sendtime.
* Then i wrote a function that would check if a logfile exists in that location and to remove it if it does. then to create a new logfile in that location after that.
* Then i wrote another statement carrying the email subject,body and the attachment that would be sent  

## Script Content
![Bash Script](https://user-images.githubusercontent.com/101622646/196383786-9ce601cc-99c8-4067-9990-7cf858bada8b.png)



## Scheduling cronjobs
* I ensured i had cron installed
* then i used the command `crontab -e` to edit the cron tab and schedule a job for every of of everyday


## cronjob
![cronjob](https://user-images.githubusercontent.com/101622646/196384723-80626c0e-cc4f-4874-a9a2-8c823397cb4a.png)

## Emails
* I installed mailutils and ssmtp 
* i configured ssmtp with the command `sudo nano /etc/ssmtp/ssmtp.conf` and added my email address, Authuser and Authpass, mailhub and others.

## sample of the email sent

