# osm4 Installation
As usual follow the primary instructions from [OSM4 official installation guide], then just in case of troubles try to apply the following procedures.


[OSM4 official installation guide]: https://osm.etsi.org/wikipub/index.php/OSM_Release_FOUR#Other_installation_options

.....

#Troubleshooting

In case of error during the installation process, please try to install at the beginning the following packages (on the host of OSM):

1. gcc
2. pip3
3. build-essential libssl-dev libffi-dev (xml2)

How to:

```bash
# gcc build-essential libssl-dev libffi-dev xml2
sudo apt install gcc build-essential libssl-dev libffi-dev xml2 -y

# pip3
sudo apt-get -y install python3-pip

```
