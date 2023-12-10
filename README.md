# Cisco DHCP Snooping


## DHCP Snooping Nedir?

DHCP Snooping, bir ağdaki DHCP trafiğini güvenli bir şekilde yönetmek için kullanılan bir güvenlik özelliğidir. Temel amacı, güvenilmeyen DHCP sunucularından gelen isteklere karşı koruma sağlamaktır.

Network tasarımımızda 2 bilgisayar, 1 switch, 2 DHCP Server bulunmaktadır. DHCP Serverlardan bir tanesi saldırgana ait diğeri ise bize aittir.







```
Pool Name   Default Gateway  DNS Server   Start IP Address  Subnet Mask     Max User  TFTP Server  WLC Address
serverPool   192.168.1.1      8.8.8.8       192.168.1.2    255.255.255.0      254       0.0.0.0      0.0.0.0
```










![image](https://github.com/ugurcomptech/C-DHCP-SNOOPING/assets/133202238/7fb50428-7a5d-4026-abc1-e8b30b6f62aa)



