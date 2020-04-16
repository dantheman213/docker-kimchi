

```
docker build -t test .
docker run -d --restart=always --net=host --name kimchi \
  -v /etc/passwd:/etc/passwd:ro \
  -v /etc/group:/etc/group:ro \
  -v /etc/shadow:/etc/shadow:ro \
  -v /var/run/libvirt/libvirt-sock:/var/run/libvirt/libvirt-sock \
  -v /var/lib/libvirt:/var/lib/libvirt \
  -v /etc/libvirt:/etc/libvirt \
  -v /storage:/storage \
  --privileged
  test:latest

#  -v /path/to/ssl/cert:/etc/kimchi/kimchi-cert.pem:ro \
#  -v /path/to/ssl/key:/etc/kimchi/kimchi-key.pem:ro \

```

## Reference

https://github.com/kimchi-project/kimchi

https://github.com/kimchi-project/wok

