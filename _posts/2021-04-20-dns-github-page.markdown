---
layout: post
title: "Configurando DNS no Github Pages!"
date: 2021-04-20
tags:
  - todos
  - github
  - dns
author: Wederson S. Machado
avatar: ../assets/profile.png
category: 
  - Dicas
  - Github
---

Como estudo de hoje iremos abordar a configuração de DNS para o [Github Pages](https://pages.github.com/){:target="_blank"}. O serviço de DNS escolhido será o [registro.br](https://registro.br/){:target="_blank"} mas é facilmente replicável em outros serviços.

Para divulgar a sua página o [Github Pages](https://pages.github.com/){:target="_blank"} fornece uma URL que poderá ser utilizada. Essa URL segue um padrão de nomenclatura:
```
<nome_do_usuario>.github.io
```

É justamente essa URL que queremos mudar.

| Como é?        | Como queremos que fique?  |
| :--------------: | :-------------------------:|
| wederson.github.io      | wedersonm.com.br |

Nessa publicação iremos abordar apenas a configuração do DNS e esperamos que vocês já tenham uma conta no github, um repositório configurado para ser um github pages e um domínio.

---

## Pré-requisito

1. Ter uma conta no Github;
2. Ter um repositório configurado para ser sua página no [github page](https://pages.github.com/){:target="_blank"};
3. Ter um domínio e acesso para as configurações de Zonas de DNS;

---

## O que é Github?

[Github](https://github.com/){:target="_blank"} é uma ferramente utilizada para versionamento de projetos que todo desenvolvedor deve ter uma conta nele pois ele também servirá como um portfólio dos códigos já trabalhados pelo desenvolvedor.

Além de facilitar o versionamento de projetos, o github também facilita a colaboração entre vários desenvolvedores em [projetos open sources](https://pt.wikipedia.org/wiki/Software_de_c%C3%B3digo_aberto){:target="_blank"} ou em projetos fechados. Hoje é inviável ter um projeto sem versionamento.

---

## O que é Github Pages?

O Github Pages é uma ferramenta do próprio Github criada para que os desenvolvedores possam disponibilizar suas páginas estáticas sem precisar contratar um Servidor.

Página estáticas são páginas que são criadas apenas com HTML, CSS e Javascript e não possuem comunicações externas (ajax).

---

## Instruçoes

A configuração é feita em 2 etapas. Na primeira etapa iremos configurar as Zonas de DNS para apontar para os servidores do Github; na segunda etapa iremos configurar o repositório e fazer com que ele utilize o domínio correto.

### Etapa 1 - Apontando o DNS para o Github

Faça login no [registro.br](https://registro.br/){:target="_blank"}, escolha seu Domínio e procure a parte de Editar Zona de DNS.

![Tela de DNS Registro.br](../assets/img/posts/2021-04-20-dns-github-page-1.jpg)

Na tela de Edição de Zona teremos que configurar o Domínio, fazendo com que ele aponte para os servidores do Github. Para isso, iremos adicionar a configuração de DNS do tipo A record.

Além dessa configuração, adicionaremos uma configuração de CNAME, apontam **www.wedersonm.com.br** para **wederson.github.io**

| IPs do Github |
| :-------------: |
| 185.199.108.153 |
| 185.199.109.153 |
| 185.199.110.153 |
| 185.199.111.153 |

a lista de IPs dos servidores podem ser encontradas [AQUI](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site#configuring-an-apex-domain){:target="_blank"}

**A configuração final deverá se parecer com essa.**
![Configuração de DNS no registro.br](../assets/img/posts/2021-04-20-dns-github-page-2.jpg)

---

### Etapa 2 - Configurando o github pages para utilizar o domínio

Para começar as configurações será necessário abrir o repositorio do Github e ir até Settings.
![Settings github](../assets/img/posts/2021-04-20-dns-github-page-3.jpg)

No menu do lado esquerdo, acesse Pages e adicione seu domínio no campo *Custom domain*

![Configuração de DNS no github](../assets/img/posts/2021-04-20-dns-github-page-4.jpg)

Se tudo correr bem até aqui o github irá sinalizar que está gerando um certificado TLS para o seu domínio e em breve você poderá acessar normalmente.

### Observação

Existem 2 erros possíveis que podem acontecer:

#### 1. Erro de Custom Domain
Esse erro acontece quando o github não conseguiu achar as configurações de IP nas Zonas de DNS. Verifique se está tudo correto e, caso esteja correto, apenas click em *Check again*.
![Erro de custom domain](../assets/img/posts/2021-04-20-dns-github-page-5.jpg)


#### 2. DNS_PROBE_FINISHED_NXDOMAIN

Esse erro acontece quando o domínio ainda não foi propagado.
Quando uma nova configuração de DNS é realizada, o servidor de DNS tem que avisar as redes que agora aquele DNS aponta para um IP diferente. Esse processo se chama propagação de DNS.

Ele tem um prazo de até 48 horas para finalizar mas costuma levar menos de 30 minutos.

Tome um café e tente novamente.

## Considerações finais

Colocar uma página online é bem simples para quem já trabalha a bastante tempo com Desenvolvimento mas pode ser um desespero para aqueles que estão começando.

E quando estamos começando queremos logo ver tudo funcionando. Tenham paciência, estudem e sejam resilientes com seus estudos.

---

E aí, o que achou desse post?

Espero que tenha curtido! 💜