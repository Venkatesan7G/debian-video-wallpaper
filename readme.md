# Linux-video-wallpaper ( This is forked from:"ghostlexly/gpu-video-wallpaper" )

Run a video as an animated live wallpaper on your Ubuntu/Debian-based Linux desktop with dual/multiple monitor support.

You can either run the application through its GUI or via the command line.

````
CLI usage: video-wallpaper.sh [--start] [--stop] [--startup true|false] "video_path.mp4"

--start Start playback of video wallpaper. 

--stop  Stop active playback.

--startup  Start/disable playback of video file on system startup."
````

## Installation

```bash
git clone https://github.com/ghostlexly/gpu-video-wallpaper.git
cd gpu-video*
./install.sh
```
These commands will download the repository and will set up all the required dependencies, install the necessary files to your system and optionally create an app menu entry.
Now you can either use the CLI or open the 'Video Wallpaper' app from your application menu.

If want to run the installer on a distribution that is not based on Debian, you may want to run the installer in distro-agnostic mode: `./install.sh --distro-agnostic`. This will disable automatic dependency-checking and installing, which will not work on non-Debian distributions that don't use `apt` as their package manager.

## Dependencies

All dependencies will be installed when running `install.sh`.

- python3
- python3-pyqt5
- xrandr
- pcregrep
- mpv
- xwinwrap

## Application

Picture After installation:


![A1](https://user-images.githubusercontent.com/59331727/168027179-ca35beb3-8d39-466e-b7ed-99cb20f3be6f.png)



Application screen:


![A2](https://user-images.githubusercontent.com/59331727/168027278-9d032bb1-5966-472a-9436-72feb1717fae.png)


## Uninstall

Run `install.sh --uninstall` to remove all files associated with video-wallpaper.

## Changelog

**2022/05/12**

* Added Videos for wallaer and a picture in assest folder

**2022/02/22**

* Updated and corrected `readme.md` instructions.
* `installer.sh` now has a `--distro-agnostic` flag (see "Installation" section of this readme).
* Bugfixes to installer

**2021/08/19**

* Bugfixes to installer and autostart functionality

**2021/08/17**

* Bugfixes to installer and autostart functionality

**2021/06/05**

* Changed name to "video-wallpaper"
* Added an uninstall functionality 
* Bugfixes to installer

**2021/06/03:**

* Added GUI front-end that handles video file selection and shell parameters and runs everything through to the shell script.
* Created installer to handle dependency checking and menu entry creation.
* Removed the xwinwrap binary from the files and added it as a dependency. The installer will download it from [this repository](https://github.com/mmhobi7/xwinwrap/releases/tag/v0.9) as part of the installation process.
* Added configuration file that stores last used video file and process ID of currently active video wallpaper. That way, stopping video playback will only kill the mpv instance used by the video wallpaper, not all other instances of mpv (including ones that are possibly used for other types of video playback that the user does not want to close).
* Fixed an undesired behaviour where it was possible to start multiple video wallpapers after one another, leading to increased CPU load.
* General clean-up inside `video-wallpaper.sh`

Known errors:

* When sourcing `settings.conf`, `video-wallpaper.sh` will throw an error because it stumbles over the "\[video-wallpaper settings\]" section. This section, however, is needed by the python script. Since the shell script does not crash, this error message is tolerated for the moment until I get around to find a more elegant way than just sourcing `settings.conf`.
