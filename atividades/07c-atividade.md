# Atividade 07 - Executando scripts de migration do .NET Core 

Nesta atividade tente configurar o pipeline de release para executar os migrations do .NET Core.

Siga os seguintes passos:
- Gere o script sql usando o **dotnet ef**
- Armazene o script sql no Azure Repos
- Altere o pipeline de Build para gerar o artefato do script sql
- Altere o pipeline de Release para executar o script usando o **SQL Server PowerShell module** numa task Powershell.


Links utéis para a atividade:

- [Comandos do dotnet ef](https://docs.microsoft.com/en-us/ef/core/miscellaneous/cli/dotnet#common-options)

- [Install SQL Server PowerShell module](https://docs.microsoft.com/pt-br/sql/powershell/download-sql-server-ps-module?view=sql-server-2017)

- [Invoke-Sqlcmd](https://docs.microsoft.com/pt-br/powershell/module/sqlserver/Invoke-Sqlcmd?view=sqlserver-ps)
