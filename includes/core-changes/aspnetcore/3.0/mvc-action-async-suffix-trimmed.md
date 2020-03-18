---
ms.openlocfilehash: 58b1190e3e6a3168d35700eed655f6756e076a29
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901586"
---
### <a name="mvc-async-suffix-trimmed-from-controller-action-names"></a><span data-ttu-id="e346c-101">MVC: Denetleyici eylem adlarından kesilmiş async sonek</span><span class="sxs-lookup"><span data-stu-id="e346c-101">MVC: Async suffix trimmed from controller action names</span></span>

<span data-ttu-id="e346c-102">[nokta/aspnetcore#4849](https://github.com/dotnet/aspnetcore/issues/4849)adresinin bir parçası olarak, ASP.NET Core MVC `Async` varsayılan olarak eylem adlarından sonekleri kırpar.</span><span class="sxs-lookup"><span data-stu-id="e346c-102">As part of addressing [dotnet/aspnetcore#4849](https://github.com/dotnet/aspnetcore/issues/4849), ASP.NET Core MVC trims the suffix `Async` from action names by default.</span></span> <span data-ttu-id="e346c-103">Core 3.0 ile ASP.NET başlayarak, bu değişiklik hem yönlendirme yi hem de bağlantı oluşturmayı etkiler.</span><span class="sxs-lookup"><span data-stu-id="e346c-103">Starting with ASP.NET Core 3.0, this change affects both routing and link generation.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="e346c-104">Sürüm tanıtıldı</span><span class="sxs-lookup"><span data-stu-id="e346c-104">Version introduced</span></span>

<span data-ttu-id="e346c-105">3,0</span><span class="sxs-lookup"><span data-stu-id="e346c-105">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="e346c-106">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="e346c-106">Old behavior</span></span>

<span data-ttu-id="e346c-107">Aşağıdaki ASP.NET Core MVC denetleyicisini göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="e346c-107">Consider the following ASP.NET Core MVC controller:</span></span>

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

<span data-ttu-id="e346c-108">Eylem üzerinden `Product/ListAsync`routable olduğunu .</span><span class="sxs-lookup"><span data-stu-id="e346c-108">The action is routable via `Product/ListAsync`.</span></span> <span data-ttu-id="e346c-109">Bağlantı oluşturma `Async` sonekinin belirtilmesi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="e346c-109">Link generation requires specifying the `Async` suffix.</span></span> <span data-ttu-id="e346c-110">Örnek:</span><span class="sxs-lookup"><span data-stu-id="e346c-110">For example:</span></span>

```cshtml
<a asp-controller="Product" asp-action="ListAsync">List</a>
```

#### <a name="new-behavior"></a><span data-ttu-id="e346c-111">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="e346c-111">New behavior</span></span>

<span data-ttu-id="e346c-112">ASP.NET Core 3.0'da, eylem `Product/List`.</span><span class="sxs-lookup"><span data-stu-id="e346c-112">In ASP.NET Core 3.0, the action is routable via `Product/List`.</span></span> <span data-ttu-id="e346c-113">Bağlantı oluşturma kodu `Async` sonek atlamalıdır.</span><span class="sxs-lookup"><span data-stu-id="e346c-113">Link generation code should omit the `Async` suffix.</span></span> <span data-ttu-id="e346c-114">Örnek:</span><span class="sxs-lookup"><span data-stu-id="e346c-114">For example:</span></span>

```cshtml
<a asp-controller="Product" asp-action="List">List</a>
```

<span data-ttu-id="e346c-115">Bu değişiklik öznitelik kullanılarak `[ActionName]` belirtilen adları etkilemez.</span><span class="sxs-lookup"><span data-stu-id="e346c-115">This change doesn't affect names specified using the `[ActionName]` attribute.</span></span> <span data-ttu-id="e346c-116">Yeni davranış aşağıdakilere `MvcOptions.SuppressAsyncSuffixInActionNames` `false` ayarlayarak `Startup.ConfigureServices`devre dışı tutulabilir:</span><span class="sxs-lookup"><span data-stu-id="e346c-116">The new behavior can be disabled by setting `MvcOptions.SuppressAsyncSuffixInActionNames` to `false` in `Startup.ConfigureServices`:</span></span>

```csharp
services.AddMvc(options =>
{
   options.SuppressAsyncSuffixInActionNames = false;
});
```

#### <a name="reason-for-change"></a><span data-ttu-id="e346c-117">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="e346c-117">Reason for change</span></span>

<span data-ttu-id="e346c-118">Kural olarak, asynchronous .NET yöntemleri `Async`ile suffixed vardır.</span><span class="sxs-lookup"><span data-stu-id="e346c-118">By convention, asynchronous .NET methods are suffixed with `Async`.</span></span> <span data-ttu-id="e346c-119">Ancak, bir yöntem bir MVC eylemi tanımladığında, sonek `Async` kullanmak istenmez.</span><span class="sxs-lookup"><span data-stu-id="e346c-119">However, when a method defines an MVC action, it's undesirable to use the `Async` suffix.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="e346c-120">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="e346c-120">Recommended action</span></span>

<span data-ttu-id="e346c-121">Uygulamanız, adın `Async` sonekini koruyan MVC eylemlerine bağlıysa, aşağıdaki azaltıcı etkenlerden birini seçin:</span><span class="sxs-lookup"><span data-stu-id="e346c-121">If your app depends on MVC actions preserving the name's `Async` suffix, choose one of the following mitigations:</span></span>

- <span data-ttu-id="e346c-122">Özgün `[ActionName]` adı korumak için özniteliği kullanın.</span><span class="sxs-lookup"><span data-stu-id="e346c-122">Use the `[ActionName]` attribute to preserve the original name.</span></span>
- <span data-ttu-id="e346c-123">Yeniden adlandırmayı aşağıdaki lere `MvcOptions.SuppressAsyncSuffixInActionNames` `false` ayarlayarak `Startup.ConfigureServices`tamamen devre dışı</span><span class="sxs-lookup"><span data-stu-id="e346c-123">Disable the renaming entirely by setting `MvcOptions.SuppressAsyncSuffixInActionNames` to `false` in `Startup.ConfigureServices`:</span></span>

```csharp
services.AddMvc(options =>
{
   options.SuppressAsyncSuffixInActionNames = false;
});
```

#### <a name="category"></a><span data-ttu-id="e346c-124">Kategori</span><span class="sxs-lookup"><span data-stu-id="e346c-124">Category</span></span>

<span data-ttu-id="e346c-125">ASP.NET Çekirdeği</span><span class="sxs-lookup"><span data-stu-id="e346c-125">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="e346c-126">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="e346c-126">Affected APIs</span></span>

<span data-ttu-id="e346c-127">None</span><span class="sxs-lookup"><span data-stu-id="e346c-127">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
