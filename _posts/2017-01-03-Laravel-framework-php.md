---
layout: post
title: Laravel - O Framework PHP para Artesãos da Web
---

Laravel é um ***framework PHP*** utilizado para o desenvolvimento web, que utiliza a arquitetura ***MVC*** e tem como principal característica ajudar a desenvolver aplicações seguras e performáticas de forma rápida, com código limpo e simples, já que ele incentiva o uso de boas práticas de programação e utiliza o padrão PSR-2 como guia para a escrita do código.

## 1. Blade ##

Para a criação de interface gráfica, o Laravel utiliza uma Engine de template chamada Blade, que traz uma gama de ferramentas que ajudam a criar interfaces bonitas e funcionais de forma rápida e evitar a duplicação de código. Para quem nunca utilizou um sistema de templates deste tipo, ele basicamente é uma maneira diferente de escrever suas views. Em vez de utilizar tags PHP diretamente no seu HTML, você vai utilizar outra sintaxe com chaves e arrobas.

## 2. Eloquent ORM ##

Para se comunicar com o banco de dados, o Laravel utiliza o Eloquent ORM, uma ferramenta que facilita a manutenção de dados. ***ORM*** é uma técnica de desenvolvimento de software que serve para o uso de tabelas de bancos de dados em formato de objetos relacionais. Usando esta técnica o programador não precisa se preocupar em escrever códigos na linguagem SQL, pois a listagem e persistência é toda feita pela interface do ORM.

## 3. Artisan ##

Artisan é o nome da ***interface para linha de comando*** que faz parte do Laravel. Com ela, podemos gerar a maioria das classes que são as ferramentas disponibilizadas pelo framework, além disso, provê inúmeros comandos úteis que você pode usar enquanto desenvolve sua aplicação. Ele é baseado no poderoso componente ***Symfony Console***. É instalado automaticamente quando se cria um novo projeto.


## 4. RESTful ##

O Laravel já foi feito pensado para facilitar a criação de serviços RESTful, portanto, quando devolvemos alguma variável, objeto, array ou qualquer outro dado em nossos Controllers, eles já são convertidos automaticamente para formato ***JSON***.

## 5. Produtividade ##

Além de todas funcionalidades apresentadas até agora, o Laravel fornece diversas ferramentas para aumentar nossa produtividade e evitar que gastemos tempo com certas tarefas, permitindo assim que o nosso foco seja o desenvolvimento de soluções para nossas aplicações e cuidando da parte “chata” do trabalho para nós. Algumas dessas ferramentas são o Elixir (automatizador de tarefas) e o SwiftMailer (Biblioteca para envio de e-mails).

## 6. Ambiente de desenvolvimento ##

Às vezes pode ser bem chato configurar um ambiente de desenvolvimento e isso pode gastar muito tempo dependendo do tipo, e pensando nisso, foi criado o <a href="https://laravel.com/docs/5.3/homestead">Laravel Homestead</a>, um box oficial para o Vagrant com todo o ambiente necessário para começarmos a desenvolver nossas aplicações. Nele temos o PHP 5.6, banco de dados MySQL, PostgreSQL e Redis, NodeJS, servidor Nginx, HHVM e várias outras ferramentas rodando no Ubuntu 16.04 para auxiliar no desenvolvimento de nossas aplicações. Com isso, podemos começar a desenvolver sem grandes esforços para montar o ambiente de desenvolvimento.

## Conclusão ##

Bem, essa foi uma pequena introdução sobre esse framework que me fez gostar de programar em PHP. Pretendo criar uma série de posts sobre, então até lá.