---
ms.openlocfilehash: 6679e38aefa7d61ce430dc5375ff3b35c641ea27
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394186"
---
### <a name="identity-signinasync-throws-exception-for-unauthenticated-identity"></a>Kimlik: Signınasync kimliği doğrulanmamış kimlik için özel durum oluşturur

Varsayılan olarak, `SignInAsync`, `IsAuthenticated` `false`olduğu sorumlular/kimlikler için bir özel durum oluşturur.

#### <a name="version-introduced"></a>Sunulan sürüm

3,0

#### <a name="old-behavior"></a>Eski davranış

`SignInAsync`, `IsAuthenticated` `false`oldukları kimlikler dahil tüm sorumlularını/kimlikleri kabul eder.

#### <a name="new-behavior"></a>Yeni davranış

Varsayılan olarak, `SignInAsync`, `IsAuthenticated` `false`olduğu sorumlular/kimlikler için bir özel durum oluşturur. Bu davranışı bastırmak için yeni bir bayrak bulunur, ancak varsayılan davranış değişmiştir.

#### <a name="reason-for-change"></a>Değişiklik nedeni

Varsayılan olarak, bu sorumlular `[Authorize]` / `RequireAuthenticatedUser()`tarafından reddedildiği için eski davranış soruna neden oldu.

#### <a name="recommended-action"></a>Önerilen eylem

ASP.NET Core 3,0 Preview 6 ' da, varsayılan olarak `true` `AuthenticationOptions` `RequireAuthenticatedSignIn` bir bayrak vardır. Eski davranışı geri yüklemek için bu bayrağı `false` olarak ayarlayın.

#### <a name="category"></a>Kategori

ASP.NET Core

#### <a name="affected-apis"></a>Etkilenen API’ler

Yok.

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
