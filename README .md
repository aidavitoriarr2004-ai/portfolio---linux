 Sessão 01 – Introdução ao Linux para Segurança e Comandos de Rede

 Objetivo
Realizar um scan de um alvo utilizando o Nmap e identificar os serviços em execução.

 Comando utilizado

```bash
nmap -sV -sC 10.128.136.238
```

 Número de portas abertas

Foram identificadas 5 portas abertas.

| Porta | Serviço | Versão |
|------:|----------|---------|
| 21 | FTP | FileZilla ftpd |
| 53 | DNS | Simple DNS Plus |
| 80 | HTTP | Microsoft IIS 10.0 |
| 135 | MSRPC | Microsoft Windows RPC |
| 3389 | RDP | Microsoft Terminal Services |

# Informações adicionais

- FTP Anonymous Login Allowed.
- HTTP TRACE ativado.
- Nome da máquina: WIN-SCAN.

 Comandos executados

```bash
ip a
```

```bash
ss -tuln
```

```bash
nmap -sV -sC 10.128.136.238
```

## Evidências

As capturas de ecrã dos comandos encontram-se nesta pasta.
