NetBSD 9.0 Dreamcast Install Guide

(1)	format external IDE/PATA HDD under a netbsd distribution with a netbsd disklabel with a partition scheme like so:

	a: ffs - your main partition
	b: ffs - your dump partition 2GB is fine
	c: ffs - c should be left blank during newfs cmds. so skip formatting c
	d: ffs - 2GB is fine
	
	NOTE YOU NEED ALL 4 partitions for this release.
	
(2)	extract all sets via this cmd to your mount location for partition all

	'for file in *.gz; do sudo tar -zxvf $file -C /mnt/"your partition location"; done'

(3) go into partition a's dev directory. and run these commands.
		apply sudo if needed.
		
	./MAKEDEV wd0
	./MAKEDEV ld0
	./MAKEDEV all
	
(4) cd to partition a's etc directory.
	edit the rc.conf and delete all contents and replace with these:
	|
	rc_configured=YES
	hostname="dreamcast"
	|
	just those two lines.
	
(5) sync the mounted hdd and unmount it now its ready for booting on the dreamcast.

(6) burn a self-boot disk with your desired kernel.

(7) Enjoy!