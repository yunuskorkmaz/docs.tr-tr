---
ms.openlocfilehash: a16d443a37fb0bb5f6bdc4a39e7dcb4f91c54ead
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394249"
---
### <a name="authorization-iauthorizationpolicyprovider-implementations-require-new-method"></a>Yetkilendirme: ıauthorizationpolicyprovider uygulamaları için yeni yöntem gerekir

ASP.NET Core 3,0 ' de, yeni bir `GetFallbackPolicyAsync` yöntemi `IAuthorizationPolicyProvider` ' e eklenmiştir. Bu geri dönüş ilkesi, ilke belirtilmediğinde yetkilendirme ara yazılımı tarafından kullanılır.

Daha fazla bilgi için bkz. [ASPNET/AspNetCore # 9759](https://github.com/aspnet/AspNetCore/pull/9759). 

#### <a name="version-introduced"></a>Sunulan sürüm

3.0

#### <a name="old-behavior"></a>Eski davranış

@No__t-0 uygulamaları `GetFallbackPolicyAsync` yöntemi gerektirmiyor.

#### <a name="new-behavior"></a>Yeni davranış

@No__t-0 uygulamaları `GetFallbackPolicyAsync` yöntemi gerektirir.

#### <a name="reason-for-change"></a>Değişiklik nedeni

Yeni @no__t için yeni bir yöntem gerekiyordu, hiçbir ilke belirtilmediğinde kullanılacak-0.

#### <a name="recommended-action"></a>Önerilen eylem

@No__t-0 yöntemini `IAuthorizationPolicyProvider` ' in uygulamalarına ekleyin.

#### <a name="category"></a>Kategori

ASP.NET Core

#### <a name="affected-apis"></a>Etkilenen API’ler

<xref:Microsoft.AspNetCore.Authorization.IAuthorizationPolicyProvider?displayProperty=fullName>

<!-- 

#### Affected APIs

`T:Microsoft.AspNetCore.Authorization.IAuthorizationPolicyProvider`

-->
