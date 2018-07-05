---
description: Sistema de disseminação dos produtos de satélites gerados.
---

# Distribuição de produtos

O MS3 é capaz de controlar o fluxo de produção de imagens de satélite a partir dos dados brutos até a entrega do produto ao usuário final, suportando as operações de navegação e pesquisa por meio de um sistema de catálogo baseado na web.

Este controle é feito por três sub-sistemas:

* Catálogo de imagens, composto por MSTIC \(MS3 Image Catalog\);
* Gestão de produção, composto por MSTERPIECE \(MS3 Resource Production & Control Environment\);
* Relatório executivo, composto pelo MSTERY \(MS3 Executive Report Yielder\).

### MSTIC

O MSTIC \(MS3 Image Catalog\) é um sistema web construído na API do Google Maps para pesquisa, seleção e entrega dos produtos gerados pelo MS3. O catálogo possui uma interface amigável que permite a sua utilização por qualquer usuário. Facilita a navegação e a localização de imagens em diferentes locais do globo. Entrega dados de nível 1, nível 2, nível 2A, nível 2B, nível 3, nível 4, ajuste, refletância, máscara de nuvem, máscara de sombra e produtos de mosaicos multitemporais \([instalação do MSTIC](http://enms3wiki.dpi.inpe.br/wiki/Mstic)\).

.[![](http://enms3wiki.dpi.inpe.br/en.w/images/thumb/f/f1/Catalog2.jpg/600px-Catalog2.jpg)](http://enms3wiki.dpi.inpe.br/wiki/File:Catalog2.jpg)[![](http://enms3wiki.dpi.inpe.br/en.w/skins/common/images/magnify-clip.png)](http://enms3wiki.dpi.inpe.br/wiki/File:Catalog2.jpg)MS3 Image Catalog.[![](http://enms3wiki.dpi.inpe.br/en.w/images/thumb/0/04/Catalog1.jpg/600px-Catalog1.jpg)](http://enms3wiki.dpi.inpe.br/wiki/File:Catalog1.jpg)[![](http://enms3wiki.dpi.inpe.br/en.w/skins/common/images/magnify-clip.png)](http://enms3wiki.dpi.inpe.br/wiki/File:Catalog1.jpg)MS3 Image Catalog.[![](http://enms3wiki.dpi.inpe.br/en.w/images/thumb/8/8d/Catalog3.jpg/600px-Catalog3.jpg)](http://enms3wiki.dpi.inpe.br/wiki/File:Catalog3.jpg)[![](http://enms3wiki.dpi.inpe.br/en.w/skins/common/images/magnify-clip.png)](http://enms3wiki.dpi.inpe.br/wiki/File:Catalog3.jpg)MS3 Image Catalog.[![](http://enms3wiki.dpi.inpe.br/en.w/images/thumb/e/e6/Catalog5.jpg/600px-Catalog5.jpg)](http://enms3wiki.dpi.inpe.br/wiki/File:Catalog5.jpg)[![](http://enms3wiki.dpi.inpe.br/en.w/skins/common/images/magnify-clip.png)](http://enms3wiki.dpi.inpe.br/wiki/File:Catalog5.jpg)MS3 Image Catalog.[![](http://enms3wiki.dpi.inpe.br/en.w/images/thumb/0/0a/Catalog6.jpg/600px-Catalog6.jpg)](http://enms3wiki.dpi.inpe.br/wiki/File:Catalog6.jpg)[![](http://enms3wiki.dpi.inpe.br/en.w/skins/common/images/magnify-clip.png)](http://enms3wiki.dpi.inpe.br/wiki/File:Catalog6.jpg)MS3 Image Catalog.

### MSTERPIECE

O MSTERPIECE \(MS3 Resource Production & Control Environment\) é um sistema web responsável por gerenciar a gerar os produtos MS3 para atender a demanda de usuários de imagem. A geração de produtos, desde os dados brutos até os ortorretificados e especiais, pode ser manual ou totalmente automático. O sistema processa imediatamente os pedidos dos usuários do MSTIC. Além disso, o sistema permite que cada operador do sistema rastreie o processamento e interfira, se necessário.

A produção é maximizada usando o Sun Grid Engine \(SGE\). O SGE é responsável por gerenciar e distribuir a execução do processamento em diferentes máquinas.Os produtos gerados passam por um controle de qualidade para atender aos requisitos especificados. \([manual do usuário MSTERPIECE](http://enms3wiki.dpi.inpe.br/wiki/Msterpiece_User_Manual) e [instalação do MSTERPIECE](http://enms3wiki.dpi.inpe.br/wiki/Msterpiece)\).

[![](http://enms3wiki.dpi.inpe.br/en.w/images/thumb/4/47/Msterpiece2.jpg/700px-Msterpiece2.jpg)](http://enms3wiki.dpi.inpe.br/wiki/File:Msterpiece2.jpg)[![](http://enms3wiki.dpi.inpe.br/en.w/skins/common/images/magnify-clip.png)](http://enms3wiki.dpi.inpe.br/wiki/File:Msterpiece2.jpg)MS3 Resource Production & Control Environment.[![](http://enms3wiki.dpi.inpe.br/en.w/images/thumb/2/2c/Msterpiece1.jpg/700px-Msterpiece1.jpg)](http://enms3wiki.dpi.inpe.br/wiki/File:Msterpiece1.jpg)[![](http://enms3wiki.dpi.inpe.br/en.w/skins/common/images/magnify-clip.png)](http://enms3wiki.dpi.inpe.br/wiki/File:Msterpiece1.jpg)MS3 Resource Production & Control Environment.[![](http://enms3wiki.dpi.inpe.br/en.w/images/thumb/0/01/Msterpiece3.jpg/700px-Msterpiece3.jpg)](http://enms3wiki.dpi.inpe.br/wiki/File:Msterpiece3.jpg)[![](http://enms3wiki.dpi.inpe.br/en.w/skins/common/images/magnify-clip.png)](http://enms3wiki.dpi.inpe.br/wiki/File:Msterpiece3.jpg)MS3 Resource Production & Control Environment.[![](http://enms3wiki.dpi.inpe.br/en.w/images/thumb/7/77/Msterpiece4.jpg/700px-Msterpiece4.jpg)](http://enms3wiki.dpi.inpe.br/wiki/File:Msterpiece4.jpg)[![](http://enms3wiki.dpi.inpe.br/en.w/skins/common/images/magnify-clip.png)](http://enms3wiki.dpi.inpe.br/wiki/File:Msterpiece4.jpg)MS3 Resource Production & Control Environment.[![](http://enms3wiki.dpi.inpe.br/en.w/images/thumb/e/e0/Msterpiece5.jpg/150px-Msterpiece5.jpg)](http://enms3wiki.dpi.inpe.br/wiki/File:Msterpiece5.jpg)[![](http://enms3wiki.dpi.inpe.br/en.w/skins/common/images/magnify-clip.png)](http://enms3wiki.dpi.inpe.br/wiki/File:Msterpiece5.jpg)MS3 Resource Production & Control Environment.

### MSTERY 

O MSTERY \(MS3 Executive Report Yielder\) é um sistema web responsável por fornecer relatórios sobre a geração e distribuição de produtos . Alguns relatórios executivos do MSTERY são: 

* Estatísticas de HRC
* Drift
* Solicitações por usuários
* Solicitações pendentes por usuários
* Solicitações pendentes por data
* Solicitações por instituição
* Solicitações por país 
* Solicitações por data
* Intervalo de entrega de cenas
* Mapa de cenas solicitadas
* Mapa de cenas catalogadas
* Solicitações por caminho/linha
* Lista de usuários
* Inscrições
* Estatísticas gerais 

  
[![](http://enms3wiki.dpi.inpe.br/en.w/images/thumb/2/25/Mstery.jpg/600px-Mstery.jpg)](http://enms3wiki.dpi.inpe.br/wiki/File:Mstery.jpg)[![](http://enms3wiki.dpi.inpe.br/en.w/skins/common/images/magnify-clip.png)](http://enms3wiki.dpi.inpe.br/wiki/File:Mstery.jpg)MS3 Executive Report Yielder.

