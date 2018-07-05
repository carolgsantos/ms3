---
description: Sistema de processamento de imagens.
---

# Processamento de imagem

O MS3 é capaz de executar as operações necessárias através de dados de telemetria por satélite para gerar produtos de imagem de satélite, até produtos ortorretificados.

O sistema de processamento é responsável pela geração de produtos. Além dos produtos tradicionais, existem os produtos especiais. Os produtos são gerados por um conjunto de módulos e ferramentas. Dentro do grupo de produtos tradicionais, estão as imagens produzidas em diferentes níveis de processamento, ou seja:

### Nível 0

É um arquivo HDF \([veja GRALHA](http://enms3wiki.dpi.inpe.br/wiki/GRALHA)\), sem nenhum processamento, contendo a imagem de dados bruta, dados orbitais e auxiliares. Este produto é gerado pelo módulo D2G.

[![](http://enms3wiki.dpi.inpe.br/en.w/images/thumb/9/95/Gralha.jpg/600px-Gralha.jpg)](http://enms3wiki.dpi.inpe.br/wiki/File:Gralha.jpg)[![](http://enms3wiki.dpi.inpe.br/en.w/skins/common/images/magnify-clip.png)](http://enms3wiki.dpi.inpe.br/wiki/File:Gralha.jpg)Level-0.

### Nível 1

Imagem corrigida radiometricamente. Mesmo que nenhuma correção geométrica seja feita na imagem de nível 1, as coordenadas geográficas dos cantos são escritas nas tags Geotiff. O módulo G2T gera este produto.

[![](http://enms3wiki.dpi.inpe.br/en.w/images/thumb/7/71/Level1.jpg/400px-Level1.jpg)](http://enms3wiki.dpi.inpe.br/wiki/File:Level1.jpg)[![](http://enms3wiki.dpi.inpe.br/en.w/skins/common/images/magnify-clip.png)](http://enms3wiki.dpi.inpe.br/wiki/File:Level1.jpg)Level-1.

### Nível 2

Imagem GeoTiff com correção radiométrica e geométrica do sistema. Este produto é gerado pelo módulo G2T.

[![](http://enms3wiki.dpi.inpe.br/en.w/images/thumb/8/83/Level2.jpg/400px-Level2.jpg)](http://enms3wiki.dpi.inpe.br/wiki/File:Level2.jpg)[![](http://enms3wiki.dpi.inpe.br/en.w/skins/common/images/magnify-clip.png)](http://enms3wiki.dpi.inpe.br/wiki/File:Level2.jpg)Level-2.

### Nível 3

Imagem GeoTiff com correção radiométrica e geométrica do sistema refinada usando pontos de controle. Este produto também é gerado pelo módulo G2T. 

### Nível 4

Imagem GeoTiff com correção radiométrica e sistema geométrico refinada usando pontos de controle e um DEM \(Digital Elevation Model\). O módulo G2T gera este produto. O uso de GPUs é suportado para acelerar o processamento, para uma lista de GPUs suportadas, consulte as [placas GPU](http://enms3wiki.dpi.inpe.br/wiki/GPU_boards). 

### Quicklook

Imagem colorida de baixa resolução espacial no formato JPEG. As visualizações rápidas são as imagens mostradas pelo MSTIC \(MS3 Image Catalog\). O módulo g2q gera este produto.

[![](http://enms3wiki.dpi.inpe.br/en.w/images/thumb/f/fd/Quicklook.jpg/400px-Quicklook.jpg)](http://enms3wiki.dpi.inpe.br/wiki/File:Quicklook.jpg)[![](http://enms3wiki.dpi.inpe.br/en.w/skins/common/images/magnify-clip.png)](http://enms3wiki.dpi.inpe.br/wiki/File:Quicklook.jpg)Quicklook.

### Produtos especiais

* Imagem de encaixe: mesmo que a imagem ortorretificada \(nível 4\) tenha alta precisão global, problemas pontuais de deslocamento ainda podem ser encontrados ao comparar a cena com uma referência. Podemos dizer que a mesma precisão não é garantida em diferentes pontos de cena. O pós-processamento da imagem ortorretificada corrige esses pequenos deslocamentos, resultando em uma imagem de alta precisão em toda a cena. A ferramenta _station\_image\_fit_ gera este produto especial. O uso de GPUs é necessário para o processamento de imagens adequadas, para uma lista de GPUs suportadas, consulte as placas GPU. 
* Imagens de refletância: dois produtos são gerados aqui, topo da atmosfera \(ToA\) e refletância de superfície. A reflectância de ToA é calculada por um modelo matemático. A refletância de superfície é calculada por 6S \(Segunda Simulação de um Sinal de Satélite no Código de Vetor de Espectro Solar\), que foi integrado ao MS3. Estes produtos são gerados pelo módulo T2R.  
* Máscara de nuvem: imagem que indica se um pixel é nuvem. O módulo _station\_classifier_ é responsável por gerar essa máscara.

[![](http://enms3wiki.dpi.inpe.br/en.w/images/thumb/5/56/Cloud_mask.jpg/400px-Cloud_mask.jpg)](http://enms3wiki.dpi.inpe.br/wiki/File:Cloud_mask.jpg)[![](http://enms3wiki.dpi.inpe.br/en.w/skins/common/images/magnify-clip.png)](http://enms3wiki.dpi.inpe.br/wiki/File:Cloud_mask.jpg)Cloud mask.

* Máscara de sombra de nuvem: imagem que indica se um pixel é sombra de nuvem. Este produto é gerado pelo módulo _station\_classifier_.

[![](http://enms3wiki.dpi.inpe.br/en.w/images/thumb/c/ca/Shadow_mask.jpg/400px-Shadow_mask.jpg)](http://enms3wiki.dpi.inpe.br/wiki/File:Shadow_mask.jpg)[![](http://enms3wiki.dpi.inpe.br/en.w/skins/common/images/magnify-clip.png)](http://enms3wiki.dpi.inpe.br/wiki/File:Shadow_mask.jpg)Cloud shadow mask.

* Mosaico multi-temporal: imagem resultante do mosaico de cenas multi-temporais. O mosaico é particionado levando em consideração uma grade de referência. Cada célula da grade define um bloco. As peças são entregues ao usuário. O mosaico multitemporal é criado pelo módulo _station\_update\_mosaic_. Veja [Mosaic Generation](http://enms3wiki.dpi.inpe.br/wiki/Mosaic_Generation) para entender os algoritmos envolvidos no processo de geração.  
* Label mask: imagem que indica a cena de origem de cada pixel de mosaico multi-temporal. Este produto é fornecido ao usuário junto com os mosaicos e também é gerado pelo módulo _station\_update\_mosaic_.

