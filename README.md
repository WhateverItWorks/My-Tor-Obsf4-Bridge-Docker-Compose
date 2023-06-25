# My-Tor-Obsf4-Bridge-Docker-Compose
Help people fight censorship from their Governments with Tor Obsf4 Bridge Standalone Proxy

### Deploy with Docker-Compose
```
docker-compose up -d obfs4-bridge
```

### Install with Dockerfile (Build from Source)
```
docker-compose up -d --build
```

### Monitor your logs

You can inspect your bridge's logs by running:
```
docker logs CONTAINER_ID
```

### Find your "Bridge Line"
To use your new bridge in Tor Browser, you need its "bridge line". Here's how you can get your bridge line:

```
docker exec CONTAINER_ID get-bridge-line
```

This will return a string similar to the following:
```
obfs4 5.161.94.149:9999 13736A1904D61E42654F479EBCE84D2F392C3D94 cert=YVmzV4a3fNnFyD81JTY3fP3KQUF38Oci3EKgEodhs/ZoS2VDu6JGxkqNDt8Xd2fH1xmHFw iat-mode=0
```
You can check the status of my bridge relay at https://bridges.torproject.org/status?id=5832F862003F38A0193D05B930F87E3809ADE045

### Upgrade your container

Upgrading to the latest version of our image is as simple as pulling the latest version of the image running:

```
docker-compose pull obfs4-bridge
```

And then restarting the container:

```
docker-compose up -d obfs4-bridge
```

Note that your bridge's data directory (which includes its key material) is stored in a docker volume, so you won't lose your bridge's identity when upgrading to the latest docker image. If you are running multiple bridges on your computer, you need to repeat this step for each bridge. We will announce new image versions on the tor-dev mailing list.
