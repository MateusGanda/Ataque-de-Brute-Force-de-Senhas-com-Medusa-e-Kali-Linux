# Ataque-de-Brute-Force-de-Senhas-com-Medusa-e-Kali-Linux
Simulando um Ataque de Brute Force de Senhas com Medusa e Kali Linux no curso Santander - Cibersegurança 2025 da DIO


# REQUISITOS:
Ter instalado o linux seja ele pelo VirtualBox ou se ter no sistema operacional da máquina.

Ter instalado o Metasploitable2 para servir como a máquina que será atacada

# 📘 1. Visão Geral do Projeto

Este documento descreve uma simulação educativa e autorizada de um ataque de força bruta (Brute Force) utilizando ferramentas do Kali Linux, com foco no utilitário Medusa.
O teste foi totalmente realizado em máquinas virtuais privadas, sem qualquer impacto externo.
Este laboratório demonstra, de forma controlada, três cenários clássicos de ataques de autenticação:

🔹 1. Força bruta em FTP

Avaliação da resistência de um serviço FTP configurado com credenciais fracas.

🔹 2. Automação de tentativas de login em formulário Web (DVWA)

Demonstração de como um formulário sem proteção pode ser automatizado.

🔹 3. Password Spraying em SMB com enumeração de usuários

Verificação de contas SMB com uma mesma senha fraca.

⚠️ Aviso ético e legal
Este material destina-se exclusivamente ao estudo e à conscientização em Segurança da Informação.
Todos os testes foram feitos em um ambiente isolado, privado e autorizado pelo próprio autor.

# 🧪 2. Ambiente do Laboratório
🖥️ Máquina Atacante

SO: Kali Linux

Ferramenta principal: Medusa

Wordlists: listas educacionais (ex.: rockyou.txt)

🎯 Máquina Alvo

DVWA (modo Low Security)

Serviço FTP com usuário de teste

Serviço SMB com contas simuladas

Senhas fracas propositalmente configuradas

🌐 Rede
[ Kali Linux ] — Host-Only — [ VM Alvo ]


Rede isolada

Sem acesso à Internet

Sem risco para sistemas reais

🗃️ Snapshots

Snapshots realizados antes de cada teste.

# 📚 3. Wordlists Utilizadas
✔ Lista de Usuários (userlist.txt)
admin
test
user
guest
ftp

✔ Lista de Senhas (passwords.txt)
123456
password
admin
admin123
guest
test


Pequenas e fracas: ideal para demonstração rápida sem impactar o sistema.

# 🎯 4. Teste 1 — Força Bruta em FTP
🔍 Objetivo

Avaliar como um servidor FTP simples responde a diversas tentativas de autenticação.

🛠 Metodologia

Identificação do serviço FTP na máquina alvo

Teste com lista pequena de usuários

Teste com wordlist simples de senhas

Registro manual das tentativas

Comparação com logs da máquina alvo

🧪 Validação

Múltiplas tentativas registradas no log do FTP

Nenhum bloqueio automático configurado

Uma das combinações fracas foi aceita → acesso obtido

Constatada ausência de criptografia

⚠ Riscos identificados

FTP é um protocolo inseguro por padrão

Sem bloqueio de tentativas

Senhas previsíveis facilitam ataques

# 🌐 5. Teste 2 — Automação de Login em Formulário Web (DVWA)
🎯 Objetivo

Demonstrar como um formulário web vulnerável pode ser automatizado para testar credenciais.

🛠 Metodologia

DVWA configurado em Low Security

Identificação dos campos enviados no POST (“username” e “password”)

Automação das tentativas usando wordlists

Comparação de respostas do servidor:

Sucesso: página com "Welcome"

Falha: "Login Failed"

🧪 Validação

DVWA aceitou tentativas rápidas sem limitações

Respostas diferentes entre sucesso e falha facilitaram detecção

A senha fraca correspondente ao usuário “admin” foi encontrada

⚠ Riscos

Sem rate limit

Sem CAPTCHA

Resposta explícita sinaliza sucesso/falha

Formulário fácil de automatizar

# 🖥️ 6. Teste 3 — Password Spraying em SMB
🎯 Objetivo

Testar a reutilização de uma única senha fraca em múltiplos usuários SMB.

🔍 Enumeração realizada

Usuários identificados no ambiente SMB (exemplo):

Administrator
Guest
User1
User2

🛠 Metodologia

Seleção de uma única senha fraca ("admin123")

Tentativa em todos os usuários listados

Monitoramento de logs SMB

Observação de possíveis bloqueios

🧪 Validação

A maioria retornou falha de autenticação

Um dos usuários possuía a senha fraca

Logs capturaram as tentativas corretamente

Nenhum bloqueio automático ocorreu

⚠ Riscos

Contas SMB com senha repetida

Password spraying difícil de detectar

Existência de usuários inativos facilita exploração

# 📊 7. Registro Consolidado dos Testes
| Teste                 | Usuários   | Wordlist      | Resultado       | Observações               |
| --------------------- | ---------- | ------------- | --------------- | ------------------------- |
| FTP Brute Force       | admin, ftp | passwords.txt | Sucesso parcial | Sem bloqueio              |
| DVWA Automação        | admin      | passwords.txt | Sucesso         | Sem CAPTCHA ou rate limit |
| SMB Password Spraying | 4 usuários | senha única   | 1 sucesso       | Senha fraca repetida      |

# 🛡️ 8. Recomendações de Mitigação
🔒 FTP

Desativar FTP → substituição por SFTP/FTPS

Bloquear após tentativas consecutivas

Aplicar firewall com limite de conexões

Exigir senhas fortes

🌐 Web (DVWA / Aplicações Reais)

Implementar CAPTCHA

Usar rate limit por IP

Erros genéricos ("credenciais inválidas")

Adoção de MFA

Hash seguro de senhas

📁 SMB

Políticas rígidas de senha (complexidade mínima)

Desativar contas “Guest” ou não utilizadas

Habilitar bloqueio por tentativas

Monitoramento e alertas via SIEM

Auditoria periódica

# 🧾 9. Conclusão

Os testes demonstraram a facilidade de comprometer sistemas sem proteção adequada, mesmo com wordlists extremamente simples.
A prática reforça:

A importância de senhas fortes

A necessidade de políticas de bloqueio

Monitoramento e alertas

Redução de superfície de ataque

🌱 Este laboratório reforça a conscientização e a importância de seguir boas práticas em Segurança da Informação.


# CASO UTILIZAR NO VIRTUAL BOX:
Colocar ambas as máquinas na parte de rede em "placa de rede exclusiva de hospedeiro (host-only)"

# EXEPLOS DE CÓDIGOS: 

# NO LINUX QUE VAI INVADIR:

COMANDO PARA CRIAR UMA LISTA DE USUÁRIOS:

echo -e 'users\nmsfadmin\nadmin\nroot' > users.txt

COMANDO PARA CRIAR UMA LISTA DE SENHAS:

echo -e '123456\nmsfadmin\nadmin\nroot' > pass.txt

COMANDO PARA USAR PARA TESTAR DIFERENTES USUARIOS E SENHAS NO SISTEMA DE FTP:

medusa -h IP_DA_MAQUINA_A_SER_INVADIDA -U users.txt -P pass.txt -M ftp -t 6

# NO LINUX QUE VAI SER INVADIDO:

ip a -> para descobir qual é o ip da máquina
