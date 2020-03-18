---
ms.openlocfilehash: 58b1190e3e6a3168d35700eed655f6756e076a29
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901586"
---
### <a name="mvc-async-suffix-trimmed-from-controller-action-names"></a>MVC: Denetleyici eylem adlarından kesilmiş async sonek

[nokta/aspnetcore#4849](https://github.com/dotnet/aspnetcore/issues/4849)adresinin bir parçası olarak, ASP.NET Core MVC `Async` varsayılan olarak eylem adlarından sonekleri kırpar. Core 3.0 ile ASP.NET başlayarak, bu değişiklik hem yönlendirme yi hem de bağlantı oluşturmayı etkiler.

#### <a name="version-introduced"></a>Sürüm tanıtıldı

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

Eylem üzerinden `Product/ListAsync`routable olduğunu . Bağlantı oluşturma `Async` sonekinin belirtilmesi gerektirir. Örnek:

```cshtml
<a asp-controller="Product" asp-action="ListAsync">List</a>
```

#### <a name="new-behavior"></a>Yeni davranış

ASP.NET Core 3.0'da, eylem `Product/List`. Bağlantı oluşturma kodu `Async` sonek atlamalıdır. Örnek:

```cshtml
<a asp-controller="Product" asp-action="List">List</a>
```

Bu değişiklik öznitelik kullanılarak `[ActionName]` belirtilen adları etkilemez. Yeni davranış aşağıdakilere `MvcOptions.SuppressAsyncSuffixInActionNames` `false` ayarlayarak `Startup.ConfigureServices`devre dışı tutulabilir:

```csharp
services.AddMvc(options =>
{
   options.SuppressAsyncSuffixInActionNames = false;
});
```

#### <a name="reason-for-change"></a>Değişiklik nedeni

Kural olarak, asynchronous .NET yöntemleri `Async`ile suffixed vardır. Ancak, bir yöntem bir MVC eylemi tanımladığında, sonek `Async` kullanmak istenmez.

#### <a name="recommended-action"></a>Önerilen eylem

Uygulamanız, adın `Async` sonekini koruyan MVC eylemlerine bağlıysa, aşağıdaki azaltıcı etkenlerden birini seçin:

- Özgün `[ActionName]` adı korumak için özniteliği kullanın.
- Yeniden adlandırmayı aşağıdaki lere `MvcOptions.SuppressAsyncSuffixInActionNames` `false` ayarlayarak `Startup.ConfigureServices`tamamen devre dışı

```csharp
services.AddMvc(options =>
{
   options.SuppressAsyncSuffixInActionNames = false;
});
```

#### <a name="category"></a>Kategori

ASP.NET Çekirdeği

#### <a name="affected-apis"></a>Etkilenen API’ler

None

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
