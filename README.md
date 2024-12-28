# My Arch Linux Installation guid.

> First make a boot-able USB device for installing Arch linux iso file.You can get it from [Arch Linux](https://archlinux.org/)

## Prerequisites for the installation

### Modifying BIOS settings.

1. Enable USB Boot
2. Disable secure boot
3. Then clear all secure boot keys.
4. At last save changes than exit

> Remember to Have disk space of 20gb or more for installation.Then boot into USB device and Arch Linux Install media. You will see a terminal for installation.

### On Arch terminal.

1. set font
   > `setfont ter-120n`
2. then set wifi connection

   > `iwctl` then `station wlan0 get-networks` then `station wlan0 connect <network-name >` after giving the password to the network `exit` and `ping -c 5 archlinux.org` to confirm the wifi connection.
   > DONE

3. update the packages

   > `pacman -Sy archlinux-keyring`

4. to make the /mnt and /mnt/boot directories do the fallowing

   - `lsblk` then edit the dir in `cfdisk /dev/mvme0n1 or sda dir `
   - And make the unallocated space to linux file type using new option and then write the changes and quit.
   - `mkfs.ext4 /dev/dir` for the linux filesystem to format
   - Now mount the dir to /mnt `mount /dev/dir /mnt`

- (OPTIONAL) :) Then `mkfs.fat -F32 /dev/your-dir` for the EFI file to format but don't do it if doing dual-boot and `mkdir /mnt/boot` then `mount /dev/dir /mnt/boot`
- `lsblk` to see the mnt created

5. Now run `archinstall` and after installation and perform post installation config on and Yes.

---

### Now to grub-install

1. `pacman -Syu grub efibootmgr dosfstools mtools`
2. `grub-install --target=x86_64-efi --efi-directory=/boot --bootloader-id=GRUB`
3. `grub-mkconfig -o /boot/grub/grub.cfg`

then exit and shutdown
