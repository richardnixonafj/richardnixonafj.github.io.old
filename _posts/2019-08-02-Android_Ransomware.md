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
last_modified_at: 2017-03-09T14:25:52-05:00
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

Alternatively, for H1 and H2, an underline-ish style:

Alt-H1
======

Alt-H2
------

<a name="emphasis"/>
## Emphasis

```no-highlight
Emphasis, aka italics, with *asterisks* or _underscores_.

Strong emphasis, aka bold, with **asterisks** or __underscores__.

Combined emphasis with **asterisks and _underscores_**.

Strikethrough uses two tildes. ~~Scratch this.~~
```

Emphasis, aka italics, with *asterisks* or _underscores_.

Strong emphasis, aka bold, with **asterisks** or __underscores__.

Combined emphasis with **asterisks and _underscores_**.

Strikethrough uses two tildes. ~~Scratch this.~~


<a name="lists"/>
## Lists

(In this example, leading and trailing spaces are shown with with dots: ⋅)

```no-highlight
1. First ordered list item
2. Another item
⋅⋅* Unordered sub-list.
1. Actual numbers don't matter, just that it's a number
⋅⋅1. Ordered sub-list
4. And another item.

⋅⋅⋅You can have properly indented paragraphs within list items. Notice the blank line above, and the leading spaces (at least one, but we'll use three here to also align the raw Markdown).

⋅⋅⋅To have a line break without a paragraph, you will need to use two trailing spaces.⋅⋅
⋅⋅⋅Note that this line is separate, but within the same paragraph.⋅⋅
⋅⋅⋅(This is contrary to the typical GFM line break behaviour, where trailing spaces are not required.)

* Unordered list can use asterisks
- Or minuses
+ Or pluses
```

1. First ordered list item
2. Another item
  * Unordered sub-list.
1. Actual numbers don't matter, just that it's a number
  1. Ordered sub-list
