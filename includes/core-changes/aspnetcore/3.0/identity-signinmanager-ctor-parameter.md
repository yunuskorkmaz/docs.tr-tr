---
ms.openlocfilehash: ed5a90063b8963d79f412ec1c5c0b9030f980f83
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032788"
---
### <a name="identity-signinmanager-constructor-accepts-new-parameter"></a>Kimlik: SignInManager Oluşturucusu yeni parametreyi kabul ediyor

ASP.NET Core 3,0 ' den başlayarak, oluşturucuya yeni bir `IUserConfirmation<TUser>` parametre eklenmiştir `SignInManager` . Daha fazla bilgi için bkz. [DotNet/aspnetcore # 8356](https://github.com/dotnet/aspnetcore/issues/8356).

#### <a name="version-introduced"></a>Sunulan sürüm

3,0

#### <a name="reason-for-change"></a>Değişiklik nedeni

Değişiklik için mosyon, kimlik içinde yeni e-posta/onay akışları için destek eklemektir.

#### <a name="recommended-action"></a>Önerilen eylem

El ile oluşturuyorsanız `SignInManager` , `IUserConfirmation` sağlama veya bağımlılık ekleme için bir uygulama sağlayın.

#### <a name="category"></a>Kategori

ASP.NET Core

#### <a name="affected-apis"></a>Etkilenen API’ler

<xref:Microsoft.AspNetCore.Identity.SignInManager%601.%23ctor%2A>

<!--

#### Affected APIs

`Overload:Microsoft.AspNetCore.Identity.SignInManager`1.#ctor`

-->
