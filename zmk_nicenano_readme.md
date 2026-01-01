Linux-only. 
Assumes Python, pip, and gh are already installed.

# Build ZMK Firmware.

## Set up the Build Environment.
### Required tools:
- West (Zephyr meta-tool)
- Zephyr SDK
- CMake
- nRF Command Line Tools (for flashing + debugging)
- Python 3
- pyelftools

### Optional:
- github cli

### Minimal versions needed for this to work:

- Zephyr SDK ≥ 0.16
- CMake ≥ 3.20
- Python ≥ 3.8
- pip3

To check cmake and python versions:
``` sh
cmake --version
python3 --version
```
Install pyelftools
```sh
pip3 install pyelftools
# Sometimes linux is complaining about permissions, then use:
# pip3 install --user pyelftools
```
Install west
```sh
pip3 install -U west
```
Clone the base Github repository, set variables and initialise west.
```sh
cd ~/Documents/
gh clone "https://github.com/piit79/zmk.git"
export ZMK_PATH=~/Documents/zmk
export APP_PATH=$ZMK_PATH/app
cd $APP_PATH
west init -l
```
Update west, this might take a while.
```sh
cd $ZMK_PATH
west update
```
Register the current Zephyr installation as a CMake config package.
```sh
west zephyr-export
```
Build firmware, for available keyboards see $APP_PATH/boards/shields/
Edit DSHIELD value for desired keyboard:
```sh
cd $APP_PATH
west build -b nice_nano -- -DSHIELD=
```
The resulting firmware should be at:
```sh
$APP_PATH/build/zephyr/zmk.uf2
```



