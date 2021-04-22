---
layout: post
title: "Javascript Pattern: Performando For Loop!"
date: 2021-04-21
tags:
  - todos
  - javascript
  - pattern
author: Wederson S. Machado
avatar: ../assets/profile.png
category: 
  - Dicas
  - Javascript
---

Loop de repetição é uma das lógicas mais comuns no dia a dia do desenvolvimento web e estamos tão acostumados a fazer um loop que podemos acabar neguigenciando a importantância dele na performance de uma aplicação.

---

## For loop
Para aqueles que não sabem, um Loop de repetição nada mais é do que um bloco de código que será chamado até que uma condição seja alcançada.

### Exemplo 1

``` javascript
  for (var i = 0; i < 4; i++) {
    // código aqui
  }
```

No exemplo acima, definimos um ponto de partida para o nosso loop *(var i = 0)*, uma condição para o loop ser executado *(i < 4)*, e o que acontece a cada final de chamada *(i++)*.

Em um loop de repetição simples onde sabemos exatamente quantas interações irão existir não é preciso pensar em performace. Mas e quando não sabemos o número total de repetições e precisamos automatizar?

### Exemplo 2

``` javascript
  var arr = new Array(10000)

  for (var i = 0; i < arr.length; i++) {
    // código aqui
  }
```

Nesse exemplo, criamos um array com 10.000 itens e salvamos essa lista na variável arr. Em seguinda nós criamos o loop e fizemos com que seja verificado o tamanho do array para saber se i é menor. Nada diferente do padrão, certo?

Errado! O problema nessa abordagem é que TODA VEZ que o loop é executado será verificado o tamanho da lista (arr.length).

---

## Melhorando a performance de um loop

A performance de um loop é verificada através do seu tempo de execução. Nós utilizaremos o console.time do javascript para descobrir quanto tempo demora para que um bloco de código seja executado. Existem outras formas de verificar isso mas o console.time é o jeito mais fácil.

Vamos utilizar o Exemplo 2 para verificar quanto tempo demora a sua execução

``` javascript
  var arr = new Array(10000)

  console.time()
  for (var i = 0; i < arr.length; i++) {
    // código aqui
  }
  console.timeEnd()

  // default: 0.8408203125 ms
```

A média de performance desse loop é por volta de 1.14 millesegundos (para descobrir a média, execute várias vezes o código acima).

Tá, mas como deixar esse bloco de código com um performance melhor?

Para isso podemos seguir um dos padrões de desenvolvimento javascript que diz: sempre que buscarmos o tamanho da lista de forma dinâmica para realizar um loop, devemos salvar esse tamanho em uma variável para que o javascript não precise buscar o tamanho a cada interação (salvo casos em que a lista muda a cada interação).

### Caso 1

``` javascript
  var arr = new Array(10000),
      arrLength = arr.length;

  console.time()
  for (var i = 0; i < arrLength; i++) {
    // código aqui
  }
  console.timeEnd()

  // default: 0.68994140625 ms
```

### Caso 2

Outra forma de fazer um loop de forma mais performática é utilizando o forEach.

``` javascript
  var arr = new Array(10000)

  console.time()
    arr.forEach(item => "")
  console.timeEnd()

  // default: 0.034912109375 ms
```

## Conclusão
Os ganhos de performance são diferente para cada caso e devemos considerar também a legibilidade do código para suportes futuros.

Discutam com sua equipe qual padrão vocês devem adotar!



