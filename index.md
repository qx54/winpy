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

Use pip freeze to figure out which modules you need to add to requirements.txt or save it directly to file:

```
pip freeze > requirements.txt
```

An example of configuration file requirements.txt is as follows.

```
###### Requirements without Version Specifiers ######`
nose
nose-cov
beautifulsoup4

###### Requirements with Version Specifiers ######`
docopt == 0.6.1             # Version Matching. Must be version 0.6.1
keyring >= 4.1.1            # Minimum version 4.1.1
coverage != 3.5             # Version Exclusion. Anything except version 3.5
Mopidy-Dirble ~= 1.1        # Compatible release. Same as >= 1.1, == 1.*
```

You can specify the version with `==`, `>`, `>=`, `<`, `<=`, etc. If the version is omitted, the latest version is installed. Two conditions can be specified with AND by separating them with a comma ,. In the following example, a version of 1.0 or more and 2.0 or less is installed.

```
package >= 1.0, <=2.0
```

Now you can copy or move the project files including the requirements.txt to another environment and install with it.

```
pip install -r requirements.txt
```
