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
#### iii. In /etc/, create setssdroot.conf, leave it empty
#### iv,  open terminal, 
```sudo mount /dev/nvme0n1p1 /mnt```

```sudo rsync -aAXv / --exclude={"/dev/*","/proc/*","/sys/*","/tmp/*","/run/*","/mnt/*","/media/*","/lost+found"} /mnt```
#### v.   Check if /etc/systemd/system/setssdroot.service, /sbin/setssdroot.sh, /etc/setssdroot.conf exist and correct, in terminal
```sudo cp /etc/systemd/system/setssdroot.service /mnt/etc/systemd/system/setssdroot.service```

```sudo cp /sbin/setssdroot.sh /mnt/sbin/setssdroot.sh```
#### vi.  Check if /mnt/etc/systemd/system/setssdroot.service, /sbin/setssdroot.sh /mnt/sbin/setssdroot.sh exist and correct, in terminal
```sudo cp setssdroot.service /etc/systemd/system```

```sudo cp setssdroot.sh /sbin```

```sudo chmod 777 /sbin/setssdroot.sh```

```systemctl daemon-reload```

```sudo systemctl enable setssdroot.service```
#### vii. reboot

### 3) Use SDKManager, in step 3, Target Components, uncheck Jetson OS, only check Jetson SDK Components.

## 4.Install: run commands in additional_install.txt

## 5. Other tools: https://github.com/yqlbu/jetson-packages-family
