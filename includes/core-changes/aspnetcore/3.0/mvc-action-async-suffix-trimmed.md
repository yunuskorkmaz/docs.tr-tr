---
ms.openlocfilehash: 58b1190e3e6a3168d35700eed655f6756e076a29
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901586"
---
### <a name="mvc-async-suffix-trimmed-from-controller-action-names"></a>MVC: zaman uyumsuz son ek, denetleyici eylem adlarından kırpılmakta

[DotNet/aspnetcore # 4849](https://github.com/dotnet/aspnetcore/issues/4849)adreslemesinin bir parçası olarak ASP.NET Core MVC, varsayılan olarak eylem adlarından son eki `Async` kırpar. ASP.NET Core 3,0 ' den itibaren bu değişiklik hem yönlendirme hem de bağlantı üretimini etkiler.

#### <a name="version-introduced"></a>Sunulan sürüm

3.0

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

Eylem `Product/ListAsync`aracılığıyla yönlendirilebilir. Bağlantı oluşturma, `Async` sonekin belirtilmesini gerektirir. Örneğin:

```cshtml
<a asp-controller="Product" asp-action="ListAsync">List</a>
```

#### <a name="new-behavior"></a>Yeni davranış

ASP.NET Core 3,0 ' de, eylem `Product/List`aracılığıyla yönlendirilebilir. Bağlantı oluşturma kodu `Async` sonekini atmalıdır. Örneğin:

```cshtml
<a asp-controller="Product" asp-action="List">List</a>
```

Bu değişiklik `[ActionName]` özniteliği kullanılarak belirtilen adları etkilemez. Yeni davranış `Startup.ConfigureServices``MvcOptions.SuppressAsyncSuffixInActionNames` `false` ayarlanarak devre dışı bırakılabilir:

```csharp
services.AddMvc(options =>
{
   options.SuppressAsyncSuffixInActionNames = false;
});
```

#### <a name="reason-for-change"></a>Değişiklik nedeni

Kurala göre, zaman uyumsuz .NET yöntemleri `Async`ile sonlardır. Ancak, bir yöntem bir MVC eylemini tanımladığında `Async` sonekini kullanmak istenmeyen bir işlemdir.

#### <a name="recommended-action"></a>Önerilen eylem

Uygulamanız, adın `Async` sonekini koruyan MVC eylemlerine bağımlıysa, aşağıdaki azaltenlerden birini seçin:

- Özgün adı korumak için `[ActionName]` özniteliğini kullanın.
- `Startup.ConfigureServices``MvcOptions.SuppressAsyncSuffixInActionNames` `false` olarak ayarlayarak yeniden adlandırmayı tamamen devre dışı bırakın:

```csharp
services.AddMvc(options =>
{
   options.SuppressAsyncSuffixInActionNames = false;
});
```

#### <a name="category"></a>Kategori

ASP.NET Core

#### <a name="affected-apis"></a>Etkilenen API’ler

Yok.

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
