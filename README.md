# ad-wire-guard-ui
Combination Wireguird (wg-easy latest) + Adguard Home + Unbound (Latest)

Here is the start of combination
# Requirings:
* Docker
* Docker-compose

These confinguration of AdGuard include DNS-over-HTTPS (DoH) via Cloudflare service by using DNS: https://cloudflare-dns.com/dns-query
Fow query to CF-DNS using Unbound. This is some type of DNS forwarding.

## Autors:

👤 ** Alexey **
* Git: [DigneZzZ](https://github.com/DigneZzZ)
* Site: [OpeNode.RU](https://openode.ru)

👤 ** Dmitriy **
* Git [Nuborg](https://github.com/nubortg)


## Adguard Web-UI
![image](https://user-images.githubusercontent.com/50312583/206703310-3bc8f759-91fa-42db-8d43-eca0050c70bf.png)

## Wireguard-Easy Web-UI
![image](https://user-images.githubusercontent.com/50312583/206703207-f3bd39f1-72c7-458c-9893-ad2126a0d47b.png)




# Quick Install

```bash
git clone https://github.com/dignezzz/ad-wireguard.git
cd ad-wireguard && nano docker-compose.yml

#then run
docker-compose up -d
```

## AFter Instalation
After install, follow to instruction:
Go to: http://10.2.0.100/  
<b>Login:</b> <u>admin</u> <br />
<b>Password:</b> <u>a12345678</u>

## ATTENTION! Change admin username and/or password
### First way:
1. On the server:
```bash
sudo apt install apache2-utils 
htpasswd -nbB admin 'MyNewPassword'
```

2. Open ur configuration file of AGH:
```bash
nano ../ad-wireguard/conf/AdGuardHome.yaml
```
3. Change for NEW Name and Password:
```bash
users:
  - name: admin
    password: $2y$10$G7Qu8Y3szepMfaRUyQ.FmuKR.n4U9dHOQm.GgrIMuYC9UP8vmHJri
```
4. Recreate your container:
```bash
docker-compose up -d --force-recreate
```
### Second way:
1. Go to site: https://hostingcanada.org/htpasswd-generator/
2. Change Mode: **bcrypt**
3. Enter new Username and Password
4. Open ur configuration file of AGH:
```bash
nano ../ad-wireguard/conf/AdGuardHome.yaml
```
5. Change Name and Password:
```bash
users:
  - name: admin
    password: $2y$10$G7Qu8Y3szepMfaRUyQ.FmuKR.n4U9dHOQm.GgrIMuYC9UP8vmHJri
```
6. Recreate your container:
```bash
docker-compose up -d --force-recreate
```

Full information from AGH site: https://docs.cloudron.io/apps/adguard-home/

# Adlists:
### RU-Adlist
https://easylist-downloads.adblockplus.org/advblock.txt
### BitBlock
https://easylist-downloads.adblockplus.org/bitblock.txt
### Cntblock
https://easylist-downloads.adblockplus.org/cntblock.txt
### EasyList
https://easylist-downloads.adblockplus.org/easylist.txt

# Upstream DNS-Servers
### About default DNS
  The unencrypted 1.1.1.1 is fine if you're sure the connection between your AGH instance and Cloudflare DNS won't be tampered. Otherwise use the encrypted endpoint, either https://cloudflare-dns.com/dns-query for unfiltered query or https://security.cloudflare-dns.com/dns-query for malware filtering. Note that ECH doesn't work if you're using unencrypted upstream.

### All DNS Servers
https://adguard-dns.io/kb/general/dns-providers/#cloudflare-dns

### DNS Perfomance list:
https://www.dnsperf.com/#!dns-resolvers

