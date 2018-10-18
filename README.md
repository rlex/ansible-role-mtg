### Ansible role for [mtg](https://github.com/9seconds/mtg)
Installs specified version of mtg from github, configures and starts it.
Should work on any system with systemd, so basically with any modern linux.

You will need to specify mtproto secret in mtg_secret, generated with

```
openssl rand -hex 16
```

or

```
head -c 512 /dev/urandom | md5sum | cut -f 1 -d ' '
```

Promoted channels are also supported, just specify your adtag in mtg_adtag

Configurable variables (default ones):
```
mtg_version: 0.15
mtg_checksum: sha512:8e4bc4b81ec18c2789742ad8c4c513bda9b9501c7838e131bacd689bb5be1a9d0502b1a7f16a96fabd84dc0769b34b09c72351c7b04ce09439dffb66a2c597cd
mtg_debug: false
mtg_verbose: false
mtg_ip: 0.0.0.0
mtg_port: 3128
mtg_buffer_write: 65536
mtg_buffer_read: 131072
mtg_secure_only: false
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
