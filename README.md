# osm4 Installation
As usual follow the primary instructions from [OSM4 official installation guide], then just in case of troubles try to apply the following procedures.


[OSM4 official installation guide]: https://osm.etsi.org/wikipub/index.php/OSM_Release_FOUR#Other_installation_options


# Troubleshooting

In case of error during the installation process, please try to install at the beginning the following packages (on the host of OSM):

* gcc
* pip3
* build-essential libssl-dev libffi-dev (xml2)

How to:

```bash
# gcc build-essential libssl-dev libffi-dev xml2
sudo apt install gcc build-essential libssl-dev libffi-dev xml2 -y

# pip3
sudo apt-get -y install python3-pip

```

# Other interesting notes & Utilities

## Problems linking Kibana

```bash
#Once Kibana is running, you can use the following instructions to create index pattern:

curl -f -XPOST -H "Content-Type: application/json" -H "kbn-xsrf: anything" \
          "http://127.0.0.1:5601/api/saved_objects/index-pattern/logstash-*" \
          -d"{\"attributes\":{\"title\":\"logstash-*\",\"timeFieldName\":\"@timestamp\"}}"

curl -XPOST -H "Content-Type: application/json" -H "kbn-xsrf: anything" \
          "http://127.0.0.1:5601/api/kibana/settings/defaultIndex" \
          -d"{\"value\":\"logstash-*\"}"
```
ciao


## SSH Tunnel
In order to reach services in a vitual machine/container within a host, it's easier to creare an SSH tunnel. Doing so you will achieve the possibility to access the services from your localhost, for instance from your browser.

```bash
sudo ssh -f USER@JUMP_SERVER -L LOCALHOST_PORT:TARGET:TARGET_PORT -N
```
-f allows to put the process in background
-N says that no commands have to be executed right now

As following it is shown how to check the SSH Tunnel/SSH connection avaliable at this time.
```bash
sudo lsof -i -n | egrep '\<ssh\>'
```

## Sudoers file editing

Change the `/etc/sudoers.d/...` file as following:

```bash
user ALL=(ALL) NOPASSWD:ALL
```
this procedure grants the execution of all "sudo" commands without password for a given user.
