# white-beet-installation

## Install Debian

* add user as sudoer
```
su -
sudo usermod -aG sudo USERNAME
```

* add repository

```
sudo sed -e '/security/s/^/#/' -i /etc/apt/sources.list
echo "deb http://deb.debian.org/debian-security/ bookworm-security main" |
sudo tee -a /etc/apt/sources.list
```
* install build packages
```
sudo apt update
sudo apt install git build-essential python3-venv python3-dev libpcap-dev
```
## setup FreeV2G
```
git clone https://github.com/SEVENSTAX/FreeV2G
cd FreeV2G/
python3 -m venv .venv
source .venv/bin/activate
pip install --pre scapy[basic]
pip install Cython
pip install python-libpcap
```
# check MAC Address of WHITE-beet board [MAC - 2]
```
ip link show
sudo .venv/bin/python3 Application.py eth -i enp3s0 -m c4:93:00:48:ac:f0 -r EVSE
```

# Test...

``` text
Welcome to Codico Whitebeet EVSE reference implementation
Initiating framing interface
iface: ETH, name: enp3s0, mac: c4:93:00:48:ac:f0
WHITE-beet-EI firmware version: V02_01_00
Set the CP mode to EVSE
Set the CP duty cycle to 100%
Start the CP service
Start SLAC in EVSE mode
Wait until an EV connects
```
