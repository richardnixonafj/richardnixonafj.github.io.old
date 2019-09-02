---
layout: post
title: "Ransomware Android usa SMS para infectar "
categories:
  - Security
tags:
  -- Android
  - Ransomware 
  - Android
  - Sms
  - technology
  - tecnologia
  - Security
  - Segurança
featured-img: android-malware
last_modified_at: 2019-09-02T13:00:52-05:00
---



Uma nova família de [ransomware](https://www.kaspersky.com.br/resource-center/definitions/what-is-ransomware) criada para dispositivos Android vem se espalhando fazendo vítimas enviando mensagens de texto (SMS) contendo links maliciosos para toda a lista de contatos encontrada em alvos já infectados.

O malware apelidado de Android/Filecoder.C (FileCoder) pela equipe de pesquisa da [ESET](https://www.eset.com/br/), que descobriu que código malisioso está em busca de dispositivos que executam o Android 5.1 ou posterior.

"Devido à segmentação e falhas estreitas na execução da campanha e na implementação de sua criptografia, o impacto desse novo ransomware é limitado", descobriram os pesquisadores da ESET.

"Depois que o ransomware envia esse lote de SMS maliciosos, ele criptografa a maioria dos arquivos de usuário no dispositivo e solicita um resgate. Devido à criptografia falha, é possível descriptografar os arquivos afetados sem a ajuda do invasor", acrescenta a ESET.

Apesar disso, se os desenvolvedores do ransomware conseguirem consertar seu "produto", muitos usuários do Android poderão ser expostos a uma variedade de malware muito perigosa e potencialmente altamente destrutiva.

### Vetor de infecção por Ransomware SMS

O FileCoder foi visto pela primeira vez pela ESET durante uma campanha desde 12 de julho, com os atacantes distribuindo sua carga maliciosa por meio de postagens feitas no [Reddit]( https://www.reddit.com/) e na comunidade de desenvolvimento de software móvel [XDA Developers](https://www.xda-developers.com/).

Enquanto o Forum do XDA removeu as postagens maliciosas após ser notificado, os tópicos do Reddit ainda estavam em andamento no momento em que o pesquisador de malware da ESET, [Lukas Stefanko](https://twitter.com/LukasStefanko), publicou a análise de malware do FileCoder.

Os desenvolvedores do FileCoder usam dois servidores para distribuir o ransomware, com cargas maliciosas sendo vinculadas a partir das mensagens de texto maliciosas enviadas para toda a lista de contatos das vítimas e das postagens no fórum do Reddit e do XDA.

#### SMS malicioso

As amostras de ransomware também são vinculadas com a ajuda de códigos QR, o que tornar mais rápido para os usuários móveis obterem a cópia do aplicativo malicioso(APK) em seus dispositivos e instalá-los.

Como isca para convencer as vítimas em potencial a instalar os aplicativos Android infectados em seus dispositivos, os operadores do FileCoder diriam que o aplicativo "supostamente usa as fotos da vítima em potencial".

No entanto, as postagens no fórum do Reddit e do XDA "promovem" o aplicativo mal-intencionado como um jogo online de simulador de sexo gratuito, o que também deve tornar atrativo o suficiente para que os possíveis alvos, sejam enganados a baixar e instalar o aplicativo ransomware em seus dispositivos.

Como o [BleepingComputer](https://www.bleepingcomputer.com/) encontrou ao analisar uma amostra do FileCoder, ao ser instalado no dispositivo Android da vítima, o malware solicitará as seguintes permissões:

<a name="headers"/>

```
android.permission.SET_WALLPAPER  (trocar o papel de parede do aparelho)
android.permission.WRITE_EXTERNAL_STORAGE (gravar dados em dispositivos de armazenamento externo)
android.permission.READ_EXTERNAL_STORAGE (Ler dados de dispositivos de armazenamento externo)
android.permission.READ_CONTACTS (ler os contato do telefone)
android.permission.RECEIVE_BOOT_COMPLETED (permissão que pode ser usada para inicializar o ransoware ao iniciar o telefone)
android.permission.SEND_SMS (Enviar SMS)
android.permission.INTERNET (acessar a internet)
```

"Para maximizar seu alcance, o ransomware possui as 42 versões de idioma (exatamente ele é poliglota) do modelo de mensagem [...]. Antes de enviar as mensagens, ele escolhe a versão que se ajusta à configuração de idioma do dispositivo da vítima. Para personalizar o texto malicioso, o malware precede o contato do contato e continua o ciclo de envio de envio de sms.

O FileCoder se espalhará para a lista de contatos da vítima via SMS antes de começar a criptografar arquivos em todas as pastas no armazenamento do dispositivo que tiver acesso, acrescentando a extensão .seven aos nomes de arquivos originais - os arquivos do sistema serão ignorados.

"O ransomware também deixa os arquivos não criptografa se a extensão for" .zip "ou" .rar "e o tamanho do arquivo for superior a 51.200 KB / 50 MB e os arquivos" .jpeg "," .jpg "e" .png "com um tamanho de arquivo menor que 150 KB ", conforme dito pela ESET.

O malware criptografa uma mistura estranha de tipos de arquivos específicos do Android, bem como uma combinação estranha de tipos de documentos não relacionados, com a equipe de pesquisa da ESET concluindo que "a lista foi copiada do notório WannaCryptor, também conhecido como WannaCry ransomware". (É uma especie de fork/cópia mal-feita do famoso [WannaCry](https://www.avast.com/pt-br/c-wannacry)).

#### Recuperando novos domínios de servidor C2 e endereços BTC

##### Servidores FileCoder C2 ainda ativos

Depois que todos os arquivos são bloqueados pelo malware, ele exibe a nota de resgate, detalhando o número de arquivos criptografados e em quanto tempo que a vítima precisa pagar pelo custo da chave de descriptografia - os valores do resgate variam entre US $ 94 e US $ 188. 

Enquanto a nota de resgate diz que os dados serão perdidos se o resgate não for pago dentro de três dias, "não há nada no código fonte do ransomware para apoiar a alegação de que os dados afetados serão perdidos após 72 horas" (ou seja é um blefe).

##### Nota de resgate do FileCoder

Ao contrário da maioria das outras gerações de ransomware para Android, o FileCoder não bloqueia as telas das vítimas e permite que continuem a usar seus dispositivos, dependendo apenas do fato de que seus alvos desejam que seus arquivos sejam descriptografados o mais rápido possível.

O FileCoder criptografa arquivos usando as novas chaves [AES](https://pt.wikipedia.org/wiki/Advanced_Encryption_Standard) para cada um dos arquivos bloqueados, empregando um par de chaves públicas e privadas, sendo a última criptografada com a ajuda do [algoritmo RSA](https://pt.wikipedia.org/wiki/RSA_(sistema_criptogr%C3%A1fico)).

No entanto, como os desenvolvedores do ransomware codificaram o valor usado para criptografar a chave privada no código do malware, as vítimas podem descriptografar seus dados sem pagar o resgate.

"Tudo o que é necessário é o UserID [..] fornecido pelo ransomware e o arquivo APK do ransomware, caso seus autores alterem o valor da chave codificada", descobriram os pesquisadores da ESET.

No momento em que essa pagina foi publicada, os servidores usados pelos autores do FileCoder ainda estavam online, com a página de verificação de pagamento de resgate também disponível através de um dos arquivos hospedados nos servidores C2 do malware.

A página de verificação de pagamento também fornece às vítimas um 'email de suporte' projetado para permitir que elas solicitem ajuda em caso de problemas: "Se você tiver alguma dúvida, entre em contato conosco. Nosso endereço de email: h3athledger@yandex.ru".

Mais detalhes sobre o funcionamento interno do ransomware Android / Filecoder.C, juntamente com uma lista de indicadores de compromisso (IOCs), incluindo hashes de amostra de malware, o endereço Bitcoin usado na campanha, estão disponíveis no final da análise de malware do [Filecoder do Stefanko](https://www.welivesecurity.com/2019/07/29/android-ransomware-back/).


---

Fonte: [bleepingcomputer](https://www.bleepingcomputer.com/news/security/new-android-ransomware-uses-sms-spam-to-infect-its-victims/)
