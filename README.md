# About

Turn WireGuard to HTTP & SOCKS5 proxies.

The HTTP & SOCKS5 proxies are served on same port. It runs in userspace,
without requirement of WireGuard kernel module or TUN device.

In remote exit mode, the proxy is served on local network, and the traffic
from proxy server goes to WireGuard network.

In local exit mode, the proxy is served on WireGuard network, and the traffic
from WireGuard goes to local network.

For detailed usage, see <https://github.com/zhsj/wghttp/tree/master/docs>

# Example

`wghttp --listen=127.0.0.1:1080 --client-ip=192.168.6.140 --dns=1.1.1.1 --private-key=KEY --peer-key=KEY --peer-endpoint=server.com:1024 --exit-mode=remote --resolve-dns=1.1.1.1`

Address --client-ip   
DNS --dns   
PrivateKey --private-key   
PublicKey --peer-key   
Endpoint --peer-endpoint   
PresharedKey --preshared-key   
Local HTTP/SOCKS --listen

You may need to disable DNS resolution through SOCKS proxy in the client and restart it.

# (Cross) compiling from source code
If you want to make your own build, install [Golang](https://go.dev/dl/), Git, and run the commands:
```
git clone https://github.com/zhsj/wghttp
cd wghttp
export GOARCH=386
export GOOS=windows
go build -ldflags="-s -w" -v -x
```

architectures: 386, amd64   
operating systems: windows, linux   
In Windows host use `set` instead of `export`   
You can do this without Git if you download and extract the [source code](https://github.com/zhsj/wghttp/archive/refs/heads/master.zip) yourself.
