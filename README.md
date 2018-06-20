# Development Enviornment Setup for Flask on Windows Subsystem for Linux

## Install WSL and Apps

1. Install [Windows Subsystem for Linux](https://docs.microsoft.com/en-us/windows/wsl/install-win10). Choose the "Ubuntu" option in the Microsoft Store. The Microsoft Store method of installing WSL will only work with version 1803 or higher of Windows 10.

2. Install [Docker for Windows](https://docs.docker.com/docker-for-windows/install/). Make sure to enable the setting to share a local drive with Docker. 

3. Install [Visual Studio Code](https://code.visualstudio.com/).

## Configure Visual Studio Code

1. Make bash the [default terminal in Visual Studio Code](https://code.visualstudio.com/docs/editor/integrated-terminal#_configuration), and add some other default configurations.

    ```
    "terminal.integrated.shell.windows": "C:\\WINDOWS\\sysnative\\bash.exe",
    "workbench.panel.defaultLocation": "right",
    "workbench.statusBar.visible": false,
    "workbench.activityBar.visible": false,
    ```

2. Configure bash to run docker commands.

     ```
    MOVE TO .bashrc 

    export PATH="$HOME/bin:$HOME/.local/bin:$PATH"
    export PATH="$PATH:/mnt/c/Program\ Files/Docker/Docker/resources/bin"
    alias docker=docker.exe
    alias docker-compose=docker-compose.exe
    ```

## Configure Python and the App

1. Install venv for python3.

    ```
    sudo apt-get install python3-venv
    ```

2. Create a virtual enviornment.

    ```
    python3 -m venv venv
    source /venv/bin/activate
    ```

3. Install dependencies for project.

    ```
    pip install -r requirements.txt
    ```

4. Set enviornment variable for flask app.

    ```
    MOVE TO .bashrc

    export FLASK_APP=flasky.py
    ```

5. Create the db and run the app.

    ```
    flask db upgrade
    flask run
    ```



