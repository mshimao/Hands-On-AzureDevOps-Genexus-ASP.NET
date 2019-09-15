# Atividade 04

Nesta atividade vamos subir os programas Genexus para o Azure Repos usando o Git for Windows.

### Instalação do Git for Windows

Usaremos o Git for Windows para interagirmos com o Azure Repos, acesse o link abaixo para realizar o download. 

- [Download do Git for Windows](https://git-scm.com/download/win)

Após a instalação do Git, vamos usá-lo para iniciar um repositório no diretório da KB Genexus. Para isso abra o Git CMD.

![git cmd](../imagens/git1.png)

Vamos criar um novo repositório, para isso usando o Git CMD, ir até o diretório do environment .NET. Posicionado no diretório do environment .NET, vamos digitar o comando **git init** para inicializar o repositório Git.

![git new](../imagens/git2.png)

Crie um arquivo chamado **.gitignore** no diretório web do environment .NET.

![git ignoore](../imagens/git4.png)

Digite o seguinte conteúdo: 

```bash
*.cs
*.rsp
**/PrivateTempStorage
**/PublicTempStorage
```

![git ignoore](../imagens/git5.png)

Essas linhas vão fazer com que os arquivos com extensão **cs** e **rsp**, e o conteúdo das pastas **PrivateTempStorage** e **PublicTempStorage** sejam ignoradas pelo Git e não sejam armazenadas.

- [Mais informações gitignore](https://git-scm.com/docs/gitignore)

Vamos adicionar os arquivos ao repositório usando o comando:

```bash
git add *.*
```

![git add](../imagens/git6.png)

Vamos executar o comando commit para que os arquivos sejam armazenados no repositório.

```bash
git commit -m 'inicio'
```

![git add](../imagens/git7.png)

Neste momento os arquivos estão armazenados no repositório local, agora vamos conectar com o Azure Repos e enviar os arquivos para lá. Para isso acesse a instância do Azure DevOps criada anteriormente.

![azure repos](../imagens/azurerepos1.png)



Agora vamos criar o token de autenticação para que o Git acesse o Azure Repos. Para isso, clicar no icone do avatar no canto superior direito e na opção **Azure DevOps profile**.

![devops profile](../imagens/token1.png)

Clicar na opção **Personal access tokens** e depois em **New Token**.

![new token](../imagens/token2.png)

Informar no campo **Name** o valor **token full** e selecionar o item **Full access** e clicar em **Create**.

![token full](../imagens/token3.png)

Copie o token e cole num arquivo texto para ser utilizado posteriormente, e feche a tela.

![copy token](../imagens/token4.png)

Clicar no icone do Azure DevOps no canto superior esquerdo da tela para retornar a tela inicial.

Clicar no botão **+ New project** para criar um novo projeto. No campo **Project Name** digite **HandsOnDevOps** e cliquem em **Create**.

![new project azure repos](../imagens/azurerepos2.png)

Clicar na opção **Repos**, e copiar os comandos da seção **or push an existing repository from command line**.

![azure repos remote](../imagens/azurerepos3.png)

E cole os comandos na janela do Git CMD, e informe no campo senha cole o token gerado anteriormente.

![azure repos remote 2](../imagens/azurerepos4.png)

![git push](../imagens/git8.png)

Atualize a tela do browser, e verá que os arquivos agora estão no repositório do Azure.

![azure repos remote 3](../imagens/azurerepos5.png)

- [Mais informações sobre o Git](https://git-scm.com/doc)

Próxima atividade: [Atividade 05](05-atividade.md)