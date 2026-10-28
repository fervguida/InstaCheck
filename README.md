<p align="center">
  <img src="docs/logo.png" alt="Logo do InstaCheck" width="140">
</p>

<h1 align="center">InstaCheck</h1>

<p align="center">Aplicativo para descobrir <strong>quem você segue no Instagram e não te segue de volta</strong>, usando os dados que o próprio Instagram permite você baixar. Funciona direto no navegador ou como app Android (APK).</p>

- **Sem login e sem senha.** O app nunca acessa a sua conta.
- **100% local.** Os arquivos são lidos no seu aparelho e nada é enviado para a internet.
- **Funciona offline** depois de instalado.

> Projeto independente, sem ligação com o Instagram ou a Meta.

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

## Gerar o APK (Android)

O projeto usa o [Capacitor](https://capacitorjs.com/) e o GitHub Actions compila o APK automaticamente.

1. Envie todos os arquivos deste projeto para um repositório no GitHub (inclusive a pasta `.github`).
2. Abra a aba **Actions** > **Build APK** > **Run workflow**.
3. Quando terminar (5 a 10 minutos), baixe **InstaCheck-apk** em *Artifacts*.
4. Descompacte, envie o `app-debug.apk` para o celular e instale, permitindo instalar de fontes desconhecidas.

O APK gerado é de teste (debug). Para publicar na Play Store, é preciso assinar um APK de lançamento.

## Estrutura

```
www/index.html        o app (HTML, CSS e JavaScript)
www/assets/           estilos e fontes locais
assets/               ícone e tela de abertura
capacitor.config.json configuração do app Android
.github/workflows/    compilação automática do APK
```

## Limitações

- O app não consegue saber sozinho quais contas foram apagadas; por isso existem as opções do passo 3.
- Os dados são uma foto do momento em que você pediu a exportação ao Instagram. Quem você seguiu ou deixou de seguir depois não aparece.
