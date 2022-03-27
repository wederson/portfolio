---
layout: post
title: "Parte 2: Azure DevOps + EC2 - Build Artifact"
date: 2022-03-27 11:50:00
tags:
  - todos
  - azure DevOps
  - ec2
  - aws cloud
  - CI/CD
author: Wederson S. Machado
avatar: ../assets/profile.png
category:
  - Dicas
  - DevOps
---

Nesse artigo vamos detalhar os passos necessários para criar uma entrega contínua com o Azure DevOps e servidores EC2 da AWS, explicando o processo de criar um artefato que será utilizado na criação do CI/CD.


Iremos dividir este guia em 4 etapas:
1. [Parte 1: Azure DevOps + EC2 - Introdução](/azure-pipeline-ec2-introducao)
2. [Parte 2: Azure DevOps - Definição de Build e Build Artefato](/azure-pipeline-ec2-build-artifact)
3. Parte 3: Azure DevOps - Deployment Group
4. Parte 4: Azure DevOps - Criando Release

---

# Integração Contínua e Entrega Contínua
![CICD](../assets/img/posts/azure-pipeline-ec2-build-artifact/cicd.png)
Eu não irei detalhar todos os processos de CI/CD, espero que o leitor já tenha um conhecimento básico sobre cada uma das etapas e quais suas responsabilidades. Entretando, irei descrever brevimente as 2 etapas que iremos utilizar para a construção do nosso Pipeline:
1. Build;
2. Release;

## Build
No fluxo de CI/CD a etapa de build é responsável por contruir/estruturar o código necessário que será enviado para o servidor. Sendo assim, o build é realizado após uma codificação e utilizar um controlador de versão (git) é fundamental para um processo mais estruturado. No final do Build um pacote normalmente é gerado e este pacote será utilizado nas próximas etapas do Pipelina. Este pacote é chamado de Artefato.

## Release
Release é o processo de entrega, nesta etapa iremos realizar a conexão com o servidor/serviço de destino e executar todos os passos necessários para enviar o projeto para o servidor. É nessa etapa que iremos "desempacotar" nossos arquivos e enviar eles para o servidor de destino.

---
# Azure DevOps: Criando Pipeline - Build e Artefato
![Azure Pipeline](/assets/img/posts/azure-pipeline-ec2-build-artifact/0.png)
O processo de build dentro do Azure DevOps fica localizado na área de ```Projeto > Pipelines > Pipelines``` e para criar um Build basta clicar no link "Create pipeline".

![Azure Pipeline](/assets/img/posts/azure-pipeline-ec2-build-artifact/1.png)

## Etapa 1: Azure Pipelines - Conexão
A primeira etapa da criação do pipeline é a definição de "Onde está seu código?" e ela serve para você conectar o seu pipeline com a origem. Para realizar uma configuração mais fácil, iremos utilizar o "Editor Clássico" do Azure devops, para selecionar ele basta clicar em "Use the classic editor".

![Azure Pipeline](/assets/img/posts/azure-pipeline-ec2-build-artifact/2.png)


## Etapa 2: Azure Pipelines - Editor Clássico
Após selecionar o editor clássico do devops, iremos agora selecionar o nosso repositório e a branch que será utilizada para o processo da geração do Build.

![Azure Pipeline](/assets/img/posts/azure-pipeline-ec2-build-artifact/3.png)

## Etapa 3: Azure Pipelines - Escolha de Template
O Azure Pipelines possui vários modelos de pipelines prontos para que o usuário tenha menos trabalho possível ao realizar a configuração do Build. Nós iremos escolhar o "Empty Job" já que iremos criar o nosso próprio Template.

![Azure Pipeline](/assets/img/posts/azure-pipeline-ec2-build-artifact/4.png)

## Etapa 4: Azure Pipelines - Escolha do agente
Agora que já temos as configurações iniciais do pipeline realizadas, iremos selecionar qual o tipo de Agente que será utilizado. Eu irei selecionar o agente ```ubuntu-20.04```, por ter uma familiaridade maior com Linux para resoluções de problemas mas fiquem livres para selecionar qualquer agente que vocês quiserem.

![Azure Pipeline](/assets/img/posts/azure-pipeline-ec2-build-artifact/5.png)

## Etapa 5: Azure Pipelines - Tarefa de Publicar Artefato
A próxima etapa que precisaremos realizar para criar o nosso pipeline é adicionar uma tarefa no nosso agente já existente. A tarefa que utilizaremos é o Publish build artifact.

![Azure Pipeline](/assets/img/posts/azure-pipeline-ec2-build-artifact/6.png)

Não será preciso realizar nenhuma configuração na tarefa de Publish Artifact,podemos deixar com as informações padrões. Caso vocês troquem o Artifact Name, se atentem pq esse valor será usado na criação da release e vocês terão que realizar modificações para que funcione corretamente.

## Etapa 6: Azure Pipelines - Rodando e visualizando o Artefato
Após as configuração acima, está na hora de salvar e rodar o nosso pipeline para testar seu funcionamento. Basta clicar em Save & Queue.

![Azure Pipeline](/assets/img/posts/azure-pipeline-ec2-build-artifact/9.png)

Após salvar, será aberto a janela do Run Pipeline, basta deixar com as configurações padrões e rodar.


![Azure Pipeline](/assets/img/posts/azure-pipeline-ec2-build-artifact/8.png)

Uma nova página será carregada para mostrar as informações do pipeline. Para acompanhar o Jog, clique em cima do "Agent job".


![Azure Pipeline](/assets/img/posts/azure-pipeline-ec2-build-artifact/10.png)

Dentro do Agent Job nós conseguimos ver todas as etapas que o pipeline percorrerá até a criação do Artefato.

![Azure Pipeline - Agent Job](/assets/img/posts/azure-pipeline-ec2-build-artifact/11.png)

Agora, se retornar-mos na etapa anterior, iremos ver que o pipeline está com status de concluído.

![Azure Pipeline - Agent Job](/assets/img/posts/azure-pipeline-ec2-build-artifact/12.png)

## Conclusão
Nesta etapa fizemos a configuração do Pipeline e geramos o nosso artefato e agora estamos preparados para entregar no servidor os nossos arquivos.

Nas próximas etapas iremos configurar nosso Deployment Groups dentro da máquina EC2 e em seguida iremos finalizar a nossa esteira de entrega configurando o envio do nosso artefato até o servidor.