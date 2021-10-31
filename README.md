# BasicLinuxCommand
##  File Commands
- ls :   Directory listing
- ls -al  : Formatted listing with hidden files
- ls -lt : Sorting the Formatted listing by time modification
- cd dir : Change directory to dir
- cd Change : to home directory
- pwd : Show current working directory
- mkdir dir : Creating a directory dir
- cat > file : Places the standard input into the file
- more file : Output the contents of the file
- head file :  Output the first 10 lines of the file
- tail file :  Output the last 10 lines of the file
- tail -f file :  Output the contents of file as it grows,starting with last 10 lines
- touch file :  Create or update file
- rm file :  Deleting the file
- rm -r dir :  Deleting the directory
- rm -f file :  Force to remove the file
- rm -rf dir :  Force to remove the directory dir
- cp file1 file2 :  Copy the contents of file1 to file2
- cp -r dir1 dir2 :  Copy dir1 to dir2;create dir2 if not present
- mv file1 file2 :  Rename or move file1 to file2,if file2 is an existingdirectory
- ln -s file link :  Create symbolic link link to file

## Process management
- ps : To display the currently working processes
- top : Display all running process
- kill pid : Kill the process with given pid
- killall proc : Kill all the process named proc
-  pkill pattern : Will kill all processes matching the pattern
- bg : List stopped or background jobs,resume a stopped job in the background
- fg : Brings the most recent job to foreground
- fg n : Brings job n to the foreground

