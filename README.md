# NUCLEO-F767ZI: Ethernet with LwIP, FreeRTOS, and iperf

## Overview

This project demonstrates how to run a TCP/IP stack using **LwIP** and **FreeRTOS** on the **NUCLEO-F767ZI** development board. It includes an **iperf server** (version 2.2.1) for testing Ethernet performance.

It was created because no official or complete Ethernet example was available for this specific board. As a newcomer to STM32 Ethernet development, I spent several days figuring out how to configure all necessary parameters to make it work properly.



## Key Configurations

To get Ethernet working reliably, the following were manually configured:

- ETH peripheral descriptors and buffer addresses  
- LwIP heap memory relocation  to SRAM1 - 64K
- Custom linker script adjustments for LwIP  
- Memory Protection Unit (MPU) configuration  

## Features

- FreeRTOS multitasking support  
- LwIP TCP/IP networking stack  
- iperf 2.2.1 server for benchmarking network throughput  
- STM32CubeMX `.ioc` file included for reproducible configuration  
- DHCP enabled by default (can be changed to static IP via CubeMX)  
- iperf server can be disabled by commenting out the following line in `StartDefaultTask()`:

```c
lwiperf_start_tcp_server_default(NULL, NULL);
