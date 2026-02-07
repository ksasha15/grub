# grub

## Задание
- Включить отображение меню Grub.
- Попасть в систему без пароля несколькими способами.
- Установить систему с LVM, после чего переименовать VG.

### Включить отображение меню Grub.
  ```
root@Ubuntu22:~# nano /etc/default/grub  
root@Ubuntu22:~# head /etc/default/grub  
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`( . /etc/os-release; echo ${NAME:-Ubuntu} ) 2>/dev/null || echo Ubuntu`
GRUB_CMDLINE_LINUX_DEFAULT=""
root@Ubuntu22:~# update-grub
update-grub             update-grub2            update-grub-gfxpayload
root@Ubuntu22:~# update-grub
Sourcing file `/etc/default/grub'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-6.8.0-90-generic
Found initrd image: /boot/initrd.img-6.8.0-90-generic
Warning: os-prober will not be executed to detect other bootable partitions.
Systems on them will not be added to the GRUB boot configuration.
Check GRUB_DISABLE_OS_PROBER documentation entry.
Adding boot menu entry for UEFI Firmware Settings ...
done
root@Ubuntu22:~# reboot

Broadcast message from root@Ubuntu22 on pts/1 (Sat 2026-02-07 02:51:51 UTC):

The system will reboot now!

root@Ubuntu22:~#
```
