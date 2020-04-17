# docker-kimchi

This is a containerized version of Kimchi, a web GUI for managing Linux VMs.

## Getting Started

https://hub.docker.com/repository/docker/dantheman213/kimchi

```
docker run -d --restart=always --name kimchi \
  -e /run/dbus/system_bus_socket:/run/dbus/system_bus_socket:ro \
  -v /etc/passwd:/etc/passwd:ro \
  -v /run:/run \
  -v /sys/fs/cgroup:/sys/fs/cgroup:ro \
  -v /etc/group:/etc/group:ro \
  -v /etc/shadow:/etc/shadow:ro \
  -v /var/run/libvirt/libvirt-sock:/var/run/libvirt/libvirt-sock \
  -v /var/lib/libvirt:/var/lib/libvirt \
  -v /etc/libvirt:/etc/libvirt \
  -v /storage:/storage \
  -v /etc/kimchi/ssl/kimchi.crt:/etc/kimchi/kimchi-cert.pem:ro \
  -v /etc/kimchi/ssl/kimchi.key:/etc/kimchi/kimchi-key.pem:ro \
  -p 8001:8001 \
  --user 0:0 \
  --privileged \
  dantheman213/kimchi:latest
```

## Reference

https://github.com/kimchi-project/kimchi

https://github.com/kimchi-project/wok
