
<h1 align="center"> How to install Ubuntu & WSL Version 2 </h1>

## Part 1

- if you have windows 11 then skip the update part and go directly to `Windows features`
### Please follow the instructions line by line carfully:
- before we start the installation part please make sure that you have the latest update for windows 10 in order to make the WSL enviroment to work
- go to your windows search bar and type `system information` to check your OS details and <b> hit ENTER </b>
- look at the Version number as you can see in the image below
 
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  <kbd>![](images/winVersion.jpg)</kbd>

- if it is lower than `19042` then you need to update, if it's the same number then no need to update the windows, we need this because it's required to make the WSL 2 work without any problems

## How to update windows 10 or 11?
- you can go to windows search bar and type `check for updates` and it will redirect you to update the system ( it will take some time to finish so be patient )
- if you are facing some technical issues, download the `update helper tool` from Microsoft from this link <a href="https://go.microsoft.com/fwlink/?LinkID=799445">Windows 10 Update Tool</a>

<hr>

### Now, we need to enable the required services for your machine.
- go to your windows search bar again and type `Turn Windows features on or off` and hit enter, you should see a list of services ( check the image below )


<p align="center"> <kbd><img height="480px" width="600px" src="images/features.jpg" alt="update your windows now"></kbd></p>

### now scroll down and check the boxes for:
* `Virtual Machine Platform`
* `Windows Hypervisor Platform`
* `Windows Subsystem for Linux`
* `Hyper-V` (if exist)

### Not important ( just in case ):
#### if you want to run ubuntu inside a virtual machine ( virtualbox, vmware, etc ) then you need to enable extra service:
* `Containers`


- once you enabled the services click ok and then you are required to RESTART your machine in order to take effect.

<hr>

- RESTART your machine if prompted, it should work for you ( if it does SKIP this part below and start from PowerShell )
- if it didn't work, this means that you need to enable Virtualization (VT-x) in Bios, please note this might be differnt from machine to machine but it's the same proccess
1) Reboot your machine and Press the BIOS Key, try `DEL or F9 or F1 or F2 or or F12 or ESC` several times to boot, OR you can simply search in google "how to boot into BIOS `put your laptop brand name`" and search.
2) Search for the section for CPU configuration Or it could be inside Advanced configurations.
3) Find the Settings for Virtualization or VT-x and hit enter and Change it from DISABLED to ENABLED
4) Exit Your BIOS by pressing F10 and say yes and your machine should be restarted now. `ALL DONE`
 #### Note:
- You can also refer to this vedio for more information about how to enable Virtualization in BIOS <a href="https://www.youtube.com/watch?v=MOuTxfzCvMY">LINK</a>


<hr>
 
# important!!!
 
### Now we need to run several commands using PowerShell because sometimes the virtual machine service is DISABLED by default.
- search for `PowerShell` from windows search bar and open `PowerShell.exe` and run it `as Adminstartor` then run the following commands:

```
Enable-WindowsOptionalFeature -Online -FeatureName VirtualMachinePlatform
```

then run
```
dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart
```
then run
```
dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart
```
- this will enable Virtual Machine Platform for WSL, if it ask for a restart then restart your machine to continue

---------------------------------------------
### Now you need to install windows subsytem Linux ( used to run the Linux environment on windows )
<h3 align="center">  click on the icon below to download it directly</h3>
<p align="center"> <kbd><a href="https://wslstorestorage.blob.core.windows.net/wslblob/wsl_update_x64.msi"> <img height="250px" width="250px" src="images/subsystemLinux.png" alt="WinsubsystemLinux"></a></kbd>
<h3 align="center">windows subsystem linux</h3>
<br>

- after it finishes downloading, open the downloaded file `wsl_update_x64.exe` and follow the setup instructions

---------------------------------------------


# How to install Windows Terminal
- Windows Terminal is an interactive program which allows you to type commands as instructions to control your computer.

<h3 align="center"> Download Windows Terminal by clicking the icon below using Microsoft Store </h3>

