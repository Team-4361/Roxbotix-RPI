Files in this directory are meant to be used with our RPIs.

- Motd files should be dropped in /etc and renamed to "motd" or the corresponding directory depending on operating system
  This can be done with the command "sudo cp /LOCATION_OF_MOTD/MOTD_NAME /etc/motd" on *nix-based systems 
  (such as Raspbian and the FRCVision fork).
	
- For RPIs used on the robot or for active testing, there is a script to automatically toggle wifi on images with
	NetworkManager installed. To see if NetworkManager is installed, use the command "nmcli -v". The script, currently named
	'99-wlan', which makes on-the-fly configuration with the RPI off the robot *significantly easier* as it does not require
	the RPI to be connected to any network. This is done by creating a wifi access point that the user may connect to,
	allowing them to configure the system via ssh and access the gui; all at the same IPv4 address. At the time that this was
	written, the intended IPs for ssh are:
	- Connected to robot - 10.43.61.22 port 2222
	- Off the robot - 10.43.61.22 port 22
