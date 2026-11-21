DINNOEMULATOR — MVP Loja DINNOREX
================================

O QUE ESTA VERSÃO FAZ
- Interface da loja DINNOREX.
- Login Google preparado com Firebase.
- Conta administradora reservada a wilsonmiguel906@gmail.com.
- Painel de publicação para administrador.
- Publicação de jogos HTML em arquivo único (HTML + CSS/JS embutidos).
- Loja online via Firebase Firestore + Storage.
- Download para biblioteca local do dispositivo.
- Execução de jogos HTML dentro do app por iframe.
- Modo de teste local para experimentar publicação/download sem Firebase.

IMPORTANTE
Este ZIP é código-fonte. Não é APK nem EXE compilado. O ambiente de criação não tem Android SDK/Gradle/assinatura para gerar o APK aqui.

CONFIGURAÇÃO OBRIGATÓRIA PARA LOJA ONLINE
1. Crie projeto em https://console.firebase.google.com/
2. Registre app Web e copie as credenciais para firebaseConfig em www/index.html.
3. Ative Authentication > Google.
4. Crie Firestore Database e Storage.
5. Configure regras de segurança: apenas wilsonmiguel906@gmail.com pode criar/alterar/apagar documentos em games e fazer upload em Storage; usuários autenticados podem ler e baixar. Não use regras abertas em produção.
6. Configure domínios autorizados no Firebase.
7. A conta wilsonmiguel906@gmail.com deve ser uma conta Google válida e fazer login normalmente.

PUBLICAR JOGOS
- Entrar com a conta administradora.
- Abrir Painel admin.
- Preencher título/descrição, capa opcional e arquivo .html.
- Publicar. O jogo aparece na loja online.
- Usuários entram com Google, baixam e o jogo fica na biblioteca local do dispositivo.

FORMATO DE JOGOS NESTA PRIMEIRA VERSÃO
- Aceita jogos HTML de arquivo único (HTML com CSS/JS e recursos embutidos).
- Jogos HTML que dependem de uma pasta de imagens/sons ou múltiplos arquivos ainda precisam de empacotador ZIP e atualização do carregador.
- APK/EXE são formatos de instalação do próprio DINNOEMULATOR nesta arquitetura, não o formato de jogo publicado na loja.
- O emulador de consoles (PS1, PSP, Nintendo etc.) ainda não está integrado; esta versão executa jogos HTML.

TESTE RÁPIDO
1. Extraia o ZIP.
2. Abra www/index.html num navegador moderno com internet.
3. Clique em “Entrar com Google” (sem Firebase, use “Entrar em modo de teste local”).
4. No modo de teste, o painel de publicação fica liberado para simular o fluxo; publique um arquivo .html e depois baixe-o da loja para Meus Jogos.
Observação: modo de teste é local, não publica para outros usuários.

GERAR APK
npm install
npx cap add android
npx cap sync android
npx cap open android
No Android Studio: Build > Build APK(s).

GERAR EXE WINDOWS
npm install
npm run build:windows
(O pacote Electron deve estar instalado e configurado; veja package.json.)

PRIVACIDADE E SEGURANÇA
- Nunca armazene senha Google no app.
- Use Firebase Authentication.
- Proteja publicação por regras de Firebase, não apenas por esconder botões na interface.
- A biblioteca local usa localStorage nesta versão de demonstração; para jogos grandes e produção, migrar para IndexedDB/Filesystem e implementar gestão de espaço.
