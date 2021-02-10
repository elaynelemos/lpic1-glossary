# Glossary of Commands for LPIC-1
**Note:** the list of commands is based on the topic order in its first appearance at the [learning material provided by LPI](https://learning.lpi.org/en/learning-materials/learning-materials/). Although inside each topic the commands were ordered alphabetically. The sources of each description are their respective [man pages](https://www.kernel.org/doc/man-pages/) and usage/help shorts from command.

## Contents

### [101 Exam :)](#101-exam)
- [x] [Topic 101: System Architecture](#topic-101-system-architecture)
  - [`dmesg`](#dmesg)
  - [`init`](#init)
  - [`journalctl`](#journalctl)
  - [`lspci`](#lspci)
  - [`lsmod`](#lsmod)
  - [`lsusb`](#lsusb)
  - [`modinfo`](#modinfo)
  - [`modprobe`](#modprobe)
  - [`runlevel`](#runlevel)
  - [`shutdown`](#shutdown)
  - [`systemctl`](#systemctl)
  - [`telinit`](#telinit)
- [ ] [Topic 102: Linux Installation and Package Management](#topic-102-linux-installation-and-package-management)
  - [`grub-install`](#grub-install)
  - [`grub-mkconfig`](#grub-mkconfig)
  - [`ldconfig`](#ldconfig)
  - [`ldd`](#ldd)
  - [`objdump`](#objdump)
  - [`readelf`](#readelf)
  - [`update-grub`](#update-grub)
- [ ] Topic 103: GNU and Unix Commands
- [ ] Topic 104: Devices, Linux Filesystems, Filesystem Hierarchy Standard
### 102 Exam :))
- [ ] Topic 105: Shells and Shell Scripting
- [ ] Topic 106: User Interfaces and Desktops
- [ ] Topic 107: Administrative Tasks
- [ ] Topic 108: Essential System Services
- [ ] Topic 109: Networking Fundamentals
- [ ] Topic 110: Security


## 101 Exam

### Topic 101: System Architecture

#### dmesg
It is used to examine or control the kernel ring buffer. The default action is to display all messages from the kernel ring buffer.
```shell-session
$ dmesg --help

Usage:
 dmesg [options]

Display or control the kernel ring buffer.

Options:
 -C, --clear                 clear the kernel ring buffer
 -c, --read-clear            read and clear all messages
 -D, --console-off           disable printing messages to console
 -E, --console-on            enable printing messages to console
 -F, --file <file>           use the file instead of the kernel log buffer
 -f, --facility <list>       restrict output to defined facilities
 -H, --human                 human readable output
 -k, --kernel                display kernel messages
 -L, --color[=<when>]        colorize messages (auto, always or never)
                               colors are enabled by default
 -l, --level <list>          restrict output to defined levels
 -n, --console-level <level> set level of messages printed to console
 -P, --nopager               do not pipe output into a pager
 -r, --raw                   print the raw message buffer
 -S, --syslog                force to use syslog(2) rather than /dev/kmsg
 -s, --buffer-size <size>    buffer size to query the kernel ring buffer
 -u, --userspace             display userspace messages
 -w, --follow                wait for new messages
 -x, --decode                decode facility and level to readable string
 -d, --show-delta            show time delta between printed messages
 -e, --reltime               show local time and time delta in readable format
 -T, --ctime                 show human-readable timestamp (may be inaccurate!)
 -t, --notime                don't show any timestamp with messages
     --time-format <format>  show timestamp using the given format:
                               [delta|reltime|ctime|notime|iso]
Suspending/resume will make ctime and iso timestamps inaccurate.

 -h, --help                  display this help
 -V, --version               display version

Supported log facilities:
    kern - kernel messages
    user - random user-level messages
    mail - mail system
  daemon - system daemons
    auth - security/authorization messages
  syslog - messages generated internally by syslogd
     lpr - line printer subsystem
    news - network news subsystem

Supported log levels (priorities):
   emerg - system is unusable
   alert - action must be taken immediately
    crit - critical conditions
     err - error conditions
    warn - warning conditions
  notice - normal but significant condition
    info - informational
   debug - debug-level messages

For more details see dmesg(1).
```
<br/>

#### `init`
Systemd is a system and service manager for Linux operating systems. When run as first process on boot (as PID 1), it acts as init system that brings up and maintains userspace services.
```shell-session
$ init --help

init [OPTIONS...] {COMMAND}

Send control commands to the init daemon.

     --help      Show this help
     --no-wall   Don't send wall message before halt/power-off/reboot

Commands:
  0              Power-off the machine
  6              Reboot the machine
  2, 3, 4, 5     Start runlevelX.target unit
  1, s, S        Enter rescue mode
  q, Q           Reload init daemon configuration
  u, U           Reexecute init daemon
```
<br/>

#### `journalctl`
It may be used to query the contents of the systemd journal as written by systemd-journald.service.
```shell-session
$ journalctl --help

journalctl [OPTIONS...] [MATCHES...]

Query the journal.

Options:
     --system                Show the system journal
     --user                  Show the user journal for the current user
  -M --machine=CONTAINER     Operate on local container
  -S --since=DATE            Show entries not older than the specified date
  -U --until=DATE            Show entries not newer than the specified date
  -c --cursor=CURSOR         Show entries starting at the specified cursor
     --after-cursor=CURSOR   Show entries after the specified cursor
     --show-cursor           Print the cursor after all the entries
  -b --boot[=ID]             Show current boot or the specified boot
     --list-boots            Show terse information about recorded boots
  -k --dmesg                 Show kernel message log from the current boot
  -u --unit=UNIT             Show logs from the specified unit
     --user-unit=UNIT        Show logs from the specified user unit
  -t --identifier=STRING     Show entries with the specified syslog identifier
  -p --priority=RANGE        Show entries with the specified priority
  -g --grep=PATTERN          Show entries with MESSSAGE matching PATTERN
     --case-sensitive[=BOOL] Force case sensitive or insenstive matching
  -e --pager-end             Immediately jump to the end in the pager
  -f --follow                Follow the journal
  -n --lines[=INTEGER]       Number of journal entries to show
     --no-tail               Show all lines, even in follow mode
  -r --reverse               Show the newest entries first
  -o --output=STRING         Change journal output mode (short, short-precise,
                               short-iso, short-iso-precise, short-full,
                               short-monotonic, short-unix, verbose, export,
                               json, json-pretty, json-sse, cat)
     --output-fields=LIST    Select fields to print in verbose/export/json modes
     --utc                   Express time in Coordinated Universal Time (UTC)
  -x --catalog               Add message explanations where available
     --no-full               Ellipsize fields
  -a --all                   Show all fields, including long and unprintable
  -q --quiet                 Do not show info messages and privilege warning
     --no-pager              Do not pipe output into a pager
     --no-hostname           Suppress output of hostname field
  -m --merge                 Show entries from all available journals
  -D --directory=PATH        Show journal files from directory
     --file=PATH             Show journal file
     --root=ROOT             Operate on files below a root directory
     --interval=TIME         Time interval for changing the FSS sealing key
     --verify-key=KEY        Specify FSS verification key
     --force                 Override of the FSS key pair with --setup-keys

Commands:
  -h --help                  Show this help text
     --version               Show package version
  -N --fields                List all field names currently used
  -F --field=FIELD           List all values that a specified field takes
     --disk-usage            Show total disk usage of all journal files
     --vacuum-size=BYTES     Reduce disk usage below specified size
     --vacuum-files=INT      Leave only the specified number of journal files
     --vacuum-time=TIME      Remove journal files older than specified time
     --verify                Verify journal file consistency
     --sync                  Synchronize unwritten journal messages to disk
     --flush                 Flush all journal data from /run into /var
     --rotate                Request immediate rotation of the journal files
     --header                Show journal header information
     --list-catalog          Show all message IDs in the catalog
     --dump-catalog          Show entries in the message catalog
     --update-catalog        Update the message catalog database
     --new-id128             Generate a new 128-bit ID
     --setup-keys            Generate a new FSS key pair
```
<br/>

#### `lspci`
Utility for displaying information about PCI buses in the system and devices connected to them. By default, it shows a brief list of devices.
```shell-session
$ lspci -

Usage: lspci [<switches>]

Basic display modes:
-mm             Produce machine-readable output (single -m for an obsolete format)
-t              Show bus tree

Display options:
-v              Be verbose (-vv for very verbose)
-k              Show kernel drivers handling each device
-x              Show hex-dump of the standard part of the config space
-xxx            Show hex-dump of the whole config space (dangerous; root only)
-xxxx           Show hex-dump of the 4096-byte extended config space (root only)
-b              Bus-centric view (addresses and IRQ's as seen by the bus)
-D              Always show domain numbers

Resolving of device ID's to names:
-n              Show numeric ID's
-nn             Show both textual and numeric ID's (names & numbers)
-q              Query the PCI ID database for unknown ID's via DNS
-qq             As above, but re-query locally cached entries
-Q              Query the PCI ID database for all ID's via DNS

Selection of devices:
-s [[[[<domain>]:]<bus>]:][<slot>][.[<func>]]   Show only devices in selected slots
-d [<vendor>]:[<device>][:<class>]              Show only devices with specified ID's

Other options:
-i <file>       Use specified ID database instead of /usr/share/misc/pci.ids.gz
-p <file>       Look up kernel modules in a given file instead of default modules.pcimap
-M              Enable `bus mapping' mode (dangerous; root only)

PCI access options:
-A <method>     Use the specified PCI access method (see `-A help' for a list)
-O <par>=<val>  Set PCI access parameter (see `-O help' for a list)
-G              Enable PCI access debugging
-H <mode>       Use direct hardware access (<mode> = 1 or 2)
-F <file>       Read PCI configuration dump from a given file
```
<br/>

#### `lsmod`
Program which nicely formats the contents of the `/proc/modules`, showing what kernel modules are currently loaded.
```shell-session
$ lsmod --help

Usage: lsmod
```
<br/>

#### `lsusb`
Utility for displaying information about USB buses in the system and the devices connected to them.
```shell-session
$ lsusb --help

Usage: lsusb [options]...
List USB devices
  -v, --verbose
      Increase verbosity (show descriptors)
  -s [[bus]:][devnum]
      Show only devices with specified device and/or
      bus numbers (in decimal)
  -d vendor:[product]
      Show only devices with the specified vendor and
      product ID numbers (in hexadecimal)
  -D device
      Selects which device lsusb will examine
  -t, --tree
      Dump the physical USB device hierarchy as a tree
  -V, --version
      Show version of program
  -h, --help
      Show usage and help
```
<br/>

#### `modinfo`
Extracts information from the Linux Kernel modules given on the command line.
```shell-session
$ modinfo --help

Usage:
        modinfo [options] filename [args]
Options:
        -a, --author                Print only 'author'
        -d, --description           Print only 'description'
        -l, --license               Print only 'license'
        -p, --parameters            Print only 'parm'
        -n, --filename              Print only 'filename'
        -0, --null                  Use \0 instead of \n
        -F, --field=FIELD           Print only provided FIELD
        -k, --set-version=VERSION   Use VERSION instead of `uname -r`
        -b, --basedir=DIR           Use DIR as filesystem root for /lib/modules
        -V, --version               Show version
        -h, --help                  Show this help
```
<br/>

#### `modprobe`
Adds or remove modules from the Linux Kernel.
```shell-session
$ modprobe --help

Usage:
	modprobe [options] [-i] [-b] modulename
	modprobe [options] -a [-i] [-b] modulename [modulename...]
	modprobe [options] -r [-i] modulename
	modprobe [options] -r -a [-i] modulename [modulename...]
	modprobe [options] -c
	modprobe [options] --dump-modversions filename
Management Options:
	-a, --all                   Consider every non-argument to
	                            be a module name to be inserted
	                            or removed (-r)
	-r, --remove                Remove modules instead of inserting
	    --remove-dependencies   Also remove modules depending on it
	-R, --resolve-alias         Only lookup and print alias and exit
	    --first-time            Fail if module already inserted or removed
	-i, --ignore-install        Ignore install commands
	-i, --ignore-remove         Ignore remove commands
	-b, --use-blacklist         Apply blacklist to resolved alias.
	-f, --force                 Force module insertion or removal.
	                            implies --force-modversions and
	                            --force-vermagic
	    --force-modversion      Ignore module's version
	    --force-vermagic        Ignore module's version magic

Query Options:
	-D, --show-depends          Only print module dependencies and exit
	-c, --showconfig            Print out known configuration and exit
	-c, --show-config           Same as --showconfig
	    --show-modversions      Dump module symbol version and exit
	    --dump-modversions      Same as --show-modversions

General Options:
	-n, --dry-run               Do not execute operations, just print out
	-n, --show                  Same as --dry-run
	-C, --config=FILE           Use FILE instead of default search paths
	-d, --dirname=DIR           Use DIR as filesystem root for /lib/modules
	-S, --set-version=VERSION   Use VERSION instead of `uname -r`
	-s, --syslog                print to syslog, not stderr
	-q, --quiet                 disable messages
	-v, --verbose               enables more messages
	-V, --version               show version
	-h, --help                  show this help
```
<br/>

#### `runlevel`
Prints the previous and current SysV runlevel if they are known. The two runlevel characters are separated by a single space character. If a runlevel cannot be determined, N is printed instead. If neither can be determined, the word "unknown" is printed.
```shell-session
$ runlevel --help

runlevel [OPTIONS...]

Prints the previous and current runlevel of the init system.

     --help      Show this help
```
<br/>

#### `shutdown`
It may be used to halt, power-off or reboot the machine.
```shell-session
$ shutdown --help

shutdown [OPTIONS...] [TIME] [WALL...]

Shut down the system.

     --help      Show this help
  -H --halt      Halt the machine
  -P --poweroff  Power-off the machine
  -r --reboot    Reboot the machine
  -h             Equivalent to --poweroff, overridden by --halt
  -k             Don't halt/power-off/reboot, just send warnings
     --no-wall   Don't send wall message before halt/power-off/reboot
  -c             Cancel a pending shutdown
```

#### `systemctl`
It may be used to introspect and control the state of the "systemd" system and service manager.
```shell-session
$ systemctl --help

systemctl [OPTIONS...] {COMMAND} ...

Query or send control commands to the systemd manager.

  -h --help           Show this help
     --version        Show package version
     --system         Connect to system manager
     --user           Connect to user service manager
  -H --host=[USER@]HOST
                      Operate on remote host
  -M --machine=CONTAINER
                      Operate on local container
  -t --type=TYPE      List units of a particular type
     --state=STATE    List units with particular LOAD or SUB or ACTIVE state
  -p --property=NAME  Show only properties by this name
  -a --all            Show all properties/all units currently in memory,
                      including dead/empty ones. To list all units installed on
                      the system, use the &apos;list-unit-files&apos; command instead.
     --failed         Same as --state=failed
  -l --full           Don&apos;t ellipsize unit names on output
  -r --recursive      Show unit list of host and local containers
     --reverse        Show reverse dependencies with &apos;list-dependencies&apos;
     --job-mode=MODE  Specify how to deal with already queued jobs, when
                      queueing a new job
     --show-types     When showing sockets, explicitly show their type
     --value          When showing properties, only print the value
  -i --ignore-inhibitors
                      When shutting down or sleeping, ignore inhibitors
     --kill-who=WHO   Who to send signal to
  -s --signal=SIGNAL  Which signal to send
     --now            Start or stop unit in addition to enabling or disabling it
     --dry-run        Only print what would be done
  -q --quiet          Suppress output
     --wait           For (re)start, wait until service stopped again
     --no-block       Do not wait until operation finished
     --no-wall        Don&apos;t send wall message before halt/power-off/reboot
     --no-reload      Don&apos;t reload daemon after en-/dis-abling unit files
     --no-legend      Do not print a legend (column headers and hints)
     --no-pager       Do not pipe output into a pager
     --no-ask-password
                      Do not ask for system passwords
     --global         Enable/disable/mask unit files globally
     --runtime        Enable/disable/mask unit files temporarily until next
                      reboot
  -f --force          When enabling unit files, override existing symlinks
                      When shutting down, execute action immediately
     --preset-mode=   Apply only enable, only disable, or all presets
     --root=PATH      Enable/disable/mask unit files in the specified root
                      directory
  -n --lines=INTEGER  Number of journal entries to show
  -o --output=STRING  Change journal output mode (short, short-precise,
                             short-iso, short-iso-precise, short-full,
                             short-monotonic, short-unix,
                             verbose, export, json, json-pretty, json-sse, cat)
     --firmware-setup Tell the firmware to show the setup menu on next boot
     --plain          Print unit dependencies as a list instead of a tree

Unit Commands:
  list-units [PATTERN...]         List units currently in memory
  list-sockets [PATTERN...]       List socket units currently in memory, ordered
                                  by address
  list-timers [PATTERN...]        List timer units currently in memory, ordered
                                  by next elapse
  start NAME...                   Start (activate) one or more units
  stop NAME...                    Stop (deactivate) one or more units
  reload NAME...                  Reload one or more units
  restart NAME...                 Start or restart one or more units
  try-restart NAME...             Restart one or more units if active
  reload-or-restart NAME...       Reload one or more units if possible,
                                  otherwise start or restart
  try-reload-or-restart NAME...   If active, reload one or more units,
                                  if supported, otherwise restart
  isolate NAME                    Start one unit and stop all others
  kill NAME...                    Send signal to processes of a unit
  is-active PATTERN...            Check whether units are active
  is-failed PATTERN...            Check whether units are failed
  status [PATTERN...|PID...]      Show runtime status of one or more units
  show [PATTERN...|JOB...]        Show properties of one or more
                                  units/jobs or the manager
  cat PATTERN...                  Show files and drop-ins of one or more units
  set-property NAME ASSIGNMENT... Sets one or more properties of a unit
  help PATTERN...|PID...          Show manual for one or more units
  reset-failed [PATTERN...]       Reset failed state for all, one, or more
                                  units
  list-dependencies [NAME]        Recursively show units which are required
                                  or wanted by this unit or by which this
                                  unit is required or wanted

Unit File Commands:
  list-unit-files [PATTERN...]    List installed unit files
  enable [NAME...|PATH...]        Enable one or more unit files
  disable NAME...                 Disable one or more unit files
  reenable NAME...                Reenable one or more unit files
  preset NAME...                  Enable/disable one or more unit files
                                  based on preset configuration
  preset-all                      Enable/disable all unit files based on
                                  preset configuration
  is-enabled NAME...              Check whether unit files are enabled
  mask NAME...                    Mask one or more units
  unmask NAME...                  Unmask one or more units
  link PATH...                    Link one or more units files into
                                  the search path
  revert NAME...                  Revert one or more unit files to vendor
                                  version
  add-wants TARGET NAME...        Add &apos;Wants&apos; dependency for the target
                                  on specified one or more units
  add-requires TARGET NAME...     Add &apos;Requires&apos; dependency for the target
                                  on specified one or more units
  edit NAME...                    Edit one or more unit files
  get-default                     Get the name of the default target
  set-default NAME                Set the default target

Machine Commands:
  list-machines [PATTERN...]      List local containers and host

Job Commands:
  list-jobs [PATTERN...]          List jobs
  cancel [JOB...]                 Cancel all, one, or more jobs

Environment Commands:
  show-environment                Dump environment
  set-environment NAME=VALUE...   Set one or more environment variables
  unset-environment NAME...       Unset one or more environment variables
  import-environment [NAME...]    Import all or some environment variables

Manager Lifecycle Commands:
  daemon-reload                   Reload systemd manager configuration
  daemon-reexec                   Reexecute systemd manager

System Commands:
  is-system-running               Check whether system is fully running
  default                         Enter system default mode
  rescue                          Enter system rescue mode
  emergency                       Enter system emergency mode
  halt                            Shut down and halt the system
  poweroff                        Shut down and power-off the system
  reboot [ARG]                    Shut down and reboot the system
  kexec                           Shut down and reboot the system with kexec
  exit [EXIT_CODE]                Request user instance or container exit
  switch-root ROOT [INIT]         Change to a different root file system
  suspend                         Suspend the system
  hibernate                       Hibernate the system
  hybrid-sleep                    Hibernate and suspend the system
  suspend-then-hibernate          Suspend the system, wake after a period of
                                  time and put it into hibernate
```
<br/>

#### `telinit`
It may be used to change the SysV system runlevel.
```shell-session
$ telinit --help

telinit [OPTIONS...] {COMMAND}

Send control commands to the init daemon.

     --help      Show this help
     --no-wall   Don't send wall message before halt/power-off/reboot

Commands:
  0              Power-off the machine
  6              Reboot the machine
  2, 3, 4, 5     Start runlevelX.target unit
  1, s, S        Enter rescue mode
  q, Q           Reload init daemon configuration
  u, U           Reexecute init daemon
```
<br/>

### Topic 102: Linux Installation and Package Management

#### `grub-install`
It installs GRUB on your drive.

```shell-session
$ grub-install --help

Usage: grub-install [OPTION...] [OPTION] [INSTALL_DEVICE]
Install GRUB on your drive.

      --compress=no|xz|gz|lzo   compress GRUB files [optional]
  -d, --directory=DIR        use images and modules under DIR
                             [default=/usr/lib/grub/<platform>]
      --fonts=FONTS          install FONTS [default=unicode]
      --install-modules=MODULES   install only MODULES and their dependencies
                             [default=all]
  -k, --pubkey=FILE          embed FILE as public key for signature checking
      --locale-directory=DIR use translations under DIR
                             [default=/usr/share/locale]
      --locales=LOCALES      install only LOCALES [default=all]
      --modules=MODULES      pre-load specified modules MODULES
      --themes=THEMES        install THEMES [default=starfield]
  -v, --verbose              print verbose messages.
      --allow-floppy         make the drive also bootable as floppy (default
                             for fdX devices). May break on some BIOSes.
      --auto-nvram           only update NVRAM variables if possible. This
                             option is only available on EFI and IEEE1275
                             targets.
      --boot-directory=DIR   install GRUB images under the directory DIR/grub
                             instead of the boot/grub directory
      --bootloader-id=ID     the ID of bootloader. This option is only
                             available on EFI and Macs.
      --core-compress=xz|none|auto
                             choose the compression to use for core image
      --disk-module=MODULE   disk module to use (biosdisk or native). This
                             option is only available on BIOS target.
      --efi-directory=DIR    use DIR as the EFI System Partition root.
      --force                install even if problems are detected
      --force-file-id        use identifier file even if UUID is available
      --label-bgcolor=COLOR  use COLOR for label background
      --label-color=COLOR    use COLOR for label
      --label-font=FILE      use FILE as font for label
      --macppc-directory=DIR use DIR for PPC MAC install.
      --no-bootsector        do not install bootsector
      --no-extra-removable   Do not install bootloader code to the removable
                             media path. This option is only available on EFI.
      --no-nvram             don't update the `boot-device'/`Boot*' NVRAM
                             variables. This option is only available on EFI
                             and IEEE1275 targets.
      --no-rs-codes          Do not apply any reed-solomon codes when
                             embedding core.img. This option is only available
                             on x86 BIOS targets.
      --no-uefi-secure-boot  do not install an image usable with UEFI Secure
                             Boot, even if the system was currently started
                             using it. This option is only available on EFI.
      --product-version=STRING   use STRING as product version
      --recheck              delete device map if it already exists
      --removable            the installation device is removable. This option
                             is only available on EFI.
  -s, --skip-fs-probe        do not probe for filesystems in DEVICE
      --target=TARGET        install GRUB for TARGET platform
                             [default=x86_64-efi]; available targets: arm-efi,
                             arm-uboot, arm64-efi, i386-coreboot, i386-efi,
                             i386-ieee1275, i386-multiboot, i386-pc,
                             i386-qemu, i386-xen, ia64-efi, mips-arc,
                             mips-qemu_mips, mipsel-arc, mipsel-loongson,
                             mipsel-qemu_mips, powerpc-ieee1275,
                             sparc64-ieee1275, x86_64-efi, x86_64-xen
      --uefi-secure-boot     install an image usable with UEFI Secure Boot.
                             This option is only available on EFI and if the
                             grub-efi-amd64-signed package is installed.
  -?, --help                 give this help list
      --usage                give a short usage message
  -V, --version              print program version

Mandatory or optional arguments to long options are also mandatory or optional
for any corresponding short options.

INSTALL_DEVICE must be system device filename.
grub-install copies GRUB images into boot/grub.  On some platforms, it may
also install GRUB into the boot sector.

Report bugs to <bug-grub@gnu.org>.
```
<br/>

#### `grub-mkconfig`
It generates a grub config file.
```shell-session
$ grub-mkconfig --help

Usage: grub-mkconfig [OPTION]
Generate a grub config file

  -o, --output=FILE       output generated config to FILE [default=stdout]
  -h, --help              print this message and exit
  -v, --version           print the version information and exit

Report bugs to <bug-grub@gnu.org>.
```
<br/>

#### `ldconfig`
It creates the necessary links and cache to the most recent shared libraries found in the directories specified on the command line, in the file /etc/ld.so.conf, and in the trusted directories, /lib and /usr/lib (on some  64-bit  architectures such  as x86-64, lib and /usr/lib are the trusted directories for 32-bit libraries, while /lib64 and /usr/lib64 are used for 64-bit libraries).
```shell-session
$ ldconfig --help

Usage: ldconfig.real [OPTION...]
Configure Dynamic Linker Run Time Bindings.

  -c, --format=FORMAT        Format to use: new, old or compat (default)
  -C CACHE                   Use CACHE as cache file
  -f CONF                    Use CONF as configuration file
  -i, --ignore-aux-cache     Ignore auxiliary cache file
  -l                         Manually link individual libraries.
  -n                         Only process directories specified on the command
                             line.  Don't build cache.
  -N                         Don't build cache
  -p, --print-cache          Print cache
  -r ROOT                    Change to and use ROOT as root directory
  -v, --verbose              Generate verbose messages
  -X                         Don't update symbolic links
  -?, --help                 Give this help list
      --usage                Give a short usage message
  -V, --version              Print program version

Mandatory or optional arguments to long options are also mandatory or optional
for any corresponding short options.

For bug reporting instructions, please see:
<https://bugs.launchpad.net/ubuntu/+source/glibc/+bugs>.
```
<br/>

#### `ldd`
It prints  the  shared objects (shared libraries) required by each program or shared object specified on the command line.
```shell-session
$ ldd --help

Usage: ldd [OPTION]... FILE...
      --help              print this help and exit
      --version           print version information and exit
  -d, --data-relocs       process data relocations
  -r, --function-relocs   process data and function relocations
  -u, --unused            print unused direct dependencies
  -v, --verbose           print all information

For bug reporting instructions, please see:
<https://bugs.launchpad.net/ubuntu/+source/glibc/+bugs>.
```
<br/>

#### `objdump`
It displays information about one or more object files.
```shell-session
$ objdump --help

Usage: objdump <option(s)> <file(s)>
 Display information from object <file(s)>.
 At least one of the following switches must be given:
  -a, --archive-headers    Display archive header information
  -f, --file-headers       Display the contents of the overall file header
  -p, --private-headers    Display object format specific file header contents
  -P, --private=OPT,OPT... Display object format specific contents
  -h, --[section-]headers  Display the contents of the section headers
  -x, --all-headers        Display the contents of all headers
  -d, --disassemble        Display assembler contents of executable sections
  -D, --disassemble-all    Display assembler contents of all sections
  -S, --source             Intermix source code with disassembly
  -s, --full-contents      Display the full contents of all sections requested
  -g, --debugging          Display debug information in object file
  -e, --debugging-tags     Display debug information using ctags style
  -G, --stabs              Display (in raw form) any STABS info in the file
  -W[lLiaprmfFsoRtUuTgAckK] or
  --dwarf[=rawline,=decodedline,=info,=abbrev,=pubnames,=aranges,=macro,=frames,
          =frames-interp,=str,=loc,=Ranges,=pubtypes,
          =gdb_index,=trace_info,=trace_abbrev,=trace_aranges,
          =addr,=cu_index,=links,=follow-links]
                           Display DWARF info in the file
  -t, --syms               Display the contents of the symbol table(s)
  -T, --dynamic-syms       Display the contents of the dynamic symbol table
  -r, --reloc              Display the relocation entries in the file
  -R, --dynamic-reloc      Display the dynamic relocation entries in the file
  @<file>                  Read options from <file>
  -v, --version            Display this program's version number
  -i, --info               List object formats and architectures supported
  -H, --help               Display this information

 The following switches are optional:
  -b, --target=BFDNAME           Specify the target object format as BFDNAME
  -m, --architecture=MACHINE     Specify the target architecture as MACHINE
  -j, --section=NAME             Only display information for section NAME
  -M, --disassembler-options=OPT Pass text OPT on to the disassembler
  -EB --endian=big               Assume big endian format when disassembling
  -EL --endian=little            Assume little endian format when disassembling
      --file-start-context       Include context from start of file (with -S)
  -I, --include=DIR              Add DIR to search list for source files
  -l, --line-numbers             Include line numbers and filenames in output
  -F, --file-offsets             Include file offsets when displaying information
  -C, --demangle[=STYLE]         Decode mangled/processed symbol names
                                  The STYLE, if specified, can be `auto', `gnu',
                                  `lucid', `arm', `hp', `edg', `gnu-v3', `java'
                                  or `gnat'
      --recurse-limit            Enable a limit on recursion whilst demangling.  [Default]
      --no-recurse-limit         Disable a limit on recursion whilst demangling
  -w, --wide                     Format output for more than 80 columns
  -z, --disassemble-zeroes       Do not skip blocks of zeroes when disassembling
      --start-address=ADDR       Only process data whose address is >= ADDR
      --stop-address=ADDR        Only process data whose address is <= ADDR
      --prefix-addresses         Print complete address alongside disassembly
      --[no-]show-raw-insn       Display hex alongside symbolic disassembly
      --insn-width=WIDTH         Display WIDTH bytes on a single line for -d
      --adjust-vma=OFFSET        Add OFFSET to all displayed section addresses
      --special-syms             Include special symbols in symbol dumps
      --inlines                  Print all inlines for source line (with -l)
      --prefix=PREFIX            Add PREFIX to absolute paths for -S
      --prefix-strip=LEVEL       Strip initial directory names for -S
      --dwarf-depth=N        Do not display DIEs at depth N or greater
      --dwarf-start=N        Display DIEs starting with N, at the same depth
                             or deeper
      --dwarf-check          Make additional dwarf internal consistency checks.

objdump: supported targets: elf64-x86-64 elf32-i386 elf32-iamcu elf32-x86-64 a.out-i386-linux pei-i386 pei-x86-64 elf64-l1om elf64-k1om elf64-little elf64-big elf32-little elf32-big pe-x86-64 pe-bigobj-x86-64 pe-i386 plugin srec symbolsrec verilog tekhex binary ihex
objdump: supported architectures: i386 i386:x86-64 i386:x64-32 i8086 i386:intel i386:x86-64:intel i386:x64-32:intel i386:nacl i386:x86-64:nacl i386:x64-32:nacl iamcu iamcu:intel l1om l1om:intel k1om k1om:intel plugin

The following i386/x86-64 specific disassembler options are supported for use
with the -M switch (multiple options should be separated by commas):
  x86-64      Disassemble in 64bit mode
  i386        Disassemble in 32bit mode
  i8086       Disassemble in 16bit mode
  att         Display instruction in AT&T syntax
  intel       Display instruction in Intel syntax
  att-mnemonic
              Display instruction in AT&T mnemonic
  intel-mnemonic
              Display instruction in Intel mnemonic
  addr64      Assume 64bit address size
  addr32      Assume 32bit address size
  addr16      Assume 16bit address size
  data32      Assume 32bit data size
  data16      Assume 16bit data size
  suffix      Always display instruction suffix in AT&T syntax
  amd64       Display instruction in AMD64 ISA
  intel64     Display instruction in Intel64 ISA
Report bugs to <http://www.sourceware.org/bugzilla/>.
```
<br/>

#### `readelf`
It displays information about one or more ELF format object files.  The options control what particular information to display.
```shell-session
$ readelf --help

Usage: readelf <option(s)> elf-file(s)
 Display information about the contents of ELF format files
 Options are:
  -a --all               Equivalent to: -h -l -S -s -r -d -V -A -I
  -h --file-header       Display the ELF file header
  -l --program-headers   Display the program headers
     --segments          An alias for --program-headers
  -S --section-headers   Display the sections' header
     --sections          An alias for --section-headers
  -g --section-groups    Display the section groups
  -t --section-details   Display the section details
  -e --headers           Equivalent to: -h -l -S
  -s --syms              Display the symbol table
     --symbols           An alias for --syms
  --dyn-syms             Display the dynamic symbol table
  -n --notes             Display the core notes (if present)
  -r --relocs            Display the relocations (if present)
  -u --unwind            Display the unwind info (if present)
  -d --dynamic           Display the dynamic section (if present)
  -V --version-info      Display the version sections (if present)
  -A --arch-specific     Display architecture specific information (if any)
  -c --archive-index     Display the symbol/file index in an archive
  -D --use-dynamic       Use the dynamic section info when displaying symbols
  -x --hex-dump=<number|name>
                         Dump the contents of section <number|name> as bytes
  -p --string-dump=<number|name>
                         Dump the contents of section <number|name> as strings
  -R --relocated-dump=<number|name>
                         Dump the contents of section <number|name> as relocated bytes
  -z --decompress        Decompress section before dumping it
  -w[lLiaprmfFsoRtUuTgAckK] or
  --debug-dump[=rawline,=decodedline,=info,=abbrev,=pubnames,=aranges,=macro,=frames,
               =frames-interp,=str,=loc,=Ranges,=pubtypes,
               =gdb_index,=trace_info,=trace_abbrev,=trace_aranges,
               =addr,=cu_index,=links,=follow-links]
                         Display the contents of DWARF debug sections
  --dwarf-depth=N        Do not display DIEs at depth N or greater
  --dwarf-start=N        Display DIEs starting with N, at the same depth
                         or deeper
  -I --histogram         Display histogram of bucket list lengths
  -W --wide              Allow output width to exceed 80 characters
  @<file>                Read options from <file>
  -H --help              Display this information
  -v --version           Display the version number of readelf
Report bugs to <http://www.sourceware.org/bugzilla/>
```
<br/>

#### `update-grub`
It is a stub for running grub-mkconfig -o /boot/grub/grub.cfg to generate a grub2 config file.
```shell-session
$ update-grub --help

Usage: grub-mkconfig [OPTION]
Generate a grub config file

  -o, --output=FILE       output generated config to FILE [default=stdout]
  -h, --help              print this message and exit
  -v, --version           print the version information and exit

Report bugs to <bug-grub@gnu.org>.
```
<br/>


<style>
  ul {
    list-style-type: none;
  }
</style>
