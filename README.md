# Week-9-Assignment-Honeypot
> In this assignment, we had to setup a virtual machine as well as a honeypot, however, I ran into errors with creating them.
## Codepath Installation Guide

I went through Codepath's guide to install the Google Cloud Platform SDK, however, I was not able to make it work. Instead, I used the Windows installer, which allowed for an easy install of the SDK found here: https://cloud.google.com/sdk/downloads

<img src="https://i.imgur.com/y5ofYr4.png"/>

After Installing the SDK, I began to work on setting the MHN virtual Machine and honeypot. This part was a fairly straight process. On Codepath, they put up commands to create the VM and its respective firewall rules. Similar commands could be found on there to generate a honeypot along with its firewall rules

<img src="https://i.imgur.com/XbW4xyL.png"/>

My problem began with attempting to access the Admin console. The Codepath guide explains that after installing the VM with admin access and the honeypot, it is possible to access the admin console through the web browser by typing the the external ip of the admin vm while adding ":80" at the end of the URL to gain access. From there, the guide explained that should be able to deploy a script that installs the "Dionaea" honeypot, which logs malware activity directed to the honeypot. However, I was not able to access the admin console, so i had to install the Dionaea script some other way; you can see this issue in the GIF provided at the bottom. 

<img src="https://i.imgur.com/bXPQRkV.gif"/>

I took a look at the MHN repository and found a link to a website that contains a guide to install the Dionaea honeypot (https://www.edgis-security.org/single-post/dionaea-malware-honeypot); this did not work as well. After some googling, i found that the link provided was outdated. A redditor named "lrgame1983" provided a link (https://www.reddit.com/r/Malware/comments/4arc7w/installing_dionaea/) to the Dionaea website (https://dionaea.readthedocs.io/en/latest/installation.html#ubuntu-14-04) which has another installation guide for different OS's such as Linux, Ubuntu 16.04, and Ubuntu 14.04 (the one used for our VM and honeypot). Installation was successful, however, i still did not get results. I ran a command to generate a .JSON file to see whether my honeypot captured some activity, but it return a zero; shown in the following image.

<img src="https://i.imgur.com/T5QwVRP.png?1"/>

A classmate suggested that she found this other installation guide for MHN honeypot that allowed her to access the admin console to deploy the Dionaea script. I made another admin VM called admin1 to see if it would work. Installation was a success, but I had trouble accessing the admin console again. Re-ran the Dionaea script, which ran without error, but still did not get results; as shown in the following image.

<img src="https://i.imgur.com/RO3b0go.png?1"/>


