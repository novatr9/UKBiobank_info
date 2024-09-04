### Installing the command line tools on Mac OS X

In order to install the DNANexus command-line tools, you must have Python3 installed (this might already be installed by default).

Once you have Python3 installed, open a Terminal window and run the command `pip3 install dxpy`

The installer is likely to show you several warnings like "WARNING: The scripts dx, dx-app-wizard, dx-build-app and dx-build-applet are installed in '/Users/yourusername/Library/Python/3.9/bin' which is not on PATH." These warnings mean that in order to run these commands, you would need to type the full path, eg. to run dx you would type `/Users/yourusername/Library/Python/3.9/bin/dx`. This is annoying - to fix it, you need to add the directory to your PATH setting.

To add this directory to your path:
1. Check which shell you are using by running `env | grep SHELL`
2. If the result of step 1 says "/bin/zsh":
  * Edit (or create) the file ~/.zshrc, and add the following line to the bottom of the file:
        `export PATH="$PATH:/Users/yourusername/Library/Python/3.9/bin/"`
        (replace "yourusername" with your Mac OS username)
  * Run the command `source ~/.zshrc` to activate the change you made
3. If the result of step 1 says "/bin/bash", follow the instructions in step 2, but instead of using the file ~/.zshrc use either ~/.bash_profile (if you use MacOS's default Terminal.app), or ~/.bashrc (if you use almost any other terminal besides Terminal.app).

You may also get this warning message whenever you run a "dx" command:
> /Users/yourusername/Library/Python/3.9/lib/python/site-packages/urllib3/\__init__.py:34: NotOpenSSLWarning: urllib3 v2 only supports OpenSSL 1.1.1+, currently the 'ssl' module is compiled with 'LibreSSL 2.8.3'.

This message appears to be harmless (everything still works), but since it's annoying you can get rid of it by running `pip3 uninstall urllib3` and then `pip3 install urllib3==1.26.7`

### Installing the command line tools on Linux

To do a local install of the command line tools under your account on RC:
1. Connect to an interactive session on a Blanca node, or use the command `acompile` to access an interactive session on an Alpine node. ***Step 2 will not work if run from a login node***
2. Run `pip3 install --user dxpy`
3. Use the command `find ~/.local/lib/ -wholename '*dxpy/scripts' -print` to find the location the commands have been installed to
4. Copy the location from step 3, and edit the file `~/.bashrc` to add it to your PATH. If there's already a line in your .bashrc that sets PATH, add the new location to the end of that line (separated by a `:` character), otherwise add the line `export PATH=$PATH:/path/you/found/in/step3`
5. Run `source ~/.bashrc` to reload your .bashrc so the changes you made in step 4 will take effect immediately.

To install the command line tools on a Linux computer where you have root access (such as a laptop/desktop):
1. You can either install locally under your user account using steps 2-5 above, or you can install system-wide with `pip3 install dxpy` (the --user flag is what makes it install to the home directory in the previous instructions)
2. Find where it installed and add it to your PATH
Details will vary by distribution - the main thing is to make sure you have Python3 installed.

### Installing the command line tools on Windows

FIXME: Add this
