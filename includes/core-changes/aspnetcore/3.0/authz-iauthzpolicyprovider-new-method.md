---
ms.openlocfilehash: 58dbb73902c0226fa81acf1a70de2160f406f6c6
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901773"
---
### <a name="authorization-iauthorizationpolicyprovider-implementations-require-new-method"></a>Yetkilendirme: ıauthorizationpolicyprovider uygulamaları için yeni yöntem gerekir

ASP.NET Core 3,0 ' de, `IAuthorizationPolicyProvider`yeni bir `GetFallbackPolicyAsync` yöntemi eklenmiştir. Bu geri dönüş ilkesi, ilke belirtilmediğinde yetkilendirme ara yazılımı tarafından kullanılır.

Daha fazla bilgi için bkz. [DotNet/aspnetcore # 9759](https://github.com/dotnet/aspnetcore/pull/9759).

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
