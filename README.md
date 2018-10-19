# Development Enviornment Setup for Flask on Windows Subsystem for Linux

## Install WSL and Visual Studio Code

1. Install [Windows Subsystem for Linux](https://docs.microsoft.com/en-us/windows/wsl/install-win10). (NOTE: before installing the subsystem, there is a command that must be run using PowerShell as an Administrator - see the previous link). Choose the "Ubuntu" option in the Microsoft Store. The Microsoft Store method of installing WSL will only work with version 1803 or higher of Windows 10. After installing, "Launch" Ubuntu now that it is installed. You will be prompted to set a unix username and password. 

2. Install [Visual Studio Code](https://code.visualstudio.com/).

## Configure Visual Studio Code

1. Make bash the [default terminal in Visual Studio Code](https://code.visualstudio.com/docs/editor/integrated-terminal#_configuration). This can be done by editing the "settings.json" file (shown below), or by editing the settings using the GUI in Visual Studio Code. To find the setting in the GUI, follow "File", "Preferences", "Settings", then search for "termnial integrated shell windows". Use `C:\WINDOWS\Sysnative\bash.exe` in the first field that comes up.

    ```
    "terminal.integrated.shell.windows": "C:\\WINDOWS\\sysnative\\bash.exe",
    ```

## Configure Git

1. Run the following commands:

    ```
    git config --global user.email "you@example.com"
    git config --global user.name "Your Name"
    ```

## Configure Python and the App

1. Install venv for python3.

    ```
    sudo apt-get update
    sudo apt-get install python3-venv
    ```

2. Create a virtual enviornment.

    ```
    python3 -m venv venv
    source venv/bin/activate
    ```

3. Install dependencies for project.

    ```
    pip3 install -r requirements.txt
    ```

4. Set enviornment variable for flask app. Variables can be added to the enviornment by modifiying your .bashrc file. To edit the file run:

    ```
    sudo nano /home/UNIX_USERNAME/.bashrc
    ```

    Commands can be added to the top of the file, for example:

    ```
    export FLASK_APP=flasky.py
    ```

    The next time you start a bash session, the variables will be available. To see a list of all variables run `printenv`

5. Create the db and run the app.

    ```
    flask db upgrade
    flask run
    ```

## (optional) Install and setup Docker

1. Install [Docker for Windows](https://docs.docker.com/docker-for-windows/install/). Make sure to enable the setting to share a local drive with Docker.

2. Configure bash to run docker commands. Add to the .bashrc file by running `sudo nano /home/UNIX_USERNAME/.bashrc` and add to the top of the file:

     ```
    export PATH="$HOME/bin:$HOME/.local/bin:$PATH"
    export PATH="$PATH:/mnt/c/Program\ Files/Docker/Docker/resources/bin"
    alias docker=docker.exe
    alias docker-compose=docker-compose.exe
    ```