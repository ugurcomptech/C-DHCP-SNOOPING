# Cisco DHCP Snooping

## DHCP Snooping Nedir?

DHCP Snooping, bir ağdaki DHCP trafiğini güvenli bir şekilde yönetmek için kullanılan bir güvenlik özelliğidir. Temel amacı, güvenilmeyen DHCP sunucularından gelen isteklere karşı koruma sağlamaktır.

Network tasarımımızda 2 bilgisayar, 1 switch, 2 DHCP Server bulunmaktadır. DHCP Serverlardan bir tanesi saldırgana ait diğeri ise bize aittir.



### DHCP Server Config

DHCP Server(Bize ait olan)

```
Pool Name   Default Gateway  DNS Server   Start IP Address  Subnet Mask     Max User  TFTP Server  WLC Address
serverPool   192.168.1.1      8.8.8.8       192.168.1.2    255.255.255.0      254       0.0.0.0      0.0.0.0
```


Saldırgan DHCP Server

```
Pool Name   Default Gateway  DNS Server   Start IP Address  Subnet Mask     Max User  TFTP Server  WLC Address
serverPool   192.168.2.1      8.8.8.8       192.168.2.2    255.255.255.0      254       0.0.0.0      0.0.0.0
```


Bu yapılandırmayı yaptıktan sonra bilgisayarlara gelip IP ayarlarını Static'ten DHCP'ye çektiğinizde **192.168.2.1**  bloğundan IP almaya başlayacaktır. Bunu önlemek için DHCP Snooping yapacağız.



Bağlamış olduğumuz switche gelip ayarları yapalım

### Switch DHCP Snooping

```
Switch(config)#interface gigabitEthernet 0/1
Switch(config-if)#ip dhcp snooping trust 
Switch(config-if)#ip arp inspection trust 
Switch(config-if)#exit 
Switch(config)#interface gigabitEthernet 0/2
Switch(config-if)#ip dhcp snooping trust 
Switch(config-if)#ip arp inspection trust 
Switch(config-if)#exit 
```

Şimdi IP ayarlarını DHCP'ye çektiğinizde her zaman **192.168.1.1** bloğundan IP aldığını göreceksiniz.


![image](https://github.com/ugurcomptech/C-DHCP-SNOOPING/assets/133202238/310e9aa2-9e7b-4907-9abb-532ca393ff97)


![image](https://github.com/user-attachments/assets/55182175-7f82-4c8d-9e26-7a64c2993d1c)


