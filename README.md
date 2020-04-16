A set of system provisioning scripts for both Windows and OSX

# Windows

Requires chocolatey.

	choco install --yes --files windows/packages.base.config --file windows/packages.dev.config --ignore-errors 


# OSX

Requires homebrew..

	brew bundle --file osx/Brewfile
