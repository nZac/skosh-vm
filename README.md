# Skosh Virtual Machines

This project is designed to be an infrastructure in a box.

## Dev Setup

1. Pull down the project.

  ```sh
  $ git clone https://github.com/nZac/skosh-vm
  ```
1. Create a new virtual environment

  ```sh
  $ mkvirtualenv skosh-vm
  ```
1. Activate virtualenv

  ```sh
  $ workon skosh-vm
  ```
1. Add the dependencies

  ```sh
  $ pip install ansible
  ```
1. Add the `SKOSHAPPS` environment variable to your shell

  ```sh
  # in ~/.zshrc
  $ export SKOSHAPPS=/path/to/root/app/folder
  ```
1. Source your .zshrc file

  ```sh
  $ source ~/.zshrc
  ```
1. Create the VM

  ```sh
  $ vagrant up
  ```
1. Install DNSMasq

  ```sh
  $ brew install dnsmasq
  ```
1. Create the config file

  ```sh
  $ touch /usr/local/etc/dnsmasq.conf
  ```
1. Edit the config file

  ```sh
  #in /usr/local/etc/dnsmasq.conf
  $ address=/.dev/192.168.20.10
  ```
1. Make DNSMasq turn on at startup

  ```sh
  $ sudo cp -fv /usr/local/opt/dnsmasq/*.plist /Library/LaunchDaemons
  $ sudo launchctl load /Library/LaunchDaemons/homebrew.mxcl.dnsmasq.plist
  ```
1. Open System Preferences and then Network.
1. Select WiFi
1. Click Advanced
1. Select DNS at the top
1. In the bottom left corner hit the `+` button
1. Add the following records in this order
  - 127.0.0.1
  - 8.8.8.8
  - 8.8.4.4
1. Make sure it works

  ```sh
  $ ping anything.dev
  PING anything.dev (192.168.30.10): 56 data bytes
  64 bytes from 192.168.30.10: icmp_seq=0 ttl=64 time=0.254 ms
  64 bytes from 192.168.30.10: icmp_seq=1 ttl=64 time=0.335 ms
  ```
