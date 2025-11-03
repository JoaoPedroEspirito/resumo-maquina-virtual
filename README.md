🖥️ Guia: Criando uma Máquina Virtual no Microsoft Azure
📘 Visão Geral

Este guia apresenta o passo a passo para criar, configurar e acessar uma Máquina Virtual (VM) dentro do Microsoft Azure.
Com uma VM, é possível hospedar aplicações, simular servidores, testar sistemas operacionais e muito mais — tudo na nuvem, com escalabilidade, segurança e alta disponibilidade.

☁️ O que é uma Máquina Virtual?

Uma Máquina Virtual (VM) é um computador virtualizado que roda dentro da infraestrutura global da Microsoft Azure.
Ela funciona como um servidor físico, mas está hospedada em data centers distribuídos em várias regiões do mundo, permitindo ao usuário:

Escolher o sistema operacional (Windows, Linux, etc.)

Definir tamanho (quantidade de CPU, memória e disco)

Configurar rede e segurança (endereços IP, firewall, sub-redes, balanceamento de carga)

Gerenciar armazenamento, snapshots e backups automáticos

🧩 Como funciona a Infraestrutura e Rede no Azure
🌍 Infraestrutura Global

O Azure é composto por regiões e zonas de disponibilidade, cada uma contendo múltiplos data centers interconectados.
Esses data centers são projetados com redundância e segurança física, garantindo alta disponibilidade (SLA) e continuidade dos serviços.

Região: área geográfica (ex: Brazil South, East US, West Europe).

Zona de disponibilidade: data centers isolados dentro da mesma região — usados para garantir resiliência.

Rede de backbone da Microsoft: interliga globalmente as regiões com baixa latência.

🕸️ Rede Virtual (VNet - Virtual Network)

A Virtual Network (VNet) é a base da comunicação dentro do Azure.
Ela funciona como uma rede privada virtual, semelhante a uma rede local (LAN), mas hospedada na nuvem.

Cada VM criada é associada a uma VNet, que contém:

Sub-redes (Subnets): dividem a rede em segmentos lógicos.

Endereços IP: cada VM recebe um IP privado, e opcionalmente um IP público para acesso externo.

NSG (Network Security Group): define regras de firewall de entrada e saída (ex: liberar porta 22 para SSH ou 3389 para RDP).

Peering: permite conectar VNets entre diferentes regiões ou grupos de recursos.

VPN Gateway / ExpressRoute: conecta o ambiente Azure a redes locais (on-premise).

💡 Dica: Você pode isolar redes por aplicação ou ambiente (ex: DEV, TEST, PROD) e controlar o tráfego entre elas.

🔒 Segurança de Rede no Azure

O Azure oferece camadas de segurança integradas para proteger suas VMs e dados:

NSG (Network Security Group): controla tráfego de rede (semelhante a um firewall).

Azure Firewall: firewall corporativo com inspeção de tráfego e políticas avançadas.

Application Gateway + WAF: balanceador de carga com firewall de aplicação web.

Azure DDoS Protection: protege contra ataques de negação de serviço.

Private Endpoints: conectividade privada entre recursos (sem IP público).

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
📍 Aba: Básico

Assinatura: escolha a sua assinatura ativa.

Grupo de Recursos: crie um novo (ex: rg-lab-azure) ou use um existente.

Nome da Máquina Virtual: ex: vm-lab-windows.

Região: escolha a mais próxima (ex: Brazil South).

Imagem (SO): selecione o sistema operacional:

Windows Server 2022 Datacenter

Ubuntu Server 22.04 LTS

Tamanho: selecione conforme a necessidade (ex: B1s para testes).

Usuário Administrador: defina nome e senha/SSH Key.

🔹 4. Configurar Rede

Na aba Rede, o Azure criará automaticamente uma VNet (Virtual Network), uma sub-rede e um IP público.

Verifique as opções:

Portas de entrada:

Windows → habilite RDP (3389)

Linux → habilite SSH (22)

Grupo de Segurança de Rede (NSG): defina regras personalizadas, se necessário.

Endereço IP Público: usado para conexão remota à VM.

VNet/Subnet: você pode usar uma existente ou criar uma nova.

🔹 5. Revisar e Criar

Clique em Revisar + Criar.

O Azure fará uma validação automática das configurações.

Se estiver tudo certo, clique em Criar.
⏳ O processo levará alguns minutos.

🔑 Acessando sua VM
💻 Windows

Acesse o recurso da VM.

Clique em “Conectar” → “RDP”.

Baixe e abra o arquivo .rdp.

Informe o usuário e senha definidos.

🐧 Linux

Copie o IP público da VM.

No terminal, execute:

ssh usuario@IP_Publico


Digite a senha ou utilize a chave SSH configurada.

⚙️ Configurações Opcionais

Extensões: adicione agentes, antivírus, ou scripts automáticos.

Snapshots: crie pontos de restauração do disco.

Monitoramento: acompanhe CPU, memória e rede via Azure Monitor.

Backup: configure o Azure Backup para proteger dados.

Auto-shutdown: defina horário de desligamento automático (economiza custos).

💵 Custos e Boas Práticas

As VMs são cobradas por hora de execução.

Use tamanhos menores (B1s, B2s) para ambientes de teste.

Desligue (Deallocate) a VM quando não estiver em uso.

Monitore consumo em Custos + Cobrança.

Utilize a Calculadora de Custos do Azure para prever gastos:
👉 https://azure.microsoft.com/pt-br/pricing/calculator/

🧠 Dica Avançada: Estrutura da Infra Azure para VMs

Uma implantação típica de VM no Azure é composta por:

[Internet]
   |
[IP Público]
   |
[Network Security Group]
   |
[Sub-rede dentro da VNet]
   |
[Máquina Virtual]
   |
[Disco Gerenciado + Storage Account]


Cada VM está dentro de um Resource Group, com dependências como:

Network Interface (NIC)

Disco OS

VNet/Subnet

IP Público

NSG (Firewall)

Tudo isso é gerenciado de forma modular e pode ser automatizado via ARM Template, Bicep ou Terraform.

✅ Conclusão

Criar uma Máquina Virtual no Azure é simples e poderoso.
Ela permite hospedar aplicações, criar laboratórios e simular ambientes empresariais sem depender de hardware físico.
Com uma infraestrutura robusta, redes seguras e opções flexíveis de gerenciamento, o Azure oferece alta disponibilidade, segurança e escalabilidade sob demanda.

📎 Recursos Úteis

🌐 Portal do Azure

📚 Documentação Oficial do Azure VMs

💡 Calculadora de Custos do Azure

🧱 Documentação sobre Redes Virtuais

🔒 Segurança de Rede no Azure
