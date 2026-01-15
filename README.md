
# NGINX Web Server on EC2 with a Custom Domain via Cloudfare

For this Networking Assignment, The objective was to deploy a web server on an amazon EC2 Instance and host a website via custom Domain (Cloudfare).

I'll go through the steps in order to perfom this action below.


## Step 1: Purchase a Domain

- Navigate to Cloudfare and Sign up

-  Look for a domain that is available; preferably a domain in your name for availablity

- Domains Generally cost around $5 to $10 Range

- Once the domain has been acquired it should look like this

![App Screens](https://raw.githubusercontent.com/SaeedAAli/Networking/main/Screenshots/domainbuy.png)
## Step 2: Launching EC2 Instance

- Select Ubuntu for the Distro
![App Screens](https://raw.githubusercontent.com/SaeedAAli/Networking/main/Screenshots/Screenshot%202026-01-15%20at%2015.25.39.png)
- Keep the Instance type to Default since its recommended
- Create a new key pair (Select RSA and .pem)

Security Groups
- Select SSH
- Select HTTP
- Select HTTPS

![App Screens](https://raw.githubusercontent.com/SaeedAAli/Networking/main/Screenshots/Screenshot%202026-01-15%20at%2015.35.04.png)

Launch the EC2 Instance

## Elastic IP

An Elastic IP is a static public IPv4 address that you can assign to an EC2 instance. Once it’s attached, the instance will always use that fixed address, so you don’t have to deal with changing IPs or reconfiguring anything when the instance restarts.

Beneficial in the Long run

- Select Elastic IP on the Dashbord (Left side of the Screen)
- Once there, Click the Allocate IP Address
![App Screens](https://raw.githubusercontent.com/SaeedAAli/Networking/refs/heads/main/Screenshots/Screenshot%202026-01-15%20at%2016.06.29.png)

- Click the Actions Dropdown menu and click Associate IP Address in order to have a Fixed IPV4 address
![App Screens](https://raw.githubusercontent.com/SaeedAAli/Networking/refs/heads/main/Screenshots/Screenshot%202026-01-15%20at%2016.09.54.png)

- Select Instance for the Resource Type
- For Instance, Choose the EC2 Instance you launched
- Select the EC2 Private IPV4 Address from the dropdown menu
- Select Allocate
![App Screens](https://raw.githubusercontent.com/SaeedAAli/Networking/refs/heads/main/Screenshots/Screenshot%202026-01-15%20at%2016.13.41.png)



## Record Cloudfare

Once your EC2 instance is connected to an Elastic IP, you need to create a DNS Record ()

- Go to CloudFare and Selected Domain
- Add a New DNS Record
- Since its a IPV4 Address it needs to be Type A
- Since this is a NGNIX Project, for the Name write nginx
- For the IPv4 Address, copy the EC2 IPV4 address and paste it on Content box and Click Add Record


![App Screens](https://raw.githubusercontent.com/SaeedAAli/Networking/refs/heads/main/Screenshots/Screenshot%202026-01-15%20at%2016.50.02.png)
## How to Install Nginx

With the .pem key that was downloaded earlier when launching our EC2 Instance, With the .pem key, navigate to the folder where it is located and run this command. 

This command makes the file readable only by the owner

```bash
chmod 400 networking.pem
```

On the Terminal, Use this command to connect to the VM

 ```bash 
 ssh -i ~/Downloads/ubuntu-20.pem ubuntu@54.87.216.219

```
Once connected to the virtual machine Input these commands
```bash
sudo apt update -y
```

Install Nginx

```bash
sudo apt install -y Nginx
```

Start Nginx in the VM

```bash
sudo systemctl start nginx
```

Verify that Nginx Is running

```bash
sudo systemctl status nginx
```


## Last step

Once connecting everything together we can now see the site live by either typing in the IP or website link and voila.

http://nginx.saeedaali.uk/

Screenshots

![App Screens](https://raw.githubusercontent.com/SaeedAAli/Networking/refs/heads/main/Screenshots/Screenshot%202026-01-14%20at%2015.30.05.png)

![App Screens](https://raw.githubusercontent.com/SaeedAAli/Networking/refs/heads/main/Screenshots/nginxmobile.png)

## Things I Learnt
 
 - Relearning myself on knowing how to launch an EC2 Instance
 - Knowing how to use Cloudfare and the beneficial use for it in the near future
 - Educating myself and doing research in order to use NGINX
 - Having the knowledge of Elastic IP, and how useful it will be further down the line.
 

 ## Any Challenges

- When first starting, I launched an Instance in Amazaon linux, but didnt wasn't satisfied with the option of it so swithced to Linux.

- Having to manually install Sudo apt-get before installing any packages on a new Instance


 
