---
ms.openlocfilehash: 6679e38aefa7d61ce430dc5375ff3b35c641ea27
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394186"
---
### <a name="identity-signinasync-throws-exception-for-unauthenticated-identity"></a>Kimlik: SignInAsync kimliği doğrulanmamış kimlik için özel durum atar

Varsayılan olarak, `SignInAsync` ilkeler / kimlikler `IsAuthenticated` için `false`bir özel durum atar.

#### <a name="version-introduced"></a>Sürüm tanıtıldı

3,0

#### <a name="old-behavior"></a>Eski davranış

`SignInAsync`olduğu kimlikler `IsAuthenticated` de dahil olmak üzere herhangi bir `false`ilke / kimlik kabul eder.

#### <a name="new-behavior"></a>Yeni davranış

Varsayılan olarak, `SignInAsync` ilkeler / kimlikler `IsAuthenticated` için `false`bir özel durum atar. Bu davranışı bastırmak için yeni bir bayrak var, ancak varsayılan davranış değişti.

#### <a name="reason-for-change"></a>Değişiklik nedeni

Eski davranış sorunluydu, çünkü varsayılan olarak bu `[Authorize]`  /  `RequireAuthenticatedUser()`ilkeler .

#### <a name="recommended-action"></a>Önerilen eylem

Core 3.0 Preview 6ASP.NET varsayılan `RequireAuthenticatedSignIn` olarak `AuthenticationOptions` üzerinde `true` bir bayrak vardır. Eski davranışı `false` geri yüklemek için bu bayrağı ayarlayın.

#### <a name="category"></a>Kategori

ASP.NET Çekirdeği

#### <a name="affected-apis"></a>Etkilenen API’ler

None

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
