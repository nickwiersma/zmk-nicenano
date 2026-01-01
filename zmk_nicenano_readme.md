### 1st) Set up the Build Environment

## To compile ZMK, you generally need:
## Required tools

# West (Zephyr meta-tool)
# Zephyr SDK
# CMake
# nRF Command Line Tools (for flashing + debugging)
# Python 3
# pyelftools

### Minimal versions needed for this to work:

# Zephyr SDK ≥ 0.16
# CMake ≥ 3.20
# Python ≥ 3.8

## To check:
cmake --version
python3 --version


#-------#

pip3 install pyelftools
# Sometimes linux is complaining about permissions, then use:
# pip3 install --user pyelftools


pip3 install -U west

cd ~/path_to_your/zmk/app/
west init -l 

cd ~/path_to_your/zmk/

west update

west zephyr-export


# Build firmware:

cd ~/path_to_your/zmk/app/
west build -b nice_nano -- -DSHIELD=lumberjack_pro

## The resulting firmware should be at:
# ~/path_to_your/zmk/app/build/zephyr/zmk.uf2


