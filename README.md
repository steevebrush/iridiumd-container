# iridiumd-container
Iridium (IRD) full node container for docker

This container allow you to run a full Iridium node -
You can refer to the automatic build at [docker hub][4] too.

More information abour Iridium cryptonote [money here][1]

### Environment variables :		
 			
 	TIMEZONE : set your timezone to be right on time
  ex : docker run -e "TIMEZONE"="Europe/Paris" steevebrush/alpine-domoticz
  p2p-bind-ip 0.0.0.0
  p2p-bind-port 12007
  p2p-external-port 12007
  rpc-bind-ip 127.0.0.1
  rpc-bind-port=13007
  log-file=/data/iridium.log
  no-console=yes
  log-level=1
	
### Volumes : 

	/data : database, log files will be stored here.
  tip : bind a dirctory, so you won't lose the database at each restart
	ex : docker run -v /my_IRD_data:/data steevebrush/alpine-domoticz

### Ports :

	9080 : domoticz interface and API
	ex : docker run -p my_local_port:9080 steevebrush/iridiumd

### Quick start :
	
	docker run -p 9080:9080 steevebrush/alpine-domoticz (config directory will be erased at each start)
	docker run -p 9080:9080 -v /my_config_dir:/config steevebrush/alpine-domoticz (config directory will be saved)

### Fine tune :

If you map the /config volume, your config, database, log and everything else will be keeped beetwen restarts and updates.
If you want to attach an usb device, like an openZwave stick, add --device=/dev/your_device

### Example with all set :

Everything is setup : incoming port, timezone, data directory and usb device

	docker run -p 9080:9080 -e "TIMEZONE"="Europe/Paris" -v /config:/config --device=/dev/ttyUSB0 steevebrush/alpine-domoticz


### Finally, open WebUI and start configuring Domoticz :
open domoticz webUI : [http://localhost:9080][5] or your http://your_docker-server_IP:9080

[1]: https://bitcointalk.org/index.php?topic=2150442.0;all
[2]: https://www.domoticz.com
[3]: https://github.com/OpenZWave/open-zwave
[4]: https://hub.docker.com/r/steevebrush/alpine-domoticz/
[5]: http://localhost:9080
[6]: https://github.com/mjg59/python-broadlink
