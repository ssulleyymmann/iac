# check config
>log check
    ps aux | grep logs

>file write capasite
    ulimit -n
    sudo sysctl -p

>file 
    df -H 
    du -cha --max-depth=1 / | grep -E "M|G"
    sudo du -x / | sort -n | tail -40

>memory 
    free -m
    top
    cat /proc/meminfo

> redis 
    server redis cli  
    sudo apt-get install redis-tools
    redis-cli -h url
    PUBSUB CHANNELS
    redis-cli -h redis.amazonaws.com monitor 
    ps -ef | grep redis

> elasticsearch 
    vi /etc/elasticsearch/elasticsearch.yml
    vi /etc/elasticsearch/jvm.options 
    tail -f -n 200 /var/log/elasticsearch/elasticsearch.log
    service elasticsearch status
    systemctl status elasticsearch.service
    sudo journalctl --unit elasticsearch
> kibana 
    vi /etc/kibana/kibana.yml
    service kibana status

> logstash 
    vi /etc/logstash/conf.d/apache.conf
    service logstash status 
    /usr/share/logstash/bin# ./logstash -f /etc/logstash/conf.d/apache.conf
   

# elasticsearch limit update
vi /etc/security/limits.conf
    soft  nofile 65536|
    hard  nofile 65536

# clear command 
>buff cache clear 
    sync; echo 3 > /proc/sys/vm/drop_caches


# setup command
 


elasticsearch execption ubuntu 16 
command=> ls /usr/share/elasticsearch/bin/elasticsearch
result=>
java.net.UnknownHostException: ip-10-11-99-6: ip-10-11-99-6: Name or service not known


ES_JAVA_OPTS="-Des.insecure.allow.root=true"
bin/elasticsearch -Des.insecure.allow.root=true -d


journalctl -u kibana.service
journalctl -fu kibana.service


kibana index 
https://stackoverflow.com/questions/54676991/kibana-6-5-4-create-index-pattern-stuck/54691699

index check 
http://10.20.60.50:9200/_cat/indices?v

 curl -X GET "localhost:9200/_cat/indices?v"
 curl -X GET "10.20.60.89:9100/metrics"

disk mount
 sudo mkfs -t ext4 /dev/xvdf
sudo mkdir /log_data
sudo mount /dev/xvdf /log_data
chmod -R 777  /log_data/

tail -f -n 200 /var/log/elasticsearch/elasticsearch.log
redis-cli -h logservice-pubsub.luv0j6.0001.euw1.cache.amazonaws.com monitor

# default config 

elasticsearch.yml
path.data: /iac/log/compose/elasticsearch/data/
path.logs: /iac/log/compose/elasticsearch/logs/
network.host: "0.0.0.0"
http.port: 9200

kibana.yml 
server.port: 5601
server.host: "0.0.0.0"


# elasticsearch best practise
    https://www.elastic.co/guide/en/elasticsearch/reference/current/mapping-source-field.html#disable-source-field

# elasticsearch security

    https://www.elastic.co/guide/en/elasticsearch/reference/current/built-in-users.html
    https://www.elastic.co/guide/en/elasticsearch/reference/7.x/get-started-built-in-users.html
    https://www.elastic.co/guide/en/kibana/7.5/kibana-privileges.html#kibana-feature-privileges


 # docker 
  docker run -d   --net="host"       quay.io/prometheus/node-exporter

   notlar;
   ----------es--
   index.store.type, memory oriented.  
   https://www.elastic.co/guide/en/elasticsearch/reference/current/index-modules-store.html
   :ElasticSearch::HttpClient::Pool::NoConnectionAvailableError", :will_retry_in_seconds  
   -----