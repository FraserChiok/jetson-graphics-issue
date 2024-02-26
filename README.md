## Instructions for UART Cable Connection

Connect the UART cable as follows:

- J50 Pin 4 (TXD) -> Cable RXD
- J50 Pin 3 (RXD) -> Cable TXD
- J50 Pin 7 (GND) -> Cable GND

## Commands for Detecting the Device, Opening gtkterm, and Configuration

To detect the device and configure gtkterm, run the following commands:

```bash
# Detect the device
sudo dmesg --follow | grep ttyUSB0

# Open gtkterm with sudo privileges
sudo gtkterm

# Configure gtkterm to use ttyUSB0 if detected. Manually set the port and other settings if needed.

# Navigate to the module directory
cd /lib/modules

# Copy necessary files (replace versions accordingly)
cp <original_module_version>/extra <new_module_version>/

# Example:
# cp 5.10.104-tegra-original/extra 5.10.104-tegra-new/

# Navigate to the new module directory
cd 5.10.104-tegra-new/

# Update module dependency information
sudo depmod -a

# Reboot the system to apply changes
sudo reboot
