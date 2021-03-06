# Parrot-ar-drone
# Getting started - get a connection to the drone and run some commands
# The following assumes you have access to a Parrot AR Drone 2.0

NB I wasnt able to run the ps drone API and connect to the drone from my Windows machine and the authors instructions recommend a linux based machine; 
hence I started off by creating a linux VM...

#Step 1: Create a linux virtual machine to connect with the drone

I used Hyper-V on Windows and Ubuntu 18.04.3 LTS

Once created, I did the following:

- Updated the VM
- Installed/upgraded pip - sudo pip3 install --upgrade pip
- Installed virtualenv - sudo pip3 install virtualenv
- Installed git - sudo apt install git

It's good practice to work in an isolated virtual environment
- Create a virtual env
- Activate the virtualenv
- Install opencv-python (needed later on) 
	- in Python 2 use "sudo apt install python-opencv" NB this isnt in the venv"
 	- Open a python terminal and check the version
	 	- import cv2 as cv
	 	- print cv.__version__ # shoud say 3.2.0

- Pulled down the repo into the virtualenv git clone https://github.com/kshaba01/parrot-ar-drone.git


#Step 2: Edit the network settings to allow the VM to connect to the drone 

Switch the drone on. 

The drone (like all drones) has an embedded hotspot. Connect your machine to this hotspot. 

By default, VM's have separate IPs to their host, so we need to change the IP on the VM to match the host. 

You will need to edit the network settings of the VM to ensure it has the same IP as the host.

In HyperV, create a new "external" switch Action -> Virtual Switch Manager 

Once this is done, connect to your VM and manually set the following (via network interface settings, IPv4 tab):
IPv4 address: 192.168.1.2
Netmask: 255.255.255.0
Gateway: 192.168.1.1 

Switch the connection off and on (by toggling the icon to reset)

Run "ip addr" in the terminal to cnfirm the new ip is indeed what you have set it to. 

#Step 3: Test the connection to the drone

activate the virtualenv
Launch python - Python 3

Run the following commands:
#import time
#import ps_drone3 as ps_drone
#drone = ps_drone.Drone()       # Initializes the PS-Drone-API
#drone.startup()                # Connects to the drone and starts subprocesses
#drone.takeoff()                # Drone starts
#drone.land()                   # Drone lands

Alternatively run the script "firstTry.py". If doing this, be sure the drone is an open environment i.e. large room. 


