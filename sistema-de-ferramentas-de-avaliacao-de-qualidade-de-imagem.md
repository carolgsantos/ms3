---
description: Sistema de avaliação e controle de qualidade de imagens.
---

# Ferramentas de avaliação de qualidade de imagens

O MS3 fornece ferramentas para realizar avaliações de qualidade geométrica e radiométrica, incluindo ferramentas de simulação para estudar, por exemplo, como a correção geométrica é afetada por fatores como imprecisão de dados de telemetria e ruído. O sistema fornece as ferramentas Marlin e Sailfish para realizar avaliações de qualidade geométrica e radiométrica. 

O Marlin é um software gratuito para visualizar imagens de satélite e realizar avaliações de qualidade geométrica e radiométrica. E o Sailfish inclui funcionalidades para estudar assuntos sobre como a correção geométrica é afetada por fatores como imprecisão de dados de telemetria e ruído, parâmetros de calibração, entre outros.

### Marlin

O Marlin é um software livre, sob os termos da GNU \(Licença Pública Geral\), que permite a visualização simples e direta de imagens digitais \(quantização de 8 ou 16 bits\). Além da simples visualização, o usuário também possui ferramentas para melhorar a qualidade da radiometria da imagem. Isso pode ser feito através de modificação de brilho e contraste ou aplicação de filtros.

Para usuários avançados, o Marlin permite realizar avaliações de qualidade geométrica e radiométrica. Para realizar a avaliação da qualidade geométrica, o usuário pode definir pontos de controle a partir de uma imagem de referência. A qualidade é descrita por medidas de avaliação, como variação de comprimento, similaridade e anisomorfismo, e por parâmetros de transformação geométrica. Para realizar a avaliação da qualidade radiométrica, o usuário pode calcular o registro das bandas e a autocorrelação da banda. Além disso, o usuário pode analisar a curva de refletância e detectar alterações.

As seguintes funcionalidades estão disponíveis no Marlin:

* Salvar uma área selecionada;
* Encontrar pixel;
* Realizar uma avaliação de qualidade geométrica;
* Calcular o registro de bandas;
* Calcular a autocorrelação de bandas;
* Aplicar filtro;
* Aplicar máscara;
* Estatísticas de computação da imagem;
* Análise de curva de refletância;
* Detecção de mudança;
* Detecção de nuvens e sombras.

[![](http://enms3wiki.dpi.inpe.br/en.w/images/thumb/2/22/Marlin.jpg/600px-Marlin.jpg)](http://enms3wiki.dpi.inpe.br/wiki/File:Marlin.jpg)[![](http://enms3wiki.dpi.inpe.br/en.w/skins/common/images/magnify-clip.png)](http://enms3wiki.dpi.inpe.br/wiki/File:Marlin.jpg)Marlin.[![](http://enms3wiki.dpi.inpe.br/en.w/images/thumb/e/e2/Marlin_2_5.jpg/600px-Marlin_2_5.jpg)](http://enms3wiki.dpi.inpe.br/wiki/File:Marlin_2_5.jpg)[![](http://enms3wiki.dpi.inpe.br/en.w/skins/common/images/magnify-clip.png)](http://enms3wiki.dpi.inpe.br/wiki/File:Marlin_2_5.jpg)Geometric Quality Assessment.[![](http://enms3wiki.dpi.inpe.br/en.w/images/thumb/1/1c/Change_image.jpg/600px-Change_image.jpg)](http://enms3wiki.dpi.inpe.br/wiki/File:Change_image.jpg)[![](http://enms3wiki.dpi.inpe.br/en.w/skins/common/images/magnify-clip.png)](http://enms3wiki.dpi.inpe.br/wiki/File:Change_image.jpg)Change Detection.[![](http://enms3wiki.dpi.inpe.br/en.w/images/thumb/d/dd/Reflectance_curve.jpg/600px-Reflectance_curve.jpg)](http://enms3wiki.dpi.inpe.br/wiki/File:Reflectance_curve.jpg)[![](http://enms3wiki.dpi.inpe.br/en.w/skins/common/images/magnify-clip.png)](http://enms3wiki.dpi.inpe.br/wiki/File:Reflectance_curve.jpg)Reflectance curve analysis.

### Sailfish

O Sailfish é uma extensão do Marlin. Além das funcionalidades do Marlin, o Sailfish possui novas funcionalidades que permitem estudar os parâmetros envolvidos no processo de geração de cena.

Vários parâmetros influenciam a qualidade geométrica da imagem, como efemérides, atitude, parâmetros de calibração da câmera \(distância focal, tamanho do detector, disposição dos detectores no plano focal\). Quando são detectados erros acima do especificado é necessário identificar a fonte de erro.

O Sailfish trabalha com o cenário. Dentro de um cenário é possível manipular cada parâmetro envolvido no processo de geração de cena individualmente e calcular o efeito de cada um deles na qualidade da imagem.

As seguintes funcionalidades estão disponíveis no Sailfish:

* Todas as funcionalidades do Marlin;
* Criar e editar kernels;
* Trabalhar com cenários;
* Exportar kernels de um conjunto de pontos de controle;
* Calcular a correlação de detectores;
* Calcular as estatísticas dos detectores;
* Calcular a correlação inter-array;
* Criar imagens usando um cenário

  
[![](http://enms3wiki.dpi.inpe.br/en.w/images/thumb/b/b5/Sailfish.jpg/700px-Sailfish.jpg)](http://enms3wiki.dpi.inpe.br/wiki/File:Sailfish.jpg)[![](http://enms3wiki.dpi.inpe.br/en.w/skins/common/images/magnify-clip.png)](http://enms3wiki.dpi.inpe.br/wiki/File:Sailfish.jpg)Scenario.[![](http://enms3wiki.dpi.inpe.br/en.w/images/thumb/7/7a/Sailfish1.jpg/700px-Sailfish1.jpg)](http://enms3wiki.dpi.inpe.br/wiki/File:Sailfish1.jpg)[![](http://enms3wiki.dpi.inpe.br/en.w/skins/common/images/magnify-clip.png)](http://enms3wiki.dpi.inpe.br/wiki/File:Sailfish1.jpg)Geometric Quality Assessment.[![](http://enms3wiki.dpi.inpe.br/en.w/images/thumb/2/2c/Sailfish2.jpg/700px-Sailfish2.jpg)](http://enms3wiki.dpi.inpe.br/wiki/File:Sailfish2.jpg)[![](http://enms3wiki.dpi.inpe.br/en.w/skins/common/images/magnify-clip.png)](http://enms3wiki.dpi.inpe.br/wiki/File:Sailfish2.jpg)Kernels management.

