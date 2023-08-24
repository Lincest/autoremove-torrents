```shell
cd && git clone https://github.com/lincest/autoremove-torrents.git && cd autoremove-torrents && python3 setup.py install
```

## config

```yml
my_task:
  client: qbittorrent
  host: http://127.0.0.1:8080
  username: 
  password: 
  strategies:
    my_strategy:
      remove: ' 
        (size < 10 and seeding_time > 86400) or 
        (size > 10 and size < 20 and seeding_time > 172800) or 
        (size > 20 and size < 30 and seeding_time > 259200) or 
        (size > 30 and size < 40 and seeding_time > 345600) or 
        (size > 40 and size < 50 and seeding_time > 432000) or 
        seeding_time > 604800 or 
        ratio > 10 '
  delete_data: true
```

## crontab

`mkdir /root/logs` first

every 15min: 

```shell
*/15 * * * * /usr/local/bin/autoremove-torrents --conf=/root/pt-resolver/autoremove-config.yml --log=/root/logs
```
