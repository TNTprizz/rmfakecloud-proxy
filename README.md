# rmfakecloud-proxy
Single-minded HTTPS reverse proxy, but enables direct access to ngrok instead of the warning page.

(forked from https://github.com/yi-jiayu/secure)

## Installation

Do this on your tablet first: 
```bash
opkg install rmfakecloud-proxy
```

Replace `/opt/bin/rmfakecloud-proxy` with `rmfakecloud-proxy-arm7` (remember to rename the thing)  

Then, follow the guide [here](https://ddvk.github.io/rmfakecloud/remarkable/setup/).

*Note: `rmfakecloudctl status` somehow shows `invalid`, but it works, so I won't touch it.*  

### Manual

*Note: Might not work in this case as I amended the binary.*

Download `installer-rm12.sh` for rm1/2 or `installer-rmpro.sh` on a pc.  
Transfer to the tablet with `scp` / `WinSCP`  
run installer on the tablet over ssh  
```
chmod +x installer-xxx.sh
./installer-xxx.sh
```

### Use toltec if supported
`opkg install rmfakecloud-proxy`

### rmpro
To make it permanent, make root writable and unmount /etc first e.g.
```
mount -o remount,rw /
umount -R /etc
./installer-rmpro.sh
```

## Usage
```
usage: rmfakecloud-proxy [-addr host:port] -cert certfile -key keyfile upstream
  -addr string
        listen address (default ":443")
  -cert string
        path to cert file
  -key string
        path to key file
  -c configfile
  upstream string
        upstream url
```

### Example
```
rmfakecloud-proxy -cert cert.pem -key key.pem http://localhost:6060
```

## Configfile
```yaml
cert: proxy.crt 
key: proxy.key
upstream: https://somehost:123
#addr: :443
```

