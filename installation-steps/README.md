#### Ephesoft Installation Steps

1. Select the Ephesoft AMI from the AWS console.
2. Review and Launch an EC2 Instance.
3. Note down the `IP address` of this Ephesoft EC2 Instance.
4. Add it to the Inbound Rules list of the ACS EC2 Instance's Security Group.
5. RDP and connect to the Ephesoft instance using `administrator/Ephe$0ft`.
```
P.S : If you are using a Mac, do install Remote Desktop Connection app.
```
6. Open a PowerShell in Administrator mode and run the following.
```
slmgr -rearm
```
7. Open port `8080` in the windows firewall to get access the web UI without doing an RDP, for future.
8. After successfully RDP-ing to the Ephesoft instance, open browser and go to http://localhost:8080/dcma/ using `ephesoft/demo`.
```
If you do not have a Customer Portal login please send a request to Tickets@ephesoft.com to request an account.
```
9. To submit a new license request please log in to License Management page (https://ephesoft.force.com/login?ec=302&startURL=%2Fs%2Flicenses).
10. The `details.properties` file is available at `Ephesoft Installation Folder\dependencies\license` directory.
11. Perform the following steps once you receive the ephesoft.lic file.
12. Copy the your ephesoft.lic file to the following location: `Ephesoft Installation Folder\dependencies\license-util` directory.
13. Open the command line by running it as `Administrator` and navigate to the `Ephesoft Installation Folder\dependencies\license-util` directory
14. Type `install-license.bat` and run it `TWICE`.
15. Restart the `Ephesoft services` to reset the license details.
16. Open browser and go to http://localhost:8080/dcma/ using `ephesoft/demo`.

```
Tip: If you have errors when trying to run Ephesoft, try the following:

Open regedit and set the User permissions to Full Control for the following Key: HKEY_LOCAL_MACHINE\SOFTWARE\JavaSoft\Prefs\com\ephesoft  then Repeat steps 2-3.
Please Re-run the Full.bat file located in the Ephesoft Installation Folder\dependencies\license directory and re-send the details.properties file to licenses@ephesoft.com.

Important: Licenses are based on MAC addresses, any changes to the MAC addresses on the machine require a new license. (The following devices use MAC addresses: NICs, WLAN, VPN, Virtual Network adapters, VM Network adapters and Bluetooth)
```
