# Atividade 01

Criação do grupo de recursos, criação da máquina virtual com SQL Server e configuração da aplicação Genexus.

## Criação do grupo de recursos

Entrar no portal do Azure https://portal.azure.com, clicar no item **Grupo de recursos**.

O grupo de recursos é uma forma de organizar os itens do Azure dentro de um "grupo" para facilitar a identificação dos elementos e também facilita o gerenciamento dos custos.

![Grupo de recursos](../imagens/gruporecursos.png)

Clicar em **Adicionar**.

![Grupo de recursos](../imagens/gruporecursos2.png)

Preencher o campo **Grupo de recursos** com o texto "HandsOnDevOps" e clicar em **Revisar + criar**.

![Grupo de recursos](../imagens/gruporecursos3.png)

Preencher clicar em **Criar**.

![Grupo de recursos](../imagens/gruporecursos4.png)

Após a criação do grupo, clicar em **Ir para o grupo de recursos**.

![Grupo de recursos](../imagens/gruporecursos5.png)

## Criação da Máquina Virtual

Na tela do grupo de recursos, clicar em **Adicionar**.

![VM](../imagens/vm1.png)

No campo de pesquisa digitar **Windows Server** e clicar no item **Windows Server**.

![VM](../imagens/vm2.png)

Selecionar o item **Windows Server 2012 Datacenter** e clicar em **Criar**.

![VM](../imagens/vm3.png)

Preencher o campo **Nome da máquina virtual** com o texto **servidorweb**. E clicar em **Alterar tamanho** para selecionar o tamanho da VM.

![VM](../imagens/vm4.png)

Selecionar o tamanho **D2_v3** que é uma VM com 2 cores e 8 GB de RAM. Clicar em **Selecionar** para confirmar a seleção.

![VM](../imagens/vm5.png)

Preencher o campo **Nome de usuário** com o texto **adminweb** e o campo **Senha** com **Adminhandson2019**. 
Selecione o item **Permitir portas selecionadas** e no combo **Selecione as portas de entrada** selecione o item **RDP**. 
Clique em **Revisar + criar**.

![VM](../imagens/vm6.png)

Confirmar a criação da VM clicando em **Criar**.

![VM](../imagens/vm7.png)

Após a conclusão da implantação da VM, clicar em **Ir para o recurso**.

![VM](../imagens/vm8.png)

## Instalação do Chrome 

Para facilitar o acesso ao Azure DevOps vamos instalar o Chrome na VM.

Na tela da máquina virtual, clicar na opção **Conectar**.

![IIS](../imagens/sqliis1.png)

Clicar em **Baixar Arquivo RDP** para fazer o download do arquivo RDP para conectar a VM.

![IIS](../imagens/sqliis2.png)

Clicar no arquivo **servidorweb.rdp**.

![IIS](../imagens/sqliis3.png)

Informar o usuário **adminweb** e senha **Adminhandson2019** para conectar.

![IIS](../imagens/sqliis4.png)

Inicialmente é necessário desabilitar o recurso **IE Enhanced Security Configuration**. Clique no texto **On**.

![IE security](../imagens/chrome1.png)

Selecione as opções **Off** e clique em **OK**.

Depois abra o Internet Explorer e faça o download e instalação do Chrome pela URL https://www.google.com/intl/pt-BR/chrome/.


## Instalação do SQL Server Express e configuração do IIS

Agora vamos configurar o IIS, para isso clique na opção **Add roles and features** da tela do Server Manager.

![IIS](../imagens/sqliis5.png)

Clicar no botão **Next**.

![IIS](../imagens/sqliis6.png)

Clicar no botão **Next**.

![IIS](../imagens/sqliis7.png)

Clicar no botão **Next**.

![IIS](../imagens/sqliis8.png)

Selecionar os itens **Application Server** e **Web Server(IIS)**. Na tela de popup clicar em **Add Features**. E clicar no botão **Next**.

![IIS](../imagens/sqliis9.png)

Selecionar o item **ASP.NET 4.5** dentro do item **.NET Framework 4.5 Features**.

![IIS](../imagens/sqliis10.png)

Selecionar o item **WinRM IIS Extension** e clicar no botão **Add Features** na tela de popup. E clicar em Next.

![IIS](../imagens/sqliis11.png)

Clicar no botão **Next**.

![IIS](../imagens/sqliis12.png)

Selecionar o item **Web Server (IIS) Support** e e clicar no botão **Add Features** na tela de popup. E clicar em Next.

![IIS](../imagens/sqliis13.png)

Clicar no botão **Next**.

![IIS](../imagens/sqliis14.png)

Clicar no botão **Next**.

![IIS](../imagens/sqliis15.png)

Clicar no botão **Install**.

![IIS](../imagens/sqliis16.png)

Após a instalação terminar, clicar no botão **Close**.

![IIS](../imagens/sqliis17.png)

Para realizar o download do SQL Server 2016 Express e o  SQL Management, abrir o browser, e digitar a URL https://www.hanselman.com/blog/DownloadSQLServerExpress.aspx.

![IIS](../imagens/sqliis18.png)

Executar o setup do SQL Server clicando no SQLEXPR_X64_ENU.exe. Selecione a opção **New SQL Server ...** 

![IIS](../imagens/sqliis19.png)

Realize o setup padrão do SQL Server. 

![IIS](../imagens/sqliis20.png)

![IIS](../imagens/sqliis21.png)

![IIS](../imagens/sqliis22.png)

![IIS](../imagens/sqliis23.png)

![IIS](../imagens/sqliis24.png)

![IIS](../imagens/sqliis25.png)

Selecionar o modo de autenticação **Mixed Mode** e informar a senha **sa!2016**. E clicar no botão **Next**.

![IIS](../imagens/sqliis26.png)

![IIS](../imagens/sqliis27.png)

Agora vamos instalar o SQL Management Studio executando o programa **SSMS-setup-ENU.exe**.

![IIS](../imagens/sqliis28.png)

Ao finalizar a instalação, clicar na opção de **Restart**.

![IIS](../imagens/sqliis29.png)

## Configuração do Firewall 

Para configurar o firewall para permitir o acesso ao IIS, temos que acessar a opção Rede da VM no portal do Azure e clicar na opção **Adicionar regra da porta de entrada**.

![IIS](../imagens/firewall.png)

Informar no campo **Intervalo de porta de destino** o valor **80** e no campo **Nome** o texto **Port_80**, e clicar em **Adicionar**.

![IIS](../imagens/firewall2.png)

Com isso o IIS está acessível, para testar, vá até o painel da VM e copie o IP da VM, e abra o browser e digite o endereço.

![IIS](../imagens/firewall3.png)

Próxima atividade: [Atividade 02](02-atividade.md)
