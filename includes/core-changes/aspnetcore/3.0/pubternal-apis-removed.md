---
ms.openlocfilehash: b1fb9647091cecb80b9c2f04ec9b6bb156eb39ba
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/05/2020
ms.locfileid: "84466865"
---
### <a name="pubternal-apis-removed"></a><span data-ttu-id="f4674-101">"Pubternal" API 'Leri kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="f4674-101">"Pubternal" APIs removed</span></span>

<span data-ttu-id="f4674-102">ASP.NET Core ortak API yüzeyini daha iyi korumak için `*.Internal` ad alanları (API 'ler olarak adlandırılır) içindeki türlerin çoğu :::no-loc text="\"pubternal\""::: gerçekten dahili hale gelir.</span><span class="sxs-lookup"><span data-stu-id="f4674-102">To better maintain the public API surface of ASP.NET Core, most of the types in `*.Internal` namespaces (referred to as :::no-loc text="\"pubternal\""::: APIs) have become truly internal.</span></span> <span data-ttu-id="f4674-103">Bu ad alanlarındaki üyelerin herkese açık API 'Ler olarak desteklenmemesi hiç değildir.</span><span class="sxs-lookup"><span data-stu-id="f4674-103">Members in these namespaces were never meant to be supported as public-facing APIs.</span></span> <span data-ttu-id="f4674-104">API 'Ler küçük sürümlerde kesilebilir ve genellikle olur.</span><span class="sxs-lookup"><span data-stu-id="f4674-104">The APIs could break in minor releases and often did.</span></span> <span data-ttu-id="f4674-105">3,0 ASP.NET Core güncelleştirme sırasında bu API 'Lere bağlı olan kod kesilir.</span><span class="sxs-lookup"><span data-stu-id="f4674-105">Code that depends on these APIs breaks when updating to ASP.NET Core 3.0.</span></span>

<span data-ttu-id="f4674-106">Daha fazla bilgi için bkz. [DotNet/aspnetcore # 4932](https://github.com/dotnet/aspnetcore/issues/4932) and [DotNet/aspnetcore # 11312](https://github.com/dotnet/aspnetcore/issues/11312).</span><span class="sxs-lookup"><span data-stu-id="f4674-106">For more information, see [dotnet/aspnetcore#4932](https://github.com/dotnet/aspnetcore/issues/4932) and [dotnet/aspnetcore#11312](https://github.com/dotnet/aspnetcore/issues/11312).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="f4674-107">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="f4674-107">Version introduced</span></span>

<span data-ttu-id="f4674-108">3.0</span><span class="sxs-lookup"><span data-stu-id="f4674-108">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="f4674-109">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="f4674-109">Old behavior</span></span>

<span data-ttu-id="f4674-110">Etkilenen API 'Ler `public` erişim değiştiricisiyle işaretlenir ve `*.Internal` ad alanlarında bulunur.</span><span class="sxs-lookup"><span data-stu-id="f4674-110">The affected APIs are marked with the `public` access modifier and exist in `*.Internal` namespaces.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="f4674-111">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="f4674-111">New behavior</span></span>

<span data-ttu-id="f4674-112">Etkilenen API 'Ler [iç](/dotnet/csharp/language-reference/keywords/internal) erişim değiştiricisiyle işaretlenir ve artık bu derleme dışındaki kod tarafından kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="f4674-112">The affected APIs are marked with the [internal](/dotnet/csharp/language-reference/keywords/internal) access modifier and can no longer be used by code outside that assembly.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="f4674-113">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="f4674-113">Reason for change</span></span>

<span data-ttu-id="f4674-114">Bu API 'ler için rehberlik şu :::no-loc text="\"pubternal\""::: şekilde yapılır:</span><span class="sxs-lookup"><span data-stu-id="f4674-114">The guidance for these :::no-loc text="\"pubternal\""::: APIs was that they:</span></span>

* <span data-ttu-id="f4674-115">Bildirimde bulunulmadan değişebilir.</span><span class="sxs-lookup"><span data-stu-id="f4674-115">Could change without notice.</span></span>
* <span data-ttu-id="f4674-116">Son değişiklikleri engellemek için .NET ilkelerine tabi değildir.</span><span class="sxs-lookup"><span data-stu-id="f4674-116">Weren't subject to .NET policies to prevent breaking changes.</span></span>

<span data-ttu-id="f4674-117">API 'lerden çıkmak `public` ( `*.Internal` ad alanlarında bile) müşteriler için kafa karıştırıcı.</span><span class="sxs-lookup"><span data-stu-id="f4674-117">Leaving the APIs `public` (even in the `*.Internal` namespaces) was confusing to customers.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="f4674-118">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="f4674-118">Recommended action</span></span>

<span data-ttu-id="f4674-119">Bu :::no-loc text="\"pubternal\""::: API 'leri kullanmayı durdurun.</span><span class="sxs-lookup"><span data-stu-id="f4674-119">Stop using these :::no-loc text="\"pubternal\""::: APIs.</span></span> <span data-ttu-id="f4674-120">Alternatif API 'Ler hakkında sorularınız varsa, [DotNet/aspnetcore](https://github.com/dotnet/aspnetcore/issues) deposunda bir sorun açın.</span><span class="sxs-lookup"><span data-stu-id="f4674-120">If you have questions about alternate APIs, open an issue in the [dotnet/aspnetcore](https://github.com/dotnet/aspnetcore/issues) repository.</span></span>

<span data-ttu-id="f4674-121">Örneğin, bir ASP.NET Core 2,2 projesinde aşağıdaki HTTP isteği arabelleğe alma kodunu göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="f4674-121">For example, consider the following HTTP request buffering code in an ASP.NET Core 2.2 project.</span></span> <span data-ttu-id="f4674-122">`EnableRewind`Uzantı yöntemi `Microsoft.AspNetCore.Http.Internal` ad alanında bulunur.</span><span class="sxs-lookup"><span data-stu-id="f4674-122">The `EnableRewind` extension method exists in the `Microsoft.AspNetCore.Http.Internal` namespace.</span></span>

```csharp
HttpContext.Request.EnableRewind();
```

<span data-ttu-id="f4674-123">ASP.NET Core 3,0 projesinde, `EnableRewind` çağrısını uzantı yöntemine yönelik bir çağrı ile değiştirin `EnableBuffering` .</span><span class="sxs-lookup"><span data-stu-id="f4674-123">In an ASP.NET Core 3.0 project, replace the `EnableRewind` call with a call to the `EnableBuffering` extension method.</span></span> <span data-ttu-id="f4674-124">İstek arabelleğe alma özelliği geçmişte olduğu gibi çalışmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f4674-124">The request buffering feature works as it did in the past.</span></span> <span data-ttu-id="f4674-125">`EnableBuffering`Şimdi `internal` API 'yi çağırır.</span><span class="sxs-lookup"><span data-stu-id="f4674-125">`EnableBuffering` calls the now `internal` API.</span></span>

```csharp
HttpContext.Request.EnableBuffering();
```

#### <a name="category"></a><span data-ttu-id="f4674-126">Kategori</span><span class="sxs-lookup"><span data-stu-id="f4674-126">Category</span></span>

<span data-ttu-id="f4674-127">ASP.NET Çekirdeği</span><span class="sxs-lookup"><span data-stu-id="f4674-127">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="f4674-128">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="f4674-128">Affected APIs</span></span>

<span data-ttu-id="f4674-129">`Microsoft.AspNetCore.*` `Microsoft.Extensions.*` Ad alanı adında bir kesimi olan ve ad alanındaki tüm API 'ler `Internal` .</span><span class="sxs-lookup"><span data-stu-id="f4674-129">All APIs in the `Microsoft.AspNetCore.*` and `Microsoft.Extensions.*` namespaces that have an `Internal` segment in the namespace name.</span></span> <span data-ttu-id="f4674-130">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="f4674-130">For example:</span></span>

- `Microsoft.AspNetCore.Authentication.Internal`
- `Microsoft.AspNetCore.Builder.Internal`
- `Microsoft.AspNetCore.DataProtection.Cng.Internal`
- `Microsoft.AspNetCore.DataProtection.Internal`
- `Microsoft.AspNetCore.Hosting.Internal`
- `Microsoft.AspNetCore.Http.Internal`
- `Microsoft.AspNetCore.Mvc.Core.Infrastructure`
- `Microsoft.AspNetCore.Mvc.Core.Internal`
- `Microsoft.AspNetCore.Mvc.Cors.Internal`
- `Microsoft.AspNetCore.Mvc.DataAnnotations.Internal`
- `Microsoft.AspNetCore.Mvc.Formatters.Internal`
- `Microsoft.AspNetCore.Mvc.Formatters.Json.Internal`
- `Microsoft.AspNetCore.Mvc.Formatters.Xml.Internal`
- `Microsoft.AspNetCore.Mvc.Internal`
- `Microsoft.AspNetCore.Mvc.ModelBinding.Internal`
- `Microsoft.AspNetCore.Mvc.Razor.Internal`
- `Microsoft.AspNetCore.Mvc.RazorPages.Internal`
- `Microsoft.AspNetCore.Mvc.TagHelpers.Internal`
- `Microsoft.AspNetCore.Mvc.ViewFeatures.Internal`
- `Microsoft.AspNetCore.Rewrite.Internal`
- `Microsoft.AspNetCore.Routing.Internal`
- `Microsoft.AspNetCore.Server.Kestrel.Core.Adapter.Internal`
- `Microsoft.AspNetCore.Server.Kestrel.Core.Internal.Http`
- `Microsoft.AspNetCore.Server.Kestrel.Core.Internal.Infrastructure`
- `Microsoft.AspNetCore.Server.Kestrel.Https.Internal`

<!--

#### Affected APIs

- `N:Microsoft.AspNetCore.Authentication.Internal`
- `N:Microsoft.AspNetCore.Builder.Internal`
- `N:Microsoft.AspNetCore.DataProtection.Cng.Internal`
- `N:Microsoft.AspNetCore.DataProtection.Internal`
- `N:Microsoft.AspNetCore.Hosting.Internal`
- `N:Microsoft.AspNetCore.Http.Internal`
- `N:Microsoft.AspNetCore.Mvc.Core.Infrastructure`
- `N:Microsoft.AspNetCore.Mvc.Core.Internal`
- `N:Microsoft.AspNetCore.Mvc.Cors.Internal`
- `N:Microsoft.AspNetCore.Mvc.DataAnnotations.Internal`
- `N:Microsoft.AspNetCore.Mvc.Formatters.Internal`
- `N:Microsoft.AspNetCore.Mvc.Formatters.Json.Internal`
- `N:Microsoft.AspNetCore.Mvc.Formatters.Xml.Internal`
- `N:Microsoft.AspNetCore.Mvc.Internal`
- `N:Microsoft.AspNetCore.Mvc.ModelBinding.Internal`
- `N:Microsoft.AspNetCore.Mvc.Razor.Internal`
- `N:Microsoft.AspNetCore.Mvc.RazorPages.Internal`
- `N:Microsoft.AspNetCore.Mvc.TagHelpers.Internal`
- `N:Microsoft.AspNetCore.Mvc.ViewFeatures.Internal`
- `N:Microsoft.AspNetCore.Rewrite.Internal`
- `N:Microsoft.AspNetCore.Routing.Internal`
- `N:Microsoft.AspNetCore.Server.Kestrel.Core.Adapter.Internal`
- `N:Microsoft.AspNetCore.Server.Kestrel.Core.Internal.Http`
- `N:Microsoft.AspNetCore.Server.Kestrel.Core.Internal.Infrastructure`
- `N:Microsoft.AspNetCore.Server.Kestrel.Https.Internal`

-->
