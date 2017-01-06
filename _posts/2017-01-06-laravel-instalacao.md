---
layout: post
title: Laravel - Instalação no Ubuntu 16.04
---

Neste post mostrarei como instalar o framework Laravel e a configuração inicial de um projeto. Originalmente desenvolvido por Taylor Otwell, o Laravel tem atraído cada vez mais desenvolvedores. O framework foi criado utilizando as últimas funcionalidades do PHP. Imagino que para os iniciantes é uma boa forma de entrar no mundo PHP escrevendo código de qualidade e limpo.

Falando um pouco sobre a adoção do Laravel, aqui está uma pesquisa no Google Trends como base de comparação entre alguns frameworks:

<script type="text/javascript" src="https://ssl.gstatic.com/trends_nrtr/863_RC25/embed_loader.js"></script> <script type="text/javascript"> trends.embed.renderExploreWidget("TIMESERIES", {"comparisonItem":[{"keyword":"laravel","geo":"","time":"2015-01-01 2016-12-11"},{"keyword":"cakephp","geo":"","time":"2015-01-01 2016-12-11"},{"keyword":"phalcon","geo":"","time":"2015-01-01 2016-12-11"},{"keyword":"slim php","geo":"","time":"2015-01-01 2016-12-11"},{"keyword":"codeigniter","geo":"","time":"2015-01-01 2016-12-11"}],"category":5,"property":""}, {"exploreQuery":"cat=5&date=2015-01-01%202016-12-11&q=laravel,cakephp,phalcon,slim%20php,codeigniter","guestPath":"https://www.google.com.br:443/trends/embed/"}); </script> 

## 1. Mas primeiro, instalando cURL e Composer ##

O ***curl*** é uma ferramenta linha de comando que permite manipular dados, baixar arquivos, entre outras usando uma URL.

{% highlight sh %}
$ sudo apt-get update
$ sudo apt-get install curl
{% endhighlight %}

O ***Composer*** é um gerenciador de dependências que vem sendo muito utilizado nos projetos e frameworks atuais, e o Laravel não está de fora. Então, usando o comando curl vamos baixá-lo.

{% highlight sh %}
$ curl -sS https://getcomposer.org/installer | php
{% endhighlight %}

O arquivo ***composer.phar*** é baixado na pasta onde o comando foi executado. Vamos movê-lo para um diretório global e renomeá-lo para que seja possível executá-lo apenas com o nome ***composer***.

{% highlight sh %}
$ sudo mv composer.phar /usr/local/bin/composer
{% endhighlight %}

Agora para executá-lo basta digitar `composer` de qualquer lugar em seu terminal e as opções do comando serão exibidas.

## 2. Agora sim, instalando o Laravel ##

O Laravel pede alguns requerimentos no sistema:

- PHP >= 5.5.9
- Extensão PHP OpenSSL
- Extensão PHP PDO
- Extensão PHP Mbstring
- Extensão PHP Tokenizer

Primeiro baixe o instalador utilizando o composer

{% highlight sh %}
$ composer global require "laravel/installer"
{% endhighlight %}

Adicione o diretório `~/.composer/vendor/bin` na variável `$PATH` acessando o arquivo `bashrc` e alterando-o:

{% highlight sh %}
$ sudo mcedit ~/.bashrc
{% endhighlight %}

Insira as linhas abaixo no final do arquivo e salve:

{% highlight sh %}
#laravel
alias laravel='~/.composer/vendor/bin/laravel'
{% endhighlight %}

## 3. Criando um projeto Laravel ##

Uma vez instalado, um simples comando `laravel new` criará uma nova instalação do Laravel no diretório que você especificou. Por exemplo, `laravel new blog` criará um diretório chamado blog contendo os arquivos da instalação inicial do Laravel com todas as suas dependências instaladas. Esse método de instalação é muito mais rápido do que a instalação via Composer:

{% highlight sh %}
$ composer create-project laravel/laravel --prefer-dist
{% endhighlight %}

O servidor web usado nesse tutorial, no caso, foi o Apache. Assim, pelo terminal, vá na pasta de publicação do servidor, por padrão `var/www/html` e execute o comando `laravel new nome_do_projeto` para criar um novo projeto pronto para trabalhar.

Acesse o arquivo de configurações do Apache:

{% highlight sh %}
$ mcedit /etc/apache2/apache2.conf
{% endhighlight %}

Adicione as linhas abaixo para evitar erros de leitura e escrita no diretório do projeto:

{% highlight sh %}
<Directory /var/www/html/nome_do_projeto/public>
    AllowOverride All
</Directory>
{% endhighlight %}

Salve e feche o arquivo.

## 4. Testando ##

Enfim para testar sua instalação digite em seu navegador: 

`http://localhost/nome_projeto/public/`

Se tudo ocorreu bem, você está vendo a seguinte imagem:

![home laravel](/images/posts/laravel-home.jpg)
 
Qualquer dúvida mande uma mensagem! Até breve ;)