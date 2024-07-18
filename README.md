# Instruction for kernel cross-compiling in Docker environment.

# Run Docker environment.
sudo chmod a+x docker-debian-bookworm
./docker-debian-bookworm

# Once in /work/, clone linux-lts
git clone --depth 1 -b linux-5.10.y https://github.com/embeddedTS/linux-lts
cd linux-lts/

# Export variables
export CROSS_COMPILE=arm-linux-gnueabihf-
export ARCH=arm
export WILC=y

# Clone external modules
git clone https://github.com/embeddedTS/wilc3000-external-module/

# Modify configuration file for the chosen board.
# If you are using TS-7250-V3, modify arch/arm/configs/tsimx6ul_defconfig.

# Then modify device tree if needed.
# If you are using TS-7250-V3, modify /arch/arm/boot/dts/imx6ul-ts7250v3.dtsi.

# Make.
make tsimx6ul_defconfig

# Create a build.sh file and run it as
/bin/sh build.sh

# Once compilation if over, exit the Docker environment:
exit

# The tar can be sent to the device, for example (adapt depending on networks):
scp linux-lts/embeddedTS-linux-lts-20240625-v5.10.220-ts-dirty.tar.gz root@192.168.1.199:/root/kernels/

# and, on the board, unpacked as:
tar xhf embeddedTS-linux-lts-20240625-v5.10.220-ts-dirty.tar.gz -C /
