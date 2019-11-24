### Ansible role for [mtg](https://github.com/9seconds/mtg)
Installs specified version of mtg from github, configures and starts it.
Should work on any system with systemd, so basically with any modern linux.

Minimal configuration is mtproto secret in mtg_secret varible, please refer to [mtg documentation on how to generate different secrets](https://github.com/9seconds/mtg#configuration)

Promoted channels are also supported, just specify your adtag in mtg_adtag

Other configurable variables (default ones):
```
mtg_debug: false
mtg_verbose: false
mtg_ip: 0.0.0.0
mtg_port: 3128
mtg_buffer_write: 64KB
mtg_buffer_read: 128KB
mtg_antireplay_maxsize: 128MB
mtg_secure_only: false
mtg_user: mtg
mtg_cap_net_bind_service: false
```

Optional parameters for public-facing ipv4/ipv6, required if your proxy is behind NAT
```
mtg_ipv4: 203.0.113.11
mtg_ipv4_port: 51411
mtg_ipv6: 2001:DB8:DA:DE::22
mtg_ipv6_port: 51411
```

StatsD support if you need statistics from mtg:
```
mtg_statsd_ip: 127.0.0.1
mtg_statsd_port: 8125
mtg_statsd_network: tcp
mtg_statsd_prefix: mtg
mtg_statsd_tags_format: influxdb
mtg_statsd_tags: mtg=true
```

Prometheus endpoint configuration:
```
mtg_stats_bind: 127.0.0.1:3129
```

### Installing on other architectures
For running on something other than amd64, you will need to specify target architecture, ie

```
mtg_architecture: arm64
```

In addition, you will need to specify mtg_checksum for mtg binary. You can get it with this command:
```
curl -Ls https://github.com/9seconds/mtg/releases/download/v1.0.1/mtg-linux-amd64 | gsha512sum | awk {'print $1'} | xargs -I #checksum -n1 echo "mtg_checksum: sha512:#checksum"
```
