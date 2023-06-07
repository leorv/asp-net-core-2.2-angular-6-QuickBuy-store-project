# App de compras QuickBuy

Este é um projeto interessante que desenvolvi estudando C#, resultado de um curso de .NET Core 2.2.

Embora legado, resulta uma boa fonte de consulta e aprendizagem.

## Como rodar isso?

Primeiramente, clone este repositório para sua máquina.

```
git clone git@github.com:leorv/asp-net-core-2.2-angular-6-QuickBuy-store-project.git
```

Depois, entre na pasta `asp-net-core-2.2-angular-6-QuickBuy-store-project`, abra o terminal nela.

Digite:

```
dotnet run --project QuickBuy.Web 
```

**Se não possui o ambiente com as versões corretas, veja como fazer isso com as instruções que passo abaixo:**

## Instalando o Angular 6

Como é uma versão específica, recomendo o uso do nvm.

https://github.com/nvm-sh/nvm

No README.md dele tem as instruções para a instalação.

Node tem que ser maior que 8.11 e o npm tem que ser maior que 5.6.

Caso você tenha versões superiores do npm, node e do angular, acredito que funcionará também, pela questão do package.json especificar as versões.

## Download do .NET SDK

Programa necessário pra gente rodar nosso App.

https://dotnet.microsoft.com/en-us/download/dotnet/2.2


## Como instalar o .NET SDK qualquer versão no ambiente Linux?

Como trata-se de um projeto legado, vou colocar aqui um passo a passo para a instalação do SDK 2.2.0 que foi utilizado neste projeto.

Este passo a passo serve para as demais versões também. Porém, nas versão atuais pode-se usar o próprio gerenciador de pacotes para instalar. No caso do Debian, o apt.

Bom, vamos com a maneira manual por meio do script da Microsoft.

Baixar o script: https://learn.microsoft.com/pt-br/dotnet/core/runtime-discovery/troubleshoot-app-launch?pivots=os-linux
ou https://learn.microsoft.com/pt-br/dotnet/core/tools/dotnet-install-script#recommended-version

Depois, no diretório onde está baixado o script, podemos rodar:

```
./dotnet-install.sh --version 2.2.207 --verbose
```

Pode ser que tenha que ter permissão para executar, então:

```
chmod +x ./dotnet-install.sh
```

Certifique-se que o arquivo do usuário .bashrc (se usar o Sheel bash) possui a definição da variável PATH com o diretório do dotnet inserido, senão, edite. Pode ser que tenha que fazer algo do tipo:

```
DOTNET_FILE=dotnet-sdk-7.0.100-linux-x64.tar.gz
export DOTNET_ROOT=$(pwd)/.dotnet

mkdir -p "$DOTNET_ROOT" && tar zxf "$DOTNET_FILE" -C "$DOTNET_ROOT"

export PATH=$PATH:$DOTNET_ROOT:$DOTNET_ROOT/tools
```

Sem o DOTNET_FILE e o mkdir. Pois peguei esse Script da documentação, no caso, para a definição da variável de ambiente PATH, seria necessário somente os exports.

Verifique também onde estão os binários do SDK, geralmente em /home/usuario/.dotnet/sdk, pode ser que esteja em outro local como `/usr/share/dotnet/sdk`.

Se não estiverem no local correto, o bash não vai reconhecer o programa do dotnet.

## Preferências de instalação no ambiente Linux (Debian)

Minha preferência particular para a instalação do ambiente .NET é a instalação feita com o script shell. A que me referi acima.

Costumo executar o script de instalação como usuário comum mesmo. O path no meu Debian fica em `/home/leonardo/.dotnet`.

Eis o resultado de alguns comandos, os seus devem ficam parecidos.

```
leonardo@marla:~/Documentos/Source/quickbuy$ dotnet --version
2.2.207
leonardo@marla:~/Documentos/Source/quickbuy$ dotnet --list-sdks
2.2.207 [/home/leonardo/.dotnet/sdk]
leonardo@marla:~/Documentos/Source/quickbuy$ dotnet --list-runtimes
Microsoft.AspNetCore.All 2.2.8 [/home/leonardo/.dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.App 2.2.8 [/home/leonardo/.dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.NETCore.App 2.2.8 [/home/leonardo/.dotnet/shared/Microsoft.NETCore.App]
```

### Detalhe de versão do Debian

Tratando-se de pacotes que o .NET 2.2 usa, ele usa o libssl-dev na versão 1.1.

Pra cima da versão do Bullseye, teremos o 3, e aí ele não vai funcionar. Ou seja, para rodar ele, tem que ser o 1.1.

## Banco de dados

Utilizar MariaDB/MySQL.

## Utilizando Migrations

```
 dotnet ef migrations add ProdutoAddColunaNomeArquivo --project QuickBuy.Repositorio --startup-project QuickBuy.Web --verbose

 dotnet ef database update --project QuickBuy.Repositorio --startup-project QuickBuy.Web --verbose
```
