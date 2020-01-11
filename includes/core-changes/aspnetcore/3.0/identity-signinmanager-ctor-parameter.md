---
ms.openlocfilehash: 6f8e6d2786d20e055c9bef63891db4d6f88bc64b
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901823"
---
### <a name="identity-signinmanager-constructor-accepts-new-parameter"></a>Kimlik: SignInManager Oluşturucusu yeni parametreyi kabul ediyor

ASP.NET Core 3,0 ' den başlayarak `SignInManager` oluşturucusuna yeni bir `IUserConfirmation<TUser>` parametresi eklenmiştir. Daha fazla bilgi için bkz. [DotNet/aspnetcore # 8356](https://github.com/dotnet/aspnetcore/issues/8356).

#### <a name="version-introduced"></a>Sunulan sürüm

3.0

#### <a name="reason-for-change"></a>Değişiklik nedeni

Değişiklik için mosyon, kimlik içinde yeni e-posta/onay akışları için destek eklemektir.

#### <a name="recommended-action"></a>Önerilen eylem

`SignInManager`el ile oluşturuyorsanız, bir `IUserConfirmation` uygulamasını sağlayın veya bir bağımlılık ekleme işleminden bir tane alın.

#### <a name="category"></a>Kategori

ASP.NET Core

#### <a name="affected-apis"></a>Etkilenen API’ler

<xref:Microsoft.AspNetCore.Identity.SignInManager%601.%23ctor%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

`Overload:Microsoft.AspNetCore.Identity.SignInManager`1.#ctor`

-->
