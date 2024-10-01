# ACIT-2420-Assignment-1
ACIT 2420 Lvl 2 Assignment 1

## Introduction
**This is a tutorial that will teach you these main concepts:**
  -How to create SSH keys on your local machine  
  -How to create an Arch Linux Droplet using DigitalOcean  
  -How to use a cloud-init configuration file to automate initial setup tasks  
  -How to connect your SSH keys to your server 

## Step 1:Create SSH keys on your local machine.  

1. **Open Terminal:** Open your computer terminal on whatever operating system you have, for example, Windows PowerShell. For this tutorial, I will be using a Windows operating system.

2. **Generate SSH Key Pair:** To make a new SSH key pair, type in this command:  
  ```ssh-keygen -t ed25519 (You can save your key to a specified file here using: “-f C:\Users\User_name\.ssh\do-key”) -C "youremail@email.com"```

3. **Add SSH Key to DigitalOcean:**
Log into your DigitalOcean account.
Copy your SSH key to the clipboard using this command:  
```Get-Content (your file data here) | Set-Clipboard```

Navigate to the Settings tab on DigitalOcean.
Go to the Security tab and click on ADD SSH KEY.
Paste the contents of your clipboard and give your key an appropriate name.
