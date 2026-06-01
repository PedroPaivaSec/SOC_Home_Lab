# VM2 — Ubuntu Server: Splunk Enterprise

## Especificações

| Campo             | Valor                  |
|-------------------|------------------------|
| Sistema           | Ubuntu Server (LTS)    |
| Função            | SIEM — Splunk Enterprise |
| IP (lab)          | `192.168.56.20`        |
| Porta Web UI      | `8000`                 |
| Porta Forwarder   | `9997`                 |

---

## Rede (Netplan)

Duas interfaces:
- **enp0s3** — NAT (internet, DHCP)
- **enp0s8** — Host-Only (`192.168.56.20/24`)

```yaml
# /etc/netplan/00-installer-config.yaml
network:
  version: 2
  ethernets:
    enp0s3:
      dhcp4: true
    enp0s8:
      dhcp4: false
      addresses:
        - 192.168.56.20/24
```

```bash
sudo netplan apply
```

---

## Instalação

> Criei uma conta gratuita em [splunk.com/download](https://www.splunk.com/en_us/download/splunk-enterprise.html).

```bash
wget -O splunk.deb 'MEU_LINK'
sudo dpkg -i splunk.deb
sudo /opt/splunk/bin/splunk start --accept-license --answer-yes
sudo /opt/splunk/bin/splunk enable boot-start -user splunk
```

---


## Acesso

http://192.168.56.20:8000


---

## Configuração Pós-Instalação

**Criar index:**
`Settings → Indexes → New Index → Nome: soc_lab → Max Size: 10GB`

**Habilitar recebimento de forwarders:**
`Settings → Forwarding and Receiving → Configure Receiving → New → Porta: 9997`
