# Build command from Apple M1 

Assumes you already logged in to docker hub with your Hiotlabs account. If you dont have access please shout out loud to you closest colleague

```
docker buildx build -t hiotlabs/node-onbuild:15.12.0 \
  --platform linux/amd64,linux/arm64,linux/ppc64le --push .
```

