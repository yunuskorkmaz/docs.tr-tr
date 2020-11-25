---
ms.openlocfilehash: 9d138f79fcede4acac837f8d7793aa343ced737c
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032771"
---
### <a name="http-defaulthttpcontext-extensibility-removed"></a>HTTP: DefaultHttpContext genişletilebilirliği kaldırıldı

ASP.NET Core 3,0 performans geliştirmelerinden bir parçası olarak, ' nin genişletilebilirliği `DefaultHttpContext` kaldırılmıştır. Sınıfı artık `sealed` . Daha fazla bilgi için bkz. [DotNet/aspnetcore # 6504](https://github.com/dotnet/aspnetcore/pull/6504).

Birim testleriniz kullanıyorsa `Mock<DefaultHttpContext>` , `Mock<HttpContext>` veya `new DefaultHttpContext()` yerine kullanın.

Tartışma için bkz. [DotNet/aspnetcore # 6534](https://github.com/dotnet/aspnetcore/issues/6534).

#### <a name="version-introduced"></a>Sunulan sürüm

3,0

#### <a name="old-behavior"></a>Eski davranış

Sınıflar öğesinden türetilebilir `DefaultHttpContext` .

#### <a name="new-behavior"></a>Yeni davranış

Sınıflar öğesinden türetilemez `DefaultHttpContext` .

#### <a name="reason-for-change"></a>Değişiklik nedeni

Genişletilebilirlik, başlangıçta havuza izin verecek şekilde sağlandı `HttpContext` , ancak gereksiz karmaşıklık ve başka iyileştirmeler getirmiştir.

#### <a name="recommended-action"></a>Önerilen eylem

`Mock<DefaultHttpContext>`Birim testlerinizde kullanıyorsanız, `Mock<HttpContext>` bunun yerine kullanmaya başlayın.

#### <a name="category"></a>Kategori

ASP.NET Core

#### <a name="affected-apis"></a>Etkilenen API’ler

<xref:Microsoft.AspNetCore.Http.DefaultHttpContext?displayProperty=nameWithType>

<!--

#### Affected APIs

`T:Microsoft.AspNetCore.Http.DefaultHttpContext`

-->
