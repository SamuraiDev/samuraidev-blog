---
comments: true
date: 2012-06-16 19:17:21
layout: post
slug: voce-conhece-memcached
title: Você conhece Memcached?!
wordpress_id: 327
author:
- guilherme
categories:
- Dicas web
- Ferramentas
- Linguagens e frameworks
- Tutoriais
tags:
- App Engine
- Cache
- código aberto
- escalabilidade
- free
- Google App Engine
- livre
- Memcache
- Memchaced
- open-source
- python
- saas
---

[singlepic id=18 w=160 h=120 float=left]




Memcached é um sistema para lidar com memória cache de forma distribuida e com alto desempenho. Dependendo do design de sua aplicação, existem diversos lugares que poderiam ser interessantes a utilização de Memcached para melhorar a performance e a utilização de recursos. Alguns exemplos são:






	
  * a criação de cache para páginas populares, como uma página principal ou em que os dados sejam os mesmos para todos usuários;

	
  * salvar dados transientes e frequentementes atualizados, como um contador em uma página. Isso evita atingir o banco de dados a cada requisição, incrementando o contador no Memcache e atualizando o banco de tempo em tempo*;

	
  * dados frequentemente requisitados, como por exemplo o resultado de uma consulta ao banco.




[singlepic id=19 w=640 h=480 float=right]Com apenas algumas linhas extras no seu código essas utilizações acima podem melhorar a escalabilidade de seu aplicativo. Memcached nada mais é que uma cache RAM distribuida que utiliza um modelo chave, valor. Escritas na memcache nunca atingem o disco e são muito mais rápidas que acessos ao banco de dados (aproximadamente 10x mais rápido que escrever no banco de dados do Google App Engine e 5x para leituras). O tradeoff é que os dados guardados na memcache são transientes e podem ser descartados quando o espaço se aproximar do limite. Alguns exemplos de sistemas que utilizam Memcache são YouTube, Reddit, Zynga, Facebook, Orange e Twitter.




Um uso bem simples que fiz com esse sistema foi criar uma cache para os anuncios de vagas de emprego no [Tweet Vagas](http://www.tweetvagas.com.br). Nele as pessoas podem anunciar vagas de modo muito descomplicado, apenas preenchendo a descrição. Ao clicar em anunciar o Tweet Vagas cria um link permanente para esse descrição e prepara um tweet contendo esse link e um resumo do anuncio para ser tweetado pelo proprio twitter do usuário. Nesse momento a descrição é gravada no banco de dados do Google App Engine e ao mesmo tempo colocada na Memcache. Assim cada anuncio só acessa o banco de dados na sua escrita, e todas as requisições para essa vaga buscam os dados diretamente da Memcache. Como as vagas tem uma relação direta com sua idade, aquelas mais antigas e menos acessadas são as que tendem a serem limpas da cache, enquanto as mais recentes e acessadas tendem a se manter. Essa arquitetura permite fazer uso muito inteligente do banco de dados, o que é muito importante em uma plataforma SaaS, ja que o custo é proporcional a utilização do serviço.




A utilização de Memcache é bastante simples e encorajada pelo Google App Engine, fazendo parte de sua API, alem de possuir uma página exclusiva dentro do Admin Console (Data - Memcache Viewer) onde você pode ver estatisticas (hits/miss, tamanho da cache, número de itens), limpar a cache e buscar valores pela sua chave. Abaixo veja o código utilizado no Tweet Vagas que faz uso da Memcache:




[gist id=2941459]




Esse método é chamado nas requisições da página de descrição da vaga. O que ele faz na primeira linha é buscar se existe essa chave (vaga_id) na memcache. Se não estiver presente ela busca do banco de dados e coloca o par (chave,valor) em cache. Se esta presente retorna diretamente o valor. Simples assim. O parametro booleano serve para quando houver alguma alteração no banco de dados. Chamar o método com update = True fará com que a cache seja atualizada.




Você utiliza Memcache como se lógicamente fosse uma única memória para todo seu sistema. Independente de quantos servidores você possua, Memcache permite que você faça uso da Memória de cada um desses servidores de modo distribuido, sem que haja necessidade de se responsabilizar pelo gerênciamento complicado que existe por traz disso e permitindo adicionar mais servidores sem se preocupar com complicações em reestruturar a cache. E mais, pela sua filosofia todas as operações tem complexidade O(1), ou seja, toda operação tem tempo de execução constante independente de sua entrada.




Alem de tudo Memcached é Livre e de Código Aberto (Free & Open-source). Você pode pegar o código fonte no GitHub do Memcached, e se não souber utilizar o Git pode ver o tutorial sobre ele [aqui no blog](http://samuraidev.com/tutoriais/versionamento-de-codigo-c-git-p1/). Espero que tenha gostado.




_*os dados podem ser limpos da memcache a qualquer momento e sua aplicação deve levar isso em conta para lidar com a situação em que os dados foram limpos da cache._


**Veja mais:**



	
  * [http://memcached.org/](http://memcached.org/)

	
  * [http://code.google.com/p/memcached/](http://code.google.com/p/memcached/)

	
  * [https://github.com/memcached/memcached](https://github.com/memcached/memcached)

	
  * [https://developers.google.com/appengine/articles/scaling/memcache](https://developers.google.com/appengine/articles/scaling/memcache)

	
  * [https://developers.google.com/appengine/docs/python/memcache/usingmemcache?hl=pt-br](https://developers.google.com/appengine/docs/python/memcache/usingmemcache?hl=pt-br)


