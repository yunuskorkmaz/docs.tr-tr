---
ms.openlocfilehash: ae5a5fbf97ed4a03de7d35b9d5d5ca8de3aebc39
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032708"
---
### <a name="caching-responsecaching-pubternal-types-changed-to-internal"></a><span data-ttu-id="5d17e-101">Önbelleğe alma: ResponseCaching "pubternal" türleri iç olarak değiştirildi</span><span class="sxs-lookup"><span data-stu-id="5d17e-101">Caching: ResponseCaching "pubternal" types changed to internal</span></span>

<span data-ttu-id="5d17e-102">ASP.NET Core 3,0 ' de, ' deki "pubternal" türleri `ResponseCaching` olarak değiştirilmiştir `internal` .</span><span class="sxs-lookup"><span data-stu-id="5d17e-102">In ASP.NET Core 3.0, "pubternal" types in `ResponseCaching` have been changed to `internal`.</span></span>

<span data-ttu-id="5d17e-103">Buna ek olarak, ve varsayılan uygulamaları, `IResponseCachingPolicyProvider` `IResponseCachingKeyProvider` artık, metodun bir parçası olarak hizmetlere eklenmez `AddResponseCaching` .</span><span class="sxs-lookup"><span data-stu-id="5d17e-103">In addition, default implementations of `IResponseCachingPolicyProvider` and `IResponseCachingKeyProvider` are no longer added to services as part of the `AddResponseCaching` method.</span></span>

#### <a name="change-description"></a><span data-ttu-id="5d17e-104">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="5d17e-104">Change description</span></span>

<span data-ttu-id="5d17e-105">ASP.NET Core, "pubternal" türleri olarak belirtilir, `public` ancak ile düzeltilen bir ad alanında bulunur `.Internal` .</span><span class="sxs-lookup"><span data-stu-id="5d17e-105">In ASP.NET Core, "pubternal" types are declared as `public` but reside in a namespace suffixed with `.Internal`.</span></span> <span data-ttu-id="5d17e-106">Bu türler genel olsa da, destek ilkesi yoktur ve bu değişiklikler önemli değişikliklere tabidir.</span><span class="sxs-lookup"><span data-stu-id="5d17e-106">While these types are public, they have no support policy and are subject to breaking changes.</span></span> <span data-ttu-id="5d17e-107">Ne yazık ki, bu türlerin yanlışlıkla kullanılması yaygındır ve bu projelerde oluşan değişikliklere neden olacak ve Framework 'ün bakımını yapma yeteneğini sınırlandırmıştır.</span><span class="sxs-lookup"><span data-stu-id="5d17e-107">Unfortunately, accidental use of these types has been common, resulting in breaking changes to these projects and limiting the ability to maintain the framework.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="5d17e-108">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="5d17e-108">Version introduced</span></span>

<span data-ttu-id="5d17e-109">3,0</span><span class="sxs-lookup"><span data-stu-id="5d17e-109">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="5d17e-110">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="5d17e-110">Old behavior</span></span>

<span data-ttu-id="5d17e-111">Bu türler herkese açık olarak görünür, ancak desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="5d17e-111">These types were publicly visible, but unsupported.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="5d17e-112">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="5d17e-112">New behavior</span></span>

<span data-ttu-id="5d17e-113">Bu türler artık `internal` .</span><span class="sxs-lookup"><span data-stu-id="5d17e-113">These types are now `internal`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="5d17e-114">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="5d17e-114">Reason for change</span></span>

<span data-ttu-id="5d17e-115">`internal`Kapsam, desteklenmeyen ilkeyi daha iyi yansıtır.</span><span class="sxs-lookup"><span data-stu-id="5d17e-115">The `internal` scope better reflects the unsupported policy.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="5d17e-116">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="5d17e-116">Recommended action</span></span>

<span data-ttu-id="5d17e-117">Uygulamanız veya kitaplığınız tarafından kullanılan türleri kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="5d17e-117">Copy types that are used by your app or library.</span></span>

