---
ms.openlocfilehash: 58dbb73902c0226fa81acf1a70de2160f406f6c6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901773"
---
### <a name="authorization-iauthorizationpolicyprovider-implementations-require-new-method"></a>Yetkilendirme: IAuthorizationPolicyProvider uygulamaları yeni bir yöntem gerektirir

core 3.0ASP.NETde `IAuthorizationPolicyProvider`yeni `GetFallbackPolicyAsync` bir yöntem eklendi. Bu geri dönüş ilkesi, hiçbir ilke belirtilmediğinde yetkilendirme aracı tarafından kullanılır.

Daha fazla bilgi için [dotnet/aspnetcore#9759'a](https://github.com/dotnet/aspnetcore/pull/9759)bakın.

#### <a name="version-introduced"></a>Sürüm tanıtıldı

3,0

#### <a name="old-behavior"></a>Eski davranış

Uygulamaları bir `IAuthorizationPolicyProvider` `GetFallbackPolicyAsync` yöntem gerektirmedi.

#### <a name="new-behavior"></a>Yeni davranış

Uygulamaları bir `IAuthorizationPolicyProvider` `GetFallbackPolicyAsync` yöntem gerektirir.

#### <a name="reason-for-change"></a>Değişiklik nedeni

İlke belirtilmediğinde yeninin `AuthorizationMiddleware` kullanması için yeni bir yöntem gerekiyordu.

#### <a name="recommended-action"></a>Önerilen eylem

Uygulamalarınıza `GetFallbackPolicyAsync` yöntemi `IAuthorizationPolicyProvider`ekleyin.

#### <a name="category"></a>Kategori

ASP.NET Çekirdeği

#### <a name="affected-apis"></a>Etkilenen API’ler

<xref:Microsoft.AspNetCore.Authorization.IAuthorizationPolicyProvider?displayProperty=fullName>

<!-- 

#### Affected APIs

`T:Microsoft.AspNetCore.Authorization.IAuthorizationPolicyProvider`

-->
