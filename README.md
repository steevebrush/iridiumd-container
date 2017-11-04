# iridiumd-container
Iridium (IRD) full node container for docker

This container allow you to run a full Iridium node -
You can refer to the automatic build at [docker hub][4] too.

More information abour Iridium cryptonote [money here][1]

### Environment variables :		
 			
 	TIMEZONE : set your timezone to be right on time.
  	p2p-bind-ip 0.0.0.0
  	p2p-bind-port 12007
  	p2p-external-port 12007
  	rpc-bind-ip 127.0.0.1
  	rpc-bind-port=13007
  	log-file=/data/iridium.log
  	no-console=yes
  	log-level=1
	
	ex : docker run -e "TIMEZONE"="Europe/Paris" -e "p2p-bind-ip"="1.2.3.4 -e "p2p-bind-port"="12007" -e "p2p-external-port"="12007" -e "rpc-bind-ip"="5.6.7.8 -e "rpc-bind-port"="13007" -e "log-level"="4"   steevebrush/iridiumd
	
### Volumes : 

	/data : database, log files will be stored here.
  	tip : bind a dirctory, so you won't lose the database at each restart
	ex : docker run -v /my_IRD_data:/data steevebrush/alpine-domoticz

### Default Ports :

	12007 : p2p port, to be connected with the real world !
	13007 : rpc port, to query the daemon !
	ex : docker run -p my_local_p2p_port:12007 --p my_local_rpc_port:13007 steevebrush/iridiumd

### Quick start :
	
	docker run -it steevebrush/iridiumd (config directory will be erased at each start)
	docker run -v /my_config_dir:/config steevebrush/iridiumd (config directory will be saved)

### Fine tune :

If you map the /data volume, your config, database, log and everything else will be keeped beetwen restarts and updates.

### Example with all set :

Everything is setup : incoming port, timezone, data directory and usb device

	docker run -e "TIMEZONE"="Europe/Paris" -e "p2p-bind-ip"="1.2.3.4 -e "p2p-bind-port"="12007" -e "p2p-external-port"="12007" -e "rpc-bind-ip"="5.6.7.8 -e "rpc-bind-port"="13007" -e "log-level"="4"   steevebrush/iridiumd


### Finally, you are running an IRD node !

[1]: https://bitcointalk.org/index.php?topic=2150442.0
