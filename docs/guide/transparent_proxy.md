proxy transparente

Consulte https://docs.mitmproxy.org/stable/howto-transparent/ para obter os documentos.

sudo sysctl -w net.ipv4.ip_forward=1
sudo sysctl -w net.ipv6.conf.all.forwarding=1
sudo sysctl -w net.ipv4.conf.all.send_redirects=0

sudo useradd --create-home mitm
sudo -u mitm -H bash -c 'good-mitm run -r rules/log.yaml -b 0.0.0.0:34567'

sudo iptables -t nat -A OUTPUT -p tcp -m owner ! --uid-owner mitm --dport 80 -j REDIRECT --to-port 34567
sudo iptables -t nat -A OUTPUT -p tcp -m owner ! --uid-owner mitm --dport 443 -j REDIRECT --to-port 34567
sudo ip6tables -t nat -A OUTPUT -p tcp -m owner ! --uid-owner mitm --dport 80 -j REDIRECT --to-port 34567
sudo ip6tables -t nat -A OUTPUT -p tcp -m owner ! --uid-owner mitm --dport 443 -j REDIRECT --to-port 34567
```
