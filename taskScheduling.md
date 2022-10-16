# Task scheduling in cron
## Crontab file location 
/etc/crontab
## editor preference
Vi is the default editor to edit crontab file<br/>
To change it nano use the command bellow  <br/>
$EDITOR=nano crontab -e

## Parameters
- crontab -l : display content of the cron file<br/>
- crontab -e : edit the crontab file<br/>
- crontab -r : remove<br/>
- crontab -v : display the last time of crontab file edition <br/>

## crontab file Syntax
***** command_to_execute

*[1] *[2] *[3] *[4] *[5] command_to_execute  <br/>

- *[1] : minute (0 - 59) <br/>
- *[2]  : hour (0- 23)   <br/>
- *[3] : day of month (1-31) <br/>
- *[4] : month (1-12) <br/>
- *[5] : day (0-6) (sunday, monday, ...., saturday) <br/>

additinal (non - standard): <br/>
- @yearly	(non-standard)<br/>
- @annually	(non-standard)<br/>
- @monthly	(non-standard)<br/>
- @weekly	(non-standard)<br/>
- @daily	(non-standard)<br/>
- @hourly	(non-standard)<br/>
- @reboot	(non-standard) : after reboot <br/>

## eg
0 0 * * 6 rm /home/manantsoa/tmp/*: remove temp file for user "manantsoa" At 00:00 on Saturday

## Check here
* [Click here to check](https://crontab.guru/)
