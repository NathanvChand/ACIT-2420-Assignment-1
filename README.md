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

## Step 2: Create a Droplet Running Arch Linux Using the DigitalOcean Web Console and Adding a Custom Arch Linux Image  
1.**Create Droplet:**  
On the DigitalOcean homepage, click the big green Create button and select Droplet from the drop-down list.  

2.**Choose Region:** Select the region closest to you for a better connection.  

3.**Get Arch Linux Image:** Download your Arch Linux image from here.  
https://gitlab.archlinux.org/archlinux/arch-boxes/-/packages/

4.**Add Custom Image:**  
Click on the Custom Images button and upload your Arch Linux image.
Choose the basic size for your image.  

5.**Pick CPU Option:** Select a CPU option that fits your needs. For this tutorial, I am choosing the AMD premium option for $7.  

6.**Choose SSH Key:** Select SSH KEY for your authentication method and choose your key.  

7.**Set Hostname:** Change your hostname to something appropriate.  

## Step 3: Use a Cloud-Init Configuration File to Automate Initial Setup Tasks  
1.**Install Cloud-Init:** you'll need to install cloud-init onto your machine. You can do this by using this code:  

```sudo pacman -S cloud-init```

2.**Create Cloud-Init Configuration File:**  
Open a plain text editor and input your configuration. Save it as cloud-init.yaml. Your file should look similar to this:  

```
#cloud-config

# Create new user
users:
  - name: newuser
    sudo: ALL=(ALL) NOPASSWD:ALL
    groups: users
    shell: /bin/bash
    ssh_authorized_keys:
      - ssh-rsa AAAAB3NzaC1yc2EAAAABIwAAAQEAr...your-public-key... user@host


# Install initial packages
packages:
  - git  
  - vim  

# Disable root access using SSH  
ssh_pwauth: false  
disable_root: true
```

3.**Add Initialization Script:**
Go back to your DigitalOcean droplet setup.  

Scroll down to the Advanced Options drop-down tab.  

Click Add Initialization scripts (free) and paste the content from your cloud-init.yaml file into the user data section.  

## Step 4: Connect to Your Server Using Your SSH Keys  
1. **Get Droplet IP Address:**  
Go to the Droplets tab on the left side of DigitalOcean and select your droplet.

Copy its IP address.  

2. **SSH into Your Droplet:**
   
```ssh (-i “your file here”) Username@(Your I.P. here)```  

Finally, you’ve finished the tutorial!  

## Sources  

https://docs.digitalocean.com/products/droplets/how-to/automate-setup-with-cloud-init/  

https://docs.digitalocean.com/products/app-platform/how-to/deploy-from-container-images/  

https://www.digitalocean.com/community/tutorials/how-to-deploy-a-react-application-to-digitalocean-app-platform  

https://www.howtogeek.com/devops/how-to-deploy-your-own-container-to-digitaloceans-app-platform/  

https://docs.digitalocean.com/products/kubernetes/getting-started/deploy-image-to-cluster/  

https://docs.digitalocean.com/products/droplets/how-to/provide-user-data/  

https://www.digitalocean.com/blog/automating-application-deployments-with-user-data  

