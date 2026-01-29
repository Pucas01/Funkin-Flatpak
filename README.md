# Friday Night Funkin' Flatpak
A Flatpak package for the popular rhythm game Friday Night Funkin'.

## Installation
1. **Add the remote**
```bash
flatpak remote-add --no-gpg-verify --user funkin-flatpak https://pucas01.github.io/Funkin-Flatpak/
```
2. **Install the flatpak**
```bash
flatpak install --user funkin-flatpak io.github.Pucas01.Funkin-Flatpak
```
**and you're done!**

## Mods
The mods folder is located at `~/.var/app/io.github.Pucas01.Funkin-Flatpak/mods`
Just put your mods in there and it should work!

## Common Issues
If you encounter any problems, please refer to the following common issues:

**The game is zoomed in :(**
This happens when playing the game using Wayland and having a screen scale above 1. Execute the following command to revert to X11, this will fix the issue.
```bash
flatpak override --nosocket=wayland io.github.Pucas01.Funkin-Flatpak
```

## .Flatpak Build Guide
1. Install the flatpak by either installing it via the remote in the above guide. If I've long abandoned this project you can build it yourself below.
2. Open your terminal and execute this command (don't panic if it looks like it's not doing anything, it just takes a long time)
```bash
flatpak build-bundle ~/.local/share/flatpak/repo Funkin.flatpak io.github.Pucas01.Funkin-Flatpak master
```
**You should now have a Funkin.flatpak file in your home directory!**

## Self Build Guide
If you want to build the Flatpak yourself, follow these steps:

1.  **Download the Source Code:**
    Begin by downloading the source code directly from this repository.

2.  **Navigate to the Build Configuration:**
    Open your terminal and change the current directory to the `FunkinFlatpak` folder within the downloaded source code.
    ```bash
    cd FunkinFlatpak
    ```

3. **Self-Provided Game Files:** 
    Please download the game files corresponding to this flatpak's version from [itch.io](https://ninja-muffin24.itch.io/funkin). Place said game files in the `FunkinSource/Funkin` folder. If official pre-built game files aren't readily available, you will have to compile them yourself from the [Funkin' GitHub repository](https://github.com/FunkinCrew/Funkin).

4.  **Execute the Build Command:**
    Go back to your terminal and run the following `flatpak-builder` command:
    ```bash
    flatpak-builder --user --install --force-clean build-dir io.github.Pucas01.Funkin-Flatpak.json
    ```
    * `--user`: Builds and installs for the current user.
    * `--install`: Installs the built Flatpak to your local Flatpak repository.
    * `--force-clean`: Cleans the `build-dir` before starting the build, ensuring a fresh build.
    * `build-dir`: A temporary directory where the build process will take place. It will be created if it doesn't exist.
    * `io.github.Pucas01.Funkin-Flatpak.json`: The path to your Flatpak manifest file.

5.  **Launch and Play:**
    Once the build and installation are complete, you should be able to launch Friday Night Funkin' from your app launcher or by running:
    ```bash
    flatpak run io.github.Pucas01.Funkin-Flatpak
    ```