4. And another item.

   You can have properly indented paragraphs within list items. Notice the blank line above, and the leading spaces (at least one, but we'll use three here to also align the raw Markdown).

   To have a line break without a paragraph, you will need to use two trailing spaces.
   Note that this line is separate, but within the same paragraph.
   (This is contrary to the typical GFM line break behaviour, where trailing spaces are not required.)

* Unordered list can use asterisks
- Or minuses
+ Or pluses

<a name="links"/>
## Links

There are two ways to create links.

```no-highlight
[I'm an inline-style link](https://www.google.com)

[I'm an inline-style link with title](https://www.google.com "Google's Homepage")

[I'm a reference-style link][Arbitrary case-insensitive reference text]

[I'm a relative reference to a repository file](../blob/master/LICENSE)

[You can use numbers for reference-style link definitions][1]

Or leave it empty and use the [link text itself].

URLs and URLs in angle brackets will automatically get turned into links.
http://www.example.com or <http://www.example.com> and sometimes
example.com (but not on Github, for example).

Some text to show that the reference links can follow later.

[arbitrary case-insensitive reference text]: https://www.mozilla.org
[1]: http://slashdot.org
[link text itself]: http://www.reddit.com
```

[I'm an inline-style link](https://www.google.com)

[I'm an inline-style link with title](https://www.google.com "Google's Homepage")

[I'm a reference-style link][Arbitrary case-insensitive reference text]

[I'm a relative reference to a repository file](../blob/master/LICENSE)

[You can use numbers for reference-style link definitions][1]

Or leave it empty and use the [link text itself].

URLs and URLs in angle brackets will automatically get turned into links.
http://www.example.com or <http://www.example.com> and sometimes
example.com (but not on Github, for example).

Some text to show that the reference links can follow later.

[arbitrary case-insensitive reference text]: https://www.mozilla.org
[1]: http://slashdot.org
[link text itself]: http://www.reddit.com

<a name="images"/>
## Images

```no-highlight
Here's our logo (hover to see the title text):

Inline-style:
![alt text](https://github.com/adam-p/markdown-here/raw/master/src/common/images/icon48.png "Logo Title Text 1")

Reference-style:
![alt text][logo]

[logo]: https://github.com/adam-p/markdown-here/raw/master/src/common/images/icon48.png "Logo Title Text 2"
```

Here's our logo (hover to see the title text):

Inline-style:
![alt text](https://github.com/adam-p/markdown-here/raw/master/src/common/images/icon48.png "Logo Title Text 1")

Reference-style:
![alt text][logo]

[logo]: https://github.com/adam-p/markdown-here/raw/master/src/common/images/icon48.png "Logo Title Text 2"

<a name="code"/>
## Code and Syntax Highlighting

Code blocks are part of the Markdown spec, but syntax highlighting isn't. However, many renderers -- like Github's and *Markdown Here* -- support syntax highlighting. Which languages are supported and how those language names should be written will vary from renderer to renderer. *Markdown Here* supports highlighting for dozens of languages (and not-really-languages, like diffs and HTTP headers); to see the complete list, and how to write the language names, see the [highlight.js demo page](http://softwaremaniacs.org/media/soft/highlight/test.html).

```no-highlight
Inline `code` has `back-ticks around` it.
```

Inline `code` has `back-ticks around` it.

Blocks of code are either fenced by lines with three back-ticks <code>```</code>, or are indented with four spaces. I recommend only using the fenced code blocks -- they're easier and only they support syntax highlighting.

<pre lang="no-highlight"><code>```javascript
var s = "JavaScript syntax highlighting";
alert(s);
```

```python
s = "Python syntax highlighting"
print s
```

```
No language indicated, so no syntax highlighting.
But let's throw in a &lt;b&gt;tag&lt;/b&gt;.
```
</code></pre>



```javascript
var s = "JavaScript syntax highlighting";
alert(s);
```

```python
s = "Python syntax highlighting"
print s
```

```
No language indicated, so no syntax highlighting in Markdown Here (varies on Github).
But let's throw in a <b>tag</b>.
```


<a name="tables"/>
## Tables

Tables aren't part of the core Markdown spec, but they are part of GFM and *Markdown Here* supports them. They are an easy way of adding tables to your email -- a task that would otherwise require copy-pasting from another application.

```no-highlight
Colons can be used to align columns.

| Tables        | Are           | Cool  |
| ------------- |:-------------:| -----:|
| col 3 is      | right-aligned | $1600 |
| col 2 is      | centered      |   $12 |
| zebra stripes | are neat      |    $1 |

There must be at least 3 dashes separating each header cell.
The outer pipes (|) are optional, and you don't need to make the
raw Markdown line up prettily. You can also use inline Markdown.

Markdown | Less | Pretty
--- | --- | ---
*Still* | `renders` | **nicely**
1 | 2 | 3
```

Colons can be used to align columns.

| Tables        | Are           | Cool |
| ------------- |:-------------:| -----:|
| col 3 is      | right-aligned | $1600 |
| col 2 is      | centered      |   $12 |
| zebra stripes | are neat      |    $1 |

There must be at least 3 dashes separating each header cell. The outer pipes (|) are optional, and you don't need to make the raw Markdown line up prettily. You can also use inline Markdown.

Markdown | Less | Pretty
--- | --- | ---
*Still* | `renders` | **nicely**
1 | 2 | 3

<a name="blockquotes"/>
## Blockquotes

```no-highlight
> Blockquotes are very handy in email to emulate reply text.
> This line is part of the same quote.

Quote break.

> This is a very long line that will still be quoted properly when it wraps. Oh boy let's keep writing to make sure this is long enough to actually wrap for everyone. Oh, you can *put* **Markdown** into a blockquote.
```

> Blockquotes are very handy in email to emulate reply text.
> This line is part of the same quote.

Quote break.

> This is a very long line that will still be quoted properly when it wraps. Oh boy let's keep writing to make sure this is long enough to actually wrap for everyone. Oh, you can *put* **Markdown** into a blockquote.

<a name="html"/>
## Inline HTML

You can also use raw HTML in your Markdown, and it'll mostly work pretty well.

```no-highlight
<dl>
  <dt>Definition list</dt>
  <dd>Is something people use sometimes.</dd>

  <dt>Markdown in HTML</dt>
  <dd>Does *not* work **very** well. Use HTML <em>tags</em>.</dd>
</dl>
```

<dl>
  <dt>Definition list</dt>
  <dd>Is something people use sometimes.</dd>

  <dt>Markdown in HTML</dt>
  <dd>Does *not* work **very** well. Use HTML <em>tags</em>.</dd>
</dl>

<a name="hr"/>
## Horizontal Rule

```
Three or more...

---

Hyphens

***

Asterisks

___

Underscores
```

Three or more...

---

Hyphens

***

Asterisks

___

Underscores

<a name="lines"/>
## Line Breaks

My basic recommendation for learning how line breaks work is to experiment and discover -- hit &lt;Enter&gt; once (i.e., insert one newline), then hit it twice (i.e., insert two newlines), see what happens. You'll soon learn to get what you want. "Markdown Toggle" is your friend.

Here are some things to try out:

```
Here's a line for us to start with.

This line is separated from the one above by two newlines, so it will be a *separate paragraph*.

This line is also a separate paragraph, but...
This line is only separated by a single newline, so it's a separate line in the *same paragraph*.
```

Here's a line for us to start with.

This line is separated from the one above by two newlines, so it will be a *separate paragraph*.

This line is also begins a separate paragraph, but...
This line is only separated by a single newline, so it's a separate line in the *same paragraph*.

(Technical note: *Markdown Here* uses GFM line breaks, so there's no need to use MD's two-space line breaks.)

<a name="videos"/>
## Youtube videos

They can't be added directly but you can add an image with a link to the video like this:

```no-highlight
<a href="http://www.youtube.com/watch?feature=player_embedded&v=YOUTUBE_VIDEO_ID_HERE
" target="_blank"><img src="http://img.youtube.com/vi/YOUTUBE_VIDEO_ID_HERE/0.jpg"
alt="IMAGE ALT TEXT HERE" width="240" height="180" border="10" /></a>
```

Or, in pure Markdown, but losing the image sizing and border:

```no-highlight
[![IMAGE ALT TEXT HERE](http://img.youtube.com/vi/YOUTUBE_VIDEO_ID_HERE/0.jpg)](http://www.youtube.com/watch?v=YOUTUBE_VIDEO_ID_HERE)
```

Referencing a bug by #bugID in your git commit links it to the slip. For example #1.

---

License: [CC-BY](https://creativecommons.org/licenses/by/3.0/)
