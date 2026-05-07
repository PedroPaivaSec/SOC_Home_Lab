# SOC_Home_Lab
Laboratório virtualizado focado em detecção, monitoramento e análise de eventos de segurança utilizando Wazuh, Splunk, Suricata e Zeek em ambiente segmentado no VirtualBox.

# SOC Lab Virtualizado

## Objetivo
Laboratório virtualizado focado em estudos de:
- SIEM
- análise de logs
- monitoramento
- investigação de incidentes

## Ambiente
| VM | Função |
|---|---|
| Kali Linux | Geração de tráfego ofensivo |
| Debian 12 | Wazuh Manager |
| Ubuntu Server | Splunk Enterprise |
| Ubuntu Server | Servidor HTTP alvo |

## Arquitetura de Rede
Cada máquina virtual utiliza:
- NAT para acesso externo e atualização de pacotes
- Host-Only para comunicação interna do laboratório

## Status Atual
- [x] Criação das VMs
- [x] Configuração das interfaces NAT e Host-Only
- [x] Configuração inicial do Kali Linux
- [ ] Configuração do Wazuh
- [ ] Configuração do Splunk
- [ ] Integração de logs
