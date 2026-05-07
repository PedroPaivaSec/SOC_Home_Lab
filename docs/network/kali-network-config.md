# Configuração de Rede - Kali Linux

## Objetivo
Preparar máquina atacante do laboratório SOC com comunicação previsível entre VMs.

## Interfaces de Rede

### NAT
Utilizada para:
- atualização de pacotes
- acesso externo

### Host-Only
Configurada com IP estático:
- 192.168.56.10/24

Objetivo:
- comunicação interna entre VMs
- geração de tráfego controlado
- integração com ferramentas SIEM/IDS

## Status
- [x] Interfaces configuradas
- [x] IP estático definido
- [ ] Testes de conectividade
