---
ms.openlocfilehash: ae5a5fbf97ed4a03de7d35b9d5d5ca8de3aebc39
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72393969"
---
### <a name="caching-responsecaching-pubternal-types-changed-to-internal"></a><span data-ttu-id="3aea5-101">Önbelleğe alma: YanıtCaching "pubternal" türleri iç değiştirildi</span><span class="sxs-lookup"><span data-stu-id="3aea5-101">Caching: ResponseCaching "pubternal" types changed to internal</span></span>

<span data-ttu-id="3aea5-102">core 3.0 ASP.NET, "pubternal" `ResponseCaching` türleri `internal`değiştirildi.</span><span class="sxs-lookup"><span data-stu-id="3aea5-102">In ASP.NET Core 3.0, "pubternal" types in `ResponseCaching` have been changed to `internal`.</span></span>

<span data-ttu-id="3aea5-103">Buna ek olarak, `IResponseCachingPolicyProvider` varsayılan `IResponseCachingKeyProvider` uygulamaları ve artık yöntemin `AddResponseCaching` bir parçası olarak hizmetlere eklenir.</span><span class="sxs-lookup"><span data-stu-id="3aea5-103">In addition, default implementations of `IResponseCachingPolicyProvider` and `IResponseCachingKeyProvider` are no longer added to services as part of the `AddResponseCaching` method.</span></span>

#### <a name="change-description"></a><span data-ttu-id="3aea5-104">Açıklamayı değiştir</span><span class="sxs-lookup"><span data-stu-id="3aea5-104">Change description</span></span>

<span data-ttu-id="3aea5-105">ASP.NET Core'da "pubternal" türleri `public` olarak bildirilir, ancak bir ad `.Internal`alanı içinde yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="3aea5-105">In ASP.NET Core, "pubternal" types are declared as `public` but reside in a namespace suffixed with `.Internal`.</span></span> <span data-ttu-id="3aea5-106">Bu tür ler herkese açık olsa da, destek politikaları yoktur ve kırılma değişikliklerine tabidirler.</span><span class="sxs-lookup"><span data-stu-id="3aea5-106">While these types are public, they have no support policy and are subject to breaking changes.</span></span> <span data-ttu-id="3aea5-107">Ne yazık ki, bu tür kazara kullanımı, bu projelerde değişiklikler kırma ve çerçeve korumak için yeteneği sınırlayan sonuçlanan yaygın olmuştur.</span><span class="sxs-lookup"><span data-stu-id="3aea5-107">Unfortunately, accidental use of these types has been common, resulting in breaking changes to these projects and limiting the ability to maintain the framework.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="3aea5-108">Sürüm tanıtıldı</span><span class="sxs-lookup"><span data-stu-id="3aea5-108">Version introduced</span></span>

<span data-ttu-id="3aea5-109">3,0</span><span class="sxs-lookup"><span data-stu-id="3aea5-109">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="3aea5-110">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="3aea5-110">Old behavior</span></span>

<span data-ttu-id="3aea5-111">Bu türler genel olarak görünür, ancak desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="3aea5-111">These types were publicly visible, but unsupported.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="3aea5-112">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="3aea5-112">New behavior</span></span>

<span data-ttu-id="3aea5-113">Bu tür `internal`şimdi .</span><span class="sxs-lookup"><span data-stu-id="3aea5-113">These types are now `internal`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="3aea5-114">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="3aea5-114">Reason for change</span></span>

<span data-ttu-id="3aea5-115">`internal` Kapsam, desteklenmeyen ilkeyi daha iyi yansıtır.</span><span class="sxs-lookup"><span data-stu-id="3aea5-115">The `internal` scope better reflects the unsupported policy.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="3aea5-116">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="3aea5-116">Recommended action</span></span>

<span data-ttu-id="3aea5-117">Uygulamanız veya kitaplığınız tarafından kullanılan kopya türleri.</span><span class="sxs-lookup"><span data-stu-id="3aea5-117">Copy types that are used by your app or library.</span></span>

#### <a name="category"></a><span data-ttu-id="3aea5-118">Kategori</span><span class="sxs-lookup"><span data-stu-id="3aea5-118">Category</span></span>

<span data-ttu-id="3aea5-119">ASP.NET Çekirdeği</span><span class="sxs-lookup"><span data-stu-id="3aea5-119">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="3aea5-120">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="3aea5-120">Affected APIs</span></span>

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
