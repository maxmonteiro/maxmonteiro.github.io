---
layout: post
title: Como instalar Apache, PostgreSQL, PHP (LAPP) no Ubuntu 16.04
---

LAPP é o acrônimo para: **Linux** (sistema operacional), **Apache** (servidor web), **PostgreSQL** (gerenciador de banco de dados) e **PHP** (linguagem de programação), componentes principais para viabilizar o desenvolvimento de aplicações web, de alta disponibilidade e de alto desempenho.

Apesar de não terem sido desenvolvidos para trabalhar especificamente um com o outro, a filosofia e o conjunto de ferramentas de desenvolvimento são compartilhados e foram desenvolvidos em conjunção próxima. Essa combinação de software tornou-se popular devido serem de código aberto, livres de custo, e assim de fácil adaptação.

## 1. Instalando o Apache ##

O servidor web Apache é um dos servidores mais populares no mundo. Pode ser facilmente instalado no Linux pelo gerenciador de pacotes  `apt` . Um gerenciador de pacotes nos permite instalar a maioria dos softwares, sem sofrimento, de um repositório mantido pelo Ubuntu.

Para instalar execute os comandos:

{% highlight sh %}
$ sudo apt update
$ sudo apt install apache2
{% endhighlight %}

Como estamos utilizando o comando  `sudo` , essas operações serão executadas com privilégios de root. Será solicitada a senha do usuário por segurança.

Após confirmar o usuário, o `apt` irá exibir quais pacotes serão instalados. Pressione **S** para confirmar e **Enter** para continuar.

Teste a instalação acessando no browser a url `http://localhost`. Será exibida a página de boas-vindas do Apache.

## 2. Instalando o PostgreSQL ##

**PostgreSQL** ou **postgres**, é um sistema gerenciador de banco de dados relacional que fornece uma implementação da linguagem de consulta SQL. É bastante popular entre pequenos e grande projetos, e tem muitos recursos avançados como transações confiáveis e simultâneas sem bloqueios de leitura.

Para instalar execute os comandos:

{% highlight sh %}
$ sudo apt update
$ sudo apt install postgresql postgresql-contrib
{% endhighlight %}

Pressione **S** para confirmar e **Enter** para continuar. Verifique o status do serviço executando o comando:

{% highlight sh %}
$ service postgresql status
{% endhighlight %}

Será exibido o status **active**  conforme a imagem.

![postgres status](/images/posts/postgres-status.png)

## 3. Instalando o PHP ##

O **PHP** é o componente da nossa configuração que processará o código para exibir conteúdo dinâmico. Ele pode executar scripts, conectar-se aos nossos bancos de dados para obter informações e entregar o conteúdo processado para o nosso servidor web exibir.

Instalaremos novamente utilizando o  `apt` , incluiremos alguns pacotes que ajudarão a rodar sob o Apache e a se conectar com o PostgreSQL.

Primeiro iremos adicionar o repositório do pacote PHP 5.6:

{% highlight sh %}
$ sudo add-apt-repository ppa:ondrej/php5-5.6
{% endhighlight %}

Se ocorrer algum erro, será necessário instalar `python-software-properties` antes:

{% highlight sh %}
$ sudo apt update
$ sudo apt install python-software-properties
{% endhighlight %}

Execute o comando abaixo para instalar o PHP 5.6:

{% highlight sh %}
$ sudo apt install php5.6 libapache2-mod-php5.6 php5.6-mbstring php5.6-mcrypt php5.6-pgsql
{% endhighlight %}

Antes de testar, vamos configurar algumas coisas.

No momento, se um usuário  envia uma solicitação, o Apache procura primeiro pelo arquivo  `index.html` . Temos que dizer ao servidor para dar preferência ao arquivo  `index.php` . Para isso execute o comando abaixo para editar o arquivo  `dir.conf`.

{% highlight sh %}
$ sudo mcedit /etc/apache2/mods-enabled/dir.conf 
{% endhighlight %}

[ Caso não tenha o `mcedit` instale com o comando `$sudo apt mcedit install` ]

Aparecerá isso:
{% highlight sh %}
<IfModule mod_dir.c>
    DirectoryIndex index.html index.cgi index.pl index.php index.xhtml index.htm
</IfModule>
{% endhighlight %}
Moveremos o arquivo  `index.php`  para a primeira posição após  `DirectoryIndex` . Quando finalizar, feche o mcedit **(F10)** confirmando a alteração teclando **S**.

Depois temos que reiniciar o Apache para a alteração fazer efeito.

{% highlight sh %}
$ sudo systemctl restart apache2
{% endhighlight %}


## 4. Instalando módulos do PHP ##

Para aprimorar as funcionalidades do PHP, podemos opcionalmente instalar alguns módulos adicionais. Para ver uma lista de todos os módulos e bibliotecas disponíveis, execute o comando:

{% highlight sh %}
$ apt-cache search php- | less
{% endhighlight %}

Use as setas para cima e para baixo para percorrer a lista e **q** para sair.

Para ver os detalhes de algum módulo ou biblioteca, execute o comando:

{% highlight sh %}
$ apt-cache show nome_modulo
{% endhighlight %}

Para instalar um módulo, por exemplo o  `php5.6-cli` , execute o comando:

{% highlight sh %}
$ sudo apt install php5.6-cli
{% endhighlight %}

Para instalar mais de um módulo, apenas inclua-os no mesmo comando, separando-os com um espaço.

## 5. Testando o PHP ##

Para testar se nosso sistema está configurado com PHP, basta criarmos um script básico PHP. Podemos chamá-lo de `info.php`.

Para que o arquivo seja visto pelo Apache, devemos colocá-lo em uma pasta muito específica chamada **web root**.

No Ubuntu 16.04, essa pasta está em  `/var/www/html` . Execute o comando para criar o arquivo:

{% highlight sh %}
$ sudo mcedit var/www/html/info.php
{% endhighlight %}

Abrirá um arquivo em branco. Precisamos adicionar o seguinte script dentro do arquivo:

{% highlight sh %}
<?php
phpinfo();
{% endhighlight %}

Salve e feche confirmando a alteração.

Para testar, entre com a url `http://localhost/info.php` 

Será exibida uma página como na imagem abaixo. Caso ocorra, o PHP está funcionando corretamente.

![php status](/images/posts/php.jpg)

O arquivo `info.php` deve ser apagado pois pode ser acessado por usuário não autorizados. Esse arquivo pode ser criado novamente para visualizar essas informações futuramente.

## Conclusão ##

Você instalou uma plataforma bastante popular que permitirá instalar uma infinidade de websites e sistemas web no seu servidor.

