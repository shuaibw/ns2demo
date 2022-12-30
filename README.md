# Installing ns2 on WSL version 2

**If you are not using Windows 11 and WSL version 2, this may not work**.

Check your WSL version from Command Prompt:
- `wsl -l -v`

If you are not using WSL version 2, follow [this guide](https://learn.microsoft.com/en-us/windows/wsl/install).

## Step 1: Installing `g++-4.8`

1. Try `sudo apt install g++-4.8`. If this works, you are done. Proceed to step 2.
2. If the above command doesn't work, you will have to manually add the older repository to your system. Execute the following commands:
- `echo "deb http://th.archive.ubuntu.com/ubuntu bionic main universe" | sudo tee -a /etc/apt/sources.list `
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
- `ns-2.35/`
- `sudo make install`
4. If the above commands have executed successfully, you should be able to type `ns` in the terminal and a prompt beggining with `%` will appear. This marks a successful installation. 

## Step 3: Cleanup (optional)

You might want to remove the older repository link from your system by running the following command:

- `sudo sed -i '$ d' /etc/apt/sources.list`


