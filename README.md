# Week-9-Assignment-Honeypot
> In this assignment, we had to setup a virtual machine as well as a honeypot, however, I ran into errors with creating them.
>> Week 9 Lab is at the bottom, after Week 9 Assignment
## Codepath Installation Guide

I went through Codepath's guide to install the Google Cloud Platform SDK, however, I was not able to make it work. Instead, I used the Windows installer, which allowed for an easier install of the SDK found here: https://cloud.google.com/sdk/downloads

<img src="https://i.imgur.com/y5ofYr4.png"/>

After Installing the SDK, I began to work on setting the MHN virtual Machine and honeypot. This part was a fairly straight process. On Codepath, they put up commands to create the VM and its respective firewall rules. Similar commands could be found on there to generate a honeypot along with its firewall rules

<img src="https://i.imgur.com/XbW4xyL.png"/>

My problem began with attempting to access the Admin console. The Codepath guide explains that after installing the VM with admin access and the honeypot, it is possible to access the admin console through the web browser by typing the external ip of the admin vm while adding port number ":80" at the end of the URL to gain access. From there, the guide explained that, through the admin console, a user  should be able to deploy a script that installs the "Dionaea" honeypot, which logs malware activity directed to the honeypot. However, I was not able to access the admin console, so I had to install the Dionaea script some other way; you can see this issue in the GIF provided at the bottom. 

<img src="https://i.imgur.com/bXPQRkV.gif"/>

