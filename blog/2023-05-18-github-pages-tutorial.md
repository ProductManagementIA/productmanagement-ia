---
slug: github pages
title: Como criar uma página web utilizando docusaurus e hospedar no Github Pages!
authors:
  - name: Roger Silva
    title: Product Manager
    url: https://github.com/roger8b
    image_url: https://avatars.githubusercontent.com/u/20045773?v=4
tags: [github pages]
---

Se você está procurando criar uma página web para o seu projeto ou negócio, o Docusaurus é uma ótima opção para criar documentação e páginas web estáticas. Neste artigo, vamos guiá-lo passo a passo no processo de criação de uma página web utilizando o Docusaurus e hospedando-a no Github Pages.
<!-- truncate -->
## Passo 1: Criar um repositório no Github

O primeiro passo é criar um repositório com o nome do seu projeto no Github. Este repositório será usado para hospedar a sua página web.

## Passo 2: Criar um projeto do Docusaurus

O próximo passo é criar um projeto do Docusaurus. Você pode fazer isso executando o seguinte comando no seu terminal:

```
npx create-docusaurus@latest my-website classic

```

Substitua `my-website` pelo nome do seu projeto.

## Passo 3: Configurar o projeto

Agora, abra o arquivo `docusaurus.config.js` no seu editor de código favorito. Você precisará atualizar algumas configurações para que o Docusaurus possa ser construído corretamente.

- url: `http://github.com`
- baseUrl: `/my-website/`
- deploymentBranch: `gh-pages`
- organization: `my-organization`
- projectName: `my-website`

Substitua `my-website` pelo nome do seu projeto e `my-organization` pelo nome da sua organização.

## Passo 4: Adicionar e enviar para o Github

Agora você precisará adicionar todos os arquivos ao git e fazer o commit. Execute os seguintes comandos no seu terminal:

```
git init
git add .
git commit -m 'first commit'
git branch -M main
git remote add origin <https://github.com/my-username/my-website.git>
export USE_SSH=true
GIT_USER=my-username yarn deploy

```

Substitua `my-username` pelo seu nome de usuário do Github e `my-website` pelo nome do seu projeto.

## Passo 5: Configurar o Github Actions

O Github Actions é o serviço de integração contínua do Github e é usado para automatizar o processo de implantação da sua página web. Para começar, crie uma pasta `.github` no diretório raiz do seu projeto. Em seguida, crie uma pasta `workflows` dentro da pasta `.github`. Crie um arquivo chamado `deploy.yml` dentro da pasta `workflows`. Em seguida, copie o conteúdo do seguinte endereço: [https://docusaurus.io/docs/deployment#triggering-deployment-with-github-actions](https://docusaurus.io/docs/deployment#triggering-deployment-with-github-actions) e cole-o no arquivo `deploy.yml`.

## Passo 6: Publicar a página web

Agora você está pronto para publicar a sua página web. Para fazer isso, execute o seguinte comando no seu terminal:

```
GIT_USER=my-username yarn deploy

```

Substitua `my-username` pelo seu nome de usuário do Github.

## Passo 7: Configurar o domínio personalizado

Se você quiser usar um domínio personalizado para a sua página web, precisará configurar os registros DNS para apontar para o Github Pages. Acesse o seguinte endereço: [https://docs.github.com/pt/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site#configuring-an-apex-domain](https://docs.github.com/pt/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site#configuring-an-apex-domain) para obter as informações necessárias para configurar os registros APEX.

No Google Domain, configure os Resource Records da seguinte maneira:

1. Host Name: `@`
    - Type: A
    - TTL: 3600
    - Data:
        - `185.199.108.153`
        - `185.199.109.153`
        - `185.199.110.153`
        - `185.199.111.153`
2. Host Name: `www`
    - Type: CNAME
    - TTL: 3600
    - Data: `[my-username.github.io](http://my-username.github.io/)`

Substitua `my-username` pelo seu nome de usuário do Github.

Em seguida, crie um arquivo chamado `CNAME` no diretório raiz do seu projeto e adicione o endereço do seu domínio, por exemplo `www.my-website.com`. Isso evitará que você perca o domínio sempre que fizer deploy. Em `docusaurus.config.js`, deixe a configuração `baseUrl` como `/`. Faça o commit e envie as alterações para o Github.

Por fim, vá para as configurações do seu repositório no Github, clique em "Pages", adicione o seu endereço personalizado e salve.

Parabéns! Você agora tem uma página web estática hospedada no Github Pages.