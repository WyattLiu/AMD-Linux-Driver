# AMD-Linux-Driver
Aggregate information found online about how to install AMD Linux Driver and works for APU.
Tested system:
5600G Ubuntu 20.04 + RTX A2000

# Recovery from faulty installs
You may want to do ./amdgpu-pro-install --uninstall and other measures to clean up

# Install latest driver

Using this article: https://www.aventurabinaria.es/2020/12/Install-amd-drivers-linux-debian-ubuntu

```
curl -SL https://repo.radeon.com/amdgpu-install/21.40.1/ubuntu/focal/amdgpu-install_21.40.1.40501-1_all.deb -o amdgpu-install_21.40.1.40501-1_all.deb
sudo apt-get install ./amdgpu-install_21.40.1.40501-1_all.deb
sudo apt-get update

amdgpu-install --usecase=graphics,opencl --opencl=rocr,legacy --vulkan=amdvlk,pro --no-32
sudo reboot
```

# Must set the permission well, otherwise clinfo cannot see it and of course OpenCL code cannot run

```
sudo usermod -a -G video $LOGNAME
sudo usermod -a -G render $LOGNAME
```

https://community.amd.com/t5/drivers-software/no-opencl-devices-ubuntu-20-04-2/td-p/444567

# what happened to your nvidia GPU if you have a mixed system like I do

Reinstall cuda/gpu driver using the run file downloaded. The only thing lost is the driver, suggest a full upgrade install.
Yes, stop lightdm/X server first as it is required by nvidia

# Raven Mining on APU (5600G) Vega 8

Although we have OpenCL 2.0 here, most miners on the market cannot work such as NBMiner, Gminer, Teamredminer, Lolminer. The only one works is xmrig.
```
[2022-01-09 14:27:17.522]  opencl   KawPow program for period 699151 compiled (501ms)
[2022-01-09 14:27:44.892]  opencl   accepted (29/0) diff 431M (30 ms)
[2022-01-09 14:28:06.935]  opencl   accepted (30/0) diff 431M (30 ms)
[2022-01-09 14:28:07.622]  opencl   #0 04:00.0   0W 69C    0RPM 1900/0MHz
[2022-01-09 14:28:07.622]  miner    speed 10s/60s/15m 1.71 1.72 1.77 MH/s max 2.04 MH/s
[2022-01-09 14:28:17.059]  net      new job from stratum-ravencoin.flypool.org:3333 diff 431M algo kawpow height 2097450
[2022-01-09 14:28:54.345]  net      new job from stratum-ravencoin.flypool.org:3333 diff 431M algo kawpow height 2097451
```

If this helps, BTC:

Have a nice day.
