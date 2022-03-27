---
layout: post
title: "Parte 1: Azure DevOps + EC2 - Introdução"
date: 2022-03-15 12:00:00
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

Nesse artigo vamos detalhar os passos necessários para criar uma entrega contínua com o Azure DevOps e servidores EC2 da AWS.

Iremos dividir este guia em 4 etapas:
1. [Parte 1: Azure DevOps + EC2 - Introdução](/azure-pipeline-ec2-introducao)
2. [Parte 2: Azure DevOps - Definição de Build e Artefato](azure-pipeline-ec2-build-artifact)
3. Parte 3: Azure DevOps - Deployment Group
4. Parte 4: Azure DevOps - Criando Release

## Pré-requisitos:
- Máquina EC2 previamente configurada / rodando;
- Acesso a máquina EC2 por linha de comando;
- Código versionado (utilizaremos o Azure Repos)
- Acesso Administrativo no Azure Project;
- Conhecimento básico de comandos Bash;
- Conhecimento básico de CI/CD;

---

# Introdução
O processo de integração contínua do azure devops não é um processo complicado, embora seja necessário algumas configurações manuais prévias para que ele funcione da forma correta, e este processo é dividido em 3 etapas:
1. Configuração do Build e criação do Artefato (Pipeline)
2. Configuração do Deployment Group - cria uma conexão do azure devops com a máquina ec2. Essa conexão será utilizada na entrega do Artefato;
3. Criação da Release - aqui iremos configurar a entrega do artefato na máquina;


## Pré-requisitos 1: Máquina EC2 - acesso e configuração
![EC2](../assets/img/posts/2022-03-15-ec2.jpg)
Nesse guia não temos como objeitov detalhar o processo de criação de uma instâncie EC2 e nem o processo de configuração da máquina. Partiremos da premissa que a sua máquina já está configurada. Essa etapa é necessária pois iremos instalar um Deployment Group dentro da máquina.

**Configuração base do EC2 que utilizaremos**: Servidor Ubuntu com Apache (httpd);

## Pré-requisitos 2: Azure Devops - Conta, acesso Administrativo, Azure Project

![Azure Devops](../assets/img/posts/2022-03-15-azure-devops.webp)

Essa etapa é um pré-requisito pois será necessário acesso administrativo no Azure DevOps para criar o Deployment Group. Partiremos da premissa que o usuário já possui uma conta no Azure DevOps e que o usuário dele é um usuário administrador. Também iremos considerar que o usuário já possui um projeto criado no Azure DevOps.

Caso tenha qualquer dúvida sobre esta etapa vocês podem consultar a <a href="https://docs.microsoft.com/pt-br/azure/devops/organizations/projects/create-project?view=azure-devops&tabs=preview-page" target="_blank">Documentação Oficial</a>..

## Pré-requisito 3: Conhecimentos básicos - CI/CD e comandos Bash
![CICD](../assets/img/posts/2022-03-15-cicd.png)
E para finalizar, é necessário que o usuário tenha um conhecimento básico de comandos bash, fluxo de Integração Contínua e Entrega Contínua.

Nós iremos comentar o que cada comando bash significa no processo mas caso tenha que ser realizado qualquer adaptação para o projeto EC2 testado, vocês terão dificuldade nesse processo.



