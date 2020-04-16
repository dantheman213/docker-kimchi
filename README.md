# docker-kimchi

This is a containerized version of Kimchi, a web GUI for managing Linux VMs.

## Getting Started

https://hub.docker.com/repository/docker/dantheman213/kimchi

```
docker run -d --restart=always --net=host --name kimchi \
  -v /etc/passwd:/etc/passwd:ro \
  -v /etc/group:/etc/group:ro \
  -v /etc/shadow:/etc/shadow:ro \
  -v /var/run/libvirt/libvirt-sock:/var/run/libvirt/libvirt-sock \
  -v /var/lib/libvirt:/var/lib/libvirt \
  -v /etc/libvirt:/etc/libvirt \
  -v /storage:/storage \
  -p 8001:8001 \
  --privileged
  dantheman213/kimchi:latest

#  -v /path/to/ssl/cert:/etc/kimchi/kimchi-cert.pem:ro \
#  -v /path/to/ssl/key:/etc/kimchi/kimchi-key.pem:ro \
```

## Reference

https://github.com/kimchi-project/kimchi

https://github.com/kimchi-project/wok

