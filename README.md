# grub

## Задание
- Включить отображение меню Grub.
- Попасть в систему без пароля несколькими способами.
- Установить систему с LVM, после чего переименовать VG.

#### Включить отображение меню Grub.
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
#### Попасть в систему без пароля несколькими способами
1. Способ 1. init=/bin/bash
<img width="667" height="415" alt="image" src="https://github.com/user-attachments/assets/64a716fc-ef73-4787-adc8-1a57b5b53246" />
<img width="668" height="227" alt="image" src="https://github.com/user-attachments/assets/fd6a57c8-775f-4e37-84b5-8e0b082da6f5" />
2. Способ 2. Recovery mode
<img width="643" height="320" alt="image" src="https://github.com/user-attachments/assets/44e64845-7c65-4cc8-88ca-1b67146818d7" />

#### Установить систему с LVM, после чего переименовать VG.
```root@Ubuntu22:~# vgs
  VG        #PV #LV #SN Attr   VSize  VFree
  ubuntu-vg   1   1   0 wz--n- 18.22g 8.22g
root@Ubuntu22:~# lvs
  LV        VG        Attr       LSize  Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
  ubuntu-lv ubuntu-vg -wi-ao---- 10.00g                                          
root@Ubuntu22:~# vgrename ubuntu-vg ubuntu-otus
  Volume group "ubuntu-vg" successfully renamed to "ubuntu-otus"
root@Ubuntu22:~# vgs
  VG          #PV #LV #SN Attr   VSize  VFree
  ubuntu-otus   1   1   0 wz--n- 18.22g 8.22g
root@Ubuntu22:~# nano /boot/grub/grub.cfg
root@Ubuntu22:~# reboot
Broadcast message from root@Ubuntu22 on pts/1 (Sat 2026-02-07 04:31:55 UTC):
The system will reboot now!

root@Ubuntu22:~#
```
