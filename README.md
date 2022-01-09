# AMD-Linux-Driver
Aggregate information found online about how to install AMD Linux Driver and works for APU

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
