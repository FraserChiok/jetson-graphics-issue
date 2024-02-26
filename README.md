# Fix Custom Kernel Compilation Black Screen

## Purpose of the Tutorial: Fixing Black Screen Issue on NVIDIA Jetson Orin NX 16GB

This tutorial addresses the common issue of encountering a black screen when using a custom kernel on the NVIDIA Jetson Orin NX 16GB. Many users face this challenge where the system appears to boot correctly, as indicated by the spinning fan and visible UEFI bootloader menu, but fails to display anything beyond a black screen afterward.

The objective here is to guide users through the process of diagnosing and resolving this issue effectively. By following the steps outlined in this tutorial, users will:

- Gain insights into the potential causes behind the black screen problem post-UEFI bootloader.
- Learn troubleshooting techniques to identify the root cause of the issue.
- Implement appropriate fixes or adjustments, including potential kernel configuration changes or driver updates, to resolve the black screen problem.
- Ensure smooth and successful booting of the system with a custom kernel, enabling users to utilize the full capabilities of the NVIDIA Jetson Orin NX 16GB without encountering display-related obstacles.

This tutorial serves as a valuable resource for developers, enthusiasts, and system administrators working with NVIDIA Jetson Orin NX 16GB boards, empowering them to overcome the black screen issue.

## Video Demostration and Explanation
[![Demo and Explanation](http://img.youtube.com/vi/QZCLWzL3CG8/0.jpg)](http://www.youtube.com/watch?v=QZCLWzL3CG8)]

## Instructions for UART Cable Connection

Connect the UART cable as follows:

- J50 Pin 4 (TXD) -> Cable RXD
- J50 Pin 3 (RXD) -> Cable TXD
- J50 Pin 7 (GND) -> Cable GND

## Commands for Detecting the Device, Opening gtkterm, and Configuration

To detect the device and configure gtkterm, run the following commands:


### Detect the device
```bash
sudo dmesg --follow | grep ttyUSB0
```

### Open gtkterm with sudo privileges
```bash
sudo gtkterm
```

### Configure gtkterm to use ttyUSB0 if detected. Manually set the port and other settings if needed.

### Navigate to the module directory
```bash
cd /lib/modules
```

### Copy necessary files (replace versions accordingly)
```bash
cp <original_module_version>/extra <new_module_version>/
```

#### Example:
```bash
# cp 5.10.104-tegra-original/extra 5.10.104-tegra-new/
```

### Navigate to the new module directory
```bash
cd 5.10.104-tegra-new/
```

### Update module dependency information
```bash
sudo depmod -a
```

### Reboot the system to apply changes
```bash
sudo reboot
```
