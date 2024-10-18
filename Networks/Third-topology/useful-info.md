# Topology n°3: Virtual Machines
Unfortunately we can not upload all the virtual disk used in ourr topology, but we can help you recreating our final testing environment. Notice that during this "guide" we will use [Proxmox](https://www.proxmox.com/en/) as virtual environment manager.

## Creating the virtual networks
Based on our topology design, we need 5 virtual network:
<ol>
    <li> Internet connection
    <li> Attacker - Router 1
    <li> Router 1 - Router 2
    <li> Router 2 - Zombie
    <li> Router 2 - Target
</ol>

The first one depends on your LAN and is useful to update the virtual machines and install dependencies. If you are using Proxmox, this network is generated automatically during the first setup.
The other 4 networks, should be set on "bridge" mode and have a prefix lenght of 24. You can choose different IP ranges, just make sure to not overlap them. 

## Creating virtual machines
Depending on the experiment you want to perform, you have to download the ISO files from the [official Ubuntu release archive](https://old-releases.ubuntu.com/releases/) and then prepare the virtual machine. In Proxmox we set for each machine ACTING AS HOST:
<ul>
    <li> 1 core
    <li> 1024MB RAM (we suggest 2048MB for Ubuntu version greater than 18.04)
    <li> 10GB HDD (please select SATA as virtual driver to avoid boot errors)
    <li> 2 Network Interface Cards:
        <ol>
            <li> Attached to one internal network
            <li> Attached to Internet virtual network (Disable it during experiments!)
        </ol>
</ul>

For virtual machines ACTING AS ROUTERS please add as many NICs as network managed by itself. Please refer to report.pdf for the topology schema.
Remember also to configure all thee routers with the correct routing path specified in the report. 

We strongly suggest to install Nmap to debug your testing environment and check if every VM is able to reach others machines. 

### Machine configuration
The VMs does not require special configuration. Just manually assign IP addresses according to the IP range you previously decided using the GUI if available; otherwise Netplan has done a great job during our experiments. IMPORTANT: remember to disable the NIC for Internet connection every time you perform an experiment (it will automatically activate at every boot). 

Remember also to disable SYN_COOKIES decommenting the line on the configuration file and set the value to 0; if you don't do that, SYN cookies will remain enabled also if by defaut should be disabled. 

### Useful information
If you perform multiple experiments on the backlog size, we suggest to reboot the VM in order to empty the backlog. If you are using our custom sockets, killing the process should be sufficient. 