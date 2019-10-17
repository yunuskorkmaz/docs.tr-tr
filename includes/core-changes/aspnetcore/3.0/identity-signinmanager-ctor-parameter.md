---
ms.openlocfilehash: 56b394c4698f60baeb70d3c17d1abee5d867deb7
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394002"
---
### <a name="identity-signinmanager-constructor-accepts-new-parameter"></a>Kimlik: SignInManager Oluşturucusu yeni parametreyi kabul ediyor

ASP.NET Core 3,0 ' den başlayarak, `SignInManager` oluşturucusuna yeni bir `IUserConfirmation<TUser>` parametresi eklenmiştir. Daha fazla bilgi için bkz. [ASPNET/AspNetCore # 8356](https://github.com/aspnet/AspNetCore/issues/8356).

#### <a name="version-introduced"></a>Sunulan sürüm

3.0

#### <a name="reason-for-change"></a>Değişiklik nedeni

Değişiklik için mosyon, kimlik içinde yeni e-posta/onay akışları için destek eklemektir.

#### <a name="recommended-action"></a>Önerilen eylem

@No__t el ile bir @no__t oluşturursanız-1 ' in bir uygulamasını sağlayın ya da bir bağımlılık ekleme işleminden bir tane alın.

#### <a name="category"></a>Kategori

ASP.NET Core

#### <a name="affected-apis"></a>Etkilenen API’ler

<xref:Microsoft.AspNetCore.Identity.SignInManager%601.%23ctor%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

`Overload:Microsoft.AspNetCore.Identity.SignInManager`1.#ctor`

-->
