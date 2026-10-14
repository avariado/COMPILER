EPUBOOKOBO — PROJETO ANDROID NATIVO
===================================

Objetivo
--------
Leitor EPUB Android nativo inspirado no script epubookobo.py, preparado como
projeto Gradle Android existente para compilação pelo apkompiler_git.

Funcionalidades
---------------
- Abertura de EPUB através do chooser Android.
- Aceita igualmente EPUBs enviados/abertos a partir de outras apps.
- Leitura do META-INF/container.xml, OPF, spine e índices EPUB 2/EPUB 3.
- Preservação estrutural de parágrafos, blocos, text-indent, margens CSS e
  formatação integral de blocos em negrito/itálico quando aplicável.
- Títulos de capítulos sem duplicação do título no corpo.
- Paginação nativa adaptada ao ecrã e justificação de texto.
- Cabeçalho por capítulo e rodapé com percentagem lida.
- Toque no terço esquerdo/direito para página anterior/seguinte.
- Swipe da direita para a esquerda para página seguinte e da esquerda para a
  direita para página anterior.
- Ajuste vertical contínuo de luminosidade: ao deslocar o dedo para cima/baixo,
  a luminosidade aumenta/reduz em tempo real, em passos de 1%, com indicação
  percentual ao centro; sem alterar a luminosidade global do sistema.
- Toque longo numa palavra, com arrastamento, para selecionar uma ou várias
  palavras; menu contextual com Copiar, Pesquisar no Google e Partilhar com aplicações do sistema.
- Toque no centro para progresso e opções.
- Toque na zona superior central para navegação por capítulos.
- Menu Leitura com:
    tamanho da letra: 10–28 (padrão 18)
    espaçamento: 1,10–2,20 (padrão 1,40)
    margens laterais: 8–80 dp (padrão 20 dp)
    temperatura do fundo: 0–100% (padrão 50%)
- Persistência manual de progresso e preferências em epubookobo.json no
  armazenamento privado da aplicação.
- A área de leitura respeita o inset superior/display cutout para evitar que o
  cabeçalho fique tapado pela câmara frontal.
- Confirmação antes de sair.
- Teclado físico:
    ← / →                mudar página
    Shift + ↑ / ↓        tamanho da letra
    Ctrl + ↑ / ↓         espaçamento
    Enter                 progresso/opções
    Espaço                capítulos

Seleção de ficheiros
--------------------
A app usa ACTION_GET_CONTENT diretamente. Desta forma, o Android pode apresentar
no próprio fluxo «Abrir de» as fontes e gestores de ficheiros instalados que
anunciem capacidade para fornecer conteúdo. ACTION_OPEN_DOCUMENT é usado apenas
como fallback em dispositivos sem handler para ACTION_GET_CONTENT.

Compilar com apkompiler_git
---------------------------
1. Abrir apkompiler_git.
2. Selecionar esta pasta como pasta do projeto.
3. Manter assinalado:
      "Compilar projeto Android existente (não alterar Gradle/Manifest/recursos)"
4. Confirmar JAVA_HOME e Android SDK.
5. Selecionar "Release (assinado)".
6. Ativar "Usar assinatura personalizada (keystore)".
7. Escolher o .jks/.keystore e preencher alias e palavras-passe.
8. Premir "Compilar APK".

O projeto contém signingConfigs compatível com o comportamento do
apkompiler_git: quando este cria keystore.jks e keystore.properties na raiz, o
build Release usa automaticamente essa assinatura.

Configuração Android
--------------------
Package:     com.epubookobo.reader
Version:     1.13 (versionCode 14)
Min SDK:     21
Target SDK:  35
Compile SDK: 35
Java:        17
AGP:         8.2.1

Notas
-----
- Não existem rotinas de migração nem perfis de compatibilidade com versões
  anteriores da própria app. O formato atual é tratado como o formato inicial.
- Não são necessárias permissões gerais de armazenamento.
- O projeto não inclui keystore nem palavras-passe.
- Não inclui Gradle Wrapper, para o apkompiler_git usar a instalação Gradle que
  já procura no computador.
