# Atividade 06

Nesta atividade iremos configurar um pipeline de release para implantar os programas Genexus.

### Pipeline Release

Criaremos um pipeline que buscará o artefato no Azure Pipeline, fará a extração do arquivo zip e cópia para o diretório do IIS.

Acessar o Azure DevOps e abrir o projeto HandsOnDevOps. Clicar na opção **Pipelines**, depois na opção **Releases** e depois na opção **New pipeline**.

![new pipeline](../imagens/release1.png)

Clicar na opção **Empty job**.

![empty](../imagens/release2.png)

Preencher o campo **Stage name** com **QA**.

![stage](../imagens/release3.png)

Clicar no texto **New release pipeline**, apagar o texto e digitar **Deploy QA**.

![stage](../imagens/release4.png)

Clicar em **Save** para salvar. Depois clicar no texto **+ Add** do box **Artifacts** para selecionar o artefato que será utilizado para a implantação.

![stage](../imagens/release5.png)

Selecione **Build** como **Source type**, configure as seguintes propridades e cliquem em **Add**.

| Campo | Valor | 
| --- | --- |
| Project | HandsOnDevOps |
| Source (build pipeline) | HandsOnDevOps-CI |
| Default version | Latest |
| Source alias | _HandsOnDevOps-CI |

![add artifact](../imagens/release6.png)

Clique no ícone de raio no box **Artifacts**.

![add trigger](../imagens/release7.png)

Habilitar o trigger para habilitar o deploy contínuo, dessa forma toda vez que um build terminar com sucesso, o deploy será realizado em seguida. Clicar no **X** para fechar a janela.

![cd](../imagens/release8.png)

Clicar no texto **1 job, 0 task** para abrir a tela de configuração das tasks.

![tasks](../imagens/release9.png)

Clicar no item **Agent job** e alterar o Agent pool para **Default**, com isso será usado o agente instalado anteriormente para execução do deploy.

![agent](../imagens/jobagent.png)

Clicar no **+** do item **Agent job**, digitar **extract** no campo de pesquisa, selecionar o item **Extract files** e clicar em **Add**.

![extract](../imagens/release10.png)

Clicar no item **Extract files** e editar as seguintes propriedades.

| Campo | Valor | 
| --- | --- |
| Display name | Extract files web |
| Archive file patterns | $(System.DefaultWorkingDirectory)/_HandsOnDevOps-CI/drop/web.zip |
| Destination folder | $(Agent.WorkFolder)/webzip |

![extract prop](../imagens/release11.png)

Nessa tarefa estamos descompactando o arquivo web.zip que foi baixado do Azure Pipelines para a VM do agente no diretório **_HandsOnDevOps-CI/drop**  e vai ser descompactado no diretório **webzip**.

Clicar no **+** do item **Agent job**, digitar **copy** no campo de pesquisa, selecionar o item **Copy files** e clicar em **Add**.

![copy](../imagens/release12.png)

Clicar no item **Copy files** e editar as seguintes propriedades.

| Campo | Valor | 
| --- | --- |
| Display name | Copy Files web |
| Source Folder | $(Agent.WorkFolder)/webzip/web |
| Contents | ** |
| Target Folder | c:\inetpub\wwwroot |

Marcar a opção **Overwrite**.

![copy prop](../imagens/release13.png)

Clicar em **Save** para salvar o pipeline.

![save](../imagens/release14.png)

Vamos configurar os direitos do usuário do agente para que ele possa copiar os arquivos, para isso vamos conectar na VM. 
Abrir o Explorer e clicar no botão direito na pasta c:\inetpub\wwwroot, e clicar em **Properties**.

![properties](../imagens/seguranca1.png)

Clicar na aba **Security** e clicar em **Edit**.

![properties 2](../imagens/seguranca2.png)

Clicar em **Add**.

![properties 3](../imagens/seguranca3.png)

Clicar em **Advanced**.

![properties 4](../imagens/seguranca4.png)

Clicar em **Find Now** e ir até o final da lista e selecionar o item **VSTS_Agent...**.

![properties 5](../imagens/seguranca5.png)

Clicar em **OK** para confirmar a seleção do usuário.

![properties 6](../imagens/seguranca6.png)

Marcar o item **Full control** e clicar me **OK**. E **OK** na próxima tela.

![properties 7](../imagens/seguranca7.png)

Abrir o Azure Pipelines, clicar em **Create release**.

![create](../imagens/release15.png)

Clicar em **Create**.

![create](../imagens/release16.png)

Clicar em **Release-1**.

![release1](../imagens/release17.png)

Podemos ver o log clicando no texto **Succeeded**.

![release1](../imagens/release18.png)

![release1](../imagens/release19.png)

Próxima atividade: [Atividade 07](07-atividade.md)



