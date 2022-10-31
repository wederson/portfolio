---
layout: post
title: "Responsabilidades de um Desenvolvedor"
date: 2022-10-30 13:07:00
tags:
  - treinamento
author: Wederson S. Machado
avatar: ../assets/profile.png
category:
  - Dicas
---

# Introdução
Vocês já pararam para pensar qual a responsabilidade de um desenvolvedor no dia a dia?

Nos últimos meses eu tenho feito parte de uma equipe responsável por desenvolver um novo produto que unificará várias plataformas. Após o desenvolvimento do *core*, estamos iniciando a passagem para os times de Ongoing que farão a sustentação.

Antes de receber o convite para fazer parte da equipe de sustentação eu fiz parte das equipes de ongoing durante 1 ano. Digo isso para evidenciar que eu participei dos dois mundos e minha opinião aqui não é limitada a minha visão de apenas um único lado.

Quando iniciamos a passagem para os times de sustentação, notei que a diferença entre a maturidade e a visão de responsabilidade do desenvolvedor eram gritantes se comparar a equipe de Projetos com a equipe de Ongoing.

# Comunicação
Essa é a parte mais difícil e que trás maiores resultados. Ter uma boa comunicação (escrita e falada) irá ajudar no dia a dia ao realizar as tarefas e os alinhamentos.

Além disso, os desenvolvedores devem também saber quando pedir ajuda ou continuar quebrando a cabeça em um problema. A adoção do home office dificultou esses pedidos de ajudas, já peguei alguns desenvolvedores quebrando cabeça por 1 dia em um problema que poderia ter sido resolvido em 30 min de conversa com algum outro dev.

Comuniquem-se, leiam, falem nas dailys e nos canais oficiais, peçam ajuda quando precisarem...

# Refinamento Funcional
O desenvolvedor deverá dá uma atenção para o refinamento funcional. É aqui que ele irá entender juntos as áreas (Negócio, UX, Dados...) tudo o que deverá ser feito durante o desenvolvimento da História.

É nessa etapa que os desenvolvedores deverão se atentar as Dependências. O refinamento funcional não deveriam ser considerados "finalizados" se ainda existem dependências a serem resolvidas.

Negligenciar essa etapa irá gerar dúvidas e, consequentemente, retrabado durante o desenvolvimento.

# Refinamento Não Funcional
É total responsabilidade dos desenvolvedores se atentarem a problemas não funcionais para que se tenha uma maior qualidade na entrega.

Arquitetura, tempo de carregamento, portabilidade, jurídico (ética/legais), custos... Faz partes das preocupações que os desenvolvedores devem ter para construir uma aplicação.

# Refinamento Ténico
Após conhecer a solução através do refinamento funcional e não funcional, chegou a hora de refinar tecnicamente como será construída a solução.

Nessa etapa o desenvolvedor irá se dedicar a entender todos os sistemas impactos, todos os serviços que deverão ser modificados ou criados para que a solução seja implementada. No final do refinamento técnico é recomendado que seja gerado um documento de implantação para que o time possa consultar durante toda a etapa de desenvolvimento.

É no refinamento técnico que será levantado todos os testes que deverão ser feitos para que a entrega tenha uma boa qualidade. Em qualquer etapa os desenvolvedores podem consultar os seus pares ou a área de negócio, UX, QA e TL.

# Código
> se um membro acerta, todos acertam. Se um membro erra, todos erram.

O desenvolvedor é responsável pela qualidade do código que ele entrega. Como o desenvolvedor normalmente não trabalha sozinho, ele também é responsável pela qualidade do código de seus pares!

Existe um ponto muito importante no parágrafo acima: se o desenvolvedor faz parte de um time, ele é diretamente responsável pelo que é entregue sem qualidade.


Ele deverá respeitar os padrões já adotados pelo time e também deverá propor novos padrões caso ele identifique alguma coisa que possa melhorar.

# Código Limpo
> Incentive na Squad a "Postura do Escoteiro": deixe sempre o local melhor do que você o encontrou.

É total responsabilidade do desenvolvedor escrever um código limpo, testável, seguindo os padrões do projeto e que possa ser reaproveitável. 

Negligenciar essa etapa por falta de conhecimento do código ou por que "essa entrega é pra ontem" não deveria ser aceito pelo desenvolvedor. Um sistema bem feito não é representado apenas por botões na tela, mas também por um código/arquitetura que seja intendível por qualquer desenvolvedor que voltar naquela etapa.


Isso significa que caso encontre algum código que possa ser melhorado você tem a responsabilidade de corrigir no momento que encontrou.

# Codereview
Codereview é uma etapa de processo de desenvolvimento muito útil para compartilhar conhecimento e garantir que o código está funcionando/seguindo as melhores práticas definidas.

O desenvolvedor tem que garantir que o processo de codereview está sendo realizado corretamente e também é reponsável por propor melhorias para que a cada dia o codereview rode com mais naturalidade.

O processo de codereview nunca deve ser tratado como uma etapa que irá extender o tempo de entrega, muito pelo contrário. O codereview garante que mais de um desenvolvedor tenha o conhecimento do que foi feito além de achar bugs antes do desenvolvimento ser finalizado, garantindo uma maior qualidade para o produto.

# Registro de Débitos Técnicos
Registrar débitos técnicos corretamente é primordial para um maior controle do que estamos deixando para trás. Além de realizar os registro de débitos técnicos, o desenvolver, alinhado com o Tech lead, tem que garantir que parte do seu tempo do dia/semana seja reservado para a solução desses débitos.

Se estamos criando mais débitos técnicos do que resolvendo, isso certamente pode indicar que o time não está enganjado com a qualidade da entrega.

# Bugfix
Faz parte das responsabilidades do desenvolvedor registrar corretamente e corrigir Bugs em produção. Isso significa que ele deverá não só implementar as correções como também entender o por quê os bugs aconteceram, e um bom registro dos problemas irão fornecer insumos para que sejam criados planos de ações para que eles não voltem.

Até mesmo os bugs que são considerados rápidos de serem solucionados devem ter total atenção do desenvolver. Se um bug pode ser corrigido em questões de minutos, isso pode significar que alguma coisa não foi mapeada durante as etapas de refinamento/desenvolvimento.

### Fontes
1. <a href="https://www.amazon.com.br/C%C3%B3digo-limpo-Robert-C-Martin/dp/8576082675" target="_blank">Livro: Código Limpo</a>
2. <a href="https://www.amazon.com.br/Arquitetura-Limpa-Artes%C3%A3o-Estrutura-Software/dp/8550804606" target="_blank">Livro: Arquitetura Limpa</a>
3. <a href="https://brainhub.eu/library/how-to-deal-with-technical-debt" target="_blank">Artigo: How to Reduce Technical Debt and Secure Your Code for the Future</a>
4. <a href="https://open.spotify.com/episode/2EwQI1YpxyJSXAkzgFELTp" target="_blank">Spotify: Devs e a Cultura de Qualidade</a>