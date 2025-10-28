# MAC Ansible Setup

A tool using Ansible to setup your mac device.

## Prerequisites
DO NOT INSTALL PYTHON TO THE SYSTEM!

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
- Install pyenv using the following
  ```
  curl -L https://github.com/pyenv/pyenv-installer/raw/master/bin/pyenv-installer | bash
  ```  
- Add the following into your ```~/.zshrc``` using ```nano ~/.zshrc```:
  ```
  export PYENV_ROOT="$HOME/.pyenv"
  [[ -d $PYENV_ROOT/bin ]] && export PATH="$PYENV_ROOT/bin:$PATH"
  eval "$(pyenv init -)"
  ```
- Install Python 3.10:
  ```
  pyenv install 3.10
  ```
- Install Python 2.7
  ```
  pyenv install 2.7
  ```
- Set Python to use 3.10 and then 2.7:
  ```
  pyenv global 3.10 2.7
  ```
- Confirm Python 3.10 is being used
  ```
  python3 --version
  ```
  ```
  python --version
  ```
- Confirm Python 2.7 is being used
  ```
  python2 --version
  ```
- Install pexpect
  ```
  pip install pexpect
  ```  
- Install Ansible
  ```
  pip install ansible
  ```

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
In a new terminal, run the following command
```
ansible-playbook setup.yml -K -e ansible_become_password=YOUR-PASSWORD
```
You will be prompted to enter your password. Once entered correctly, ansible will run to configure your mac device.

## Configuration
This ansible setup will configure the following on your mac device:
- Installs via brew (Homebrew)
  - git
  - mas (Mac App Store CLI)
  - node
  - dockutil
  - awscli
  - composer
- Installs via brew cask (Homebrew Cask)
  - Google Chrome
  - Google Drive
  - Docker
  - Spotify
  - Discord
  - JetBrains Toolbox
  - PHP Storm
  - Web Storm
  - Sourcetree
  - Sublime Text
  - Insomnia
  - DataGrip
  - Logi Options +
- Installs via mas (Mac App Store CLI):
  - Slack
  - NordLayer
  - Microsoft Teams
- Creates a `development` folder located in the Documents path
- Configures Dock
