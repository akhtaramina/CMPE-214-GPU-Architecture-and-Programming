In this lab, you will learn how to run a CUDA program and check the GPU's configurations with it. After you finish, answer the questions and submit them to Canvas.

Note that lab submissions are per team. Although a later deadline is given in assignment 0 for forming teams, it is highly recommended to form your team and start working together early. Feel free to walk around and talk with your classmates during the lab to find your team.

 

There are a few ways you can get the GPU resource, including borrowing a TX1 board (per team and limited), using Google Colab (free and paid tiers), using the GPU on your own machine, applying for department and college resources, etc. If you have a hard time getting any of these, sharing one with your teammates can also be sufficient for the course.

 

1. If you choose to use Colab and other options, go directly to step 5. If you want to borrow the Jetson TX1 board, fetch the board and complete the equipment check-out formDownload check-out form

 (will be provided during the class). Please follow the regulations listed on the form. Make sure your board is working properly.

Test your board by connecting it to a monitor via HDMI cable. Connect keyboard and mouse to the USB hub attached to the board. Then turn on the provided Jetson board.

Login credentials (do not change them):
ID: nvidia
PASSWORD: nvidia

You can choose to reset the Jetson TX1 system (optional). If you choose not to do so, skip step 2 and go to step 5.


2. If your machine has Ubuntu 16.04 or 18.04 skip this step. Download, install, and setup VMware Workstation Player (https://www.vmware.com/products/workstation-player.html).

After installing VMware Workstation Player. Create a virtual machine with Ubuntu 18.04 (https://releases.ubuntu.com/18.04/) and 256GB disk. Assign more resources to the VM for better performance. Use USB 3.1 and bridged network (make sure to disable routers for other VMs in your system).

Install the OS, and then open a terminal and do:
sudo apt-get install libxml2-utils


After the installation, power off and go to the VM folder. Open your .vmx file and insert those two lines:

usb.autoConnect.device0 = "vid:0x0955 pid:0x7020 autoclean:1"
usb.autoConnect.device1 = "vid:0x0955 pid:0x7721 autoclean:1"

This makes sure the USB cable is working properly during the flashing.


3. Download and install Nvidia SDK Manager (https://docs.nvidia.com/sdk-manager/index.html) in Ubuntu 18.04. Connect your Jetson board to the host machine and turn it to force recovery mode (hold the force recovery button, then power up or reset). Then follow the steps in SDK Manager.

In the SDK Manager, you should deselect the host installation and choose Jetpack 4.6.

If the flashing fails, you should debug it. Go to the downloaded Jetpack folder and do:
sudo ./flash.sh jetson-tx1-devkit mmcblk0p1

Observe and fix the errors.


4. After flashing, your board would automatically exit force recovery mode and enter the OS installation stage. Simply follow the instructions to start the OS installation. And then install CUDA tools on the board.

Please use the following login credentials for the board:
ID: nvidia
PASSWORD: nvidia

After the OS installation, you can continue to install the CUDA tools. Use the ifconfig command on the board to make sure the IP address is correct on the host.

Due to the time limitation, you can stop after installing CUDA. You can install the rest of the tools later.

You can also try VirtualBox (but you need to download the extension pack to use USB 3.1 and set filters for the vid and pid) if VMware does not work.


5. If you are using an environment with CUDA samples installed (including TX1), go to its folder. Compile and run DeviceQuery. Otherwise, DeviceQuery is also available here: DeviceQuery.zipDownload DeviceQuery.zip.

For Colab, enabling the GPU is a simple process. Follow the instructions provided during the lab or this guide:

Setting Up Google Colab for CUDA - GeeksforGeeksLinks to an external site.

If you are using other resources without CUDA installed, the following guides can be useful to set it up:

CUDA Installation Guide for Linux — Installation Guide for Linux 13.3 documentationLinks to an external site.

CUDA Installation Guide for Microsoft Windows — Installation Guide Windows 13.3 documentationLinks to an external site.

 

6. With the DeviceQuery output, answer the following questions. 

1) What is the CUDA driver version?

2) What is the CUDA compute capability?

3) What is the number of multiprocessors?

4) What is the number of CUDA cores per multiprocessor?

5) What is the size of constant memory?

6) What is the max size of shared memory per thread block?

7) What is the max register number per thread block?

 

7. Submit your results to Canvas (one per team).
1) A text file containing your answers.
2) A screenshot of the OS and nvcc version of your environment.

 

Useful command:
tegrastats
https://docs.nvidia.com/drive/drive_os_5.1.6.1L/nvvib_docs/index.html#page/DRIVE_OS_Linux_SDK_Development_Guide/Utilities/util_tegrastats.html


Useful resources:
Download and Run SDK Manager
https://docs.nvidia.com/sdk-manager/download-run-sdkm/index.html

Install Jetson Software with SDK Manager
https://docs.nvidia.com/sdk-manager/install-with-sdkm-jetson/index.html

NVIDIA Jetson Linux Driver Package Software Features
https://docs.nvidia.com/jetson/archives/l4t-archived/l4t-3261/index.html#page/Tegra%20Linux%20Driver%20Package%20Development%20Guide/introduction.html#

Jetson/General debug
https://elinux.org/Jetson_TX1
https://elinux.org/Jetson/General_debug

NVIDIA® Jetson™ Linux Driver Package (L4T)
https://developer.nvidia.com/embedded/develop/software

Automatically connecting USB devices at virtual machine power on
https://kb.vmware.com/s/article/1648


Sample location:
TensorRT 
/usr/src/tensorrt/samples/ 

cuDNN 
/usr/src/cudnn_samples_<version>/ 

CUDA 
/usr/local/cuda-<version>/samples/ 

MM API 
/usr/src/jetson_multimedia_api 

VisionWorks 
/usr/share/visionworks/sources/samples/  
/usr/share/visionworks-tracking/sources/samples/  
/usr/share/visionworks-sfm/sources/samples/  

OpenCV 
/usr/share/opencv4/samples/ 

VPI
/opt/nvidia/vpi/samples/
