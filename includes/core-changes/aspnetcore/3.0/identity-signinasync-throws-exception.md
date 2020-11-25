---
ms.openlocfilehash: 6679e38aefa7d61ce430dc5375ff3b35c641ea27
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032780"
---
### <a name="identity-signinasync-throws-exception-for-unauthenticated-identity"></a>Kimlik: Signınasync kimliği doğrulanmamış kimlik için özel durum oluşturur

Varsayılan olarak, `SignInAsync` olan sorumlular/kimlikler için bir özel durum `IsAuthenticated` oluşturur `false` .

#### <a name="version-introduced"></a>Sunulan sürüm

3,0

#### <a name="old-behavior"></a>Eski davranış

`SignInAsync` içindeki kimlikler dahil tüm sorumluları/kimlikleri kabul eder `IsAuthenticated` `false` .

#### <a name="new-behavior"></a>Yeni davranış

Varsayılan olarak, `SignInAsync` olan sorumlular/kimlikler için bir özel durum `IsAuthenticated` oluşturur `false` . Bu davranışı bastırmak için yeni bir bayrak bulunur, ancak varsayılan davranış değişmiştir.

#### <a name="reason-for-change"></a>Değişiklik nedeni

Varsayılan olarak, bu sorumlular tarafından reddedildiği için eski davranış soruna neden oldu `[Authorize]`  /  `RequireAuthenticatedUser()` .

#### <a name="recommended-action"></a>Önerilen eylem

ASP.NET Core 3,0 Preview 6 ' da, varsayılan olarak ' de bir `RequireAuthenticatedSignIn` bayrak vardır `AuthenticationOptions` `true` . `false`Eski davranışı geri yüklemek için bu bayrağı ayarlayın.

#### <a name="category"></a>Kategori

ASP.NET Core

#### <a name="affected-apis"></a>Etkilenen API’ler

Yok

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
