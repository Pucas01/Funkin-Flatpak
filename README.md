# Friday Night Funkin' Flatpak

A Flatpak package for the popular rhythm game Friday Night Funkin'.

## Installation

1. **Add the remote**
```bash
flatpak remote-add --no-gpg-verify --user funkin-flatpak https://pucas01.github.io/FunkinFlatpak/
```

2. **install the flatpak**
```bash
flatpak install --user funkin-flatpak io.github.Pucas01.FunkinFlatpak
```

**and your done!**

## Mods

The mods folder is located at ~/.var/app/io.github.Pucas01.FunkinFlatpak/mods

Just put your mods in there and it should work!

## .Flatpak Build Guide

1. install the flatpak by either installing it via the remote in the above guide, if ive long abandoned this project you can build it yourself below

2. open your terminal and execute this command (dont panic if it looks like its not doing anything it just takes a long time)
```bash
flatpak build-bundle ~/.local/share/flatpak/repo Funkin.flatpak io.github.Pucas01.FunkinFlatpak master
```

**you should now have a Funkin.flatpak file in your home directory!**

## Self build Guide

If you want to build the Flatpak yourself, follow these steps:

1.  **Download the Source Code:**
    Begin by downloading the source code directly from this repository.

2.  **Navigate to the Build Configuration:**
    Open your terminal and change the current directory to the `Build-JSON` folder within the downloaded source code.

    ```bash
    cd Build-JSON
    ```

3.  **Edit the Build Manifest:**
    Open the file `io.github.Pucas01.FunkinFlatpak.json` in your preferred text editor

4.  **Specify the Game Source:**
    Within the `io.github.Pucas01.FunkinFlatpak.json` file, you'll need to provide the link to the corosponding release and the location of your LOCAL Friday Night Funkin' game files:

    * **Latest Release Link and Hash:** 
    You will need to replace the placeholder link in the JSON to the release corosponding to the flatpak and game version your building for, you will also need to add the hash, you can find the hash in the description of the release on github **(the line you will need to change is in the funkin module under sources around line 70)**.

    * **Self-Provided Game Files:** 
    please download the game files corosponding to this flatpaks version from [itch.io](<https://ninja-muffin24.itch.io/funkin>) and set the path in the JSON the path to a folder with these sub folders Funkin/theactualgamefiles **(the line you will need to change is in the funkin module under sources around line 70)**, If official pre-built game files aren't readily available you will have to compile them yourself from the [Funkin' GitHub repository](<https://github.com/FunkinCrew/Funkin>).

5.  **Execute the Build Command:**
    Go back to your terminal and run the following `flatpak-builder` command:

    ```bash
    flatpak-builder --user --install --force-clean build-dir io.github.Pucas01.FunkinFlatpak.json
    ```

    * `--user`: Builds and installs for the current user.
    * `--install`: Installs the built Flatpak to your local Flatpak repository.
    * `--force-clean`: Cleans the `build-dir` before starting the build, ensuring a fresh build.
    * `build-dir`: A temporary directory where the build process will take place. It will be created if it doesn't exist.
    * `io.github.Pucas01.FunkinFlatpak.json`: The path to your Flatpak manifest file.

6.  **Launch and Play:**
    Once the build and installation are complete, you should be able to launch Friday Night Funkin' from your app runner or by running:

    ```bash
    flatpak run io.github.Pucas01.FunkinFlatpak
    ```

## Common Issues

If you encounter any problems during the build or installation process, please refer to the following common issues:

* **`hash didn't match Error:`**
    This error indicates that the checksum of the downloaded game files doesn't match the hash specified in the `io.github.Pucas01.FunkinFlatpak.json` file. To resolve this:
    1.  Copy the hash value that the error message spits out in your terminal.
    2.  Open the `io.github.Pucas01.FunkinFlatpak.json` file again.
    3.  Locate the hash value you previously entered for the game files.
    4.  Replace the old hash with the new hash you copied from the error message.
    5.  Try running the `flatpak-builder` command again.

