---
ms.openlocfilehash: 58dbb73902c0226fa81acf1a70de2160f406f6c6
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032699"
---
### <a name="authorization-iauthorizationpolicyprovider-implementations-require-new-method"></a>Yetkilendirme: ıauthorizationpolicyprovider uygulamaları için yeni yöntem gerekir

ASP.NET Core 3,0 ' de yeni bir `GetFallbackPolicyAsync` Yöntem eklenmiştir `IAuthorizationPolicyProvider` . Bu geri dönüş ilkesi, ilke belirtilmediğinde yetkilendirme ara yazılımı tarafından kullanılır.

Daha fazla bilgi için bkz. [DotNet/aspnetcore # 9759](https://github.com/dotnet/aspnetcore/pull/9759).

#### <a name="version-introduced"></a>Sunulan sürüm

3,0

#### <a name="old-behavior"></a>Eski davranış

Uygulamabir `IAuthorizationPolicyProvider` `GetFallbackPolicyAsync` metodu gerektirmez.

#### <a name="new-behavior"></a>Yeni davranış

Uygulamaları için `IAuthorizationPolicyProvider` bir `GetFallbackPolicyAsync` Yöntem gerekir.

#### <a name="reason-for-change"></a>Değişiklik nedeni

Yeni bir ilke belirtilmediğinde kullanılması için yeni bir yöntem gerekiyordu `AuthorizationMiddleware` .

#### <a name="recommended-action"></a>Önerilen eylem

`GetFallbackPolicyAsync`Uygulamasına yöntemini ekleyin `IAuthorizationPolicyProvider` .

#### <a name="category"></a>Kategori

ASP.NET Core

#### <a name="affected-apis"></a>Etkilenen API’ler

<xref:Microsoft.AspNetCore.Authorization.IAuthorizationPolicyProvider?displayProperty=fullName>

<!-- 

#### Affected APIs

`T:Microsoft.AspNetCore.Authorization.IAuthorizationPolicyProvider`

-->
