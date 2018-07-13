---
description: Dados utilizados pelos sistemas.
---

# Tipos de dados gerados

### DRD

O dado DRD \(Dated Raw Data\), é um arquivo que contém os dados brutos transmitidos por um satélite. Tais dados se encontram codificados e em formatos específicos que dependem do satélite e do sensor em questão. Desta forma, não podem ser usados diretamente como entrada para os processos de geração de imagens, uma vez que tais processos são implementados com base em um dado de mesmo formato para todos os satélites e sensores. 

### GRALHA

O dado GRALHA \(Generic Raw Level Hierarchical Archive\), é um arquivo que possui as informações do DRD decodificadas e armazenadas de forma padrão para todos os satélites e sensores, servindo de entrada para os processos de geração de imagens. Estes arquivos são gerados utilizando a biblioteca de código aberto HDF5, gerando arquivos do tipo HDF.

#### HDF e  HDF-EOS

O formato HDF \(Hierarquical Data Format\) foi gerado com o intuito de compartilhar dados em ambientes distribuídos e orientado para dados científicos, podendo conter uma quantidade finita de estruturas, dentre as quais: imagens brutas, dados multidimensionais, paleta de cores e grupos de dados. Já o formato HDF-EOS, foi criado como uma melhoria do HDF, suportando a inclusão de dados geo-espaciais, divididos em três conjuntos: Grid, Swath e Point. 

### IMAGEM

A imagem é o tipo final de dado processado pelo sistema. Conforme já apresentado, são utilizadas bibliotecas de código aberto para geração de imagens do tipo jpg, tiff e geotiff.

#### JPG

O formato JPG \(Joint Pictures Expert Group\), é um formato de imagem que se tornou um dos padrões populares. Tem tamanho pequeno quando comparado a outros formatos, facilitando o seu armazenamento e a sua distribuição. Ele comprime os dados para um tamanho muito menor, gerando perda na qualidade da imagem. É mais utilizado quando o tamanho do arquivo é mais importante do que a máxima qualidade de imagem \(por exemplo, em páginas web, blogs, e-mail, cartões de memória, etc\).

#### TIFF e GEOTIFF

O formato TIFF \(Tagged Image File Format\) por sua vez, é um formato que possui pouca ou nenhuma compressão não perdendo quaisquer detalhes, embora os arquivos possam ser grandes. É o mais versátil, exceto para páginas web, pois alguns navegadores não apresentam este tipo de arquivo. Oferece grande quantidade de cores e excelente qualidade de imagem, permitindo o uso de _camadas_ \(como nos arquivos PSD originais do photoshop\) que são versões diferenciadas da imagem existentes num mesmo arquivo. Já o formato GeoTIFF \(Geographic Tagged Image File Format\) é um tipo de metadado que permite embutir informações geográficas em um arquivo TIFF. A informação adicional inclui projeções cartográficas, sistema de coordenadas, elipsoides, data e o necessário para estabelecer a referência espacial exata no arquivo.

