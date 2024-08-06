# MAC Ansible Setup

A tool using Ansible to setup your mac device.

## Prerequisites
Follow the steps below which will then allow you to run the `ansible` commands.

- In the App Store, make sure you are signed in (Account Settings > Sign In)
- Install XCode via the App Store
- Ensure Apple's command line tools are installed using the following command
  ```
  xcode-select --install
  ```
- Accept the XCode license agreement. Run the command
  ```
  xcodebuild -license
  ```
   and then, type agree at the end and press enter.
- Add the following into your ```~/.zshrc``` using ```nano ~/.zshrc```:
  ```
  eval "$(pyenv init --path)"
  ```
- Upgrade Pip:
  ```
  sudo -H pip3 install --upgrade pip
  ```
- Install Ansible
  ```
  pip3 install ansible
  ```
- In the file `dependencies.yml`, change line number 21 to include your username. This is currently set to `jakesixsmith`.

## Confriming Ansible is Installed
Run the command to return `ansible` information:
  ```
  ansible-playbook
  ```
If the above did not work and showed an error, follow these steps to fix:
- In a terminal, type in:
```
find ~/ -name ansible-playbook 2>/dev/null
```
- Copy the output, this will now be referenced as `OUTPUT` in any samples.
- In a terminal, type in:
```
nano ~/.zshrc
```
- Enter in the following:
```
export PATH=$PATH:OUTPUT
```
- Save & Close
- In a terminal, type in:
```
source ~/.zshrc
```
- Retry the following command to confirm ansible is working:
```
ansible-playbook
```

## Running Ansible
In a terminal, run the following command
```
ansible-playbook main_setup.yml -K
```
You will be prompted to enter your password. Once entered correctly, ansible will run to configure your mac device.

## Configuration
This ansible setup will configure the following on your mac device:
- Installs brew (Homebrew)
- Installs via brew (Homebrew)
  - git
  - mas (Mac App Store CLI)
  - Google Chrome
  - Google Drive
  - Docker
  - Spotify
  - Discord
  - JetBrains Toolbox
  - Sourcetree
- Installs via mas (Mac App Store CLI):
  - Slack
  - NordLayer
- Creates a `development` folder located in the Documents path
- Configures Dock