I took a look at the MHN repository and found a link to a website that contains a guide to install the Dionaea honeypot (https://www.edgis-security.org/single-post/dionaea-malware-honeypot); this did not work as well. After some googling, I found that the link provided was outdated. A redditor named "lrgame1983" (https://www.reddit.com/r/Malware/comments/4arc7w/installing_dionaea/) provided a link to the Dionaea website (https://dionaea.readthedocs.io/en/latest/installation.html#ubuntu-14-04) which has another installation guide for different OS's such as Linux, Ubuntu 16.04, and Ubuntu 14.04 (the one used for our VM and honeypot). Installation was successful, however, I still did not get results. I ran a command to generate a .JSON file to see whether my honeypot captured some activity, but it return a zero; as shown in the following image:

<img src="https://i.imgur.com/T5QwVRP.png?1"/>

A classmate suggested that she found this other installation guide for MHN honeypot that allowed her to access the admin console to deploy the Dionaea script (https://www.attacusatlas.com/how-to-set-up-dionaea-honeypot-with-modern-honey-network-and-slack-alerts/). We speculated that this differented method could have corrected what Codepath provided since they were not able to obtain access to the Admin console for the honeypot as well. After this trying this different method, she was able to gain access. Since this could be a potential solution, I made another admin VM called admin1 to see if it would work. Installation was a success, but I had trouble accessing the admin console again. I re-ran the Dionaea script, which ran without error, but still did not get results; as shown in the following image.

<img src="https://i.imgur.com/RO3b0go.png?1"/>

In the end, I was not able get the environment to work.
----------------------------------------------------------------------------------------------------------------------------------------

# WEEK 9 LAB

## Milestone 0: Networking Toolbox

[Running ifconfig / ipconfig / ip]

* What is your primary interface’s IP address? Is it different from your public IP? Why or why not?

> My device’s primary IP is 192.168.1.68. It is different than my Public IP. The reason being is that my private IP, through the use of NAT, will convert into a public IP to gain access to the internet.

* What is the MAC address of your primary interface?

> 0C-84-DC-B1-CB-A0

<img src="https://i.imgur.com/G0fHrBN.png?2"/>

* Identify and understand your loopback interface

> My loopback (127.0.0.1) is used to experiment with software within the localhost. This loopback exists in all host machines.

<img src="https://i.imgur.com/3MkILo4.png?1"/>

[Using Ping]

* What is the IP address of codepath.com?

> 198.58.125.217

* What is the IP address of google.com?

> They use IPv6: 2607:f8b0:4000:80c::200e

<img src="https://i.imgur.com/XdEyVwG.png?1"/>

* Why would the IP address of google.com change between runs or from different locations?

> I do not understand the question. I am assuming that pinging google.com should return different results? If that is the case, then it does not occur when I ping the site.

<img src="https://i.imgur.com/yth2AAO.png?1"/>

[Using Nslookup]

* Using the IP for codepath.com from the previous, pass it to nslookup

<img src="https://i.imgur.com/3LqvV8W.png?1"/>

* Does the domain return from nslookup match? If not, why not?

> Instead of returning codepath.com, it returns thecodepath.com. Could be that the DNS server responded with a server that would respond to my inquiry faster, thus sending thecodepath.com instead of codepath.com

[Using Traceroute]

* Compare the traceroutes for codepath.com and google.com

<img src="https://i.imgur.com/P7XE7mT.png?1"/>

* How many of the hops are the same? what accounts for this?

> 4 hops are the same. The first hop, refers to my router. The remaining 3 hops could be that those are the best paths to take before deviating.

* Which has more hops? What accounts for the difference?

> Google.com has more hops than codepath.com. What could account for the difference is that google simply takes longer to reach than codepath, which would allow for a couple more hops.

[Using Telnet]

* What’s one thing that makes telnet insecure?

> Connecting to the internet with telnet, will send information as cleartext, so anyone with a packet sniffer would be able to capture this information and be able to view and understand it.

* Can you telnet to codepath.com? What port is open and why?

> "telnet google.com 80" will connect to codepath. And entering "GET / HTTP/1.1" will return a page, as shown in the top terminal. This means that port 80 is open since I was able to connect to it. 

> "telnet codepath.com" will results in an error stating that a connection through port 23 could not be made, as shown in the bottom terminal. This means that port 23 is closed on codepath

<img src="https://i.imgur.com/O8pbUj3.png?1"/>

[Curl and Wget]

* Identify some differences between the two

> Wget is a command utility that is meant retrieve or download content immediately. It is also independent of any libraries.

> cURL is command utility that can be used along with proxies such as TOR. cURL can also be used to work with email services (send/retrieve)

[https://www.maketecheasier.com/curl-vs-wget/]

* Which would you be more likely to use for interacting with a RESTful API from the command line

> I would suppose that cURL would be the best choice. cURL was developed with a library to make transferring files easier when accessing the internet via command tool. It has countless protocols that it supports which widens its usefulness

* Which support recursive downloading?

> Wget supports recursive downloading

* Which are you more likely to find pre-installed on a Linux OS?

> Wget would be the one come pre-installed on a Linux OS

* What is the syntax for each for downloading a file to the current directory?

> Wget: wget -P  www.example.com

> cURL:  curl -O http://example.com

[Ssh and Scp]

* Why is the key authentication preferred to passwords?

> Using keys to authenticate could be safer than using passwords. These keys can be encrypted, making it difficult or impossible to crack, which make them more reliable than passwords since people are known to create weak passwords.

* What is the syntax for copying a file from a local folder to a remote one?

> scp -r [path where your file is currently located (separate directories with backslashes)] user@host: [path where you would like to store your file (use forward slashes to separate directories)]

## Milestone 1: Security-Flavored Net Tools

### Challenge 1: Run nmap against your localhost IP to see all open ports:

* See how many of the ports you can match to services (try shutting Docker or Virtualbox and re-running nmap)

> Nothing occurred when shutting Vbox down 

<img src="https://i.imgur.com/MyaDKu0.png?1"/>

### Challenge 2: Map your home LAN using nmap:

<img src="https://i.imgur.com/taMwOTb.png?1"/>

## Milestone 2: Grabbing Packets with tcpdump

### Challenge 1: Determine the IP address for codepath.com and use tcpdump to display packets with that IP as the destination. Then open http://www.codepath.com in the browser and check the output. Notice the output displays the HTTP requests in addition to the packets

<img src="https://i.imgur.com/8Vrnyx0.png?1"/>

* How many requests to load the main codepath.com page?

> 43 HTTP requests

* What type of resource accounts for most of the requests?

> Both images and javascript accounts for most of the requests

* Now try the same exercise with https://security.codepath.com. what differences do you see in the output? What accounts for those differences?

> I don’t see any request packets. I am uncertain why http requests were not captured. I could only assume it might have something to do with the fact that security.codepath.com uses port 443 (https) unlike codepath.com that runs on port 80 (http).

<img src="https://i.imgur.com/jhdhjym.png?1"/>

### Challenge 2: you can also monitor DNS queries on port 53 with tcpdump. Use this to determine the IP of your primary DNS:

* Listen for DNS queries on port 53: sudo tcpdump -vvv -s 0 -l -n port 53

* Think of a domain name that probably exists (common word or phrase + .com) but that you’ve never visited before (suggestion: zombo.com) and open it in a browser.

* Look at the tcpdump output for the UDP packets trying to resolve the domain. The destination IP should be the DNS

> I chose hello.com as my choice. Found that the address, 216.239.36.21, resolved into its domain name of hello.com

<img src="https://i.imgur.com/r67uQUd.png?1"/>

## Milestone 3: Hello, Wireshark

### Challenge: Get a capture of the baseline traffic on your wireless interface. Start by closing every running app on your system: every window, every tab, every shell… try to go completely dark (restart your system first if you need to). Then open Wireshark (which should be the only app running) and start capturing on your primary interface

<img src="https://i.imgur.com/I49Wv2J.gif"/>

* Look at the source and destination IPs; how much of the traffic is inbound vs. outbound?

> Looking at the captured data, most of it appears to be inbound traffic (my IP constantly being the destination: 192.168.1.68) 

* Try nslookup on a couple of IPs that aren’t in your network. See if you can figure out who those IPs belong to

<img src="https://i.imgur.com/Put98Po.png?1"/>

* Try to identify traffic associated with at least of process on your host that’s either part of the OS itself or it auto-launched at startup

> I am not sure what this question is asking

* See if you can spot any ARP packets used to resolve IPs to MAC addresses

> You can see that my Sender IP is shown below my Sender MAC, whereas the Target IP is shown below the Target Broadcast MAC:

<img src="https://i.imgur.com/C6in1y7.png?1"/>

## Milestone 4: Traffic Analysis – Mike’s Computer is Acting Weird

<img src="https://i.imgur.com/R8amiwI.png?1"/>

* What’s the purpose of the request to checkup.dyndns.org?

> I found that checkup.dyndns is used to retrieve the IP of the network that the host is using. 

* What’s up with the three jpg requests? Why two different domains?

[https://www.trendmicro.com/vinfo/us/threat-encyclopedia/malware/troj_upatre.smnf]

> I found that the malware contacts the domains harveyouellet and cwvancouver and download the arrowu.jp files which are malicious content that is placed within the hosts temp folder.

* How was the malware delivered? What isn’t Mike telling us?

> Based on the information found online, the malware was most likely installed via email. It could be that Mike fell for a phishing attempt, which turned out to be successful. He probably felt embarrassed that something like that happened to him.

## Milestone 5: Traffic Analysis – Mystery Meat Malware

* The pcap for this is a bit more realistic, but the malicious activity is still fairly easy to spot. The objective is to identify the probable malware from the traffic patterns. This one won't be quite so easy as googling the host names

* Hint: one of the captured requests attempted to download an .exe file; try searching for the filename instead of the host.

<img src="https://i.imgur.com/MX5aTE1.png?1"/>

> I found the .exe file called “g39b2cx.exe”

> It is known as TWEXT which was downloaded after the host made contact with Host “185.91.175.64”

[https://www.virustotal.com/#/ip-address/185.91.175.64]

[https://www.virustotal.com/#/file/7c9d5724064693dfeef76fd4da8d6f159ef0e6707e67c4a692a03e94f4a6e27a/details]

## Milestone 6: Wi-Fi Hacking – Crack a Handshake

### Challenge: Crack a WPA2 handshake

<img src="https://i.imgur.com/gO14urh.png?1"/>

## Milestone 7: Wi-Fi Hacking – Grab a Handshake
* Answers are based off the cap file from the previous challenge

<img src="https://i.imgur.com/lubN54P.png?1"/>

* What is the protocol of the handshake packets?

> It is using Extensible Authentication Protocol over LAN (EAPoL/EAPOL)

* Where is the SSID?

> Underneath ESSID within the terminal; the SSID is “teddy”

* Where specifically is the hash?

> I am uncertain as to where it is. I am assuming it is the one, in the terminal, by “EAPOL HMAC” with the output of “AE 83 8A AD 75 5C 16 1D 08 87 CD 2C F3 8C AE 60”

* What is a nonce?

> A nonce is a randomly generated string that is used one time to initiate a conversation between 2 hosts. It is generated as soon as 2 different computers talk to each other.
