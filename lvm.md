1. Насильно ресканим диски :
```bash
echo 1>/sys/class/block/sda/device/rescan
```
2. Ресайзним диск через cfdisk:
```bash
sudo cfdisk
```
Не забываем нажать Write

3. Проверяем тома :
```bash
sudo lsblk
```
4. Проверяем свободное место в lvm-группе :
```bash
sudo vgdisplay
```
5. Для расширения раздела LVM нужно сначала увеличить PV (Physical Volume):
```bash
sudo pvresize /dev/sda3
```
6. Теперь можно увеличить логический том. В этом примере мы расширим том за счет всего доступного пространства:
```bash
sudo lvextend -l +100%FREE /dev/mapper/ubuntu--vg-ubuntu--lv
```
7. Осталось расширить файловую систему. Для ext2, ext3 и ext4 выполните:
```bash
sudo resize2fs /dev/mapper/ubuntu--vg-ubuntu--lv
```
8. Проверьте свободное место:
```bash

```
