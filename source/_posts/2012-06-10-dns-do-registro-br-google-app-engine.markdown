---
comments: true
date: 2012-06-10 21:34:40
layout: post
slug: dns-do-registro-br-google-app-engine
title: DNS do Registro.br + Google App Engine
wordpress_id: 294
author:
- bsouza
- guilherme
categories:
- Dicas web
- Tutoriais
tags:
- aplicativo web
- DNS
- Google App Engine
- Google Apps
- Registro.br
- saas
- site
- Tutorial
---

Primeiramente quero deixar claro que esse post não vai ensinar a criar um sistema web, apenas será mostrado que é possivel publicar aquela sua ideia pagando apenas o registro de seu domínio. Então, se você tem uma ideia revolucionaria para um sistema web, nada melhor do que desenvolver um protótipo publicando ele na web para provar o seu conceito. Ressalto que nem mesmo um dominio é necessário se você quiser apenas provar sua ideia, mas é um passo importante depois que ela amadurece.




No meu caso eu fiz isso para o [Tweet Vagas](http://www.tweetvagas.com.br) com o Google App Engine, colocando o meu site no ar com dominio e email próprio, pagando apenas pelo domínio. Para isso precisa registrar o domínio no [Registro.br](http://registro.br/) (onde você pode registrar por R$30,00/ano), ter seu applicativo web no [Google App Engine](https://developers.google.com/appengine/?hl=pt-BR) e criar uma conta no [Google Apps](http://www.google.com/apps/intl/pt-BR/business/) para o seu dominio.




O processo é meio tortuoso se você não sabe por onde começar, por isso resolvi fazer esse post. Você tem que ir até o painel de administração do Google App Engine, no menu Application Setting e Clicar no botão Add Domain em Domain Setup. Digitar o seu dominio e seguir para a página do Google Apps, onde fará o cadastro se ainda não tiver conta para esse dominio. Ao fim você deve chegar na página do seu aplicativo e adicionar a url correspondente (Veja algumas imagens abaixo)




[caption id="" align="aligncenter" width="614" caption="Encontra-se no menu Administration Settings do seu aplicativo no Google App Engine"]![](https://lh6.googleusercontent.com/GUZ9mQFRcyufitezcinlUYH3uGM1_LpluFS0h0zCWPDY8rEiHYuvJk997cKJPxXbfjJt_3Ud9kKTXqEQA8WX7e82Xm_HL1jLeSZpnP3UodwAR9OlcaQ)[/caption]

[caption id="" align="aligncenter" width="622" caption="Após clicar em Add Domain, deve preencher seu dominio e será encaminhado para o Google Apps."]![](https://lh6.googleusercontent.com/XAAqmu4uL7UeaoYgRTkFJMaTxuRL0TUHM_oxHfXlcenFIPsKeGPHlbEoyYl3YRC5gSNhVBDHkCJxNP6FNFpaPMoTzz9g8gBtlN_805TD_v7q5vHUNFA)[/caption]

[caption id="" align="aligncenter" width="394" caption="Página do seu aplicativo (no meu caso tweetvagas) onde você deve adicionar a url do seu dominio."]![](https://lh6.googleusercontent.com/5s53_VmweH1GVXpdvJNikUMggE8emaMYtTlQvQqYjc5kpNHkApMSds2UFqxzJh1U7uJAJjNR2PTLXUA3DrGQbTghtNFrBHRgUUugaCmOJpZhbxVsOQo)[/caption]


Depois de se cadastrar e adicionar a url do seu dominio para a aplicação, você terá que criar um CNAME no servidor DNS (provavelmente será necessário marcar uma opção para validar seu dominio em outro momento no Google Apps). Então vá para Registro.br na página de administração do seu domínio, marque a opção “Utilizar os servidores DNS do Registro.br”, clique em Salvar & Editar, selecione o Modo Avançado. Agora você deve configurar CNAME do seu dominio para ghs.google.com.




[caption id="" align="aligncenter" width="385" caption="Na página de administração do seu domínio."]![](https://lh6.googleusercontent.com/SCejf5vYJgdfk5GfRx7Z6cb2yfgw_xoLE5sOicdTNvuU9O6xsaOufdwK0aMZrpNRAZMYfBx52XempYuSIfUCoYaX-WAVOFJxe1qOeozKFvTgBymdayw)[/caption]

[caption id="" align="aligncenter" width="684" caption="Modo Avançado."]**![](https://lh5.googleusercontent.com/fnzxfDS4uOdMC_mtphfqxQBVWfWyWJrHoro7ZusJHh3Dz_6pk0cy4DM40aHj5Ak6lOdoIvnrs81evVPn3FHQlS8nr1MnR7JxgYGCZzOth7ipLPRHibI)**[/caption]



ATENÇÃO: Os servidores DNS demoram cerca de 30 min para refletirem a configuração.




Agora o seu dominio deve estar funcionando, mas ele só é acessível através do www. Para você validar o seu dominio no Google Apps pelo método padrão, ainda é preciso fazer uma configuração para que seu site seja acessivel sem o www. Vá para o menu Domain Setting do Google Apps, em Domain Names, clique no link “Change de A record”, onde você encontra os endereços IPs que você deve adicionar lá no Registro.br conforme imagens.




[caption id="" align="aligncenter" width="647" caption="Clique no Link “change the A record"]![](https://lh4.googleusercontent.com/t452VMAVkKBE1jB9U6E8FTFhNUK6JB1UCO2Bb-qtsU1Mu7jUg-tUWBJZGqOmzlRmdpRZ-wY4kjMIYaEIST1LeLbJgzGrmY_niMFQACoBvo4Us-JDUn0)[/caption]

[caption id="" align="alignnone" width="648" caption="Adicione A record no DNS do Registro.br"]![](https://lh3.googleusercontent.com/Xz70cn1vI4pPVK44DNNvC-CdhmdwZv77JqQkfA4XRWiicpe1ycMiRSQ5gXrSUS2QIb_VymIp-xrBPQ6HNFHAvahI55dIlogqyKqw3pw7C9AQJ2BPGME)[/caption]


Depois disso você terá configurado tudo, seu site estará acessível pelo dominio e ainda terá todos os recursos fornecidos pelo Google, sem nenhum custo além do registro de domínio.
