# VMware

### VMware Command Line Interface (CLI)

#### Basic VM Management

- **List All Virtual Machines:**
  ```bash
  vmrun list
  ```

- **Start Virtual Machine:**
  ```bash
  vmrun start "path/to/vm.vmx"
  ```

- **Stop Virtual Machine:**
  ```bash
  vmrun stop "path/to/vm.vmx"
  ```

- **Reset Virtual Machine:**
  ```bash
  vmrun reset "path/to/vm.vmx"
  ```

- **Suspend Virtual Machine:**
  ```bash
  vmrun suspend "path/to/vm.vmx"
  ```

- **Delete Virtual Machine:**
  ```bash
  vmrun deleteVM "path/to/vm.vmx"
  ```

#### VM Configuration

- **Modify VM Memory:**
  ```bash
  vmware-vim-cmd vmsvc/reconfig vmid memsize 2048
  ```

- **Modify VM CPU Count:**
  ```bash
  vmware-vim-cmd vmsvc/reconfig vmid numvcpus 2
  ```

- **Set VM to Autostart:**
  ```bash
  vim-cmd hostsvc/autostartmanager/update_autostartentry vmid autostart-enabled true
  ```

#### Snapshot Management

- **Create Snapshot:**
  ```bash
  vmrun snapshot "path/to/vm.vmx" "Snapshot Name"
  ```

- **List Snapshots:**
  ```bash
  vmrun listSnapshots "path/to/vm.vmx"
  ```

- **Revert to Snapshot:**
  ```bash
  vmrun revertToSnapshot "path/to/vm.vmx" "Snapshot Name"
  ```

- **Delete Snapshot:**
  ```bash
  vmrun deleteSnapshot "path/to/vm.vmx" "Snapshot Name"
  ```

#### Cloning and Exporting

- **Clone Virtual Machine:**
  ```bash
  vmrun clone "path/to/source.vmx" "path/to/destination.vmx" full
  ```

- **Export Virtual Machine to OVF:**
  ```bash
  ovftool "path/to/source.vmx" "path/to/destination.ovf"
  ```

- **Import OVF to Virtual Machine:**
  ```bash
  ovftool "path/to/source.ovf" "path/to/destination.vmx"
  ```

#### Network Configuration

- **Configure Network Adapter:**
  ```bash
  vmware-vim-cmd vmsvc/device.connection vmid adapterid connect
  ```

- **Add Network Adapter:**
  ```bash
  vmware-vim-cmd vmsvc/device.add vmid adapterid
  ```

- **Remove Network Adapter:**
  ```bash
  vmware-vim-cmd vmsvc/device.remove vmid adapterid
  ```

#### Disk Management

- **Create Virtual Disk:**
  ```bash
  vmware-vdiskmanager -c -t 0 -s 20GB -a lsilogic "path/to/disk.vmdk"
  ```

- **Expand Virtual Disk:**
  ```bash
  vmware-vdiskmanager -x 40GB "path/to/disk.vmdk"
  ```

- **Defragment Virtual Disk:**
  ```bash
  vmware-vdiskmanager -d "path/to/disk.vmdk"
  ```

- **Shrink Virtual Disk:**
  ```bash
  vmware-vdiskmanager -k "path/to/disk.vmdk"
  ```

#### Guest Operations

- **Execute Command in Guest:**
  ```bash
  vmrun -gu username -gp password runProgramInGuest "path/to/vm.vmx" "/bin/ls"
  ```

- **Copy File to Guest:**
  ```bash
  vmrun -gu username -gp password copyFileFromHostToGuest "path/to/vm.vmx" "hostfile.txt" "guestfile.txt"
  ```

- **Copy File from Guest:**
  ```bash
  vmrun -gu username -gp password copyFileFromGuestToHost "path/to/vm.vmx" "guestfile.txt" "hostfile.txt"
  ```

- **Install VMware Tools in Guest:**
  ```bash
  vmrun -gu username -gp password installTools "path/to/vm.vmx"
  ```

#### ESXi and vCenter Operations

- **Connect to ESXi Host:**
  ```bash
  vim-cmd vmsvc/getallvms
  ```

- **Create New VM on ESXi:**
  ```bash
  vim-cmd solo/registervm "path/to/vm.vmx"
  ```

- **Start VM on ESXi:**
  ```bash
  vim-cmd vmsvc/power.on vmid
  ```

- **Stop VM on ESXi:**
  ```bash
  vim-cmd vmsvc/power.off vmid
  ```

- **List Datastores:**
  ```bash
  vim-cmd hostsvc/datastore/listsummary
  ```

- **Create Datastore:**
  ```bash
  esxcli storage filesystem mkdir -p "/vmfs/volumes/datastore_name"
  ```

- **Remove Datastore:**
  ```bash
  esxcli storage filesystem delete "/vmfs/volumes/datastore_name"
  ```

#### Advanced Operations

- **Configure VM Autostart:**
  ```bash
  vim-cmd hostsvc/autostartmanager/update_autostartentry vmid autostart-enabled true
  ```

- **Enable SSH on ESXi:**
  ```bash
  vim-cmd hostsvc/enable_ssh
  ```

- **Disable SSH on ESXi:**
  ```bash
  vim-cmd hostsvc/disable_ssh
  ```

- **Check Host System Health:**
  ```bash
  esxcli hardware health status get
  ```

- **Upgrade ESXi Host:**
  ```bash
  esxcli software profile update -d "/path/to/ESXi_update.zip" -p "ESXi-6.5.0-20171004001-standard"
  ```

### Summary

This comprehensive list of VMware CLI commands covers a wide range of tasks for managing virtual machines, including basic VM operations, configuration, snapshot management, cloning, exporting, network and disk management, guest operations, and advanced ESXi/vCenter operations. These commands provide the necessary tools for administrators to efficiently manage and automate their VMware environments.
