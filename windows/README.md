# Overview

This folder contains a set of package files to set up a Windows 10 machine (has not been tested with any other versions).

The files in this folder are [Chocolatey](chocolatey.org) packages and can be installed individually as follows:

    choco install --yes --file packages.base.config --file packages.dev.config --file packages.gpu.config

You can add as many `--file` options as you need.

# Other Notes

As part of the install and setup you may want to have SSH running on your machine:

	add-windowscapability -online -name OpenSSH.client~~~~0.0.1.0
	add-windowscapability -online -name OpenSSH.server~~~~0.0.1.0

	Start-Service sshd
	# OPTIONAL but recommended:
	Set-Service -Name sshd -StartupType 'Automatic'
	# Confirm the Firewall rule is configured. It should be created automatically by setup. 
	Get-NetFirewallRule -Name *ssh*
	# There should be a firewall rule named "OpenSSH-Server-In-TCP", which should be enabled
	# If the firewall does not exist, create one
	New-NetFirewallRule -Name sshd -DisplayName 'OpenSSH Server (sshd)' -Enabled True -Direction Inbound -Protocol TCP -Action Allow -LocalPort 22

# References

* https://docs.microsoft.com/en-us/windows-server/administration/openssh/openssh_install_firstuse


