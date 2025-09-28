# Swap Memory

### Create swap space
These commands create a 4GB swap file, set the appropriate permissions, initialize it as swap space, activate it, and ensure that it remains active after system reboots. This is useful for systems with limited RAM, as it allows the operating system to use disk space as additional virtual memory.

```bash
# Create a 4GB swap file
# sudo: This command is run with superuser privileges, which are required for creating files in system directories and modifying system settings.
# fallocate: This command is used to allocate space for a file without writing zeros to it, making it a fast way to create a file of a specified size.
# -l 4G: This option specifies the length of the file to be created, in this case, 4 gigabytes.
# /swapfile: This is the path where the swap file will be created. You can choose a different name or location if desired.
sudo fallocate -l 4G /swapfile

# chmod: This command changes the file permissions.
# 600: This sets the permissions so that only the owner (root) can read and write to the file, while others have no permissions. This is important for security, as the swap file may contain sensitive data.
# /swapfile: This specifies the file whose permissions are being changed.
sudo chmod 600 /swapfile

# mkswap: This command initializes the file as a swap space, preparing it for use as virtual memory.
# /swapfile: This specifies the file that will be used as the swap area.
sudo mkswap /swapfile

# swapon: This command enables the specified swap space, making it active and available for use by the system.
# /swapfile: This specifies the swap file that you want to activate.
sudo swapon /swapfile

# make it permanent across reboots
# /swapfile: The path to the swap file.
# none: This indicates that there is no specific device associated with the swap file.
# swap: This specifies the type of file system, which is swap in this case.
# sw: This option indicates that the swap file should be enabled at boot.
# 0 0: These are options for dump and fsck; they are not needed for swap files.
# |: This pipe sends the output of the echo command to the next command.
# sudo tee -a /etc/fstab: This command appends (-a) the output to the /etc/fstab file, which is the configuration file that defines how disk partitions, including swap files, are mounted at boot time.
echo '/swapfile none swap sw 0 0' | sudo tee -a /etc/fstab
```


