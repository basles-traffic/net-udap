# Net-UDAP

## Overview

Net::UDAP is a Perl module to configure the Logitech SqueezeBox Receiver (SBR) from a PC, i.e. without requiring a SqueezeBox Controller (SBC).

I have tested on linux (Fedora 8), Windows XP (ActiveState perl and cygwin).

**Important** If you don't read anything else, read this: [wiki:GettingStarted Getting Started]

## Donations

Net-UDAP is free software - you do not have to pay to use it.

However, if you find Net-UDAP useful, you might like to make a donation - I've got ~~four~~ five kids to support!

https://paypal.me/RobinBowes

## Support

Please raise issues if you have any problems with Net-UDAP

## Documentation

[wiki:GettingStarted Getting Started]

[wiki:ReceiverSetupProcedure Receiver Setup Procedure]

[wiki:SampleUsage Examples of configuration commands]

## Requirements

 * On Unix:
   * perl v5.8.5, or later (it may work on earlier versions)
   * either subversion or unzip

 * On Windows:
   * ActiveState perl
   * optionally, TortoiseSVN (or similar) 

For the 1.0.0 release, all necessary modules should either be part of base perl, or are distributed with this module. 

Note: this will change in the next release. Net::UDAP will require installing one or two supporting perl modules from CPAN or using the ActiveState [http://aspn.activestate.com/ASPN/Downloads/ActivePerl/PPM/ Perl Package Manager].

## News

### March 22, 2014

Imported code to github.

I have tried to update the documenttion to reflect the new location of the wiki, etc. but please let me know if I've missed anything.

### January 21, 2009

I just committed a change that switches to hex entry for WEP keys. This simply means that instead of entering a hex key like this: {{{abcd}}}, you should now enter it like this: {{{61626364}}}.

The change is in trunk, and also in a new 1.0.x branch I've created from the 1.0.0 release.

### January 9, 2009

Blimey, two updates in two days - what's going on???!!

I just noticed that the documentation doesn't mention anything about firewalls. Oooops. I've updated the [wiki:GettingStarted Getting Started] docs to include details of what size hole is required in the firewall.

For the record, the UDAP protocol uses broadcast traffic on port 17784 (udp).

### January 8, 2009

Happy New Year all!

No major updates to report at this stage, but I've re-arranged the wiki documentation and updated the [wiki:GettingStarted Getting Started] documentation. Also, the registration procedure should now work so you can register, login, and create tickets to report any issue. Hell, you could even go crazy and edit the wiki to update the documentation!

A couple of points regarding getting the code:

 1. Most folk should grab the 1.0.0 Release () rather than the latest development code
 1. trac is able to dynamically create a zip file of any view of the code repository. What this means in practise is that it is not necessary to install subversion to get Net::UDAP - you can simply grab a zip archive. Look for the "Zip archive" link at the bottom of the page under "'''Download in other formats:'''"

### June 2, 2008

I've moved all my projects to a new server and a new version of trac.

Please [/register register] to be able to create/modify tickets and/or modify the wiki.

https access is secured using a certificate signed by the CAcert. To import the CAcert root certificate, please go to https://www.cacert.org/index.php?id=3

## Useful Links

http://wiki.slimdevices.com/index.php/SBRFrontButtonAndLED

http://forums.slimdevices.com/showpost.php?p=280981&postcount=47

## add my test

first install

git clone https://github.com/robinbowes/net-udap.git
cd net-udap
sudo apt install cpanminus
sudo cpanm Log::StdLog
sudo cpanm Term::Shell
sudo cpanm Class::Accessor
sudo cpanm IO::Interface::Simple
scripts/udap_shell.pl



another test 

git clone https://github.com/robinbowes/net-udap.git
$ cd net-udap
$ cpan Log::StdLog Term::Shell Class::Accessor IO::Interface::Simple
$ ./scripts/udap_shell.pl
UDAP> discover


reboot pc and retry cde below




The command sequence I use is as follows:
1. Start udap
2. at udap prompt - type "discover"
3. type "list" to get a list fo the player found.
4. type "configure 1" - the number is the player from the list
5. type "list" - show current settings
6. type "set server_address=192.168.xx.xx squeezecenter_address=192.168.xx.xx" - the address xx.xx is your LMS server
7. type "save_data"
8. Usually works or try power off / on the receiver.

What sequence have you tried ? please give full details. 



real test

./scripts/udap_shell.pl 
UDAP> discover
info: <<< Broadcasting adv_discovery message to MAC address 00:00:00:00:00:00 on 255.255.255.255
info: >>> adv_discovery response received from 00:xx:20:ff:xx:01
info: <<< Broadcasting get_ip message to MAC address 00:04:20:ff:ff:01 on 255.255.255.255
info: >>> get_ip response received from 00:xx:20:ff:xx:01
info: <<< Broadcasting get_data message to MAC address 00:xx:20:ff:xx:01 on 255.255.255.255
info: >>> get_data response received from 00:xx:xx:ff:ff:01
UDAP> list
 #    MAC Address    Type       Status         
== ================= ========== ===============
 1 00:xx:xx:ff:xx:01 squeezebox wait_slimserver
UDAP> configure 1
UDAP [1] (squeezebox ffff01)> list
             bridging: 0
             hostname: classic
            interface: 1
          lan_gateway: 192.168.0.1
          lan_ip_mode: 1
  lan_network_address: 0.0.0.0
      lan_subnet_mask: 255.255.255.0
          primary_dns: 0.0.0.0
        secondary_dns: 0.0.0.0
       server_address: 0.0.0.0
squeezecenter_address: 192.168.0.100
   squeezecenter_name: NasHome
        wireless_SSID: t
     wireless_channel: 6
      wireless_keylen: 0
        wireless_mode: 0
   wireless_region_id: 4
   wireless_wep_key_0: 00000000000000000000000000
   wireless_wep_key_1: 00000000000000000000000000
   wireless_wep_key_2: 00000000000000000000000000
   wireless_wep_key_3: 00000000000000000000000000
      wireless_wep_on: 0
  wireless_wpa_cipher: 3
    wireless_wpa_mode: 1
      wireless_wpa_on: 0
---line 25/26 (any key for more, or q to quit)---




set server_address=192.168.1.100 squeezecenter_address=192.168.1.100

save_data








