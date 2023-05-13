# Free-Vpn
VPN created with Oracle cloud and OpenVPN.

Steps:

1. Create an Oracle Cloud account free tier (You will have to input your payment information, but you won't be charged.)
2. After you have finished setting up your account got to the meanu and search for "Compartments".
3. After you click into "Compartments", click the "Create Compartment" button.
4. Input a name (eg. Vpn-demo), a description (eg. vpn), and leave the parent compartment value to what it is.
5. Now in the top search bar search for "OpenVPN", and it should be under the marketplace section click that link.
6. Set the version to the latest which is the default and your comparment value should be what you named your comparment you created in this case "Vpn demo", now click "Lanuch Instance".
7. In the placement section make sure teh capcity typoe is set to "On-demand capacity".
8. UIn the image and shape section make sure the image is "OpenVPN Access Server BYOL" and the Shape is "VM.Standard.E2.1.Micro".
9. In teh networking section make sure you select "create new virtyal cloud network", input a netwok name (eg. vcn-1), and make sure the comparment is deftaued to teh comparment youc created. Then for slectc "Create new public subnet", input a subnet name (eg. subnet-1), and make sure the comparment is deftaued to teh comparment youc created.  
10. In the add SSH keys section make sure you select "generate a key pair for me", and click save private key. Make sure you store this file somehwere accessible on your device in a folder.
11. In the boot vloume section make sure "use in-taransit encryption", is selected, then  clcik create.
12. Now start your Vpn-sever, by clicking the start button, also note down you Public IPV4 Address.
13. Now open a terminal (eg. CMD, Powershell, etc.), and open the folder directory you saved your ssh key in.
14. Run this command: ssh -i filename.key openvpnas@yourpublicIPaddress
15. Follow all the instrustions and keep seletcing the default values, and once it genreates a password for you make sure you note that down somehwere.
16. Now go back to oracle cloud and go into "Instances", by typing it into the menu.
17. Click you insatnce you created and click on your subnet name, then click on the name onn the name in the securiti list. 
18. Click add ingress rules, set source CIDR to "0.0.0.0/0",make sure IP protocol is "TCP", esdtnationport should be "943,443", and fill out descrtion (OpenVPN). 
19. Add another ingress rule now, set source CIDR to "0.0.0.0/0", IP protocol to "UDP", destantion port to "1194", and fill out description (eg. VPN Tunnel)
20. Now you are allset on the Oracle cloud side, we can set up OpenVPN.
21. In your brwswer type in: https://yourpublicIPaddress
22. If uoir browser says not seruce juts bypass it.
23. Now logi, your use rname is "openvpn" and the password is the password from step 15.
24. Now click go to admin panel, and login again wth e credentials.
25. Go to configution and selet network settings.
26. Now in the hostname replace it with your public ip address, then hit enter, and then click update the rinnign server.
27. Wait a minute then, go back into the openadim vpn by typing teh url from step 21, and follow the same loggin in process.
28. Now go to configuration and click vpn settings.
29. In the DNS settings, make sure the have clients use spefoci DNS server option is on and turn off the other two options. For primary DNS put "1.1.1.1" and for secondary dns put "1.0.0.1", then hit enter, and then click update the rinnign server.
30. Now under user managment go to user permissions.
31. Create a new username, and them slect thenbox allow auto-login and then click teh box with the penicl icon inside it, create a local password and remeber it.
32. Download OpenVPN client for your operating system. https://openvpn.net/client/client-connect-vpn-for-windows/
33. Once you have dowlaoded and set it up click the plus icon, input your publuic ip adress, then input your username and password you created in step 31, and check the boxes import sutologin and connect after
34. there will will be a pop up, just click accpet.
35. Now you are connected and redy to go! 
**Side note: this shoudl be working fully free on oracle cloud but just to make sure check your cost managament in oracle once in a while to double check you ar enot being charged.**






