---
ms.openlocfilehash: ae5a5fbf97ed4a03de7d35b9d5d5ca8de3aebc39
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72393969"
---
### <a name="caching-responsecaching-pubternal-types-changed-to-internal"></a>Önbelleğe alma: ResponseCaching "pubternal" türleri iç olarak değiştirildi

ASP.NET Core 3,0 ' de, `ResponseCaching` ' daki "pubternal" türleri `internal` olarak değiştirilmiştir.

Ayrıca, `IResponseCachingPolicyProvider` ve `IResponseCachingKeyProvider` ' in varsayılan uygulamaları artık `AddResponseCaching` yönteminin bir parçası olarak hizmetlere eklenmez.

#### <a name="change-description"></a>Açıklamayı Değiştir

ASP.NET Core, "pubternal" türleri `public` olarak belirtilir, ancak `.Internal` ile düzeltilen bir ad alanı soneki içinde bulunur. Bu türler genel olsa da, destek ilkesi yoktur ve bu değişiklikler önemli değişikliklere tabidir. Ne yazık ki, bu türlerin yanlışlıkla kullanılması yaygındır ve bu projelerde oluşan değişikliklere neden olacak ve Framework 'ün bakımını yapma yeteneğini sınırlandırmıştır.

#### <a name="version-introduced"></a>Sunulan sürüm

3.0

#### <a name="old-behavior"></a>Eski davranış

Bu türler herkese açık olarak görünür, ancak desteklenmez.

#### <a name="new-behavior"></a>Yeni davranış

Bu türler artık `internal` ' dır.

#### <a name="reason-for-change"></a>Değişiklik nedeni

@No__t-0 kapsamı, desteklenmeyen ilkeyi daha iyi yansıtır.

#### <a name="recommended-action"></a>Önerilen eylem

Uygulamanız veya kitaplığınız tarafından kullanılan türleri kopyalayın.

#### <a name="category"></a>Kategori

ASP.NET Core

#### <a name="affected-apis"></a>Etkilenen API’ler

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
