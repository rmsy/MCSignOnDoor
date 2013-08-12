MINECRAFT Sign On Door
Version %VERSION%
by Tustin2121
----------------------
This program tells players attempting to connect to a minecraft server on this 
machine a message (defaulting to a 'server is off' message). This program 
cannot and is not meant to run while the minecraft server itself is running; 
it is meant to give a message to players as to why the server is not running.

Usage: java -jar MCSignOnDoor.jar [switches]
Command line switches:
	-? --help
		    Displays this message and quits
	-p --port [port]
		    Sets the port the messenger runs on (default: %PORT%)
	-i --address [ip]
		    Sets the ip address the messenger runs on (default: null)
	-m --message [message]
		    Sets the message to send to connecting players (250 char max) 
		    (default: %AWAYMSG%)
	-w --white-message [message]
		    Sets the message for whitelisted players. Default: does not 
		    differentiate between normal and whitelisted players.[1]
	-b --black-message --banned-message [message]
		    Sets the message for blacklisted players. Default: does not 
		    differentiate between normal and blacklisted players.[1]
	   --ipmessage [message]
		    Sets the message for ip-banned players. Default: does not 
		    differentiate between normal and ip-banned players.[1][2]
	   --motd [message]
	   	    Sets the server list message of the day. Default: the message
	   	    setting, truncated. (<=60 char max)
	   --ignoreping	
		    Sets McSod to ignore incoming pings; Server appears offline.
	   --ignorebannedping
		    Sets McSod to ignore incoming pings from banned IPs.
	   --players [ratio]
		    Sets the player ratio given in pings (in form "1/10")[3]

	-v --reported-version [versionstring]
	        Sets the version reported over motd. Default: %VERDEF%
	-# --show-version
	        Forces the client to show the reported version string in red.
	   --act-as-protocol [version]
		    Sets which protocol version to act as. Defaults to latest.
		    (Warning: advanced functionality - you don't need this)
		    
	-l --log [file]
		    Supplies a log file to write to (default: does not use log file)
	-s --silent
		    Does not print output to the screen
	   --sentrymode
		    When someone not banned tries to connect to the server, McSod 
		    will exit immediately with the return value 12. Useful in 
		    conjunction with a looping script.

	-c --config [file]
		    Tells McSod to read the configuration file specified. All command
		    line switches after this one will be ignored.
	   --outputconfig [filename]
		    Outputs a template config file to the specified filename. This file
		    can be edited and used with the --config command line switch.

Notes:
[1] When using special case messages (white and banned list messages), McSod 
    will attempt to load the appropriate files that the Minecraft server uses 
    to store these lists.

[2] If a blacklist message is set, it is also applied to ip-banned players, 
    unless the ip-banned players message is separately set.

[3] When setting the player ratio to show, non-numbers and a ratio with 0 max 
    players will display as "???" on the client. Player ratio also cuts into 
    the max length of the motd setting.

[4] Minecraft is backwards compatible with previous motd versions, but they are
    not forward compatible. As of MC version 1.4.2, the version is 1.

[*] Some command lines treat the bang (!) as a special command character.
    If you would like to use a bang in your server message, be sure to escape
    it with a backslash (\).
  
[*] Messages can also contain color codes by using an ampersand (&) followed 
    by a hexadecimal value (0-9 a-f). See the MC wiki's Classic Server 
    Protocol page.


Usage examples:
java -jar MCSignOnDoor
java -jar MCSignOnDoor -c mcsod.cfg
java -jar MCSignOnDoor -m "The server is down for maintenance."
java -jar MCSignOnDoor -m "OH! You woke me up!\nGive me a minute to 
wake back up and reconnect!" --sentrymode
java -jar MCSignOnDoor -ip 192.168.1.1 -m "Still waiting for bukkit to 
	upgrade..."
java -jar MCSignOnDoor -p 54321 --message "The &eMinecraftWB &fserver has
	moved to 192.168.1.1\!" --motd "Moved to 192.168.1.1"
java -jar MCSignOnDoor -l logfile.log -s -m "Slim's server is currently
	being removed of excessive genitalia." --motd "Removing d*cks" 
	--players "6/9"