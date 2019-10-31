---
ms.openlocfilehash: 74b989a2413d2192f7cf5208e400eaed879ea096
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73198587"
---
### <a name="authorization-iauthorizationpolicyprovider-implementations-require-new-method"></a>Yetkilendirme: ıauthorizationpolicyprovider uygulamaları için yeni yöntem gerekir

ASP.NET Core 3,0 ' de, yeni bir `GetFallbackPolicyAsync` yöntemi `IAuthorizationPolicyProvider` ' e eklenmiştir. Bu geri dönüş ilkesi, ilke belirtilmediğinde yetkilendirme ara yazılımı tarafından kullanılır.

Daha fazla bilgi için bkz. [ASPNET/AspNetCore # 9759](https://github.com/aspnet/AspNetCore/pull/9759).

#### <a name="version-introduced"></a>Sunulan sürüm

3.0

#### <a name="old-behavior"></a>Eski davranış

`IAuthorizationPolicyProvider` uygulamalarında `GetFallbackPolicyAsync` yöntemi gerekli değildir.

#### <a name="new-behavior"></a>Yeni davranış

`IAuthorizationPolicyProvider` uygulamaları `GetFallbackPolicyAsync` bir yöntem gerektirir.

#### <a name="reason-for-change"></a>Değişiklik nedeni

Yeni `AuthorizationMiddleware` bir ilke belirtilmediğinde kullanması için yeni bir yöntem gerekiyordu.

#### <a name="recommended-action"></a>Önerilen eylem

`GetFallbackPolicyAsync` yöntemini `IAuthorizationPolicyProvider`uygulamanıza ekleyin.

#### <a name="category"></a>Kategori

ASP.NET Core

#### <a name="affected-apis"></a>Etkilenen API’ler

<xref:Microsoft.AspNetCore.Authorization.IAuthorizationPolicyProvider?displayProperty=fullName>

<!-- 

#### Affected APIs

`T:Microsoft.AspNetCore.Authorization.IAuthorizationPolicyProvider`

-->
