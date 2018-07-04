# Sobre o MS³

## Entendendo o **MS³**

> O MS³ ****\(Sistema de Estações Multi-Satélite\) consiste num sistema para a ingestão, gravação e processamento de imagens de sensoriamento remoto, incluindo também a avaliação e o controle de qualidade de imagens CBERS \(China-Brazil Earth Resources Satellite\). \(SILVA, M. A. O, 2007\)

O **MS³** engloba os subsistemas de:

* **Ingestão e Gravação de dados:** com a função de moving-window em tempo real, dando possibilidade de acesso remoto via web;
* **Processamento:** com a geração de produtos em diversos níveis, incluindo imagens ortorretificadas;
* **Disseminação \(Catálogo\):** com as funções de pesquisa e pedido de produtos;
* **Avaliação e Qualidade:** com as funções de avaliação das qualidades geométrica e radiométrica das imagens.

O sistema ****processa dados dos seguintes satélites \(sensores\): CBERS-1 e CBERS-2 \(CCD, IRMSS e WFI\); CBERS-2B \(CCD, HRC e WFI\); Landsat -1, Landsat-2 e Landsat-3 \(MSS\); Landsat-4 e Landsat-5 \(MSS e TM\); Landsat-7 \(ETM+\) disponível no catálogo antigo. E disponíveis no catálogo novo CBERS-4 \(AWSI, IRS, MUX, PAN5M, PAN10M\); Landsat-8 \(OLI\).

### Arquitetura do Sistema

> O principal objetivo do projeto **MS³** é o barateamento do desenvolvimento e da operação do sistema de processamento de imagens de satélite do INPE, mantendo, ao mesmo tempo, um sistema flexível que permita a rápida adição de novos satélites e sensores. \(SILVA, M. A. O, 2007\)

O sistema foi construído totalmente com base em bibliotecas de código livre \(open-source\). Dentre as diversas bibliotecas utilizadas podem ser citadas: tiff, geotiff, jpeg, hdf5, etc.

{% hint style="warning" %}
**LINGUAGENS E BIBLIOTECAS UTILIZADAS PARA CONSTRUIR O SISTEMA.**

As funcionalidades de seus subsistemas são providas através de módulos, onde os gerais não têm conhecimento de como cada satélite implementa as interfaces do sistema, isto é atingido através da ligação dinâmica \(dynamic linking\), em tempo de execução, com a biblioteca de cada satélite. O processo de desenvolvimento utiliza testes unitários e funcionais que trabalham como uma rede de segurança enquanto funcionalidades do sistema são adicionadas ou alteradas. Isto é uma pré-condição em um sistema com 300.000 linhas de código \(286677 em C++, 32866 em Python e 13315 em scripts shell e Perl\). A escalabilidade do sistema é atingida através da adição de um novo hardware ao conjunto de produção. Como este hardware é comum e de baixo custo, um aumento de demanda pode ser rapidamente atendido sem aumentar desnecessariamente a complexidade do sistema.
{% endhint %}

### Principais sistemas

> O **MS³** apresenta quatro sistemas principais: Sistema de Ingestão e Gravação, Sistema de Processamento, Sistema de Disseminação e o Sistema de Avaliação e Controle de Qualidade. \(SILVA, M. A. O, 2007\)

