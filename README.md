# Jetson Xavier Installation and Configuration

## 1. Preparation
### 1) A computer with Ubuntu 16.04 or Ubuntu 18.04
### 2) Hard drive: SSD NVMe
### 3) Network cable, keyboard, mouse, screen, screwdriver

## 2. OS Installation on Jetson Xavier
### 1) Download SDKManager on your computer: https://developer.nvidia.com/embedded/downloads#?search=Jetson%20AGX%20Xavier, and follow its instructions.
### 2) Use SDKManager to install OS for Jetson Xavier
#### i.   Due to specification, wire Jetson Xavier and computer
#### ii.  Open NVIDIA account, MUST join developer grogram
#### iii. Use SDKManager, follow the instructions: https://docs.nvidia.com/sdk-manager/install-with-sdkm-jetson/index.html; in step 3, Target Components, only check Jetson OS, do Jetson SDK Components later

## 3. SSD NVMe Installation
### 1) See https://www.youtube.com/watch?v=x0TBTYw7HKs
### 2) Transfer OS to the hard drive, on Jetson Xavier:
#### i.   In /etc/systemd/system/, create setssdroot.service
#### ii.  In /sbin/, create setssdroot.sh
#### iii. In /etc/, create setssdroot.conf, no content in the file
#### iv,  open terminal, 
#### sudo mount /dev/nvme0n1p1 /mnt
#### sudo rsync -aAXv / --exclude={"/dev/*","/proc/*","/sys/*","/tmp/*","/run/*","/mnt/*","/media/*","/lost+found"} /mnt

