# Configuração de Rede — Kali Linux

## Objetivo

Configurar interfaces de rede da máquina atacante com IP estático
para garantir comunicação estável com as demais VMs do laboratório.

## Interfaces

| Interface | Tipo      | IP               | Finalidade                          |
|-----------|-----------|------------------|-------------------------------------|
| eth0      | NAT       | DHCP (automático)| Acesso externo, atualização de pacotes |
| eth1      | Host-Only | 192.168.56.10/24 | Comunicação interna com as VMs      |

## Configuração Aplicada

Arquivo editado: `/etc/network/interfaces`

```bash
# Interface Host-Only com IP estático
auto eth1
iface eth1 inet static
    address 192.168.56.10
    netmask 255.255.255.0
```

Aplicar sem reiniciar:
```bash
sudo ifdown eth1 && sudo ifup eth1
```

## Verificação

```bash
ip addr show eth1
# Esperado: inet 192.168.56.10/24

ping 192.168.56.1   # gateway Host-Only
# Esperado: resposta sem perda de pacotes
```

## Status

- [x] Interface eth0 (NAT) ativa
- [x] Interface eth1 (Host-Only) configurada com IP estático
- [x] Conectividade com gateway verificada
