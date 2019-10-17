---
ms.openlocfilehash: dc9f37ae0cd6eef2c67e62421571290bba1c2233
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394384"
---
### <a name="mvc-async-suffix-trimmed-from-controller-action-names"></a><span data-ttu-id="237e4-101">MVC: zaman uyumsuz son ek, denetleyici eylem adlarından kırpılmakta</span><span class="sxs-lookup"><span data-stu-id="237e4-101">MVC: Async suffix trimmed from controller action names</span></span>

<span data-ttu-id="237e4-102">[ASPNET/AspNetCore # 4849](https://github.com/aspnet/AspNetCore/issues/4849)adresleme 'nin bir parçası olarak ASP.NET Core MVC, varsayılan olarak eylem adlarından 1 @no__t sonekini kırpar.</span><span class="sxs-lookup"><span data-stu-id="237e4-102">As part of addressing [aspnet/AspNetCore#4849](https://github.com/aspnet/AspNetCore/issues/4849), ASP.NET Core MVC trims the suffix `Async` from action names by default.</span></span> <span data-ttu-id="237e4-103">ASP.NET Core 3,0 ' den itibaren bu değişiklik hem yönlendirme hem de bağlantı üretimini etkiler.</span><span class="sxs-lookup"><span data-stu-id="237e4-103">Starting with ASP.NET Core 3.0, this change affects both routing and link generation.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="237e4-104">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="237e4-104">Version introduced</span></span>

<span data-ttu-id="237e4-105">3.0</span><span class="sxs-lookup"><span data-stu-id="237e4-105">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="237e4-106">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="237e4-106">Old behavior</span></span>

<span data-ttu-id="237e4-107">Aşağıdaki ASP.NET Core MVC denetleyicisini göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="237e4-107">Consider the following ASP.NET Core MVC controller:</span></span>

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

<span data-ttu-id="237e4-108">Eylem `Product/ListAsync` aracılığıyla yönlendirilebilir.</span><span class="sxs-lookup"><span data-stu-id="237e4-108">The action is routable via `Product/ListAsync`.</span></span> <span data-ttu-id="237e4-109">Bağlantı oluşturma, `Async` sonekinin belirtilmesini gerektirir.</span><span class="sxs-lookup"><span data-stu-id="237e4-109">Link generation requires specifying the `Async` suffix.</span></span> <span data-ttu-id="237e4-110">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="237e4-110">For example:</span></span>

```cshtml
<a asp-controller="Product" asp-action="ListAsync">List</a>
```

#### <a name="new-behavior"></a><span data-ttu-id="237e4-111">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="237e4-111">New behavior</span></span>

<span data-ttu-id="237e4-112">ASP.NET Core 3,0 ' de eylem, `Product/List` aracılığıyla yönlendirilebilir.</span><span class="sxs-lookup"><span data-stu-id="237e4-112">In ASP.NET Core 3.0, the action is routable via `Product/List`.</span></span> <span data-ttu-id="237e4-113">Bağlantı oluşturma kodu `Async` sonekini atmalıdır.</span><span class="sxs-lookup"><span data-stu-id="237e4-113">Link generation code should omit the `Async` suffix.</span></span> <span data-ttu-id="237e4-114">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="237e4-114">For example:</span></span>

```cshtml
<a asp-controller="Product" asp-action="List">List</a>
```

<span data-ttu-id="237e4-115">Bu değişiklik, `[ActionName]` özniteliği kullanılarak belirtilen adları etkilemez.</span><span class="sxs-lookup"><span data-stu-id="237e4-115">This change doesn't affect names specified using the `[ActionName]` attribute.</span></span> <span data-ttu-id="237e4-116">Yeni davranış `Startup.ConfigureServices` ' de `MvcOptions.SuppressAsyncSuffixInActionNames` ' ı `false` ayarlanarak devre dışı bırakılabilir:</span><span class="sxs-lookup"><span data-stu-id="237e4-116">The new behavior can be disabled by setting `MvcOptions.SuppressAsyncSuffixInActionNames` to `false` in `Startup.ConfigureServices`:</span></span>

```csharp
services.AddMvc(options =>
{
   options.SuppressAsyncSuffixInActionNames = false; 
});
```

#### <a name="reason-for-change"></a><span data-ttu-id="237e4-117">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="237e4-117">Reason for change</span></span>

<span data-ttu-id="237e4-118">Kurala göre, zaman uyumsuz .NET yöntemleri `Async` ile sonlardır.</span><span class="sxs-lookup"><span data-stu-id="237e4-118">By convention, asynchronous .NET methods are suffixed with `Async`.</span></span> <span data-ttu-id="237e4-119">Ancak, bir yöntem bir MVC eylemini tanımladığında, `Async` sonekini kullanmak istenmeyen bir işlemdir.</span><span class="sxs-lookup"><span data-stu-id="237e4-119">However, when a method defines an MVC action, it's undesirable to use the `Async` suffix.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="237e4-120">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="237e4-120">Recommended action</span></span>

<span data-ttu-id="237e4-121">Uygulamanız, adın `Async` sonekini koruyan MVC eylemlerine bağımlıysa, aşağıdaki azaltmaları aşağıdakilerden birini seçin:</span><span class="sxs-lookup"><span data-stu-id="237e4-121">If your app depends on MVC actions preserving the name's `Async` suffix, choose one of the following mitigations:</span></span>

- <span data-ttu-id="237e4-122">Özgün adı korumak için `[ActionName]` özniteliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="237e4-122">Use the `[ActionName]` attribute to preserve the original name.</span></span>
- <span data-ttu-id="237e4-123">@No__t-2 ' de `MvcOptions.SuppressAsyncSuffixInActionNames` olarak `false` ' i ayarlayarak yeniden adlandırmayı tamamen devre dışı bırakın:</span><span class="sxs-lookup"><span data-stu-id="237e4-123">Disable the renaming entirely by setting `MvcOptions.SuppressAsyncSuffixInActionNames` to `false` in `Startup.ConfigureServices`:</span></span>

```csharp
services.AddMvc(options =>
{
   options.SuppressAsyncSuffixInActionNames = false; 
});
```

#### <a name="category"></a><span data-ttu-id="237e4-124">Kategori</span><span class="sxs-lookup"><span data-stu-id="237e4-124">Category</span></span>

<span data-ttu-id="237e4-125">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="237e4-125">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="237e4-126">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="237e4-126">Affected APIs</span></span>

<span data-ttu-id="237e4-127">Yok.</span><span class="sxs-lookup"><span data-stu-id="237e4-127">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
