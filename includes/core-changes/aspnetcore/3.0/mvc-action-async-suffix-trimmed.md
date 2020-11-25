---
ms.openlocfilehash: 58b1190e3e6a3168d35700eed655f6756e076a29
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032827"
---
### <a name="mvc-async-suffix-trimmed-from-controller-action-names"></a>MVC: zaman uyumsuz son ek, denetleyici eylem adlarından kırpılmakta

[DotNet/aspnetcore # 4849](https://github.com/dotnet/aspnetcore/issues/4849)adreslemesinin bir parçası olarak ASP.NET Core MVC, `Async` Varsayılan olarak eylem adlarından son eki kırpar. ASP.NET Core 3,0 ' den itibaren bu değişiklik hem yönlendirme hem de bağlantı üretimini etkiler.

#### <a name="version-introduced"></a>Sunulan sürüm

3,0

#### <a name="old-behavior"></a>Eski davranış

Aşağıdaki ASP.NET Core MVC denetleyicisini göz önünde bulundurun:

```csharp
public class ProductController : Controller
{
    public async IActionResult ListAsync()
    {
        var model = await DbContext.Products.ToListAsync();
        return View(model);
    }
}
```

Eylem aracılığıyla yönlendirilebilir `Product/ListAsync` . Bağlantı oluşturma, sonekin belirtilmesini gerektirir `Async` . Örnek:

```cshtml
<a asp-controller="Product" asp-action="ListAsync">List</a>
```

#### <a name="new-behavior"></a>Yeni davranış

ASP.NET Core 3,0 ' de, eylem aracılığıyla yönlendirilebilir `Product/List` . Bağlantı oluşturma kodu `Async` son eki atmalıdır. Örnek:

```cshtml
<a asp-controller="Product" asp-action="List">List</a>
```

Bu değişiklik, özniteliği kullanılarak belirtilen adları etkilemez `[ActionName]` . Yeni davranış, içinde olarak ayarlanarak devre dışı `MvcOptions.SuppressAsyncSuffixInActionNames` bırakılabilir `false` `Startup.ConfigureServices` :

```csharp
services.AddMvc(options =>
{
   options.SuppressAsyncSuffixInActionNames = false;
});
```

#### <a name="reason-for-change"></a>Değişiklik nedeni

Kurala göre, zaman uyumsuz .NET yöntemleri ile sonlardır `Async` . Ancak, bir yöntem bir MVC eylemini tanımladığında, sonekin kullanılması istenmeyen bir işlemdir `Async` .

#### <a name="recommended-action"></a>Önerilen eylem

Uygulamanız, adın sonekini koruyan MVC eylemlerine bağımlıysa `Async` , aşağıdaki azaltmaları aşağıdakilerden birini seçin:

- `[ActionName]`Özgün adı korumak için özniteliğini kullanın.
- Yeniden adlandırmayı tamamen devre dışı bırak `MvcOptions.SuppressAsyncSuffixInActionNames` `false` `Startup.ConfigureServices` :

```csharp
services.AddMvc(options =>
{
   options.SuppressAsyncSuffixInActionNames = false;
});
```

#### <a name="category"></a>Kategori

ASP.NET Core

#### <a name="affected-apis"></a>Etkilenen API’ler

Yok

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
