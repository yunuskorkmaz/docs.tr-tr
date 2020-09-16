---
ms.openlocfilehash: 29908ed916690e67db3cc5d72ebe1b1c6aea45c6
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325205"
---
### <a name="iis-urlrewrite-middleware-query-strings-are-preserved"></a><span data-ttu-id="25891-101">IIS: URL yeniden yazma ara yazılımı sorgu dizeleri korunur</span><span class="sxs-lookup"><span data-stu-id="25891-101">IIS: UrlRewrite middleware query strings are preserved</span></span>

<span data-ttu-id="25891-102">Bir IIS Urlyeniden yazma ara yazılım hatası sorgu dizesinin yeniden yazma kurallarında korunması engelledi.</span><span class="sxs-lookup"><span data-stu-id="25891-102">An IIS UrlRewrite middleware defect prevented the query string from being preserved in rewrite rules.</span></span> <span data-ttu-id="25891-103">Bu hata, IIS Urlyeniden yazma modülünün davranışıyla tutarlılığı sağlamak için düzeltildi.</span><span class="sxs-lookup"><span data-stu-id="25891-103">That defect has been fixed to maintain consistency with the IIS UrlRewrite Module's behavior.</span></span>

<span data-ttu-id="25891-104">Tartışma için bkz. sorun [DotNet/aspnetcore # 22972](https://github.com/dotnet/aspnetcore/issues/22972).</span><span class="sxs-lookup"><span data-stu-id="25891-104">For discussion, see issue [dotnet/aspnetcore#22972](https://github.com/dotnet/aspnetcore/issues/22972).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="25891-105">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="25891-105">Version introduced</span></span>

<span data-ttu-id="25891-106">ASP.NET Core 5,0 Preview 7</span><span class="sxs-lookup"><span data-stu-id="25891-106">ASP.NET Core 5.0 Preview 7</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="25891-107">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="25891-107">Old behavior</span></span>

<span data-ttu-id="25891-108">Aşağıdaki yeniden yazma kuralını göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="25891-108">Consider the following rewrite rule:</span></span>

```xml
<rule name="MyRule" stopProcessing="true">
  <match url="^about" />
  <action type="Redirect" url="/contact" redirectType="Temporary" appendQueryString="true" />
</rule>
```

<span data-ttu-id="25891-109">Önceki kural sorgu dizesini eklememez.</span><span class="sxs-lookup"><span data-stu-id="25891-109">The preceding rule doesn't append the query string.</span></span> <span data-ttu-id="25891-110">Yerine öğesine yeniden yönlendirme gibi bir URI `/about?id=1` `/contact` `/contact?id=1` .</span><span class="sxs-lookup"><span data-stu-id="25891-110">A URI like `/about?id=1` redirects to `/contact` instead of `/contact?id=1`.</span></span> <span data-ttu-id="25891-111">`appendQueryString`Özniteliği `true` de varsayılan olarak olur.</span><span class="sxs-lookup"><span data-stu-id="25891-111">The `appendQueryString` attribute defaults to `true` as well.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="25891-112">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="25891-112">New behavior</span></span>

<span data-ttu-id="25891-113">Sorgu dizesi korunur.</span><span class="sxs-lookup"><span data-stu-id="25891-113">The query string is preserved.</span></span> <span data-ttu-id="25891-114">[Eski davranıştaki](#old-behavior) örnekteki URI, olur `/contact?id=1` .</span><span class="sxs-lookup"><span data-stu-id="25891-114">The URI from the example in [Old behavior](#old-behavior) would be `/contact?id=1`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="25891-115">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="25891-115">Reason for change</span></span>

<span data-ttu-id="25891-116">Eski davranış IIS Urlyeniden yazma modülünün davranışıyla eşleşmedi.</span><span class="sxs-lookup"><span data-stu-id="25891-116">The old behavior didn't match the IIS UrlRewrite Module's behavior.</span></span> <span data-ttu-id="25891-117">Ara yazılım ve modülle modül arasında taşıma desteği sağlamak için, amaç tutarlı davranışları korumaktır.</span><span class="sxs-lookup"><span data-stu-id="25891-117">To support porting between the middleware and module, the goal is to maintain consistent behaviors.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="25891-118">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="25891-118">Recommended action</span></span>

<span data-ttu-id="25891-119">Sorgu dizesini kaldırma davranışı tercih edilirse, `action` öğesini olarak ayarlayın `appendQueryString="false"` .</span><span class="sxs-lookup"><span data-stu-id="25891-119">If the behavior of removing the query string is preferred, set the `action` element to `appendQueryString="false"`.</span></span>

#### <a name="category"></a><span data-ttu-id="25891-120">Kategori</span><span class="sxs-lookup"><span data-stu-id="25891-120">Category</span></span>

<span data-ttu-id="25891-121">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="25891-121">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="25891-122">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="25891-122">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Rewrite.IISUrlRewriteOptionsExtensions.AddIISUrlRewrite%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

`Overload:Microsoft.AspNetCore.Rewrite.IISUrlRewriteOptionsExtensions.AddIISUrlRewrite`

-->
