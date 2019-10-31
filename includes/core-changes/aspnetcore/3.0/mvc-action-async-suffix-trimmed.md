---
ms.openlocfilehash: 503d61cb86c83e2f32ad40c60a127ae255ef71b0
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73198592"
---
### <a name="mvc-async-suffix-trimmed-from-controller-action-names"></a>MVC: zaman uyumsuz son ek, denetleyici eylem adlarından kırpılmakta

[ASPNET/AspNetCore # 4849](https://github.com/aspnet/AspNetCore/issues/4849)adresleme 'nin bir parçası olarak ASP.NET Core MVC, varsayılan olarak eylem adlarından son eki `Async` kırpar. ASP.NET Core 3,0 ' den itibaren bu değişiklik hem yönlendirme hem de bağlantı üretimini etkiler.

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

Bu değişiklik `[ActionName]` özniteliği kullanılarak belirtilen adları etkilemez. Yeni davranış `Startup.ConfigureServices` ' de `MvcOptions.SuppressAsyncSuffixInActionNames` ' ı `false` ayarlanarak devre dışı bırakılabilir:

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
