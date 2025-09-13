# Git Commands:
```
  git fetch #gets the most recent info on the most recent changes to the repository. Doesn't affect your version.
  git status #tells you the difference between your version and the version you have info on.
  git pull #updates your code to the same as the github repository.
```
# Git Bash Commands
```
  echo - Output the parameters of the command
  cd - Change directory
  mkdir - Make directory
  rmdir - Remove directory
  rm - Remove file(s)
  mv - Move file(s)
  cp - Copy files
  ls - List files
  curl - Command line client URL browser
  grep - Regular expression search
  find - Find files
  top - View running processes with CPU and memory usage
  df - View disk statistics
  cat - Output the contents of a file
  less - Interactively output the contents of a file
  wc - Count the words in a file
  ps - View the currently running processes
  kill - Kill a currently running process
  sudo - Execute a command as a super user (admin)
  ssh - Create a secure shell on a remote computer
  scp - Securely copy files to a remote computer
  history - Show the history of commands
  ping - Check if a website is up
  tracert - Trace the connections to a website
  dig - Show the DNS information for a domain
  man - Look up a command in the manual
```
# Chaining Git Bash Commands
```
  | - Take the output from the command on the left and pipe, or pass, it to the command on the right
  > - Redirect output to a file. Overwrites the file if it exists
  >> - Redirect output to a file. Appends if the file exists
```
## Example:
This finds all files that were created in November, using grep to find them \("Global Regular Expression Print\), and count how many of them there are.
`ls -l | grep ' Nov ' | wc -l`

# Git Bash Console Shortcuts
```
CTRL-R - Use type ahead to find previous commands
CTRL-C - Kill the currently running command
```
# How to SSH into a server. 
```
ssh -i [key pair file] ubuntu@[ip address]
```
Server Public IP: 98.87.60.92

## How to Keep the Same Public IP Address
"You have two choices in order to keep the same public IP address:

Never stop your server.
Assign an elastic IP address to your server so that it keeps the same address even if you stop it.
Your first elastic IP address is free. However, the catch is that it is only free while the server instance it is assigned to is running. While your server is not running you are charged $0.005/hr. This is the same cost for running a t3.nano server instance. So if you assign an elastic IP address, you don't save any money unless you are running a more powerful instance, and are stopping your instance when you, or the TAs, don't need it.

We would suggest that you do both options. Keep your server running and associate an elastic IP. That way if you do need to reboot it for some reason, you will still keep the same IP address, and it doesn't cost you anything more either way."

"Note that your elastic IP address is allocated until you release it, not until you terminate your instance. So make sure you release it when you no longer need it. Otherwise you will get a nasty $3 bill every month."

I did both.
