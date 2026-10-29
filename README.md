<p align="center">
  <img src="docs/logo.png" alt="Logo do InstaCheck" width="140">
</p>

<h1 align="center">InstaCheck</h1>

<p align="center">Aplicativo para descobrir <strong>quem você segue no Instagram e não te segue de volta</strong>, usando os dados que o próprio Instagram permite você baixar. Disponível para Android, Windows e Linux.</p>

- **Sem login e sem senha.** O app nunca acessa a sua conta.
- **100% local.** Os arquivos são lidos no seu aparelho e nada é enviado para a internet.
- **Funciona offline** depois de instalado.

> Projeto independente, sem ligação com o Instagram ou a Meta.

## Baixar

Abra a aba **Releases** (na coluna da direita da página do repositório), escolha a versão mais recente (a marcada como *Latest*) e baixe o arquivo do seu aparelho. O `N` nos nomes é o número da versão:

| Sistema | Arquivo | Como instalar |
|---|---|---|
| Android | `InstaCheck.apk` | Envie para o celular, toque no arquivo e permita instalar de fontes desconhecidas |
| Windows (instalador) | `InstaCheck-Instalador-1.0.N.exe` | Execute e siga as telas |
| Windows (portátil) | `InstaCheck-Portatil-1.0.N.exe` | Execute direto, sem instalar |
| Linux | `InstaCheck-1.0.N.AppImage` | Dê permissão de execução (`chmod +x`) e abra |

> Os aplicativos não são assinados digitalmente. No Windows, se aparecer "O Windows protegeu o computador", clique em **Mais informações** e depois em **Executar assim mesmo**. No Android, se o Play Protect avisar, toque em **Instalar mesmo assim**.

## O que ele mostra

| Número | Significado |
|---|---|
| Seguidores | Quantas pessoas seguem você |
| Seguindo | Quantas pessoas você segue hoje |
| Não te seguem de volta | Pessoas que você segue e que não seguem você |
| Te seguem e você não segue | Seguidores seus que você não segue de volta |

Na lista de resultados você pode:
- alternar entre **"não me seguem de volta"** e **"me seguem e eu não sigo"** pelo botão acima da lista;
- ver desde quando você segue cada conta e ordenar por mais recentes, mais antigos ou A–Z;
- buscar um usuário, abrir o perfil dele e copiar a lista inteira.

## Como usar

### 1. Baixe os seus dados no Instagram
1. No Instagram, abra **Central de Contas** > **Suas informações e permissões** > **Baixar suas informações**.
2. Escolha apenas **Seguidores e seguindo** e o formato **JSON**.
3. Quando o Instagram avisar que está pronto, baixe e extraia o arquivo ZIP.

### 2. Carregue no app
- Em **Arquivo de SEGUIDORES**, escolha o `followers_1.json`. Se existirem `followers_2.json`, `followers_3.json`..., selecione todos de uma vez.
- Em **Arquivo de SEGUIDOS**, escolha o `following.json`.
- Clique em **Analisar Arquivos**.

Também dá para colar listas de usuários, um por linha, na aba **Copiar e Colar Texto**.

### 3. (Opcional) Deixar os números exatos
O arquivo do Instagram inclui contas apagadas ou desativadas, que o seu perfil não conta. Por isso o "seguindo" do arquivo pode ser maior que o do perfil. Para o app tirar essas contas, escolha uma opção:

- **Colar a sua lista atual de "Seguindo"** (computador): no Instagram abra Seguindo, role até o final, `Ctrl+A`, `Ctrl+C` e cole no campo do app. O app mostra quantas contas reconheceu.
- **Digitar o número de "seguindo" do seu perfil**: corrige os números dos cards, mas a lista continua com as contas que não existem mais. Dá para marcá-las com o botão **Não existe**.

Sem nenhuma das duas, o app funciona, mas mostra os números do arquivo.

## Apoie o projeto

O InstaCheck é grátis e de código aberto. Se ele te ajudou e você quiser retribuir, qualquer valor é bem-vindo, mas é totalmente opcional.

**[ko-fi.com/fervzeira](https://ko-fi.com/fervzeira)**

*If InstaCheck helped you, you can support it on [Ko-fi](https://ko-fi.com/fervzeira). Thank you!*

## Gerar as versões (para quem mantém o projeto)

O GitHub Actions compila tudo automaticamente:

- **Android (APK):** usa o [Capacitor](https://capacitorjs.com/).
- **Computador (Windows e Linux):** usa o [Electron](https://www.electronjs.org/) (pasta `desktop/`).

A cada envio de alterações para o repositório (branch `main`), o workflow `build-apk.yml` compila o APK e os apps de computador e cria sozinho uma release nova, com a versão seguinte (`v1.0.13`, `v1.0.14`...) e todos os arquivos dentro. Mudanças só em arquivos `.md` ou na pasta `docs` não geram release.

Também dá para compilar na mão: aba **Actions** > escolha o workflow > **Run workflow**. Os arquivos ficam em *Artifacts* no fim da execução.

### Rodar a versão de computador no seu PC

Com o [Node.js](https://nodejs.org/) instalado:

```
cd desktop
npm install
npm start
```

## Estrutura

```
www/index.html        o app, versão Android (HTML, CSS e JavaScript)
www/assets/           estilos e fontes locais
assets/               ícone e tela de abertura do Android
capacitor.config.json configuração do app Android
desktop/              versão de computador (Electron)
docs/logo.png         logo usado neste README
.github/workflows/    compilação automática (APK e computador)
```

## Limitações

- O app não consegue saber sozinho quais contas foram apagadas; por isso existem as opções do passo 3.
- Os dados são uma foto do momento em que você pediu a exportação ao Instagram. Quem você seguiu ou deixou de seguir depois não aparece.
