## Tutorial: Python on Windows with VS Code

### 1. Installing Visual Studio Code and Python on Windows

Go to [VS Code download page](https://code.visualstudio.com/Download) to download and install the latest version. Don't go for the portable version in the ZIP archive or you'll run into problems.

Next install the latest stable executable Python installer for Windows from the [official Python download page](https://www.python.org/downloads/windows/).

### 2. Creating the first workspace

After the Python interpretor has been installed, open a command prompt in Windows (type _cmd_ in the search and hit enter), create a project directory and start VS code from there:

```
mkdir project1
cd project1
code .
```

By starting Visual Studio Code in a folder, that folder becomes your _workspace_. VS Code stores settings that are specific to that workspace in .vscode/settings.json, which are separate from user settings that are stored globally.

Once Visual Studio Code has started, make sure to install the Python extension for VS Code from the Visual Studio Marketplace.

For more details read [Getting Started with Python in VS Code](https://code.visualstudio.com/docs/python/python-tutorial).

### 3. Creating and activating a virtual environment

Create a new terminal (Ctrl+Shift+") and type:

```
python -m venv .venv
.\.venv\Scripts\activate.bat
```

You might get the following error:

```
File C:\Your\Path\project1\.venv\Scripts\activate.ps1 cannot be loaded because running scripts is disabled on this system. For more information, see about_Execution_Policies at https:/go.microsoft.com/fwlink/?LinkID=135170.
```

In this case go to File -> Preferences -> Settings and in the search bar write _terminal.integrated.shellArgs.windows_. Then apply the following setting:

```
"terminal.integrated.shellArgs.windows": ["-ExecutionPolicy", "Bypass"]
```

Restart VS Code and you should be all set.

### 4. Working with requirements.txt

Use pip freeze to figure out which modules you need to add to requirements.txt.

```
pip freeze > requirements.txt
pip install -r requirements.txt
```
