# Azure VNET Gateway Configuration

Short description of configuring a point-to-site vpn in Azure VNET Gateway

## Main steps

* [Generate certificates](https://learn.microsoft.com/en-us/azure/vpn-gateway/vpn-gateway-certificates-point-to-site)
* [Configure server settings for P2S VPN Gateway connections - certificate authentication - Azure portal](https://learn.microsoft.com/en-us/azure/vpn-gateway/vpn-gateway-howto-point-to-site-resource-manager-portal)
* [Configure OpenVPN for Point-to-Site VPN gateways](https://learn.microsoft.com/en-us/azure/vpn-gateway/vpn-gateway-howto-openvpn)
* [Configure point-to-site VPN clients: certificate authentication - Windows](https://learn.microsoft.com/en-us/azure/vpn-gateway/point-to-site-vpn-client-cert-windows#openvpn)
* [Configure point-to-site VPN clients: certificate authentication - Linux](https://learn.microsoft.com/en-us/azure/vpn-gateway/point-to-site-vpn-client-cert-linux)

## Export private and public key

``` batch
openssl pkcs12 -in "filename.pfx" -nodes -out "profileinfo.txt"
```

## Install OpenVPN on Linux

```
sudo zypper install openvpn
sudo openvpn --config vpnconfig.ovpn --deamon
```

## Install NPM and Node.js

Needed for test purposes
```
sudo zypper install npm nodejs
npx http-server .
```

## Configure OpenVPN

You have to download the profile in Azure portal and configure the certs in your `vpnconfig.ovpn`.

## Test P2S in Azure

Install simple web server and provide a web site
```
# npm install -g http-server
http-server .
```

Test in Kudu console
``` batch
curl -s http://172.16.201.2:8080/
```