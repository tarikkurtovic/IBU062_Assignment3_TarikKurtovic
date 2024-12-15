Devices in the network:

-Router:
Model: Cisco 2811
Interfaces:
   - FastEthernet 0/0: 168.90.0.1 (First Network)
   - FastEthernet 1/0: 210.3.14.1 (Second Network)

-Switches:
1. Switch 2
Model: Cisco 2960
Connected devices:
    -Laptop: 168.90.0.2
    -PC0: 168.90.0.3
    -PC1: 168.90.0.5
    -Server0: 168.90.0.4
    -PC3: 168.90.0.2(DHCP assigned)

2. Switch 3
Model: Cisco 2960
Connected devices:
    -PC2: 210.3.14.4
    -Server1: 210.3.14.2
    -Server2: 210.3.14.3
    -PC4: 210.3.14.2(DHCP assigned)

-------------------------------------------------------------------------
DHCP configuration steps:
Firstly, we click on router and open up Command Line Interface (CLI) where we press enter and we write this:

Router> enable
Router# configure terminal
Router(config)# ip dhcp pool FIRST_SWITCH
Router(dhcp-config)# network 168.90.0.0 255.255.0.0
Router(dhcp-config)# default-router 168.90.0.1
Router(dhcp-config)#exit

Router(config)# ip dhcp pool SECOND_SWITCH
Router(dhcp-config)# network 210.3.14.0 255.255.255.0
Router(dhcp-config)# default-router 210.3.14.1
Router(dhcp-config)# exit
Router(config)# exit
Router# exit
Router> enable
Router# show ip dhcp binding
Router# show ip interface brief