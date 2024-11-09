ce you have downloaded the installation image, you can create a new VM.

1. Open VirtualBox and create a new VM (**Machine** > **New** or **Ctrl+N**) on which Kali Linux will be installed.
	![[Creating a New VM-20241109063623323.webp]]
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
			![[Creating a New VM-20241109063933190.webp]]
	- **Hard Disk**
	    - Create a virtual hard disk now.
	    - Set the virtual disk file location, for example, _D:\Virtual\VirtualBox\Kali_x6Kali_x64.vdi_
	        
	        It is recommended that you store virtual disk files in the VM folder (this folder is selected by default).
	        
	    - Set the virtual disk file size – at least 20 GB.
	    - _Hard disk file type_: VDI. A native VirtualBox format is selected.
	    - _Storage on physical disk_: Dynamically allocated (the analog of [thin provisioning](https://www.nakivo.com/blog/thick-and-thin-provisioning-difference/) in VMware).
	    
		Click **Create** to finish creating the new VM.
		![[Creating a New VM-20241109064115990.webp|459]]
3. After creating a new VM, you should configure some additional settings. Select your recently created virtual machine and open the **VM settings** by clicking the appropriate icon.
	![[Creating a New VM-20241109064252387.webp]]
	