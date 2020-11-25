---
ms.openlocfilehash: 58b1190e3e6a3168d35700eed655f6756e076a29
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032827"
---
### <a name="mvc-async-suffix-trimmed-from-controller-action-names"></a><span data-ttu-id="7cd71-101">MVC: zaman uyumsuz son ek, denetleyici eylem adlarından kırpılmakta</span><span class="sxs-lookup"><span data-stu-id="7cd71-101">MVC: Async suffix trimmed from controller action names</span></span>

<span data-ttu-id="7cd71-102">[DotNet/aspnetcore # 4849](https://github.com/dotnet/aspnetcore/issues/4849)adreslemesinin bir parçası olarak ASP.NET Core MVC, `Async` Varsayılan olarak eylem adlarından son eki kırpar.</span><span class="sxs-lookup"><span data-stu-id="7cd71-102">As part of addressing [dotnet/aspnetcore#4849](https://github.com/dotnet/aspnetcore/issues/4849), ASP.NET Core MVC trims the suffix `Async` from action names by default.</span></span> <span data-ttu-id="7cd71-103">ASP.NET Core 3,0 ' den itibaren bu değişiklik hem yönlendirme hem de bağlantı üretimini etkiler.</span><span class="sxs-lookup"><span data-stu-id="7cd71-103">Starting with ASP.NET Core 3.0, this change affects both routing and link generation.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="7cd71-104">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="7cd71-104">Version introduced</span></span>

<span data-ttu-id="7cd71-105">3,0</span><span class="sxs-lookup"><span data-stu-id="7cd71-105">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="7cd71-106">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="7cd71-106">Old behavior</span></span>

<span data-ttu-id="7cd71-107">Aşağıdaki ASP.NET Core MVC denetleyicisini göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="7cd71-107">Consider the following ASP.NET Core MVC controller:</span></span>

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

<span data-ttu-id="7cd71-108">Eylem aracılığıyla yönlendirilebilir `Product/ListAsync` .</span><span class="sxs-lookup"><span data-stu-id="7cd71-108">The action is routable via `Product/ListAsync`.</span></span> <span data-ttu-id="7cd71-109">Bağlantı oluşturma, sonekin belirtilmesini gerektirir `Async` .</span><span class="sxs-lookup"><span data-stu-id="7cd71-109">Link generation requires specifying the `Async` suffix.</span></span> <span data-ttu-id="7cd71-110">Örnek:</span><span class="sxs-lookup"><span data-stu-id="7cd71-110">For example:</span></span>

```cshtml
<a asp-controller="Product" asp-action="ListAsync">List</a>
```

#### <a name="new-behavior"></a><span data-ttu-id="7cd71-111">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="7cd71-111">New behavior</span></span>

<span data-ttu-id="7cd71-112">ASP.NET Core 3,0 ' de, eylem aracılığıyla yönlendirilebilir `Product/List` .</span><span class="sxs-lookup"><span data-stu-id="7cd71-112">In ASP.NET Core 3.0, the action is routable via `Product/List`.</span></span> <span data-ttu-id="7cd71-113">Bağlantı oluşturma kodu `Async` son eki atmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7cd71-113">Link generation code should omit the `Async` suffix.</span></span> <span data-ttu-id="7cd71-114">Örnek:</span><span class="sxs-lookup"><span data-stu-id="7cd71-114">For example:</span></span>

```cshtml
<a asp-controller="Product" asp-action="List">List</a>
```

<span data-ttu-id="7cd71-115">Bu değişiklik, özniteliği kullanılarak belirtilen adları etkilemez `[ActionName]` .</span><span class="sxs-lookup"><span data-stu-id="7cd71-115">This change doesn't affect names specified using the `[ActionName]` attribute.</span></span> <span data-ttu-id="7cd71-116">Yeni davranış, içinde olarak ayarlanarak devre dışı `MvcOptions.SuppressAsyncSuffixInActionNames` bırakılabilir `false` `Startup.ConfigureServices` :</span><span class="sxs-lookup"><span data-stu-id="7cd71-116">The new behavior can be disabled by setting `MvcOptions.SuppressAsyncSuffixInActionNames` to `false` in `Startup.ConfigureServices`:</span></span>

```csharp
services.AddMvc(options =>
{
   options.SuppressAsyncSuffixInActionNames = false;
});
```

#### <a name="reason-for-change"></a><span data-ttu-id="7cd71-117">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="7cd71-117">Reason for change</span></span>

<span data-ttu-id="7cd71-118">Kurala göre, zaman uyumsuz .NET yöntemleri ile sonlardır `Async` .</span><span class="sxs-lookup"><span data-stu-id="7cd71-118">By convention, asynchronous .NET methods are suffixed with `Async`.</span></span> <span data-ttu-id="7cd71-119">Ancak, bir yöntem bir MVC eylemini tanımladığında, sonekin kullanılması istenmeyen bir işlemdir `Async` .</span><span class="sxs-lookup"><span data-stu-id="7cd71-119">However, when a method defines an MVC action, it's undesirable to use the `Async` suffix.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="7cd71-120">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="7cd71-120">Recommended action</span></span>

<span data-ttu-id="7cd71-121">Uygulamanız, adın sonekini koruyan MVC eylemlerine bağımlıysa `Async` , aşağıdaki azaltmaları aşağıdakilerden birini seçin:</span><span class="sxs-lookup"><span data-stu-id="7cd71-121">If your app depends on MVC actions preserving the name's `Async` suffix, choose one of the following mitigations:</span></span>

- <span data-ttu-id="7cd71-122">`[ActionName]`Özgün adı korumak için özniteliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="7cd71-122">Use the `[ActionName]` attribute to preserve the original name.</span></span>
- <span data-ttu-id="7cd71-123">Yeniden adlandırmayı tamamen devre dışı bırak `MvcOptions.SuppressAsyncSuffixInActionNames` `false` `Startup.ConfigureServices` :</span><span class="sxs-lookup"><span data-stu-id="7cd71-123">Disable the renaming entirely by setting `MvcOptions.SuppressAsyncSuffixInActionNames` to `false` in `Startup.ConfigureServices`:</span></span>

```csharp
services.AddMvc(options =>
{
   options.SuppressAsyncSuffixInActionNames = false;
});
```

#### <a name="category"></a><span data-ttu-id="7cd71-124">Kategori</span><span class="sxs-lookup"><span data-stu-id="7cd71-124">Category</span></span>

<span data-ttu-id="7cd71-125">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="7cd71-125">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="7cd71-126">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="7cd71-126">Affected APIs</span></span>

<span data-ttu-id="7cd71-127">Yok</span><span class="sxs-lookup"><span data-stu-id="7cd71-127">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
