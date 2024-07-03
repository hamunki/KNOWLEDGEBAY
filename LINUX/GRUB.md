GRUB Boot Menu/Shell
====================

The GRUB 2 command shell is just as powerful as the shell in legacy GRUB. You can use it to discover boot images, kernels, and root filesystems. In fact, it gives you complete access to all filesystems on the local machine regardless of permissions or other protections. Which some might consider a security hole, but you know the old Unix dictum: whoever has physical access to the machine owns it.
When you’re at the grub> prompt, you have a lot of functionality similar to any command shell such as history and tab-completion. The grub rescue> mode is more limited, with no history and no tab-completion.
If you are practising on a functioning system, press C when your GRUB boot menu appears to open the GRUB command shell. You can stop the bootup countdown by scrolling up and down your menu entries with the arrow keys. It is safe to experiment at the GRUB command line because nothing you do there is permanent. If you are already staring at the grub> or grub rescue>prompt then you’re ready to rock.
The next few commands work with both `grub>` and `grub rescue>`. The first command you should run invokes the pager, for paging long command outputs:

`grub> set pager=1`

There must be no spaces on either side of the equals sign. Now let’s do a little exploring. Type ls to list all partitions that GRUB sees:

`grub> ls`  
`(hd0) (hd0,msdos2) (hd0,msdos1)`

What’s all this `msdos` stuff? That means this system has the old-style MS-DOS partition table, rather than the shiny new Globally Unique Identifiers partition table (GPT). If you’re running GPT it will say `(hd0,gpt1)`. Now let’s snoop. Use the ls command to see what files are on your system:

`grub> ls (hd0,1)/`  
`lost+found/ bin/ boot/ cdrom/ dev/ etc/ home/  lib/ lib64/ media/ mnt/ opt/ proc/ root/ run/ sbin/ srv/ sys/ tmp/ usr/ var/ vmlinuz vmlinuz.old initrd.img initrd.img.old`

Hurrah, we have found the root filesystem. You can omit the msdos and gpt labels. If you leave off the slash it will print information about the partition. You can read any file on the system with the cat command:

`grub> cat (hd0,1)/etc/issue`  
`Ubuntu 14.04 LTS n l`

Reading `/etc/issue` could be useful on a multi-boot system for identifying your various Linuxes.

**Booting From grub>** This is how to set the boot files and boot the system from the grub> prompt. We know from running the ls command that there is a Linux root filesystem on `(hd0,1)`, and you can keep searching until you verify where `/boot/grub` is. Then run these commands, using your own root partition, kernel, and `initrd` image:

`grub> set root=(hd0,1)`  
`grub> linux /boot/vmlinuz-3.13.0-29-generic root=/dev/sda1`  
`grub> initrd /boot/initrd.img-3.13.0-29-generic`  
`grub> boot`

The first line sets the partition that the root filesystem is on. The second line tells GRUB the location of the kernel you want to use. Start typing `/boot/vmli`, and then use tab-completion to fill in the rest. Type `root=/dev/sd{n}` to set the location of the root filesystem. Yes, this seems redundant, but if you leave this out you’ll get a kernel panic. How do you know the correct partition? hd0,1 = /dev/sda1. hd1,1 = /dev/sdb1. hd3,2 = /dev/sdd2. I think you can extrapolate the rest. The third line sets the initrd file, which must be the same version number as the kernel.

The fourth line boots your system.

### Making Permanent Repairs

When you have successfully booted your system, run these commands to fix GRUB permanently:

`$ update-grub`  
`Generating grub configuration file ...
Found background: /usr/share/images/grub/Apollo_17_The_Last_Moon_Shot_Edit1.tga
Found background image: /usr/share/images/grub/Apollo_17_The_Last_Moon_Shot_Edit1.tga
Found linux image: /boot/vmlinuz-3.13.0-29-generic
Found initrd image: /boot/initrd.img-3.13.0-29-generic
Found linux image: /boot/vmlinuz-3.13.0-27-generic
Found initrd image: /boot/initrd.img-3.13.0-27-generic
Found linux image: /boot/vmlinuz-3.13.0-24-generic
Found initrd image: /boot/initrd.img-3.13.0-24-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
done`

`$ grub-install /dev/sda`  
`Installing for i386-pc platform.`  
`Installation finished. No error reported.`

When you run `grub-install` remember you’re installing it to the boot sector of your hard drive and not to a partition, so do not use a partition number like `/dev/sda1`.

#### Sources

* https://superuser.com/questions/1237684/how-to-boot-from-grub-shell
* https://www.linuxfoundation.org/blog/blog/classic-sysadmin-how-to-rescue-a-non-booting-grub-2-on-linux