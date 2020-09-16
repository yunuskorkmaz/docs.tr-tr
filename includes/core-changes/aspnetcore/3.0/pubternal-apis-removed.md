---
ms.openlocfilehash: 224cd3c7897c64ef05baba7d3d31dbe5ac0dd610
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90606264"
---
### <a name="pubternal-apis-removed"></a><span data-ttu-id="44bff-101">"Pubternal" API 'Leri kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="44bff-101">"Pubternal" APIs removed</span></span>

<span data-ttu-id="44bff-102">ASP.NET Core ortak API yüzeyini daha iyi korumak için `*.Internal` ad alanları (API 'ler olarak adlandırılır) içindeki türlerin çoğu :::no-loc text="\"pubternal\""::: gerçekten dahili hale gelir.</span><span class="sxs-lookup"><span data-stu-id="44bff-102">To better maintain the public API surface of ASP.NET Core, most of the types in `*.Internal` namespaces (referred to as :::no-loc text="\"pubternal\""::: APIs) have become truly internal.</span></span> <span data-ttu-id="44bff-103">Bu ad alanlarındaki üyelerin herkese açık API 'Ler olarak desteklenmemesi hiç değildir.</span><span class="sxs-lookup"><span data-stu-id="44bff-103">Members in these namespaces were never meant to be supported as public-facing APIs.</span></span> <span data-ttu-id="44bff-104">API 'Ler küçük sürümlerde kesilebilir ve genellikle olur.</span><span class="sxs-lookup"><span data-stu-id="44bff-104">The APIs could break in minor releases and often did.</span></span> <span data-ttu-id="44bff-105">3,0 ASP.NET Core güncelleştirme sırasında bu API 'Lere bağlı olan kod kesilir.</span><span class="sxs-lookup"><span data-stu-id="44bff-105">Code that depends on these APIs breaks when updating to ASP.NET Core 3.0.</span></span>

<span data-ttu-id="44bff-106">Daha fazla bilgi için bkz. [DotNet/aspnetcore # 4932](https://github.com/dotnet/aspnetcore/issues/4932) and [DotNet/aspnetcore # 11312](https://github.com/dotnet/aspnetcore/issues/11312).</span><span class="sxs-lookup"><span data-stu-id="44bff-106">For more information, see [dotnet/aspnetcore#4932](https://github.com/dotnet/aspnetcore/issues/4932) and [dotnet/aspnetcore#11312](https://github.com/dotnet/aspnetcore/issues/11312).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="44bff-107">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="44bff-107">Version introduced</span></span>

<span data-ttu-id="44bff-108">3.0</span><span class="sxs-lookup"><span data-stu-id="44bff-108">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="44bff-109">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="44bff-109">Old behavior</span></span>

<span data-ttu-id="44bff-110">Etkilenen API 'Ler `public` erişim değiştiricisiyle işaretlenir ve `*.Internal` ad alanlarında bulunur.</span><span class="sxs-lookup"><span data-stu-id="44bff-110">The affected APIs are marked with the `public` access modifier and exist in `*.Internal` namespaces.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="44bff-111">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="44bff-111">New behavior</span></span>

<span data-ttu-id="44bff-112">Etkilenen API 'Ler [iç](../../../../docs/csharp/language-reference/keywords/internal.md) erişim değiştiricisiyle işaretlenir ve artık bu derleme dışındaki kod tarafından kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="44bff-112">The affected APIs are marked with the [internal](../../../../docs/csharp/language-reference/keywords/internal.md) access modifier and can no longer be used by code outside that assembly.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="44bff-113">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="44bff-113">Reason for change</span></span>

<span data-ttu-id="44bff-114">Bu API 'ler için rehberlik şu :::no-loc text="\"pubternal\""::: şekilde yapılır:</span><span class="sxs-lookup"><span data-stu-id="44bff-114">The guidance for these :::no-loc text="\"pubternal\""::: APIs was that they:</span></span>

* <span data-ttu-id="44bff-115">Bildirimde bulunulmadan değişebilir.</span><span class="sxs-lookup"><span data-stu-id="44bff-115">Could change without notice.</span></span>
* <span data-ttu-id="44bff-116">Son değişiklikleri engellemek için .NET ilkelerine tabi değildir.</span><span class="sxs-lookup"><span data-stu-id="44bff-116">Weren't subject to .NET policies to prevent breaking changes.</span></span>

<span data-ttu-id="44bff-117">API 'lerden çıkmak `public` ( `*.Internal` ad alanlarında bile) müşteriler için kafa karıştırıcı.</span><span class="sxs-lookup"><span data-stu-id="44bff-117">Leaving the APIs `public` (even in the `*.Internal` namespaces) was confusing to customers.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="44bff-118">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="44bff-118">Recommended action</span></span>

<span data-ttu-id="44bff-119">Bu :::no-loc text="\"pubternal\""::: API 'leri kullanmayı durdurun.</span><span class="sxs-lookup"><span data-stu-id="44bff-119">Stop using these :::no-loc text="\"pubternal\""::: APIs.</span></span> <span data-ttu-id="44bff-120">Alternatif API 'Ler hakkında sorularınız varsa, [DotNet/aspnetcore](https://github.com/dotnet/aspnetcore/issues) deposunda bir sorun açın.</span><span class="sxs-lookup"><span data-stu-id="44bff-120">If you have questions about alternate APIs, open an issue in the [dotnet/aspnetcore](https://github.com/dotnet/aspnetcore/issues) repository.</span></span>

<span data-ttu-id="44bff-121">Örneğin, bir ASP.NET Core 2,2 projesinde aşağıdaki HTTP isteği arabelleğe alma kodunu göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="44bff-121">For example, consider the following HTTP request buffering code in an ASP.NET Core 2.2 project.</span></span> <span data-ttu-id="44bff-122">`EnableRewind`Uzantı yöntemi `Microsoft.AspNetCore.Http.Internal` ad alanında bulunur.</span><span class="sxs-lookup"><span data-stu-id="44bff-122">The `EnableRewind` extension method exists in the `Microsoft.AspNetCore.Http.Internal` namespace.</span></span>

```csharp
HttpContext.Request.EnableRewind();
```

<span data-ttu-id="44bff-123">ASP.NET Core 3,0 projesinde, `EnableRewind` çağrısını uzantı yöntemine yönelik bir çağrı ile değiştirin `EnableBuffering` .</span><span class="sxs-lookup"><span data-stu-id="44bff-123">In an ASP.NET Core 3.0 project, replace the `EnableRewind` call with a call to the `EnableBuffering` extension method.</span></span> <span data-ttu-id="44bff-124">İstek arabelleğe alma özelliği geçmişte olduğu gibi çalışmaktadır.</span><span class="sxs-lookup"><span data-stu-id="44bff-124">The request buffering feature works as it did in the past.</span></span> <span data-ttu-id="44bff-125">`EnableBuffering` Şimdi `internal` API 'yi çağırır.</span><span class="sxs-lookup"><span data-stu-id="44bff-125">`EnableBuffering` calls the now `internal` API.</span></span>

```csharp
HttpContext.Request.EnableBuffering();
```

#### <a name="category"></a><span data-ttu-id="44bff-126">Kategori</span><span class="sxs-lookup"><span data-stu-id="44bff-126">Category</span></span>

<span data-ttu-id="44bff-127">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="44bff-127">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="44bff-128">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="44bff-128">Affected APIs</span></span>

<span data-ttu-id="44bff-129">`Microsoft.AspNetCore.*` `Microsoft.Extensions.*` Ad alanı adında bir kesimi olan ve ad alanındaki tüm API 'ler `Internal` .</span><span class="sxs-lookup"><span data-stu-id="44bff-129">All APIs in the `Microsoft.AspNetCore.*` and `Microsoft.Extensions.*` namespaces that have an `Internal` segment in the namespace name.</span></span> <span data-ttu-id="44bff-130">Örnek:</span><span class="sxs-lookup"><span data-stu-id="44bff-130">For example:</span></span>

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
