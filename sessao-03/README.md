# Sessão 03: Hardening de Redes Linux e Configuração de Firewalls

# Objetivo

Configurar uma política defensiva utilizando UFW e iptables para proteger um servidor Linux contra acessos não autorizados.

 ## Comandos executados

```bash
sudo ufw status
sudo ufw enable
sudo ufw default deny incoming
sudo ufw default allow outgoing
sudo ufw allow 22/tcp
sudo iptables -A INPUT -s 203.0.113.50 -j DROP
sudo iptables-save | sudo tee /etc/iptables/rules.v4
sudo ufw status verbose
sudo iptables -L -v
```



# Explicação da política aplicada

Foi configurada uma política defensiva em que todas as ligações de entrada são bloqueadas por defeito e todas as ligações de saída são permitidas. O acesso SSH foi autorizado apenas na porta 22/TCP. Além disso, foi criada uma regra no iptables para bloquear o endereço IP fictício **203.0.113.50**, simulando o bloqueio de um IP malicioso.

## Capturas de ecrã 

<img width="952" height="898" alt="Captura de pantalla 2026-07-20 182420" src="https://github.com/user-attachments/assets/27f1c0ee-0c8a-41e7-bf80-8e910a5bcf81" /> <img 
<img width="952" height="906" alt="Captura de pantalla 2026-07-20 182444" src="https://github.com/user-attachments/assets/a89f2a1e-bafe-4a14-936a-c5c5a507405d" /> 
<img width="941" height="915" alt="Captura de pantalla 2026-07-20 182513" src="https://github.com/user-attachments/assets/3db4624c-649e-46e4-880b-4651a0e356cc" />

<img width="947" height="895" alt="Captura de pantalla 2026-07-20 182531" src="https://github.com/user-attachments/assets/75d68e18-a1c5-4f88-aacd-9032bcc2e584" />
<img width="947" height="901" alt="Captura de pantalla 2026-07-20 182600" src="https://github.com/user-attachments/assets/27a8ef54-94e6-4a09-bf82-e092f194b07f" />
<img width="942" height="892" alt="Captura de pantalla 2026-07-20 182751" src="https://github.com/user-attachments/assets/1334814d-81ac-4045-8b84-fba69cfe8bed" /> 

<img width="947" height="896" alt="Captura de pantalla 2026-07-20 182925" src="https://github.com/user-attachments/assets/cf20418a-c780-4663-b074-a4d0fa24873c" />









