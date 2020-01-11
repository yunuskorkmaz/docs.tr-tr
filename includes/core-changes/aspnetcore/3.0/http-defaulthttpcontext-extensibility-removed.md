---
ms.openlocfilehash: 1b4b0aba3ea24682ae972bf283ac387692c83781
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75902011"
---
### <a name="http-defaulthttpcontext-extensibility-removed"></a>HTTP: DefaultHttpContext genişletilebilirliği kaldırıldı

ASP.NET Core 3,0 performans geliştirmelerinden bir parçası olarak, `DefaultHttpContext` genişletilebilirliği kaldırılmıştır. Sınıf artık `sealed`. Daha fazla bilgi için bkz. [DotNet/aspnetcore # 6504](https://github.com/dotnet/aspnetcore/pull/6504).

Birim testleriniz `Mock<DefaultHttpContext>`kullanıyorsa, bunun yerine `Mock<HttpContext>` kullanın.

Tartışma için bkz. [DotNet/aspnetcore # 6534](https://github.com/dotnet/aspnetcore/issues/6534).

#### <a name="version-introduced"></a>Sunulan sürüm

3.0

#### <a name="old-behavior"></a>Eski davranış

Sınıflar `DefaultHttpContext`türetilebilir.

#### <a name="new-behavior"></a>Yeni davranış

Sınıflar `DefaultHttpContext`türetilemiyor.

#### <a name="reason-for-change"></a>Değişiklik nedeni

Genişletilebilirlik, başlangıçta `HttpContext`havuza izin verecek şekilde sağlandı, ancak gereksiz karmaşıklık ve başka iyileştirmeler getirmiştir.

#### <a name="recommended-action"></a>Önerilen eylem

Birim testlerinizde `Mock<DefaultHttpContext>` kullanıyorsanız, bunun yerine `Mock<HttpContext>` kullanmaya başlayın.

#### <a name="category"></a>Kategori

ASP.NET Core

#### <a name="affected-apis"></a>Etkilenen API’ler

<xref:Microsoft.AspNetCore.Http.DefaultHttpContext?displayProperty=nameWithType>

<!--

#### Affected APIs

`T:Microsoft.AspNetCore.Http.DefaultHttpContext`

-->
