# Overview

# Prerequisites
## Operating Systems
Most of the development process can be done on either Windows or Linux, though there are certain processes that can be only be done on Linux. If Windows is your choice of operating system, you will have to set up a Linux Virtual machine for the Linux-only steps. A preconfigured Ubuntu Linux Virtual Box image is available for [download](https://www.dropbox.com/sh/jsr9qw5ecr3webo/AAAuiHvovjQSC5wr1897HN1Ea?dl=0). Refer to `virtual_box_setup.md` for more information on setting up the virtual machine development environment. 

## Tools
- Matlab
    - Simulink
    - HDL Coder 
    - HDL Verifier
    - DSP System Toolbox
    - Fixed-Point Designer
    - MATLAB Coder
    - Signal Processing Toolbox
    - Simulink Coder
- Intel Quartus Prime
    - lite edition for DE10-Nano projects
    - standard edition for Arria 10 projects
- Python
    - **NOTE:** for Windows users, ensure you download the 64-bit version of Python
- [Linaro armhf toolchain](https://releases.linaro.org/components/toolchain/binaries/latest-7/arm-linux-gnueabihf/)
    - For Linux hosts, this will be installed on your host machine so you can cross-compile for the ARM processor on the SoC FPGA
    - For Windows hosts, this will be need to be installed on your Linux virtual machine
    - The Linaro toolchain might be available in your Linux distribution's package manager; it is available in Ubuntu, for instance.

## Github Repositories
Several [FPGA Open Speech Tools](https://github.com/fpga-open-speech-tools) repositories are required for basic development. 

For Simulink-related development, the following repositories are required:
- [simulink_models](https://github.com/fpga-open-speech-tools/simulink_models)
- [simulink_codegen](https://github.com/fpga-open-speech-tools/simulink_codegen)
- [simulink_library](https://github.com/fpga-open-speech-tools/simulink_library)

Model and algorithm development take place in the `simulink_models` repository. The other repositories contain supporting software, but don't need to be modified.

For projects being deployed to a DE10-Nano, you need
- [de10nano_projects](https://github.com/fpga-open-speech-tools/de10nano_projects)
- [component_library](https://github.com/fpga-open-speech-tools/component_library)

For projects being deployed to an Arria 10, you need
- [arria10_projects](https://github.com/fpga-open-speech-tools/arria10_projects)
- [component_library](https://github.com/fpga-open-speech-tools/component_library)

All of the repositories above should live in the same root folder, i.e. 
```
<main folder>
├── arria10_projects
├── component_library
├── de10nano_projects
├── simulink_codegen
├── simulink_library
├── simulink_models
```


If you are using Linux as your development host OS, you will also want to include the [linux-socfgpa](https://github.com/fpga-open-speech-tools/linux-socfpga) kernel repository in the same directory as above; for Windows hosts, this repository will need to live in your Linux virtual machine. This repository is needed to compile device drivers for the embedded Linux running on the SoC FPGA. On a Linux host, device drivers will be compiled automatically for you during Simulink code generation. For Windows hosts, device drivers have to be manually compiled in your Linux virtual machine


# Simulink Model Creation

# Code Generation

# Quartus Project Creation

# Deploying the Project

# Using the Project