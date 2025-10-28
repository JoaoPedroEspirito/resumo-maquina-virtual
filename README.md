🖥️ Guia: Criando uma Máquina Virtual no Microsoft Azure
📘 Visão Geral

Este guia apresenta o passo a passo para criar, configurar e acessar uma Máquina Virtual (VM) dentro do Microsoft Azure.
Com uma VM, é possível hospedar aplicações, simular servidores, testar sistemas operacionais e muito mais — tudo na nuvem, com escalabilidade e segurança.

☁️ O que é uma Máquina Virtual?

Uma Máquina Virtual (VM) é um computador virtualizado que roda dentro da infraestrutura da Microsoft Azure.
Ela funciona como um servidor físico, mas está hospedada em data centers da Microsoft, permitindo escolher:

Sistema operacional (Windows, Linux etc.)

Tamanho (quantidade de CPU, RAM, disco)

Rede e segurança (IP, firewall, grupos de segurança)

Armazenamento e backups

🧭 Passo a Passo — Criando sua VM no Azure
🔹 1. Acessar o Portal do Azure

Vá para: https://portal.azure.com

Faça login com sua conta Microsoft.

Caso ainda não tenha, crie uma conta gratuita:
👉 https://azure.microsoft.com/pt-br/free

🔹 2. Criar um Novo Recurso

No menu lateral, clique em “Criar um recurso”.

Selecione “Máquina Virtual” (ou busque por “Virtual Machine” na barra de pesquisa).

🔹 3. Configurar a VM

Preencha os campos principais:

📍 Aba: Básico

Assinatura: escolha a sua assinatura ativa.

Grupo de Recursos: crie um novo (ex: rg-lab-azure) ou use um existente.

Nome da Máquina Virtual: ex: vm-lab-windows.

Região: escolha a mais próxima (ex: Brazil South).

Imagem (SO): escolha o sistema operacional, ex:

Windows Server 2022 Datacenter

Ubuntu Server 22.04 LTS

Tamanho: escolha conforme sua necessidade (ex: B1s para testes).

Usuário Administrador: defina um nome de usuário e senha/SSH Key.

🔹 4. Configurar Rede

Na aba Rede, será criado um IP público e uma VNet (Virtual Network) automaticamente.

Confirme as opções:

Porta de entrada:

Para Windows → habilite RDP (3389)

Para Linux → habilite SSH (22)

Isso permitirá o acesso remoto à sua VM.

🔹 5. Revisar e Criar

Clique em Revisar + Criar.

O Azure fará uma validação das configurações.

Se tudo estiver certo, clique em Criar.
⏳ O processo leva alguns minutos.

🔑 Acessando sua VM
💻 Se for Windows

Após criada, vá até o recurso da VM.

Clique em “Conectar” → “RDP”.

Baixe o arquivo .rdp e abra no seu computador.

Insira o usuário e senha definidos na criação.

🐧 Se for Linux

Copie o endereço IP público da VM.

No terminal, conecte via SSH:

ssh usuario@IP_Publico


Digite a senha ou use a chave SSH configurada.

🧩 Configurações Opcionais

Extensões: instale agentes, antivírus ou scripts automáticos.

Snapshots: crie pontos de restauração do disco.

Monitoramento: acompanhe CPU, memória e rede via Azure Monitor.

Backup: configure o Azure Backup para proteger os dados.

Auto-shutdown: defina um horário para desligamento automático e economize custos.

💵 Custos e Boas Práticas

As VMs são cobradas por hora de uso.

Use tamanhos menores (B1s, B2s) para testes.

Desligue (deallocate) a VM quando não estiver em uso.

Monitore custos no painel “Custo de Gerenciamento”.

✅ Conclusão

Criar uma Máquina Virtual no Azure é simples e rápido.
Ela permite experimentar sistemas, rodar servidores e testar aplicações sem precisar de hardware físico.
Com o Azure, você tem alta disponibilidade, segurança, e escalabilidade sob demanda.

📎 Recursos Úteis

🌐 Portal do Azure

📚 Documentação Oficial do Azure VMs

💡 Calculadora de Custos do Azure
