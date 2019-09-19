# Atividade 05 - Build do projeto ASP.NET Core

Nesta atividade iremos configurar um pipeline de build para gerar os artefatos que serão utilizados para o deploy.

### Pipeline Build

Criaremos um pipeline que buscará os arquivos no repositório do Azure Repos, fará a geração de um arquivo zip e subir o arquivo como artefato para o Azure Pipeline.

Acessar o Azure DevOps e abrir o projeto HandsOnDevOpsNETCore. Clicar na opção **Pipelines**, clicar em **Builds** e depois na opção **New pipeline**.

![new pipeline](../imagens/buildcore1.png)

Clicar em **Azure Repos Git YAML**.

![classic editor](../imagens/buildcore2.png)

Clique em **HandsOnDevOpsNETCore**.

![source](../imagens/buildcore3.png)

Clique em **Show more**.

![Show more](../imagens/buildcore4.png)

Selecionar o item **ASP.NET Core**.

![ASP.NET Core](../imagens/buildcore5.png)

Clicar em **Save and run**.

![Save and run](../imagens/buildcore6.png)

Deixar o item **Commit directly to the master branch.** selecionado e clicar novamente em **Save and run**.

![Save and run](../imagens/buildcore7.png)

O processamento irá gerar um erro devido ao fato da ausência do SDK .NET Core compatível com o projeto.

![erro](../imagens/buildcore8.png)

Clicar no item **Builds** do menu lateral e clicar em **Edit**.

![builds](../imagens/buildcore9.png)

No campo de pesquisa digitar **Use .NET** e selecione o item **Use .NET Core**.

![Use .NET](../imagens/buildcore10.png)

No campo **Version** informar **3.0.100-rc1-014190**, acrescente linhas abaixo do texto **steps**, posicione o cursor como na imagem e clicar me **Add**.

![sdk version](../imagens/buildcore11.png)

Clicar em **Save** e novamente em **Save** na próxima tela.

![salvar](../imagens/buildcore12.png)

Como a trigger de push de codigo está ativo, o build vai ser disparado ao salvar o a configuração do pipeline. Clicar em **Builds** e depois no pipeline para ver os detalhes.

![build 2](../imagens/buildcore13.png)

Clique em **Summary**.

![Summary](../imagens/buildcore14.png)

Veja que nenhum artefato foi gerado pelo Build, isso ocorreu porque está faltando uma tarefa após o build para fazer upload dos artefatos gerados. 

![sem artefato](../imagens/buildcore15.png)

Clique em **Builds** e depois em **Edit** para abrirmos o pipeline para edição, vamos incluir uma task para realizar o publish do .NET Core e gerar um zip, e a uma task para fazer o upload do zip gerado.
Adicionar o código abaixo no final do pipeline e salvar o yaml.

```yaml
- task: DotNetCoreCLI@2
  inputs:
    command: 'publish'
    publishWebProjects: true
    arguments: '--configuration $(BuildConfiguration) --output $(Build.ArtifactStagingDirectory) --self-contained --runtime win10-x64'
    zipAfterPublish: True

- task: PublishBuildArtifacts@1
  inputs:
    PathtoPublish: '$(Build.ArtifactStagingDirectory)'
    ArtifactName: 'drop'
    publishLocation: 'Container'
```

![publish](../imagens/buildcore16.png)

Clicar em **Builds** e no item em execução para acompanhar o build. No final do processo será possível verificar que desta vez o artefato foi gerado.

![artefato](../imagens/buildcore17.png)

Clique em **Artifacts** e clique em **Drop** para realizar o download do zip, e veja que os arquivos da aplicação estão dentro do zip.

![drop](../imagens/buildcore18.png)

![drop](../imagens/buildcore19.png)

Próxima atividade: [Atividade 06](06-atividade.md)