#### <a name="category"></a><span data-ttu-id="5d17e-118">Kategori</span><span class="sxs-lookup"><span data-stu-id="5d17e-118">Category</span></span>

<span data-ttu-id="5d17e-119">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="5d17e-119">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="5d17e-120">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="5d17e-120">Affected APIs</span></span>

- `Microsoft.AspNetCore.ResponseCaching.Internal.CachedResponse`
- `Microsoft.AspNetCore.ResponseCaching.Internal.CachedVaryByRules`
- `Microsoft.AspNetCore.ResponseCaching.Internal.IResponseCache`
- `Microsoft.AspNetCore.ResponseCaching.Internal.IResponseCacheEntry`
- `Microsoft.AspNetCore.ResponseCaching.Internal.IResponseCachingKeyProvider`
- `Microsoft.AspNetCore.ResponseCaching.Internal.IResponseCachingPolicyProvider`
- `Microsoft.AspNetCore.ResponseCaching.Internal.MemoryResponseCache`
- `Microsoft.AspNetCore.ResponseCaching.Internal.ResponseCachingContext`
- `Microsoft.AspNetCore.ResponseCaching.Internal.ResponseCachingKeyProvider`
- `Microsoft.AspNetCore.ResponseCaching.Internal.ResponseCachingPolicyProvider`
- <xref:Microsoft.AspNetCore.ResponseCaching.ResponseCachingMiddleware.%23ctor(Microsoft.AspNetCore.Http.RequestDelegate,Microsoft.Extensions.Options.IOptions{Microsoft.AspNetCore.ResponseCaching.ResponseCachingOptions},Microsoft.Extensions.Logging.ILoggerFactory,Microsoft.AspNetCore.ResponseCaching.Internal.IResponseCachingPolicyProvider,Microsoft.AspNetCore.ResponseCaching.Internal.IResponseCache,Microsoft.AspNetCore.ResponseCaching.Internal.IResponseCachingKeyProvider)?displayProperty=fullName>

<!-- 

#### Affected APIs

- `T:Microsoft.AspNetCore.ResponseCaching.Internal.CachedResponse`
- `T:Microsoft.AspNetCore.ResponseCaching.Internal.CachedVaryByRules`
- `T:Microsoft.AspNetCore.ResponseCaching.Internal.IResponseCache`
- `T:Microsoft.AspNetCore.ResponseCaching.Internal.IResponseCacheEntry`
- `T:Microsoft.AspNetCore.ResponseCaching.Internal.IResponseCachingKeyProvider`
- `T:Microsoft.AspNetCore.ResponseCaching.Internal.IResponseCachingPolicyProvider`
- `T:Microsoft.AspNetCore.ResponseCaching.Internal.MemoryResponseCache`
- `T:Microsoft.AspNetCore.ResponseCaching.Internal.ResponseCachingContext`
- `T:Microsoft.AspNetCore.ResponseCaching.Internal.ResponseCachingKeyProvider`
- `T:Microsoft.AspNetCore.ResponseCaching.Internal.ResponseCachingPolicyProvider`
- `M:Microsoft.AspNetCore.ResponseCaching.ResponseCachingMiddleware.#ctor(Microsoft.AspNetCore.Http.RequestDelegate,Microsoft.Extensions.Options.IOptions{Microsoft.AspNetCore.ResponseCaching.ResponseCachingOptions},Microsoft.Extensions.Logging.ILoggerFactory,Microsoft.AspNetCore.ResponseCaching.Internal.IResponseCachingPolicyProvider,Microsoft.AspNetCore.ResponseCaching.Internal.IResponseCache,Microsoft.AspNetCore.ResponseCaching.Internal.IResponseCachingKeyProvider)",
"nameWithType": "ResponseCachingMiddleware.ResponseCachingMiddleware(RequestDelegate, IOptions<ResponseCachingOptions>, ILoggerFactory, IResponseCachingPolicyProvider, IResponseCache, IResponseCachingKeyProvider)`

-->
