All devices in my Network:

1. Router
   Model - Cisco 1941
   Network 1 - IP address 168.90.0.1
   Network 2 - IP address 210.3.14.1

2. First Switch
   Model - Cisco 2960-24TT

3. Second Switch
   Model - Cisco 2960-24TT

4. First PC (Network 1)
   Model - PC
   IP address 168.90.0.2

5. Second PC (Network 1)
   Model - PC
   IP address 168.90.0.3

6. Laptop (Network 1)
   Model - PC (laptop)
   IP address 168.90.0.4

7. Server (Network 1)
   Model - Server
   IP address 168.90.0.5

8. First Server (Network 2)
   Model - Server
   IP address 210.3.14.2

9. Second Server (Network 2)
   Model - Server
   IP address 210.3.14.3

10. PC (Network 2)
    Model - PC
    IP address 210.3.14.4

11. New PC (Network 1)
    Model - PC
    IP address 168.90.0.6

12. New PC (Network 2)
    Model - PC
    IP address 210.3.14.5

Here is an explanation of how I set up DHCP:
I have accessed the router's CLI by clicking on the router and going to the CLI tab, and then entered global configuration mode:

Router> enable
Router# configure terminal

Then I have assigned IP addresses to the router's interfaces for both networks. Here's how I did it:
1. For Network 1:

Router(config)# interface gigabitethernet0/0
Router(config-if)# ip address 168.90.0.1 255.255.0.0

2. For Network 2:
Router(config)# interface gigabitethernet0/1
Router(config-if)# ip address 210.3.14.1 255.255.255.0

Then I exited the interface configuration:
Router(config-if)# exit

After I configured the router interfaces, I set up DHCP for the hosts on Network 1:
Router(config)# ip dhcp pool Network1
Router(dhcp-config)# network 168.90.0.0 255.255.0.0
Router(dhcp-donfig)# default-router 168.90.0.1
Router(dhcp-config)# exit

And then I set up DHCP for the hosts on Network 2:
Router(config)# ip dhcp pool Network2
Router(dhcp-config)# network 210.3.14.0 255.255.255.0
Router(dhcp-donfig)# default-router 210.3.14.1
Router(dhcp-config)# exit

That's how I set up DHCP on the router for two different networks.
