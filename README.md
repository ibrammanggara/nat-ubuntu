# nat-ubuntu

---

sudo apt update

sudo apt install iptables-persistent -y

sudo nano /etc/sysctl.conf

#net.ipv4.ip_forward=1

sudo sysctl -p

ip link show

sudo iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE

sudo iptables -A FORWARD -i eth0 -o eth0 -j ACCEPT

sudo iptables -A FORWARD -i eth0 -m state --state RELATED,ESTABLISHED -j ACCEPT

sudo netfilter-persistent save

sudo netfilter-persistent reload

sudo iptables -t nat -L -n -v

cat /proc/sys/net/ipv4/ip_forward




