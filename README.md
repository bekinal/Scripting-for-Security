<h1>Scripting for Security</h1>

<h2>Description</h2>
Project consists of designing a script that checks for open ports listening on the machine. Crontab is then used to run the script every five minutes.
<br />


<h2>Tools & Environemts Used</h2>

- <b>VirtualBox</b>
- <b>Debian Environment</b>
- <b>Terminal</b>

<h2>Writing a Script that Checks for Listening Ports:</h2>
A script will be written that checks for listening ports and notifies when new ports are added to the listening list.
<br />
<br />
On the Debian machine, a new file named CheckPortListen.sh is created under the root user's home directory:<br/>
<img src="https://imagizer.imageshack.com/img923/4186/iefqBT.png"
<br />
<br />
A new variable is defined that will be used later to save the open ports report:<br/>
<img src="https://imagizer.imageshack.com/img924/929/3xkGD8.png"
<br />
<br />
An if-then statement is written that uses netstat and grep to create a new log file in the previously defined /var/log/openPorts path:<br/>
<img src="https://imagizer.imageshack.com/img922/3756/Yv32ld.png"
<br />
<br />
Two new variables are defined that use md5 to hash the original log file and current netstat log. Then cat, grep, and echo are used to filter and print only the required information and hashes:<br/>
<img src="https://imagizer.imageshack.com/img922/4941/wdjASR.png"
<br />
<br />
An if-then statement is written that compares the two variables created previously, then prints whether or not the list of open ports changed:<br/>
<img src="https://imagizer.imageshack.com/img924/3986/flqqSR.png"
<br />
<br />
The script is saved and given execute authority:<br/>
<img src="https://imagizer.imageshack.com/img922/2784/Wv2EQ5.png"
<br />
<br />
The script is run for the first time to build the baseline:<br/>
<img src="https://imagizer.imageshack.com/img922/6048/Y33p2E.png"
<br />
<br />
A port listener is created with the nc tool:<br/>
<img src="https://imagizer.imageshack.com/img922/9695/cYI1zD.png"
<br />
<br />
The script is rerun. This time, the output changes due to the new listening port:<br/>
<img src="https://imagizer.imageshack.com/img923/6416/xQ7X0k.png"
<br />
<br />

<h2>Combining Crontab with the Script:</h2>
The Crontab tool is installed by first using apt update:<br/>
<img src="https://imagizer.imageshack.com/img922/864/5i75Rz.png"
<br />
<br />
Apt install Crontab is executed:<br/>
<img src="https://imagizer.imageshack.com/img923/9764/Idwxoa.png"
<br />
<br />
Crontab -e is used and the nano text editor is selected:<br/>
<img src="https://imagizer.imageshack.com/img924/690/QfckO0.png"
<br />
<br />
The following line is added at the bottom of the script to ensure that CheckPortListen.sh will run every five minutes:<br/>
<img src="https://imagizer.imageshack.com/img924/9273/Yv7euh.png"
<br />
<br />

<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
