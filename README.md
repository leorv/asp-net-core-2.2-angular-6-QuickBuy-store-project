# App de compras QuickBuy

Este é um projeto particular, resultado de um curso de .NET Core 2.2.

Embora legado, resulta uma boa fonte de consulta e aprendizagem.

## Utilizando Migrations

```
 dotnet ef migrations add ProdutoAddColunaNomeArquivo --project QuickBuy.Repositorio --startup-project QuickBuy.Web --verbose

 dotnet ef database update --project QuickBuy.Repositorio --startup-project QuickBuy.Web --verbose
```
