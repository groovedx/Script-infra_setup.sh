#!/bin/bash

# Criando grupos
echo "Criando grupos de usuários..."
groupadd TI
groupadd DevOps
groupadd Seguranca

# Criando usuários e adicionando aos grupos
echo "Criando usuários e adicionando aos grupos..."
useradd -m -s /bin/bash -G TI carlos
useradd -m -s /bin/bash -G DevOps mariana
useradd -m -s /bin/bash -G Seguranca roberto

# Configurando senhas para os usuários (pode ser ajustado conforme necessidade)
echo "Definindo senhas padrão para os usuários..."
echo "carlos:Senha123" | chpasswd
echo "mariana:Senha123" | chpasswd
echo "roberto:Senha123" | chpasswd

# Criando diretórios e ajustando permissões
echo "Criando diretórios e configurando permissões..."
mkdir -p /home/shared/TI
mkdir -p /home/shared/DevOps
mkdir -p /home/shared/Seguranca
chown root:TI /home/shared/TI
chown root:DevOps /home/shared/DevOps
chown root:Seguranca /home/shared/Seguranca
chmod 770 /home/shared/TI
chmod 770 /home/shared/DevOps
chmod 770 /home/shared/Seguranca

# Finalizando
echo "Infraestrutura configurada com sucesso!"
