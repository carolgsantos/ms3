# Módulos de Processamento

## Conhecendo os Módulos de Processamento

Para a produção de imagens em diferentes níveis de processamento, o MS³ é composto por um conjunto de módulos. Estes módulos manipulam diferentes tipos de dados para gerar o produto desejado.

Os principais módulos de processamento do MS³ são: D2G, G2Q, G2T e H2T. Que vão desde o dado bruto até a imagem em nível 4 de processamento. Dados necessários para a realização destes procedimentos, de forma geral, se encontram armazenados em arquivos de calibração existentes para cada satélite e para cada sensor específico. 

### D2G

O módulo denominado **D2G** \(DRD to GRALHA\), utiliza o dado bruto do satélite para gerar o arquivo compatível com o sistema de processamento de imagens do MS³. Este processo envolve a decodificação de todos os dados da cena enviados pelos satélites e sua gravação num arquivo GRALHA. Uma vez gerado o GRALHA, o MS3 está apto a gerar imagens em diferentes níveis de processamento. A gravação é feita agrupando as informações em conjuntos, que por sua vez, são subdivididos em grupos específicos de dados. 

Para melhor ilustrar esta hierarquia, sabe-se que cada cena possui dados de efemérides, atitude, tempo, valor de brilho de cada banda do sensor, entre outros. Cada um destes dados é armazenado em um conjunto separado. No caso do conjunto dos valores de brilho, é criado um grupo específico para cada banda, ou seja, os dados são subdivididos em grupos referentes a cada banda específica. Neste módulo, é gerado um ou mais GRALHAs para cada cena. 

### G2Q

O módulo denominado **G2Q** \(GRALHA to Quicklook\), produz, a partir do GRALHA, imagens denominadas _Quicklook_, que são de baixa resolução espacial e consistem em uma composição colorida de três bandas pré-determinadas no arquivo de configuração. Neste processo, é possível realizar algumas correções radiométricas e geométricas nas imagens, dependentes do tipo de sensor, tais como: correção de linhas perdidas, correção do tamanho da linha, do deslocamento entre as bandas, equalização de detectores, entre outras. Os Quicklooks gerados são gravados no formato [JPG](tipos-de-dados.md#jpg). Estes arquivos correspondem as imagens apresentadas pelo Catálogo de Imagens. 

### G2T

O principal módulo de geração de imagens denominado **G2T** \(GRALHA to Tiff\), é onde são geradas, a partir do GRALHA, as imagens de nível 1 a 4 de processamento citadas na explicação do [**Sistema de Processamento**](sobre-o-ms3.md#principais-sistemas)**.**

ADICIONAR NOVOS MODULOS QUE SÃO UTILIZADOS

{% hint style="warning" %}
### Interação com o **MS³**

Para executar os módulos do MS3 são necessários os WOF \(Work Order File\). O WOF consiste num arquivo em formato XML e é a maneira principal de interação com os módulos de processamento. Eles permitem que sejam configurados desde informações gerais tais como nome e número do satélite, nome do instrumento, dados de entrada dos módulos, diretórios dos arquivos, até informações mais específicas de cada módulo. No caso da ferramenta G2T, é possível configurar no WOF o datum da imagem a ser gerada, o nível de processamento, o tipo de interpolação a ser utilizada, etc. Este arquivo é gerado automaticamente pelo catálogo de imagens de acordo com informações fornecidas em uma solicitação de imagem.
{% endhint %}



