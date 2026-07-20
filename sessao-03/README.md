# Sessão 03: Hardening de Redes Linux e Configuração de Firewalls

# Objetivo

Configurar uma política defensiva utilizando UFW e iptables para proteger um servidor Linux contra acessos não autorizados.

 Comandos executados

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

Output do UFW

*(Inserir aqui a imagem do comando `sudo ufw status verbose`.)*

Output do iptables

*(Inserir aqui as imagens do comando `sudo iptables -L -v`.)*

 Explicação da política aplicada

Foi configurada uma política defensiva em que todas as ligações de entrada são bloqueadas por defeito e todas as ligações de saída são permitidas. O acesso SSH foi autorizado apenas na porta 22/TCP. Além disso, foi criada uma regra no iptables para bloquear o endereço IP fictício **203.0.113.50**, simulando o bloqueio de um IP malicioso.
