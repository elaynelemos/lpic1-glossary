# Glossary of Commands for LPIC-1
**Note:** the list of commands is based on the topic order in its first appearance at the [learning material](https://learning.lpi.org/en/learning-materials/learning-materials/). Although inside each topic the commands were ordered alphabetically. The sources of each description are their respective [man pages](https://www.kernel.org/doc/man-pages/) and usage/help shorts from command.

## Contents

### 101 Exam
  - [Topic 101: System Architecture](#topic-101-system-architecture)
  - Topic 102: Linux Installation and Package Management #TODO
  - Topic 103: GNU and Unix Commands #TODO
  - Topic 104: Devices, Linux Filesystems, Filesystem Hierarchy Standard #TODO

### 102 Exam #TODO
  - Topic 105: Shells and Shell Scripting
  - Topic 106: User Interfaces and Desktops
  - Topic 107: Administrative Tasks
  - Topic 108: Essential System Services
  - Topic 109: Networking Fundamentals
  - Topic 110: Security


## 101 Exam

### Topic 101: System Architecture

**`dmesg`**: It is used to examine or control the kernel ring buffer. The default action is to display all messages from the kernel ring buffer.
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

**`journalctl`**: It may be used to query the contents of the systemd journal as written by systemd-journald.service.
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

**`lspci`**: Utility for displaying information about PCI buses in the system and devices connected to them. By default, it shows a brief list of devices.
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

**`lsmod`**: Program which nicely formats the contents of the `/proc/modules`, showing what kernel modules are currently loaded.
```shell-session
$ lsmod --help

Usage: lsmod
```
<br/>

**`lsusb`**: Utility for displaying information about USB buses in the system and the devices connected to them.
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

**`modinfo`**: Extracts information from the Linux Kernel modules given on the command line.
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

**`modprobe`**: Adds or remove modules from the Linux Kernel.
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
