# WSL-for-windows10
To Install Windows Sub-System for Linux on Windows10<br>
Best suited for developers who need Linux shell on windows system<p>
Step 1:  Enable WSL2: <br>
https://docs.microsoft.com/en-us/windows/wsl/install-win10<br>
GoTo  PowerShell & Execute the following commands :<br>
  1. Install WSL on windows<br>
  command : <b>wsl --install</b><br>
  By default, the installed Linux distribution will be Ubuntu. This can be changed using the -d flag.<br>
  command : <b>wsl --install -d "Distribution-Name"</b>. Replace <Distribution Name> with the name of the distribution you would like to install.<p>

2. Check which version of WSL you are running<br>
  command : <b> wsl -l -v </b><br>
  To set the default version to WSL 1 or WSL 2 , use this <br>
  command:<b> wsl --set-default-version <Version#></b>, replacing <Version#> with either 1 or 2.<p>
  
  3. Configure Sudo access for non-root user<br>
  command : <b>grep -E 'sudo|wheel' /etc/group </b><br>
  (should get: sudo:27:myusername  Else run: <b>usermod -aG sudo myusername</b>)<br>
  command : <b>sudo grep -E '%sudo|%wheel' /etc/sudoers  </b><br>
(should get: %wheel ALL=(ALL) ALL else edit and uncomment)<br>
 command :  <b>su myusername</b><br>
 command : <b>sudo -v</b><br>
(should get: no errors)<p>
  
  4. Update/upgrade packages(test network) <br>
  <b>sudo apt update && sudo apt upgrade </b><br>
(should get: no errors, else run below 2 commands) <br>
  <b>echo -e "[network]\ngenerateResolvConf = false" | sudo tee -a /etc/wsl.conf </b><br>
  command : <b>sudo unlink /etc/resolv.conf  </b><br>
  command : <b>echo nameserver 1.1.1.1 | sudo tee /etc/resolv.conf  </b> <br>
  (------try above command, if still errors, try below 4 commands------) <br>
  command : <b>netsh winsock reset </b><br>
  command : <b>netsh int ip reset all </b> <br>
  command : <b>netsh winhttp reset proxy  </b><br>
  command : <b>ipconfig /flushdns </b><br>
  command : <b>reboot </b> <p>
  
  5. Start using WSL after Reboot, In Powershell<br>
  command :  <b> wsl</b><br>
 This will start the Linux shell & you will see the Memory utilisation increase by 2 GB <br>
  command:  <b> wsl -l --running </b><br>
  This will give the list of distributtions running <br>
  command:  <b> ifconfig </b><br>
  If this command works and returns network adapters that means linux is up. <br>
  command:  <b> wsl --shutdown </b><br>
  This will terminate the running linux shell and utilised memory will be released
  </br>
  <b><u> Please Follow Next Step from another Repo - "Brew Package Manager setup for WSL" </u></b>
  <p><p>
    I hope this guidelines have helped you.
    <br>
    Happy coding
  
