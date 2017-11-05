# iridiumd-container
[Iridium (IRD)][2] full node container for docker

This container allow you to run a full Iridium node -
You can refer to the automatic build at [docker hub][1] too.

Iridium official [website][2]
More information abour Iridium cryptonote money [here][3]

### Environment variables with defaults values :
	
 	TIMEZONE Europe/Paris
  	P2P_BIND_IP 0.0.0.0
  	P2P_BIND_PORT 12007
  	P2P_EXTERNAL_PORT 12007
  	RPC_BIND_IP 127.0.0.1
  	RPC_BIND_PORT 13007
  	LOG_FILE /data/iridium.log
  	LOG_LEVEL 1
	
	ex : docker run -it -e "TIMEZONE"="Europe/Paris" -e "P2P_BIND_IP"="1.2.3.4 -e "P2P_BIND_PORT"="12007" -e "P2P_EXTERNAL_PORT"="12007" -e "RPC_BIND_IP"="5.6.7.8 -e "RPC_BIND_PORT"="13007" -e "LOG_LEVEL"="4" -e "LOG_FILE"="/data/iridium.log" steevebrush/iridiumd
	
### Volumes : 

	/data : database, log files will be stored here.
  	tip : bind a directory, so you won't lose the (big) database at each restart
	ex : docker run -it -v /my_IRD_data:/data steevebrush/alpine-domoticz

### Default Ports :

	12007 : p2p port, to be connected with the real world !
	13007 : rpc port, to query the daemon !
	ex : docker run -it -p my_local_p2p_port:12007 --p my_local_rpc_port:13007 steevebrush/iridiumd

### Quick start :
	
	docker run -it steevebrush/iridiumd (config directory will be erased at each start)
	docker run -it -v /my_config_dir:/config steevebrush/iridiumd (config directory will be saved)

### Fine tune :

If you map the /data volume, your config, database, log and everything else will be keeped beetwen restarts and updates.

### Example with all set :

Everything is setup : ports, timezone, data, log

	docker run -it -e "TIMEZONE"="Europe/Paris" -p my_local_p2p_port:12007 --p my_local_rpc_port:13007 -e "P2P_BIND_IP"="1.2.3.4 -e "P2P_BIND_PORT"="my_local_p2p_port" -e "P2P_EXTERNAL_PORT"="12007" -e "RPC_BIND_IP"="5.6.7.8 -e "RPC_BIND_PORT"="my_local_rpc_port" -e "LOG_LEVEL"="4" -e "LOG_FILE"="/data/iridium.log" steevebrush/iridiumd


### Finally, you are running an IRD node !
[1]: https://hub.docker.com/r/steevebrush/iridiumd-container
[2]: http://ird.cash
[3]: https://bitcointalk.org/index.php?topic=2150442.0
