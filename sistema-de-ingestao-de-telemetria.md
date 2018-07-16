---
description: Sistema de ingestão e gravação de dados brutos de satélites.
---

# Ingestão e Gravação de Imagens

O  MS³ é capaz de ingerir dados brutos de satélites e, para alguns dispositivos, exibir uma janela de movimentação em tempo quase real, na qual os dados gravados são mostrados. A janela móvel geralmente é usada na mesma máquina em que os dados são gravados, mas também pode ser usada em locais remotos.

### Características 

As principais características relacionadas à ingestão de telemetria são:

* Ingestão de dados em taxas de até 150 Mbps;
* Exibição da janela em movimento em tempo real para alguns geradores de imagens;
  * Para uma lista de imagens compatíveis;
  * Exibição de janela de movimentação remota pode ser executada em máquinas Linux e Windows.
* Sistema de arquivamento de dados brutos;
* Ferramentas de geração e medição BER. 

### Arquitetura

Cada máquina física possui uma placa de aquisição de telemetria instalada. Esta placa é responsável por converter a telemetria de informação analógica para digital. Para obter uma lista de placas de ingestão suportadas, características elétricas e de interface, consulte [Ingestion Boards](http://enms3wiki.dpi.inpe.br/wiki/Ingestion_Boards). Cada máquina física é conectada às outras através de uma rede Ethernet.

O módulo  MS³ T2D, telemetria para dados, é responsável por coletar os dados da placa de aquisição, registrando os dados brutos em um arquivo local, um arquivo DRD, sincroniza e decodifica os dados em tempo real para enviar a imagem e algumas informações auxiliares para o _Moving Windows_.

A [_Moving Windows_](sistema-de-ingestao-de-telemetria.md#moving-window) __exibe a imagem e os dados auxiliares para o usuário. Ele é executado localmente e pode ser executado remotamente também, permitindo que os usuários, longe do local de ingestão, visualizem os dados que estão sendo gravados. A comunicação entre as janelas móveis através do protocolo TCP e uma repetição pode ser usada em algumas configurações para melhorar o desempenho da rede.

Com o aplicativo _Recording Interface_ ou RI, o usuário pode criar e manter os agendamentos de aquisição e supervisionar as ingestões sendo feitas em cada máquina física. O aplicativo pode ser executado em qualquer máquina física e é capaz de controlar as operações de todas as máquinas através da rede.

Alguns serviços externos: 

Referência temporal: Cada máquina física deve se conectar a um servidor NTP para garantir uma referência de tempo suficiente. Os relógios de todas as máquinas físicas estão definidos como UTC.

Recuperação de TLE: Cada máquina física se conecta a um repositório TLE externo e obtém automaticamente dados TLE atualizados para cada satélite suportado. Os TLEs são usados ​​por alguns módulos  MS³ para algumas funções, como previsões de passagem de satélite para um site específico. Esta atualização é realizada por um módulo  MS³ chamado oda.

#### Moving Window

A ferramenta Moving Window permite que o usuário verifique a telemetria da imagem e alguns dados auxiliares quase em tempo real durante a recepção e, posteriormente, a partir do arquivo gravado de dados brutos. É também usado para exibir informações de Taxa de Erros de Bits.

[![](http://enms3wiki.dpi.inpe.br/en.w/images/thumb/1/1e/Mw.jpg/600px-Mw.jpg)](http://enms3wiki.dpi.inpe.br/wiki/File:Mw.jpg)[![](http://enms3wiki.dpi.inpe.br/en.w/skins/common/images/magnify-clip.png)](http://enms3wiki.dpi.inpe.br/wiki/File:Mw.jpg)Moving Window Screenshot

Existem 3 painéis separados que exibem informações para o passe de satélite atual, na interface da aplicação.

No canto superior esquerdo, temos o painel de informações, onde as informações textuais são exibidas. Temos a identificação do satélite, a composição da cor da imagem exibida, o último código de tempo decodificado \(do satélite\) e timestamp \(da estação receptora\), a posição do satélite, a taxa de recepção, a faixa do instrumento e outros dados específicos do instrumento.

No canto inferior esquerdo, um mapa é exibido. Enquanto nenhum dado está sendo recebido, o usuário pode selecionar qual mapa será usado. O histórico da posição do satélite é mostrado em amarelo enquanto a faixa do instrumento é mostrada em vermelho.

À direita, temos a imagem, ela rola automaticamente durante a passagem do satélite, mas o usuário pode se mover para cima ou para baixo para ver qualquer ponto de interesse na imagem. Ao clicar, o código de tempo da linha da imagem é exibido e o mapa é centrado em torno da posição desejada.

O usuário pode aumentar ou diminuir o zoom para ver melhor a imagem, qualquer fator de zoom diferente de 1 causará um impacto no desempenho do aplicativo durante a ingestão. Isso deve ser levado em consideração ao testar uma nova instalação.

A visibilidade, posição e tamanho do painel são configuráveis ​​pelo usuário.

O aplicativo funciona como um servidor que permite que aplicativos clientes se conectem a ele. Esses clientes recebem as mesmas mensagens MW que o aplicativo está processando para exibir seus dados. O MW escuta conexões na porta 49001.

#### Remote Moving Window

[![](http://enms3wiki.dpi.inpe.br/en.w/images/thumb/7/78/Mwremote.jpg/600px-Mwremote.jpg)](http://enms3wiki.dpi.inpe.br/wiki/File:Mwremote.jpg)[![](http://enms3wiki.dpi.inpe.br/en.w/skins/common/images/magnify-clip.png)](http://enms3wiki.dpi.inpe.br/wiki/File:Mwremote.jpg)Remote Moving Window Screenshot

Um aplicativo irmão chamado _Remote Moving Window_ pode ser usado para conectar-se a uma janela em movimento de qualquer lugar, desde que haja uma conexão de rede disponível entre os dois aplicativos.

A única diferença entre os dois aplicativos é a informação de conexão no Remote Moving Window. Pode ser visto na barra de ferramentas à esquerda dos botões Zoom. Na caixa de edição, o usuário pode inserir o &lt;host&gt;:&lt;porta&gt; para conectar-se e pode usar os botões para conectar e desconectar da janela móvel.

