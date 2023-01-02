# Installing ns2 on WSL/Ubuntu

**This tutorial may not be compatible with Windows 10, but it is worth attempting to follow the instructions and see if it works on your system.**

Check your WSL version from Command Prompt:
- `wsl -l -v`

Ensure that you are running WSL version 2. If that is not the case, follow [this guide](https://learn.microsoft.com/en-us/windows/wsl/install) to upgrade.

Install `nam` from [this link](https://drive.google.com/file/d/0B7S255p3kFXNdmxzSmRzaVRWb28/view?resourcekey=0-ouf369XFh7Azj3brgm-UEQ). First download the file, then run `sudo dpkg -i FILE_NAME`. The `apt` version didn't seem to work for me.

## Step 1: Installing `g++-4.8`

1. Try `sudo apt install g++-4.8`. If this works, you are done. Proceed to step 2.
2. If the above command doesn't work, you will have to manually add the older repository to your system. Execute the following commands:
- `echo "deb [trusted=yes] http://th.archive.ubuntu.com/ubuntu bionic main universe" | sudo tee -a /etc/apt/sources.list `
- `sudo apt update`
- `sudo apt install g++-4.8`
3. If the above commands are successfully executed, you are done. Proceed to step 2.
4. If there are errors, try `sudo apt --fix-broken install` and then proceed to step 2.

## Step 2: Installing `ns2-allinone-2.35`

1. Download the installer from [this link](https://drive.google.com/file/d/0B7S255p3kFXNVVlxR0ZNRGVORjQ/view?usp=sharing).
2. Unzip the downloaded file: `tar xvf ns-allinone-2.35_gcc5.tar.gz`
3. This will create a directory named `ns-allinone-2.35`. Now run the following commands to install `ns2`:
- `cd ns-allinone-2.35/`
- `export CC=gcc-4.8 CXX=g++-4.8 && ./install`
- `cd ns-2.35/`
- `sudo make install`
4. If the above commands have executed successfully, you should be able to type `ns` in the terminal and a prompt beggining with `%` will appear. This marks a successful installation. 
5. Once installed, you can make changes to the source code within the `ns-2.35/` directory. Then you can incorporate those changes by executing:
- `make`
- `sudo make install`

## Step 3: Cleanup (optional)

You might want to remove the older repository link from your system by running the following command:

- `sudo sed -i '$ d' /etc/apt/sources.list`


