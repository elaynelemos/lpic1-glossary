# Glossary of Terms for LPIC-1
**Note:** list of "must know" terms for LPIC-1 based on the [learning material provided by LPI](https://learning.lpi.org/en/learning-materials/learning-materials/) by alphabetical order.

## Track of Progress

### 101 Exam
- [x] Topic 101: System Architecture
- [ ] Topic 102: Linux Installation and Package Management
- [ ] Topic 103: GNU and Unix Commands
- [ ] Topic 104: Devices, Linux Filesystems, Filesystem Hierarchy Standard

### 102 Exam
- [ ] Topic 105: Shells and Shell Scripting
- [ ] Topic 106: User Interfaces and Desktops
- [ ] Topic 107: Administrative Tasks
- [ ] Topic 108: Essential System Services
- [ ] Topic 109: Networking Fundamentals
- [ ] Topic 110: Security

## LPIC-1 Terms

**BIOS:** Basic Input/Output System

**Bootloader:** short for "bootstrap loader" also known as a boot program. It is a special operating system software that loads into the working memory of a computer after start-up. For this purpose, immediately after a device starts, a bootloader is generally launched by a bootable medium like a hard drive, a CD/DVD or a USB stick. The boot medium receives information from the computer’s firmware about where the bootloader is. _[(source)](https://www.ionos.com/digitalguide/server/configuration/what-is-a-bootloader/)_

**Daemon:** Program that runs continuously and exists for the purpose of handling periodic service requests that a computer system expects to receive. The daemon program forwards the requests to other programs (or processes) as appropriate. _[(source)](https://whatis.techtarget.com/definition/daemon)_

**DMA:** short for Direct Memory Access. It is a method that allows an input/output (I/O) device to send or receive data directly to or from the main memory, bypassing the CPU to speed up memory operations. The process is managed by a chip known as a DMA controller (DMAC). _[(source)](https://www.techopedia.com/definition/2767/direct-memory-access-dma)_

**DOS:** short for Disk Operating System. It is an operating system that runs from a hard disk drive. The term can also refer to a particular family of disk operating systems, most commonly Microsoft Disk Operating System (MS-DOS). _[(source)](https://searchsecurity.techtarget.com/definition/DOS)_

**EFI:** hort for Extensible Firmware Interface. It is a new firmware standard developed by Intel and introduced with the release of Intel Architecture 64 that greatly improves the features available in the BIOS. _[(source)](https://www.computerhope.com/jargon/e/efi.htm)_

**ESP:** short for EFI System Partition. It is an OS independent partition that acts as the storage place for the EFI bootloaders, applications and drivers to be launched by the UEFI firmware. It is mandatory for UEFI boot. _[(source)](https://wiki.archlinux.org/index.php/EFI_system_partition)_

**FAT:** short for File Allocation Table. It is a file system developed for hard drives that originally used 12 or 16 bits for each cluster entry into the file allocation table. It is used by the operating system to manage files on hard drives and other computer systems. _[(source)](https://www.techopedia.com/definition/1369/file-allocation-table-fat)_

**Firmware:** Program stored in a non-volatile memory chip attached to the motherboard, executed every time the computer is powered on. Unlike normal software, firmware cannot be changed or deleted by an end-user without using special programs, and remains on that device whether it's on or off. _[(1st source)](https://learning.lpi.org/en/learning-materials/101-500/101/101.2/101.2_01/)_ _[(2nd source)](https://www.computerhope.com/jargon/f/firmware.htm)_

**GRUB:** short for Grand Unified Bootloader. It is a complete program for loading and managing the boot process. It is the most common bootloader for Linux distributions. _[(source)](https://itsfoss.com/what-is-grub/)_

**IRQ:** short for Interrupt Request. It is an asynchronous signal sent from a device to a processor indicating that in order to process a request. _[(source)](https://www.techopedia.com/definition/5297/interrupt-request-irq)_

**Kernel:** Software code that serves as a layer between the hardware and main programs that run on a computer. It is the first part to load when the OS boots up. It is loaded in memory and stays there throughout the entire time the computer is in session. _[(source)](http://www.linuxandubuntu.com/home/what-is-linux-kernel)_

**MBR:** short for Master Boot Record. It is also sometimes referred to as the master boot block, master partition boot sector, and sector 0. The MBR is the first sector of the computer hard drive. It tells the computer how the hard drive is partitioned, and how to load the operating system. _[(source)](https://www.computerhope.com/jargon/m/mbr.htm)_

**NVRAM:** short for Non-Volatile Random Access Memory. It is the computer memory that can hold data even when power to the memory chips has been turned off. Today, a good example of NVRAM is flash memory like that used in a Jump drive. NVRAM is also in your computer monitor, printers, cars, smart cards, and other devices that require remembered settings. _[(source)](https://www.computerhope.com/jargon/n/nvram.htm)_

**PCI:** short for Peripheral Component Interconnect. It is a hardware bus used for adding internal components to a desktop computer. For example, a PCI card can be inserted into a PCI slot on a motherboard, providing additional I/O ports on the back of a computer. _[(source)](https://techterms.com/definition/pci)_

**POST:** shor for Power-On Self-Test. It is a set of routines performed by firmware or software immediately after a computer is powered on, to determine if the hardware is working as expected. _[(source)](https://www.geeksforgeeks.org/what-is-postpower-on-self-test/)_

**RAM:** short for Random Access Memory, alternatively referred to as main memory, primary memory, or system memory. It is a hardware device that allows information to be stored and retrieved on a computer. Because data is accessed randomly instead of sequentially like it is on a CD or hard drive, access times are much faster. However, RAM is a volatile memory and requires power to keep the data accessible. If the computer is turned off, all data contained in RAM is lost. _[(source)](https://www.computerhope.com/jargon/r/ram.htm)_

**ROM:** short for Read-Only Memory. It is a type of memory that is non-volatile and where modifications are difficult, if they’re possible to do. Non-volatile means that the information is not going to be deleted if the device is turned off. This type of memory is typically used to store firmware that is unlikely to need to be updated, or that is not intended to be updated. _[(source)](https://www.biteno.com/en/what-is-rom/)_

**SATA:** short for Serial Advanced Technology Attachment. It is a standard for connecting and transferring data from hard disk drives (HDDs) to computer systems. As its name implies, SATA is based on serial signaling technology, unlike Integrated Drive Electronics hard drives that use parallel signaling. _[(source)](https://searchstorage.techtarget.com/definition/Serial-ATA)_

**SCSI:** Small Computer System Interface. It is a hardware bus specification for connecting peripherals to a computer using a parallel transmission interface. _[(source)](https://networkencyclopedia.com/small-computer-system-interface-scsi/)_

**UEFI:** short for Unified Extensible Firmware Interface. It is a specification for a software program that connects a computer's firmware to its operating system. UEFI is expected to eventually replace BIOS. It does the same job as a BIOS, but with one basic difference: it stores all data about initialization and startup in an .efi file, instead of storing it on the firmware. _[(1st source)](https://whatis.techtarget.com/definition/Unified-Extensible-Firmware-Interface-UEFI)_ _[(2nd source)](https://www.freecodecamp.org/news/uefi-vs-bios/)_

**USB:** short for Universal Serial Bus. It is an industry standard for short-distance digital data communications. USB ports allow USB devices to be connected to each other with and transfer digital data over USB cables. They can also supply electric power across the cable to devices that need it. _[(source)](https://www.lifewire.com/what-is-a-usb-port-818166)_


<style>
  ul {
    list-style-type: none;
  }
</style>
