---
title: Hello World
date: 2022-01-12 13:00:00 +500
categories: [test1,test2]
tags: [test1,test2]     # TAG names should always be lowercase
---

In this post, we will be discussing how to install, list, and change the default kernel using the Grubby tool in Fedora.

First, let's discuss what Grubby is. Grubby is a command-line tool that allows users to configure and display information about the system's bootloader. It is particularly useful for managing multiple kernels on a single system.

To install Grubby if it isn't already present, we can use the following command:

```
sudo dnf install grubby
```

This command uses the package manager DNF (Dandified Yum) to install Grubby. The "sudo" command is used to run the command with administrative privileges.

Once Grubby is installed, we can use it to list all of the installed kernels on the system by running the following command:

```
sudo grubby --info=ALL | grep -E "^kernel|^index"
```

The `grubby --info=ALL` command displays all of the information about the system's bootloader, including the paths to all of the installed kernels. The `grep -E` command is used to filter the output, only displaying the lines that start with "kernel" or "index".

The output of this command should be something like this:

```
index=0 
kernel="/boot/vmlinuz-5.15.10-200.fc35.x86_64" 
index=1 
kernel="/boot/vmlinuz-5.15.10-lqx1.0.fc35.x86_64" 
index=2 
kernel="/boot/vmlinuz-5.15.8-200.fc35.x86_64" 
index=3 
kernel="/boot/vmlinuz-5.15.8-lqx1.0.fc35.x86_64"
```

This output shows the index number of each installed kernel, as well as the path to the kernel file.

Once we have the index number of the kernel that we want to set as the default, we can use the following command to change the default kernel:
```
sudo grubby --set-default-index=1
```

This command uses the "grubby --set-default-index" option to set the kernel with index number 1 as the default.

To verify that the right kernel has been set as default, we can use the following command:
```
sudo grubby --default-title
```
This command displays the title of the default kernel. The output should be something like this:
```
Fedora Linux (5.15.10-lqx1.0.fc35.x86_64) 35 (Workstation Edition)
```

In conclusion, Grubby is a powerful tool that allows users to easily manage multiple kernels on a Fedora Linux system. With Grubby, we can install, list, and change the default kernel with just a few simple commands. It is a must-have tool for any Linux system administrator.