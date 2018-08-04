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

# Other interesting notes

## Problem linking Kibana

```bash
#Once Kibana is running, you can use the following instructions to create index pattern:

curl -f -XPOST -H "Content-Type: application/json" -H "kbn-xsrf: anything" \
          "http://127.0.0.1:5601/api/saved_objects/index-pattern/logstash-*" \
          -d"{\"attributes\":{\"title\":\"logstash-*\",\"timeFieldName\":\"@timestamp\"}}"

curl -XPOST -H "Content-Type: application/json" -H "kbn-xsrf: anything" \
          "http://127.0.0.1:5601/api/kibana/settings/defaultIndex" \
          -d"{\"value\":\"logstash-*\"}"
```
