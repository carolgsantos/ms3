---
description: Sistema de ingestão e gravação de dados de telemetria.
---

# Ingestão de telemetria

O MS3 é capaz de ingerir dados brutos de satélites e, para alguns dispositivos, exibir uma janela de movimentação em tempo quase real, na qual os dados gravados são mostrados. A janela móvel geralmente é usada na mesma máquina em que os dados são gravados, mas também pode ser usada em locais remotos.

#### Ambiente operacional

Salvo indicação anterior, os recursos de processamento apresentados neste documento requerem o Red Hat Enterprise Linux 5 ou similar, como o CentOS 5. Atualmente, a única exceção é a exibição da janela de movimentação remota, que também é executada nos sabores do Windows XP e do Windows Vista.

#### Características 

As principais características relacionadas à ingestão de telemetria são:

* Ingestão de dados em taxas de até 150 Mbps;
* Exibição da janela em movimento em tempo real para alguns geradores de imagens;
  * Para uma lista de imagens compatíveis;
  * Exibição de janela de movimentação remota pode ser executada em máquinas Linux e Windows.
* Sistema de arquivamento de dados brutos;
* Ferramentas de geração e medição BER. 

#### Arquitetura

Cada máquina física possui uma placa de aquisição de telemetria instalada. Esta placa é responsável por converter a telemetria de informação analógica para digital. Para obter uma lista de placas de ingestão suportadas, características elétricas e de interface, consulte [Ingestion Boards](http://enms3wiki.dpi.inpe.br/wiki/Ingestion_Boards). Cada máquina física é conectada às outras através de uma rede Ethernet.

O módulo MS3 T2D, telemetria para dados, é responsável por coletar os dados da placa de aquisição, registrando os dados brutos em um arquivo local, um arquivo DRD, sincroniza e decodifica os dados em tempo real para enviar a imagem e algumas informações auxiliares para o _Moving Windows_.

A _Moving Windows_ exibe a imagem e os dados auxiliares para o usuário. Ele é executado localmente e pode ser executado remotamente também, permitindo que os usuários, longe do local de ingestão, visualizem os dados que estão sendo gravados. A comunicação entre as janelas móveis através do protocolo TCP e uma repetição pode ser usada em algumas configurações para melhorar o desempenho da rede.

Com o aplicativo _Recording Interface_ ou RI, o usuário pode criar e manter os agendamentos de aquisição e supervisionar as ingestões sendo feitas em cada máquina física. O aplicativo pode ser executado em qualquer máquina física e é capaz de controlar as operações de todas as máquinas através da rede.

Alguns serviços externos: 

Referência temporal: Cada máquina física deve se conectar a um servidor NTP para garantir uma referência de tempo suficiente. Os relógios de todas as máquinas físicas estão definidos como UTC.

Recuperação de TLE: Cada máquina física se conecta a um repositório TLE externo e obtém automaticamente dados TLE atualizados para cada satélite suportado. Os TLEs são usados ​​por alguns módulos MS3 para algumas funções, como previsões de passagem de satélite para um site específico. Esta atualização é realizada por um módulo MS3 chamado oda.

