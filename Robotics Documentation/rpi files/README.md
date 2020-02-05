Files in this directory are meant to be used with our RPIs.

- Motd files should be dropped in /etc and renamed to "motd" or the corresponding directory depending on operating system
  This can be done with the command "sudo cp /LOCATION_OF_MOTD/MOTD_NAME /etc/motd" on *nix-like systems 
  (ex: Raspbian or the FRCVision fork).
	
- For RPIs used on the robot or for active testing, there is a script to automatically toggle wifi on images with
	NetworkManager installed. To see if NetworkManager is installed, use the command "nmcli -v". The script, currently named
	'99-wlan', which makes on-the-fly configuration with the RPI off the robot *significantly easier* as it does not require
	the RPI to be connected to any network. This is done by creating a wifi access point that the user may connect to,
	allowing them to configure the system via ssh and access the gui; all at the same IPv4 address. At the time that this was
	written, the intended IPs for ssh are:
	- Connected to robot - 10.43.61.22 port 22 (To use ssh while connected to the roboRIO over USB, you need to have a port
	forwarding rule in the robots code to push port 2222 to port 22. Refer to the [FRC documentation](https://docs.wpilib.org/en/latest/docs/networking/networking-utilities/portforwarding.html)
	for more on how to setup port forwarding.)
	- Off the robot - 10.43.61.22 port 22
	
	To install the script, use the command "sudo chmod +x /LOCATION_OF_SCRIPT/SCRIPT_NAME" to make it executable, then,
	"sudo cp /LOCATION_OF_SCRIPT/SCRIPT_NAME /etc/NetworkManager/dispatcher.d/99-wlan".
	WARNING - If you are using an image that by default boots in read-only, such as FRCVision, use '99-wlan-vis' as it
	automatically remounts in read/write to change the wifi state and returns back to read-only after the script is finished.
	
	Note - The access point must be setup seperately; the AP will already be setup if the image being used is our preconfigured
	FRCVision image. If not, [this is a walkthrough](https://www.raspberrypi.org/documentation/configuration/wireless/access-point.md) on how to get the AP installed and running.
