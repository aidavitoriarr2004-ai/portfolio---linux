# Sessão 04 - Gestão Segura de Acessos Remotos SSH em Linux

---

## 🎯 Objetivo

Proteger o canal de gestão remota do servidor Ubuntu, eliminando a autenticação tradicional por password e migrando para autenticação criptográfica com chave Ed25519.

---

##  Ambiente Utilizado

- **TryHackMe — Linux Strength Training**  
  https://tryhackme.com/room/linuxstrengthtraining

---

##  Tarefas 

### 1. Criação de utilizador de teste
```bash
sudo useradd -m -s /bin/bash teste
sudo passwd teste
Evidência:

text
uid=1001(teste) gid=1001(teste) groups=1001(teste)
passwd: password updated successfully
2. Geração do par de chaves Ed25519
bash
ssh-keygen -t ed25519
Evidência:

text
Your identification has been saved in /root/.ssh/id_ed25519
Your public key has been saved in /root/.ssh/id_ed25519.pub
The key fingerprint is:
SHA256:6GXDYzfJREf5yTILed7mo7KNm+9v5FBX8V+DR0ocMZY root@ubuntu
3. Transferência da chave pública para o servidor
bash
ssh-copy-id teste@172.30.1.2
Evidência:

text
Number of key(s) added: 1
Now try logging into the machine, with: "ssh 'teste@172.30.1.2'"
4. Teste de autenticação com chave (porta padrão 22)
bash
ssh -i ~/.ssh/id_ed25519 -p 22 teste@172.30.1.2
Evidência:

text
teste@ubuntu:~$
Login realizado com sucesso utilizando a chave Ed25519.

5. Configuração do ficheiro sshd_config
bash
nano /etc/ssh/sshd_config
Linhas adicionadas/modificadas:

ini
Port 2222
PermitRootLogin no
PasswordAuthentication no
6. Validação da sintaxe
bash
sshd -t
Resultado: Nenhum erro retornado, sintaxe válida ✅

7. Reinício do serviço SSH
bash
service ssh restart
8. Teste de acesso na nova porta
bash
ssh -i ~/.ssh/id_ed25519 -p 2222 teste@172.30.1.2
 Desafios Encontrados 
Durante a execução do laboratório, foram identificados os seguintes desafios:

🔹 Erro: teste is not in the sudoers file
Causa: O utilizador teste não tinha permissões de superutilizador.

Solução: Como root, não é necessário utilizar sudo. Os comandos foram executados diretamente.

🔹 Erro: Connection refused na porta 2222
Causa: O ficheiro sshd_config não foi salvo corretamente ou o serviço não reiniciou com a nova configuração.

Aprendizagem: É fundamental salvar as alterações e verificar a porta com ss -tlnp | grep ssh.

🔹 Erro: Error writing /etc/ssh/sshd_config: No such file or directory
Causa: O caminho do ficheiro foi digitado incorretamente.

Aprendizagem: Verificar sempre o caminho exato do ficheiro antes de salvar.
