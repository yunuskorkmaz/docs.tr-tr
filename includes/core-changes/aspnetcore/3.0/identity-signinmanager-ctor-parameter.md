---
ms.openlocfilehash: ed5a90063b8963d79f412ec1c5c0b9030f980f83
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/13/2020
ms.locfileid: "81275504"
---
### <a name="identity-signinmanager-constructor-accepts-new-parameter"></a>Kimlik: SignInManager constructor yeni parametre kabul eder

Core 3.0 ile ASP.NET `IUserConfirmation<TUser>` ile `SignInManager` başlayan, yeni bir parametre oluşturucuya eklendi. Daha fazla bilgi için [dotnet/aspnetcore#8356'ya](https://github.com/dotnet/aspnetcore/issues/8356)bakın.

#### <a name="version-introduced"></a>Sürüm tanıtıldı

3,0

#### <a name="reason-for-change"></a>Değişiklik nedeni

Değişiklik için motivasyon kimlik yeni e-posta / onay akışları için destek eklemek oldu.

#### <a name="recommended-action"></a>Önerilen eylem

El ile bir `SignInManager`inşa, bir `IUserConfirmation` uygulama sağlamak veya sağlamak için bağımlılık enjeksiyon bir kapmak.

#### <a name="category"></a>Kategori

ASP.NET Çekirdeği

#### <a name="affected-apis"></a>Etkilenen API’ler

<xref:Microsoft.AspNetCore.Identity.SignInManager%601.%23ctor%2A>

<!--

#### Affected APIs

`Overload:Microsoft.AspNetCore.Identity.SignInManager`1.#ctor`

-->
