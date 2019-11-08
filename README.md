---
description: >-
  Este documento mostra de forma simples como instalar esta ferramenta que
  auxilia na utilização da guarda de dados locais.
---

# Postgresql no Ubuntu 18.04

## Pre-requisitos

Antes de começarmos, sera necessario que voce esteja logado em uma conta com acesso de super usuario, de maneira geral, sera necessario a utilização de alguns comandos para efetuar a instalação do banco.

## Preparando o sistema

Eremos utilizar comandos do terminal linux para instalar nosso banco, para isso abra o terminal.

Voçe pode abrir em modo grafico, clicando em:

```text
Mostrar arquivo > Terminal
```

ou voce pode utilizar a tecla de apoio do seu teclado, tambem conhecida como **winkey**:

```
<winkey> > na barra de pesquisa digite <Terminal>
```

Uma outra forma de acessar o terminal é atravez da tecla de atalho:

```text
Ctrl + Alt + t
```

Essas são algumas das formas de se acessar a tela do terminal em sua conta atual.

Agora é recomendado que os pacotes do seu sistema estejam atualizados para que a instalaçao dessa instancia do servidor seja instalada, vamos fazer isso seguindo os comandos abaixo.

```text
sudo apt update && sudo apt -y upgrade
sudo reboot
```

Logo que o sistema estiver rebootado, instale o vim e o wget se eles ja nao tiverem sido instalados no seu sistema.

```text
sudo apt install -y wget vim
```

## Adicione o repositorio postgres

Antes de instalar o conteudo do postgres, precisamos importar as chaves para o repositorio.

```text
wget --quiet -O - https://www.postgresql.org/media/keys/ACCC4CF8.asc | sudo apt-key add -
```

Depois de importar a chave GPG, adicione o conteudo ao seu repositorio.

```text
RELEASE=$(lsb_release -cs)
echo "deb http://apt.postgresql.org/pub/repos/apt/ ${RELEASE}"-pgdg main | sudo tee  /etc/apt/sources.list.d/pgdg.list
```

## Instalando o postgreSQL

Agora o ultimo passo para a instalação do postgres, nesse caso estou instalando a versao 11, porem caso voce queira instalar outra versao, recomendo que entre diretamente no site oficial atraves do link postgreSQL🐘 

Siga os comandos para continuar a instalação pelo terminal:

```text
sudo apt update
sudo apt -y install postgresql-11
```

## Configurando usuario admin

Para configurar as credenciais para admin, voce precisara estar em um perfil root, para prosseguir siga os comandos a seguir:

```text
$ sudo su - postgres
postgres@silvio:~$ psql -c "alter user postgres with password 'senha'"
ALTER ROLE
```

Voce pode adicionar uma base de dados:

```text
createuser dbsilvio1
```

Adicionar banco teste:

```text
postgres@silvio-1:~$ createdb testedb -O dbsilvio1
```

Faça um teste de operação logando como **dbsilvio1** e operando o **testedb:**

```text
~$ psql -l  | grep testdb
 testdb    | dbsilvio1  | LATIN1   | en_US   | en_US |
```

Configure a senha:

```text
$ psql
psql (11.2 (Ubuntu 18.04.pgdg18.04+1))
Type "help" for help.
postgres=# alter user dbsilvio1 with password 'Password';
ALTER ROLE
```

## Conclusão

Apartir desse ponto voce podera utilizar os comandos padroes do **PostgreSQL** para  **CRIAR**, **INSERIR**, **ATUALIZAR** e **DELETAR** os dados no seu banco.

Tambem é possivel instalar o gerenciador web para que voce possar fazer tudo isso atravez da ferramenta grafica, eu particularmente recomendo o **PGAdmin 4**, pois ate o momento é a melhor versao de gerenciamento do postgres.

## Autor <a id="autor"></a>

* ​[Linkedin](https://www.linkedin.com/in/silvio-antonio-de-oliveira-junior-621813142/)​
* ​[Github](https://github.com/silvioantonio)​
* ​[website](http://silvioantonio.ml/)​

> Compartilhar conhecimento é a melhor forma de aprender
>
> -OLIVEIRA, Silvio Antonio Junior.

