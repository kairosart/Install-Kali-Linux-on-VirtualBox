
Kali Linux is a Debian-based Linux distribution developed for penetration testing and is especially useful for security specialists and enthusiasts. Kali Linux, formerly known as BackTrack Linux, includes a lot of tools and applications for network audits. Kali can be run as a Live DVD and can be installed on a computer as a host operating system (OS) as any other Linux.

However, it is not recommended that you use Kali as a general-purpose desktop operating system. At the same time, when using Kali Live DVD, settings are not saved after a system reboot. In this situation, virtual machines can be of great help.

Here we will explain how to install Kali Linux on VirtualBox with the basic network configuration. Windows is used as a host operating system in this article, but you can use this workflow on Linux and macOS.

![NAKIVO for Linux Machines Backup](Install%20Kali%20Linux%20on%20VirtualBox/Attachments/linux-1.webp)


## Preparation Steps For Installing Kali Linux on VirtualBox

### Downloading the Installation Image of Kali Linux

[Go to the official website](https://www.kali.org/get-kali/) and download the ISO image of Kali Linux. There are multiple 32-bit and 64-bit images. Each image allows you to select one of the graphical user interfaces (Gnome, KDE, XFCE, LXDE, etc.) during installation. The latest version is available on the main download page. You can also [download older Kali Linux images](https://old.kali.org/kali-images/) if needed.

Let’s download Kali Linux 64-bit v.2023.3 and then go over the installation process. You can download images via HTTP and Torrent protocols. Save the ISO file to a custom folder, for example, _D:\VirtualBox\kali-linux-2023.3-installer-amd64.iso_. You can also verify the SHA256 checksum to make sure that your image is consistent after finishing downloading.

![Downloading the installation ISO image of Kali Linux 64-bit](Install%20Kali%20Linux%20on%20VirtualBox/Attachments/downloading_the_installation_iso_image_of_kali_linux_64-bit.webp)

### Creating a New VM

Once you have downloaded the installation image, you can create a new VM.

1. Open VirtualBox and create a new VM (**Machine** > **New** or **Ctrl+N**) on which Kali Linux will be installed.
    
    ![Creating a new VM to install Kali Linux](Install%20Kali%20Linux%20on%20VirtualBox/Attachments/creating_a_new_vm_to_install_kali_linux.webp)
    
2. Set the following VM parameters in the appropriate sections:
    
    - **Name and Operating System**
        - _Name_: Kali_x64
        - _Machine Folder_: D:\Virtual\VirtualBox (Try not to use a system partition C: to store VMs).
        - _Type_: Linux
        - _Version_: Debian (64-bit)
    - **Hardware**
        - _Memory size_: 4096 MB.
            
            The VM memory size must be large enough to run a guest OS, though you should leave enough unallocated memory to run your host OS. In our example, a host machine with 16 GB of RAM is used, which leaves enough memory for a host OS.
            
        - _Processors_: 1 CPU
    
    ![Creating a new virtual hard disk](Install%20Kali%20Linux%20on%20VirtualBox/Attachments/creating_a_new_virtual_hard_disk.webp)
    
    - **Hard Disk**
        - Create a virtual hard disk now.
        - Set the virtual disk file location, for example, _D:\Virtual\VirtualBox\Kali_x6Kali_x64.vdi_
            
            It is recommended that you store virtual disk files in the VM folder (this folder is selected by default).
            
        - Set the virtual disk file size – at least 20 GB.
        - _Hard disk file type_: VDI. A native VirtualBox format is selected.
        - _Storage on physical disk_: Dynamically allocated (the analog of [thin provisioning](https://www.nakivo.com/blog/thick-and-thin-provisioning-difference/) in VMware).
    
    Click **Create** to finish creating the new VM.
    
    ![configuring virtual disk settings for the new VM](Install%20Kali%20Linux%20on%20VirtualBox/Attachments/configuring_virtual_disk_settings_for_the_new_vm.webp)
    
3. After creating a new VM, you should configure some additional settings. Select your recently created virtual machine and open the **VM settings** by clicking the appropriate icon.
    
    ![Windows 10 – starting a new VM created before](Install%20Kali%20Linux%20on%20VirtualBox/Attachments/windows_10_–_starting_a_new_vm_created_before.webp)
    

#### Display options

1. Go to **Display** > **Screen** and set Video Memory to **128 MB**. This will prevent the installer from hanging.
2. Next, select the checkbox **Enable 3D acceleration** (optional). It will be useful for applications that need 3D acceleration and help to avoid performance degradation.
    
    ![configuring display settings for the VM](Install%20Kali%20Linux%20on%20VirtualBox/Attachments/configuring_display_settings_for_the_vm.webp)
    

#### Network options

1. Go to the network settings and select the networking mode of the VM’s virtual network adapter.
2. Let’s select the **Bridged** mode to use the VM network adapter as you would for a physical network adapter of a host machine. In this case, the VM network adapter is connected to the same physical network as the host machine.
3. You can set additional options such as network adapter name, type, MAC address, etc.
    
    ![Configuring VM network settings](Install%20Kali%20Linux%20on%20VirtualBox/Attachments/configuring_vm_network_settings.webp)
    

#### Boot options

You have to insert your virtual ISO DVD image into the VM’s virtual DVD drive and then boot a virtual machine from that ISO disk.

1. In _VM settings_, go to **Storage**, select the IDE controller of your virtual optical drive (it is empty by default).
2. Click the empty status, then click the disc icon near IDE Secondary Master (IDE Secondary Device 0) and in the menu that opens, select **Choose Virtual Optical Disk File**.
3. Browse to the Kali Linux installation ISO image that you have downloaded from the official site (_kali-linux-2023.3-installer-amd64.iso_).
4. Hit **OK** to save settings.
    
    ![Selecting the ISO installation image to boot from](Install%20Kali%20Linux%20on%20VirtualBox/Attachments/selecting_the_iso_installation_image_to_boot_from.webp)
    

## Installing Kali Linux on VirtualBox: Step-by-step Guide

Now, you can start your new VM (_Kali_x64_ in this case) and begin the Kali installation.

1. Click the **Start** button in the VirtualBox window.
    
    ![starting a new VM for Kali Linux installation](Install%20Kali%20Linux%20on%20VirtualBox/Attachments/starting_a_new_vm_for_kali_linux_installation.webp)
    
2. After booting from a virtual DVD, you will see a boot menu where you can select boot options for Kali Linux, such as _Boot from Live DVD_, _Install_, _Graphical Install_, etc. Select **Graphical Install**. Press **Enter** to continue.
    
    ![Select Graphical install](Install%20Kali%20Linux%20on%20VirtualBox/Attachments/select_graphical_install.webp)
    
3. **Select a language**. Choose the language you wish to use for the installation process and the installed system. **English** is selected for our installation. Click the **Continue** button on each screen to move forward.
    
    ![Selecting the languages](Install%20Kali%20Linux%20on%20VirtualBox/Attachments/selecting_the_languages.webp)
    
4. **Select your location**. This option is used to set your time zone, time format, etc. **United States** is selected in our example.
    
    ![Select your location](Install%20Kali%20Linux%20on%20VirtualBox/Attachments/select_your_location.webp)
    
5. **Configure the keyboard**. Select your keyboard layout. We use **American English**.
    
    ![Configuring the keyboard](Install%20Kali%20Linux%20on%20VirtualBox/Attachments/configuring_the_keyboard.webp)
    
6. **Configure the network**. Enter the hostname for your Linux system, for example, _kali-virtualbox_.
    
    ![Configuring the hostname](Install%20Kali%20Linux%20on%20VirtualBox/Attachments/configuring_the_hostname.webp)
    
7. **Configure the domain name**. If you don’t use a domain in your network, you may leave this field empty.
    
    ![Configuring the domain name](Install%20Kali%20Linux%20on%20VirtualBox/Attachments/configuring_the_domain_name.webp)
    
8. **Set up users and passwords**. Enter the full name of your user that can be the same as the username or not. This user account will be used to log in to Kali Linux on VirtualBox. We create _user1_ for this purpose.
    
    ![Setting up users and passwords](Install%20Kali%20Linux%20on%20VirtualBox/Attachments/setting_up_users_and_passwords.webp)
    
9. **Enter a username for your account.** While the previous screen requested a full user name for the explanation of the user, this screen requests that you enter a username for the account registered in the Linux system. We create an account named _user1_.
    
    ![Creating a user account during Kali Linux installation](Install%20Kali%20Linux%20on%20VirtualBox/Attachments/creating_a_user_account_during_kali_linux_installation.webp)
    
10. **User password.** Enter the password for the created user and confirm this password.
    
    ![Entering a password for a user during Kali Linux installation](Install%20Kali%20Linux%20on%20VirtualBox/Attachments/entering_a_password_for_a_user_during_kali_linux_installation.webp)
    
11. **Configure the clock**. Now, you can select a precise time zone for your country.
    
    ![Configuring the clock](Install%20Kali%20Linux%20on%20VirtualBox/Attachments/configuring_the_clock.webp)
    
12. **Partition disks**. You can use manual and guided partitioning of disks. For the first time, you can select _Guided – use entire disk_. The entire disk will be used for creating one big partition.
    
    ![partitioning a disk for the VM where Kali will be installed](Install%20Kali%20Linux%20on%20VirtualBox/Attachments/partitioning_a_disk_for_the_vm_where_kali_will_be_installed.webp)
    
13. Confirm that you want to erase the disk. There’s no reason for concern in this case, as the empty 20-GB virtual disk is used for partitioning. Note that VirtualBox uses binary (real) Gigabytes while the Kali Linux installer uses decimal Gigabytes (where 1 GB = 1000 MB) – that’s why the number differs.
    
    ![Disk partitioning](Install%20Kali%20Linux%20on%20VirtualBox/Attachments/disk_partitioning.webp)
    
14. Select a preferred partitioning scheme for your virtual disk. Let’s select **All files in one partition**.
    
    ![Kali Linux disk partitioning – all files in one partition](Install%20Kali%20Linux%20on%20VirtualBox/Attachments/kali_linux_disk_partitioning_–_all_files_in_one_partition.webp)
    
15. Check the overview and select **Finish partitioning and write changes to disk**.
    
    ![Finishing disk partitioning](Install%20Kali%20Linux%20on%20VirtualBox/Attachments/finishing_disk_partitioning.webp)
    
16. Select **Yes** and confirm that you would like to write changes to the disk.
    
    ![confirmation of writing changes to the disk](Install%20Kali%20Linux%20on%20VirtualBox/Attachments/confirmation_of_writing_changes_to_the_disk.webp)
    
17. Wait for the system to be installed. As Kali Linux is being installed, the files are being copied to the virtual disk of the VM.
    
    ![Progress of installing Kali Linux on VirtualBox](Install%20Kali%20Linux%20on%20VirtualBox/Attachments/progress_of_installing_kali_linux_on_virtualbox.webp)
    
18. **Software selection**. Select the desktop environment for the graphical user interface of Kali Linux. You can use Xfce by default, which is a lightweight choice.
    
    ![Selecting Xfce as the default desktop environment for Kali Linux](Install%20Kali%20Linux%20on%20VirtualBox/Attachments/selecting_xfce_as_the_default_desktop_environment_for_kali_linux.webp)
    
19. **Install the GRUB boot loader on a hard disk**. Since there are no other operating systems and boot loaders on the virtual disk, it is necessary to install GRUB in this case. Select **Yes** to install GRUB.
    
    ![Installing the GRUB boot loader](Install%20Kali%20Linux%20on%20VirtualBox/Attachments/installing_the_grub_boot_loader.webp)
    
20. Select a disk on which to install GRUB. In our case, _/dev/sda_ is the necessary disk and is the only disk connected to a VM.
    
    ![Installing GRUB on /dev/sda](Install%20Kali%20Linux%20on%20VirtualBox/Attachments/installing_grub_on_devsda.webp)
    
21. **Finish the installation**. When the installation of Kali Linux on VirtualBox is complete, you will see a notification message. Now, you can reboot the virtual machine to boot the Kali Linux installed on the VirtualBox VM.
    
    ![Installation is complete](Install%20Kali%20Linux%20on%20VirtualBox/Attachments/installation_is_complete.webp)
    
22. After the reboot, you will see the login screen of Kali Linux. Enter your username (_user1_ in our case) and then enter the password set while installing Kali Linux on VirtualBox to sign in.
    
    ![Enter credentials to log in](Install%20Kali%20Linux%20on%20VirtualBox/Attachments/enter_credentials_to_log_in.webp)
    
23. Now you should see the Xfce desktop of Kali Linux installed on your VirtualBox virtual machine.
    
    ![Gnome desktop of Kali Linux](Install%20Kali%20Linux%20on%20VirtualBox/Attachments/gnome_desktop_of_kali_linux.webp)
    

## Installing VirtualBox Guest Additions on Kali Linux

VirtualBox Guest Additions improve the performance and user experience, including features such as Drag & Drop and Shared Clipboard. You can install VirtualBox guest additions by inserting the ISO image located in the VirtualBox installation folder by default, or you can install Guest Additions from online Linux repositories by using your Linux package manager. Manual installation is required for v.2019.2 and older. Kali v2019.3 and newer detect that Linux is installed inside a VM, and Guest additions are usually installed automatically.

To install Guest Additions, do the following (use **sudo** if you need to run commands as root):

1. Update the package repositories tree:
    
    `apt-get update`
    
2. Install VirtualBox Guest Additions with the command:
    
    `apt-get install -y virtualbox-guest-x11`
    
    ![installing VirtualBox Guest Additions with the package manager](https://www.nakivo.com/wp-content/uploads/2019/06/installing_virtualbox_guest_additions_with_the_package_manager.webp)
    
3. Reboot the machine:
    
    `init 6`
    
4. Verify that VirtualBox Guest Additions have been installed successfully. Check the VirtualBox Guest Additions version by getting information about the appropriate Linux kernel module. In order to see general information about the _vboxguest_ module, use the command:
    
    `modinfo vboxguest`
    
5. If you want to see the version of VirtualBox Guest Additions only, use:
    
    `lsmod | grep -io vboxguest | xargs modinfo | grep -iw version`
    
    ![Checking the version of VirtualBox Guest Additions](Install%20Kali%20Linux%20on%20VirtualBox/Attachments/checking_the_version_of_virtualbox_guest_additions.webp)
    
6. After installing VirtualBox Guest Additions on a VM, go to **VM settings** > **General** > **Advanced** and enable shared clipboard and Drag & Drop in bidirectional mode.
    
    ![enabling shared clipboard and Drag n Drop features](Install%20Kali%20Linux%20on%20VirtualBox/Attachments/enabling_shared_clipboard_and_drag_n_drop_features.webp)
    

## Connecting the USB Wi-Fi Adapter to the Kali Linux VM in VirtualBox

After completing the general VM configuration, let’s connect an external USB Wi-Fi network adapter to the VirtualBox VM running Kali Linux. You will be able to use all the advantages of the physical USB Wi-Fi adapter in the VM running Kali to audit wireless networks. VirtualBox Extension Pack must be installed to continue configuring the VM.

1. Insert your USB Wi-Fi adapter into the USB port of your physical computer.
2. Open VM settings and go to the **USB** section.
3. Tick the checkbox **Enable USB Controller**, Select **USB 2.0 (EHCI) Controller** (the Wi-Fi adapter used in the current example has USB 2.0 interface).
4. Then, add the **plus** icon and select the necessary USB device from the list of USB devices connected to your host machine. Later, you can untick the checkbox near the added USB device if that device does not need to be attached to the VM.
    
    ![Enabling a USB controller and connecting a USB Wi-Fi adapter to a VM with Kali Linux](Install%20Kali%20Linux%20on%20VirtualBox/Attachments/enabling_a_usb_controller_and_connecting_a_usb_wi-fi_adapter_to_a_vm_with_kali_linux.webp)
    
5. Start your _Kali_x64_ VM and log in to Kali Linux. Open the console (Terminal) and run the command to check your network interfaces and their configuration.
    
    `ifconfig`
    
    ![Checking network configuration of Kali Linux on VirtualBox](Install%20Kali%20Linux%20on%20VirtualBox/Attachments/checking_network_configuration_of_kali_linux_on_virtualbox.webp)
    
    The USB Wi-Fi adapter is connected and the name of its interface is _wlan0_. Let’s change the MAC address to go unnoticed.
    
6. Shutdown the Wi-Fi network interface:
    
    `ifconfig wlan0 down`
    
7. Change the MAC address of the wireless network adapter. Set the random MAC address with macchanger:
    
    `macchanger -r wlan0`
    
8. Enable the _wlan0_ network interface:
    
    `ifconfig wlan0 up`
    
9. Check whether the MAC address of your Wi-Fi network interface has been changed:
    
    `macchanger -s wlan0`
    
    `ifconfig wlan0`
    
    ![changing the MAC address of USB Wi-Fi adapter](Install%20Kali%20Linux%20on%20VirtualBox/Attachments/changing_the_mac_address_of_usb_wi-fi_adapter.webp)
    
    The MAC address has been changed successfully.
    
10. Enable the monitor mode for your wireless network interface with _airmon-ng_ (by default, a Wi-Fi adapter works in the managed mode). The monitor mode is required for security testing of Wi-Fi networks.
    
    `airmon-ng start wlan0`
    
11. If there are any processes that could cause trouble, kill them with the command:
    
    `airmon-ng check kill`
    
12. Run this command again:
    
    `airmon-ng start wlan0`
    
    ![starting airmon-ng to enable the monitor mode for the Wi-Fi adapter](Install%20Kali%20Linux%20on%20VirtualBox/Attachments/starting_airmon-ng_to_enable_the_monitor_mode_for_the_wi-fi_adapter.webp)
    
13. After starting the monitoring mode, a virtual _wlan0mon_ network interface is created. You can also change the MAC address of the wlan0mon network interface to a random MAC address.
    
    `ifconfig wlan0mon down`
    
    `macchanger -r wlan0mon`
    
    `ifconfig wlan0mon up`
    
14. Now run the _airodump-ng_ utility to view the networks whose signal level allows testing them:
    
    `airodump-ng wlan0mon`
    

As you can see on the screenshot below, the physical USB Wi-Fi adapter connected to the virtual machine running Kali Linux works fine. Wi-Fi access points and associated clients are displayed in the console.

![the Wi-Fi adapter is configured to monitor Wi-Fi networks](Install%20Kali%20Linux%20on%20VirtualBox/Attachments/the_wi-fi_adapter_is_configured_to_monitor_wi-fi_networks.webp)

Now that you know how to Install Kali Linux on VirtualBox manually and how to configure a wireless network adapter for using it in Kali Linux, you can continue testing Wi-Fi networks, but further configuration of Kali Linux for testing wireless networks is out of scope for this blog post.

## How to Install Kali Linux on VirtualBox Using a Preconfigured VM

Previously, we explained manual installation of Kali Linux on VirtualBox.

There are other two methods to install Kali Linux on VirtualBox VMs: deploying an OVA [VM template](https://www.nakivo.com/blog/vm-templates-a-to-z/) (deprecated) or deploying a downloaded preconfigured VM. We will use official pre-configured VM images of Kali Linux created by the Offensive Security team (Kali development team) for VirtualBox, VMware, Hyper-V and QEMU virtualization platforms.

1. [Download the appropriate OVA template](https://www.kali.org/get-kali/#kali-virtual-machines) from the official Offensive Security website. In this example, the _Kali Linux VirtualBox 64-bit OVA_ image is downloaded. Save the archive with the VM to a custom location.
    
    ![How to install Kali Linux on VirtualBox by using an OVA VM template](Install%20Kali%20Linux%20on%20VirtualBox/Attachments/how_to_install_kali_linux_on_virtualbox_by_using_an_ova_vm_template.webp)
    
2. Unpack contents from the archive with the available archiver, for example, 7zip.
3. Click **+ Add** to add an existing virtual machine to VirtualBox.
    
    ![Adding a Kali VM](Install%20Kali%20Linux%20on%20VirtualBox/Attachments/adding_a_kali_vm.webp)
    
4. Select the **.vbox** file extracted from the downloaded archive with the virtual disk file.
    
    ![Selecting a kali-linux-2023.3-virtualbox-amd64.vbox file](Install%20Kali%20Linux%20on%20VirtualBox/Attachments/selecting_a_kali-linux-2023_3-virtualbox-amd64_vbox_file.webp)
    
5. A VM has been imported. Start the VM with Kali Linux on VirtualBox by selecting this VM and clicking the **Start** button.
    
    ![VM has been imported](Install%20Kali%20Linux%20on%20VirtualBox/Attachments/vm_has_been_imported.webp)
    

The [default credentials](https://www.kali.org/docs/introduction/default-credentials/) to log in to Kali Linux on VirtualBox by using a downloaded VM are **kali**/**kali**. VirtualBox Guest Additions are pre-installed in this case. You can use a VM with Kali Linux deployed from a downloaded VM, similarly as you use the Kali Linux VM you have created and configured manually on VirtualBox.

## Kali Linux on VirtualBox Advantages

The advantages of using Kali Linux on VirtualBox are:

- By running multiple operating systems simultaneously (a host OS and a guest OS or multiple guests), you don’t need to reboot a computer as when using dual boot.
- A VM running Kali Linux is isolated from your host OS – running Kali on a VM in an isolated environment is secure.
- You can take a snapshot and roll back to the previous VM state if something goes wrong. The risk of harm to Kali Linux on a VM is minimal as a result.
- You can copy a configured VM on which Kali Linux is installed to other computers.
- You can attach physical USB devices, such as external network adapters, directly to a VM due to the VirtualBox USB pass-through feature.

Make sure that [VirtualBox is installed](https://www.nakivo.com/blog/use-virtualbox-quick-overview/) on your host operating system before continuing, [using the latest VirtualBox version](https://www.nakivo.com/blog/how-to-update-virtualbox/) if possible. Please [install VirtualBox Extension Pack](https://www.nakivo.com/blog/how-to-install-virtualbox-extension-pack/) on your host machine to use some advanced features such as USB pass-through.




