# SOC Home Lab

Laboratório virtualizado para simulação de ataques e detecção de ameaças,
integrando Wazuh (HIDS) e Splunk (SIEM) em ambiente segmentado no VirtualBox.

Desenvolvido como preparação técnica para atuação em Blue Team/SOC,
com foco em análise de logs, correlação de eventos e investigação de incidentes.

---

## Ambiente

| VM             | OS               | Função                        | IP             |
|----------------|------------------|-------------------------------|----------------|
| Kali Linux     | Kali Linux       | Atacante                      | 192.168.56.10  |
| Ubuntu Server  | Ubuntu 25.04 LTS | Splunk Enterprise (SIEM)      | 192.168.56.20  |
| Ubuntu Server  | Ubuntu 25.04 LTS | Alvo (Wazuh Agent)            | 192.168.56.30  |
| Debian 12      | Debian 12        | Wazuh Manager                 | 192.168.56.40  |

## Arquitetura de Rede

Todas as VMs operam em rede **Host-Only** (`vboxnet0`, 192.168.56.0/24)
para comunicação interna isolada.

Kali e Ubuntu Alvo possuem interface **NAT** adicional para
acesso externo e atualização de pacotes.

Diagrama completo: [`diagrams/lab-architecture.png`](diagrams/lab-architecture.png)

## Cenários de Detecção

- Brute force SSH → detecção via Wazuh + correlação no Splunk
- Escalonamento de privilégios → alerta Wazuh nível ≥ 10
- Reconhecimento de rede (nmap) → logs de autenticação e sistema
- Acesso não autorizado → correlação falhas + login bem-sucedido

## Estrutura do Repositório

docs/setup/       → instalação e configuração de cada componente
splunk/queries/   → queries SPL por categoria de ameaça
wazuh/rules/      → regras customizadas
incidents/        → relatórios de detecção simulada
diagrams/         → arquitetura de rede
screenshots/      → evidências visuais

## Progresso

- [x] Criação das VMs
- [x] Configuração das interfaces NAT e Host-Only
- [x] Configuração inicial do Kali Linux
- [x] Configuração do Wazuh Manager (Debian)
- [ ] Configuração do Wazuh Agent (Ubuntu Alvo)
- [ ] Configuração do Splunk Enterprise
- [ ] Configuração dos Universal Forwarders
- [ ] Integração Wazuh → Splunk
- [ ] Primeiro cenário de detecção documentado
