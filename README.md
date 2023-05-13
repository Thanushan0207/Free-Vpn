# Free-Vpn-Oracle-Cloud
VPN created with Oracle cloud and OpenVPN.

Videos of VPN in action:

https://github.com/Thanushan0207/Free-Vpn/assets/131554091/9916072c-7eb5-4d5e-a190-b7d0cd6d55b8

https://github.com/Thanushan0207/Free-Vpn/assets/131554091/14ecf2ac-ef25-4bfe-893f-2a59005407fc

Steps:

1. Create an Oracle Cloud account in the free tier. (You will have to input your payment information, but you won't be charged.)
2. After you have finished setting up your account, go to the menu and search for "Compartments".
3. After you click into "Compartments", click the "Create Compartment" button.
4. Input a name (e.g., Vpn-demo), a description (e.g., vpn), and leave the parent compartment value as it is.
5. Now in the top search bar, search for "OpenVPN", and it should be under the marketplace section. Click that link.
6. Set the version to the latest, which is the default, and your comparment value should be what you named your comparment you created, in this case "Vpn demo", Now click "Lanuch Instance".
7. In the placement section, make sure the capacity type is set to "On-demand capacity".
8. U In the image and shape section, make sure the image is "OpenVPN Access Server BYOL" and the shape is "VM.Standard.E2.1.Micro".
9. In the networking section, make sure you select "Create a new virtual cloud network", input a network name (e.g., vcn-1), and make sure the comparison is appropriate to the one you created. Then, select "Create new public subnet", input a subnet name (e.g., subnet-1), and make sure the comparison is appropriate to the comparison you created.
10. In the Add SSH Keys section, make sure you select "Generate a Key Pair for Me", and click "Save Private Key." Make sure you store this file somewhere accessible on your device, in a folder.
11. In the boot volume section, make sure "use in-taransit encryption", is selected, then click create.
12. Note down your public IP address.
13. Now open a terminal (e.g., CMD, Powershell, etc.) and open the folder directory you saved your ssh key in.
14. Run this command: ssh -i filename.key openvpnas@yourpublicIPaddress
15. Follow all the instructions and keep setting the default values, and once it generates a password for you, make sure you note that somewhere.
16. Now go back to Oracle Cloud and go into "Instances", by typing it into the menu.
17. Click on the interface you created and click on your subnet name, then click on the name in the security list.
18. Click add ingress rules, set source CIDR to "0.0.0.0/0," make sure IP protocol is "TCP", destination port should be "943,443", and fill out description (OpenVPN).
19. Add another ingress rule now, set source CIDR to "0.0.0.0/0", IP protocol to "UDP", destination port to "1194", and fill out the description (e.g., VPN Tunnel).
20. Now that you are all set on the Oracle cloud side, we can set up OpenVPN.
21. In your browser, type in: https://yourpublicIPaddress
22. If your browser says not to secure, just bypass it.
23. Now login, your user name is "openvpn," and the password is the password from step 15.
24. Now click go to admin panel" and login again with the credentials.
25. Go to configuration and select network settings.
26. Now in the hostname, replace it with your public ip address, hit enter, and then click update the root server.
27. Wait a minute, then go back into the OpenVPN Admin by typing the url from step 21, and follow the same login process.
28. Now go to configuration and click "VPN Settings".
29. In the DNS settings, make sure the have clients use a specific DNS server option is on and turn off the other two options. For primary DNS put "1.1.1.1" and for secondary DNS put "1.0.0.1", then hit enter and click update the root server.
30. Now under user management, go to user permissions.
31. Create a new username, then select the box to allow auto-login, and then click the box with the penicl icon inside it to create a local password and remember it.
32. Download the OpenVPN client for your operating system. https://openvpn.net/client/client-connect-vpn-for-windows/
33. Once you have downloaded it and set it up, click the plus icon, input your public IP address, then input your username and password you created in step 31, and check the boxes for "import" and "connect".
34. There will be a pop-up, just click accept.
35. Now you are connected and ready to go!

**Side note: This should be working fully free on Oracle Cloud, but just to make sure check your cost management in Oracle once in a while to double check you are not being charged.**






