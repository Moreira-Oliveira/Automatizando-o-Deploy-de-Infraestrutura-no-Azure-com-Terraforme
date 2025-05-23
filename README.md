# Automatizando-o-Deploy-de-Infraestrutura-no-Azure-com-Terraforme

🚀 Neste projeto, exploramos um tema essencial no universo da Infraestrutura como Código (IaC): a automação do deploy de recursos no Microsoft Azure usando Terraform, em um ambiente isolado com Docker.


☁️ O que é Cloud Computing com Microsoft Azure?

É a plataforma de nuvem da Microsoft para fornecer uma ampla variedade de serviços de computação pela internet, como servidores, armazenamento, bancos de dados, redes, inteligência artificial, análises, segurança, e muito mais. Esses serviços permitem que empresas e desenvolvedores criem, testem, implantem e gerenciem aplicativos e infraestrutura de forma escalável e sob demanda. que oferece uma vasta gama de serviços como:

* Servidores virtuais,

* Armazenamento,

* Bancos de dados,

* Redes,

* Inteligência artificial,

* Segurança,

* E muito mais.


🧰 Ferramentas Utilizadas

✅ Docker

✅ Terraform

✅ Azure CLI


🛠 Preparando o Ambiente

🔍 Vamos começar o projeto preparando o ambiente com o terraform e o Azure CLI

1. Criação da imagem e container Docker com as ferramentas necessárias.

![Image](https://github.com/user-attachments/assets/ebe252d3-9252-48ff-9453-d26aed51f8c4)


2. Instalação do Azure CLI dentro do container e realização do login.

![Image](https://github.com/user-attachments/assets/4dc31913-e0b4-4fab-945d-117e2f5069c0)


3. Preparação para executar os comandos do Terraform.

![Image](https://github.com/user-attachments/assets/a6a55ca9-eb36-4120-af62-315e1573b794)


🧩 Login no Azure via Terminal Docker

![Image](https://github.com/user-attachments/assets/682f446d-5369-40ea-9bef-b8d074016f74)

Para autenticar o Terraform com o Azure, foi necessário iniciar sessão via CLI dentro do container.


🧩 Definindo os Recursos com Terraform

![Image](https://github.com/user-attachments/assets/28aa031a-08e3-44e9-b87f-8294806129ec)


🧩 Grupo de recursos no Azure

* Virtual Network
* Virtual Subnet
* Network Interface
* Azure Virtual Machine

![Image](https://github.com/user-attachments/assets/3c6eaa75-e829-4add-bfbd-9ffd9fd6a906)

Esse código em Terraform define a infraestrutura de dados básica no Microsoft Azure, automatizando a criação de uma rede virtual, uma sub-rede, uma interface de rede e uma máquina virtual Linux. 

🔹 resource "azurerm_resource_group" "projeto_dsa"
Cria um Resource Group no Azure chamado "Grupo_Recursos_Projeto3" na região "West US 2".


📌 Resource Group: container lógico que agrupa recursos relacionados no Azure.

🔹 resource "azurerm_virtual_network" "dsa_vnet"
Cria uma rede virtual (VNet) chamada "vnet_terr_dsa" com o espaço de endereçamento IP 10.0.0.0/16.


📌 Esse espaço IP é usado para organizar os dispositivos dentro da rede privada da nuvem.

🔹 resource "azurerm_subnet" "dsa_subnet1"
Cria uma sub-rede chamada "subnet_terr_dsa" dentro da VNet com um espaço IP menor 10.0.1.0/24.


📌 Sub-redes dividem a rede em blocos menores para organização e segurança.

🔹 resource "azurerm_network_interface" "dsa_ni"
Cria uma interface de rede (NIC) chamada "ni_terr_dsa", que será conectada à sub-rede.


📌 Ela será associada a uma máquina virtual e receberá um IP privado dinâmico.

🔹 resource "azurerm_linux_virtual_machine" "dsa_vm"
Cria uma máquina virtual Linux chamada "vmdsa" com as seguintes características:

Tamanho: Standard_F2 (2 vCPUs, 4 GB RAM).

Usuário admin: adminuser.

Senha: "mLMpVC1qqnoq795z" (⚠️ não recomendado deixar senhas no código).

Conectada à interface de rede criada.

Disco gerenciado tipo Standard_LRS.

Imagem: Ubuntu 20.04 LTS da Canonical.


📌 A máquina será usada provavelmente para processamento, testes ou execução de ferramentas de dados.

✅ Resumo visual da arquitetura criada

![Image](https://github.com/user-attachments/assets/17cd34d7-62d2-4d8d-9dc6-121e855c8c59)


📚 Com tudo pronto vamos executar o prejeto no contiener Docker 

![Image](https://github.com/user-attachments/assets/72d31874-00ca-428d-80f6-3a7c9ffd2e0e)


* E agora executar o terraform graph:

![Image](https://github.com/user-attachments/assets/59594daa-2e16-4c04-a4fe-b8e6a13a684e)

O comando terraform graph gera uma representação gráfica da infraestrutura descrita nos arquivos .tf do seu projeto Terraform. Ele mostra a ordem de dependência entre os recursos, ou seja, como cada recurso está conectado e qual precisa ser criado antes do outro.

* Observação do graph de maneira visual

Geramos a estrutura de dependências entre os recursos. A visualização foi feita usando: http://webgraphviz.com/

Assim ele vai criar exatamente a sequencia com tados as operações necessarias

![Image](https://github.com/user-attachments/assets/ac9cd5b1-c4af-41e3-9031-0ee874da4948)


* Provisionando a Infraestrutura

![Image](https://github.com/user-attachments/assets/6582dc98-c065-41c2-a68a-0fe617017818)

Após validar a configuração, aplicamos o plano com terraform apply, e os recursos foram criados automaticamente no Azure.


* Resultado Final no Portal do Azure

![image](https://github.com/user-attachments/assets/efd671e1-a6e3-4a47-a0ab-ae2a644708cc)

Todos os recursos foram provisionados com sucesso, conforme mostrado no portal


✅ Conclusão

Este projeto demonstrou na prática como automatizar o provisionamento de infraestrutura no Azure com Terraform, oferecendo vantagens como:

* Reprodutibilidade: os ambientes podem ser recriados de forma consistente.

* Agilidade: menos esforço manual, mais tempo para inovação.

* Segurança e controle: tudo é versionado e auditável.

* Escalabilidade: o mesmo código pode ser usado para diferentes ambientes (desenvolvimento, testes, produção).

Unir Terraform + Azure + Docker é uma excelente prática para equipes de DevOps e engenheiros de dados que buscam agilidade e padronização no gerenciamento de recursos em nuvem.