<p align="center"> <kbd><a href="https://www.microsoft.com/en-us/p/windows-terminal/9n0dx20hk701?activetab=pivot:overviewtab"> <img height="210px" width="250px" src="images/Windows_Terminal.png" alt="Windows Terminal"></a></kbd>

- after it's succefully installed open the terminal and run this command to set you enviroment to WSL version 2
```
wsl --set-default-version 2
```
- you should get this result `For information on key differences with WSL 2 please visit https://aka.ms/wsl2`

<hr>

# How to install UBUNTU
- Ubuntu for Windows runs and offer Linux developer tools on Windows.

<h3 align="center"> install UBUNTU by clicking the icon below using Microsoft Store </h3>

<p align="center"> <kbd><a href="https://www.microsoft.com/en-us/p/ubuntu/9nblggh4msv6?activetab=pivot:overviewtab"> <img height="230px" width="230px" src="images/ubuntu.png" alt="UBUNTU"></a></kbd>

<hr>

- ONLY! If you are not able to install Ubuntu from the store then open `cmd.exe` and run this command: `wsl.exe --install -d Ubuntu`

## Now follow these instructions:

- Run Ubuntu after it's done from installing then wait ... you will see a confirmation for a successful installation ( check the image below )

&nbsp; &nbsp; &nbsp; &nbsp; <kbd>![](images/ubuntuinstall.png)</kbd>

### Be Carefull about the next step:
- it will ask you to enter a new username: for example "student"
- please note that the password is hidden, so make sure you are setting your password correctly.
- set your password twice to verify it: ( make sure to memorize it ) `hint: use 1234 or 0000`
<br>

- open `Windows Terminal` and run this command ( this to check UBUNTU if it's running with WSL version 2 )
```
wsl -l -v 
``` 
- if you see output like this image then you are good to go
&nbsp; &nbsp; &nbsp; &nbsp; <kbd>![wslLV](images/wslLV.jpg)</kbd>

<hr>

## Now we need to update ubuntu profile and create a backup for some files:

### run these commands line by line in `Ubuntu`:
```
mv ~/.bashrc .bashrc.bak
```
                                                                
```
mv ~/.profile .profile.bak
```

- you should not get any output ( it's just for backup .profile & .bashrc)

<hr>
                                        
- Now run this command in `Ubuntu`
```
curl -s https://raw.githubusercontent.com/omarXzain/LTUC-ASAC/main/.profile >> ~/.profile
```

- Once it finishes, `COMPLETLY CLOSE UBUNTU` then re-open it again. 
- Your Ubuntu appearance should be changed to a different set of colors and cool features
&nbsp;&nbsp;<kbd>![wslLV](images/newubuntu.png)</kbd>

<hr>

# Reset Your Environment
- The changes you just made will take effect every time you re-open your terminal. But right now, we want to see those changes immediately, so let's "source it" by running:
```
source ~/.profile
```
## NOTE:
- You will see an error similar to this <h4>-bash: /home/linuxbrew/.linuxbrew/bin/brew: No such file or directory </h4>
### This is ok for now, you can continue.

`Close UBUNTU and run it again to take effect`

<hr>

# Installing and Updating the Linux App Manager
### you need to get the latest update for ubuntu to make sure that everything will work without any problems.

- OPEN YOUR Ubuntu then copy-paste the commands line by line!
```
sudo apt-get update
```
- put your password, when prompted ( because we are using sudo )
- once it's done, run this command: ( it will take up to ~ <img height="40px" width="30px" src="images/Time.png" alt="sudo apt-get upgrade"> 13 mins )
```
sudo apt-get upgrade
```

- Press `Y` when prompted
- Once it's done, run this
```
sudo apt autoremove 
```
- This will remove any packages that are no longer needed.

- and finally install the `Build Essentials` kit with this command: ( it will take up to ~ <img height="40px" width="30px" src="images/Time.png" alt="update your windows now"> 4 mins )
```
sudo apt-get install build-essential
```
<hr>
<a href="part2.md">MOVE TO PART2</a>
