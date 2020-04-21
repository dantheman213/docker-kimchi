# docker-kimchi

This is a containerized version of Kimchi, a web GUI for managing Linux VMs.

## Getting Started

https://hub.docker.com/repository/docker/dantheman213/kimchi

```
# Create SSL certificates
mkdir -p /etc/wok/ssl
mkdir -p /etc/kimchi/ssl
openssl dhparam -out /etc/wok/ssl/dhparam.pem 2048
openssl req -nodes -newkey rsa:2048 -keyout /etc/wok/ssl/wok.key -out /etc/wok/ssl/wok.csr -subj "/C=US/ST=California/L=San Francisco/O=Wok/OU=IT Department/CN=wok.local"
openssl x509 -signkey /etc/wok/ssl/wok.key -in /etc/wok/ssl/wok.csr -req -days 365 -out /etc/wok/ssl/wok.crt
openssl req -nodes -newkey rsa:2048 -keyout /etc/kimchi/ssl/kimchi.key -out /etc/kimchi/ssl/kimchi.csr -subj "/C=US/ST=California/L=San Francisco/O=Kimchi/OU=IT Department/CN=kimchi.local"
openssl x509 -signkey /etc/kimchi/ssl/kimchi.key -in /etc/kimchi/ssl/kimchi.csr -req -days 365 -out /etc/kimchi/ssl/kimchi.crt

# Pull and run the container
docker run --name kimchi \
  -v /etc/passwd:/etc/passwd:ro \
  -v /run:/run \
  -v /sys/fs/cgroup:/sys/fs/cgroup:ro \
  -v /etc/group:/etc/group:ro \
  -v /etc/shadow:/etc/shadow:ro \
  -v /var/run/libvirt/libvirt-sock:/var/run/libvirt/libvirt-sock \
  -v /var/lib/libvirt:/var/lib/libvirt \
  -v /etc/libvirt:/etc/libvirt \
  -v /storage:/storage \
  -v /etc/wok/ssl/dhparams.pem:/etc/wok/dhparams.pem:ro \
  -v /etc/wok/ssl/wok.crt:/etc/wok/wok-cert.pem:ro \
  -v /etc/wok/ssl/wok.key:/etc/wok/wok-key.pem:ro \
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
