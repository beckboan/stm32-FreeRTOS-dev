# Notes on STM32CubeIDE FreeRTOS

## Install

1. Manually - non CMSIS RTOS
2. STM32Cube Device Configuration Tool - CMSIS-RTOS API

**CMSIS-RTOS** - software API later for Arm Cortex-M processors. This allows to use the same application code even if the kernel changes

Layers:

1. Application Code
2. CMSIS-RTOS API
3. Real Time Kernel

**Note**: CMSIS-RTOS-API layer (general layer) is different from CMSIS-CORE layer.

**CMIS-CORE** layer gives API to deal with Cortex Mx processor peripherals.

### Manually Install

- Can be applied to other microcontrollers and IDEs

#### Steps

1. Download RTOS Kernel
2. Copy license to license folder
3. Copy c/include files to project third party folder
4. Copy portable to third party folder
5. Delete folders not related to compiler (ex: GCC) and **keep MemMang, readme, and CMakeLists**
6. In compiler folder, delete all folders not related to processor architecture (ex: ARM_CMF4F)
7. Ensure that ThirdPart is included in build (properties in STM32CubeIDE)
8. Exclude sysmem.c from build (RTOS has it's own heap management - MemMang)
9. Choose heap management from MemMang
10. Add FreeRTOS to includes
    1. Properties
    2. C/C++ Build Settings
    3. MCU GCC Compiler
    4. Include paths (include folder and processor header)
11. Add FreeRTOSConfig.h to preprocessor headers
12. Device manager NVIC, pendable request for system service, systick timer, and sys service call.
13. Fix any hook functions needed
