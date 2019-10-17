---
ms.openlocfilehash: dc9f37ae0cd6eef2c67e62421571290bba1c2233
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394384"
---
### <a name="mvc-async-suffix-trimmed-from-controller-action-names"></a>MVC: zaman uyumsuz son ek, denetleyici eylem adlarından kırpılmakta

[ASPNET/AspNetCore # 4849](https://github.com/aspnet/AspNetCore/issues/4849)adresleme 'nin bir parçası olarak ASP.NET Core MVC, varsayılan olarak eylem adlarından 1 @no__t sonekini kırpar. ASP.NET Core 3,0 ' den itibaren bu değişiklik hem yönlendirme hem de bağlantı üretimini etkiler.

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

Eylem `Product/ListAsync` aracılığıyla yönlendirilebilir. Bağlantı oluşturma, `Async` sonekinin belirtilmesini gerektirir. Örneğin:

```cshtml
<a asp-controller="Product" asp-action="ListAsync">List</a>
```

#### <a name="new-behavior"></a>Yeni davranış

ASP.NET Core 3,0 ' de eylem, `Product/List` aracılığıyla yönlendirilebilir. Bağlantı oluşturma kodu `Async` sonekini atmalıdır. Örneğin:

```cshtml
<a asp-controller="Product" asp-action="List">List</a>
```

Bu değişiklik, `[ActionName]` özniteliği kullanılarak belirtilen adları etkilemez. Yeni davranış `Startup.ConfigureServices` ' de `MvcOptions.SuppressAsyncSuffixInActionNames` ' ı `false` ayarlanarak devre dışı bırakılabilir:

```csharp
services.AddMvc(options =>
{
   options.SuppressAsyncSuffixInActionNames = false; 
});
```

#### <a name="reason-for-change"></a>Değişiklik nedeni

Kurala göre, zaman uyumsuz .NET yöntemleri `Async` ile sonlardır. Ancak, bir yöntem bir MVC eylemini tanımladığında, `Async` sonekini kullanmak istenmeyen bir işlemdir.

#### <a name="recommended-action"></a>Önerilen eylem

Uygulamanız, adın `Async` sonekini koruyan MVC eylemlerine bağımlıysa, aşağıdaki azaltmaları aşağıdakilerden birini seçin:

- Özgün adı korumak için `[ActionName]` özniteliğini kullanın.
- @No__t-2 ' de `MvcOptions.SuppressAsyncSuffixInActionNames` olarak `false` ' i ayarlayarak yeniden adlandırmayı tamamen devre dışı bırakın:

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