O **Sistema de Ingestão e Gravação** é responsável pela ingestão e gravação dos dados transmitidos pelos satélites. A partir de um arquivo TLE \(two-line elements\), o qual contém informações de órbita do satélite, são determinados a data e os horários de início e término da passagem, com esses dados todas as passagens são agendadas automaticamente para gravação. Os dados ingeridos são gravados em arquivos no formato DRD \([Dated Raw Data](tipos-de-dados.md#drd)\). As operações de planejamento, manutenção das gravações, verificação das operações realizadas, gravação e transferência dos dados, são realizadas a partir de uma ferramenta de controle do sistema de ingestão. 

Para o sistema de Ingestão e Gravação, sete máquinas \(sir 1-7\) são responsáveis pela gravação dos canais de transmissão dos satélites. Os computadores estão configurados para funcionar em rede, mas caso haja algum problema de conexão, o sistema continuará sendo capaz de realizar a ingestão de qualquer canal corretamente.

Durante a ingestão é possível a visualização em tempo real dos dados através da ferramenta _Moving Window_, onde além da imagem ela apresenta as informações do satélite, do canal e os dados da recepção \(identificação do satélite, time-code, time-stamp, e configuração de bandas\). Os dados ingeridos também podem ser visualizados remotamente.

O **Sistema de Processamento** é responsável pela geração das imagens em diferentes níveis de processamento. Podem ser gerados cinco produtos diferentes por este sistema: 

* Imagem Nível 0: imagem bruta, sem tratamento de espécie alguma, armazenada juntamente com os dados de calibração radiométrica e os parâmetros orbitais \(atitude e efemérides\), entre outros;
* Imagem Nível 1: imagem com correção radiométrica. O cabeçalho do arquivo contém informações geográficas básicas, tais como coordenadas geodésicas dos cantos e do centro da cena;
* Imagem Nível 2: imagem com correção radiométrica e correção geométrica de sistema; 
* Imagem Nível 3: imagem com correções radiométrica e geométrica de sistema, refinada pelo uso de pontos de controle; 
* Imagem Nível 4: imagem com correções radiométrica e geométrica de sistema, refinada pelo uso de pontos de controle e de um Modelo Numérico de Elevação do Terreno \(MNET\). 

As imagens nos níveis de processamento 1 a 4 são geradas no formato [GeoTiff ](tipos-de-dados.md#tiff-e-geotiff)acompanhadas de um arquivo de metadados no formato XML \([eXtensable Markup Language](tipos-de-dados.md#xml)\). A imagem nível 0 é gerada no formato GRALHA \([Generic Raw Level Hierarchical Archive](tipos-de-dados.md#gralha)\), um formato desenvolvido para o armazenamento de dados brutos decodificados. O processamento é dívido em [módulos](modulos-de-processamento.md), que serão melhor explicados ao longo do documento.

 O **Sistema de Disseminação \(Catálogo\)** é responsável pela distribuição dos produtos. Essa distribuição é feita pela internet a partir do [Catálogo de Imagens](http://www.dgi.inpe.br/CDSR/) onde o usuário, a partir das ferramentas de consulta do catálogo, identifica as imagens desejadas e faz o pedido. As informações a respeito do processamento do pedido e o endereço para download das imagens via FTP são fornecidas via e-mail.

{% embed data="{\"url\":\"http://www.dgi.inpe.br/CDSR/\",\"type\":\"link\",\"title\":\"Catálogo de Imagens\",\"icon\":{\"type\":\"icon\",\"url\":\"http://www.dgi.inpe.br/CDSR/img/icone.png\",\"aspectRatio\":0},\"caption\":\"Antigo Catálogo de imagens\"}" %}

{% embed data="{\"url\":\"http://www.dgi.inpe.br/catalogo/\",\"type\":\"link\",\"title\":\"Divisão de Geração de Imagem :: Catálogo de Imagens\",\"description\":\"Página principal do site da DGI \(Divisão de Geração de Imagem\)\",\"icon\":{\"type\":\"icon\",\"url\":\"http://www.dgi.inpe.br/catalogo/img/icone.png\",\"aspectRatio\":0},\"caption\":\"Novo Catálogo de Imagens\"}" %}

O **Sistema de Avaliação e Controle de Qualidade** é formado por dois aplicativos que possuem quatro objetivos principais: Visualização, Avaliação, Análise e Simulação.

{% hint style="warning" %}
O primeiro aplicativo, chamado **Marlin**, responde pelos dois primeiros objetivos. Foi desenvolvido tanto para o sistema operacional Linux quanto Windows, sendo distribuído gratuitamente pelo INPE aos usuários de imagens de satélite. O sistema pode trabalhar com imagens de qualquer satélite, independente da tecnologia do sensor e das resoluções espacial e radiométrica. O principal objetivo desta distribuição é fazer com que o sistema de processamento seja constantemente aprimorado para eliminar os problemas identificados e reportados pelos usuários. 

O segundo aplicativo, chamado **Sailfish**, responde pela análise e simulação estando integrado ao Marlin e aos modelos geométricos do MS³. Ele permite que o analista altere parâmetros do sistema como, por exemplo, os da geometria do sensor, dados orbitais, comparando resultados obtidos por diferentes fontes de efemérides \(transmitida, pré-processada e pósprocessada\) e atitude \(transmitida e pós-processada\), sempre no sentido de identificar uma melhoria para o sistema de geração de produtos. O sistema pode ser utilizado pela área de Engenharia de Satélites, responsável pelo projeto dos diversos sistemas de um satélite, pois permite quantificação da distorção média relativa a cada um dos sistemas na qualidade geométrica das imagens.
{% endhint %}



