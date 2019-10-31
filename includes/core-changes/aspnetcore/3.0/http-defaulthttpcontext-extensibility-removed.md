---
ms.openlocfilehash: 7b5ae84d02b83a10a4b9e002fc2ed4ee0833b84c
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73198596"
---
### <a name="http-defaulthttpcontext-extensibility-removed"></a>HTTP: DefaultHttpContext genişletilebilirliği kaldırıldı

ASP.NET Core 3,0 performans geliştirmelerinden bir parçası olarak, `DefaultHttpContext` ' ın genişletilebilirliği kaldırılmıştır. Sınıf artık `sealed` ' dır. Daha fazla bilgi için bkz. [ASPNET/AspNetCore # 6504](https://github.com/aspnet/AspNetCore/pull/6504).

Birim testleriniz `Mock<DefaultHttpContext>` kullanıyorsa, bunun yerine `Mock<HttpContext>` kullanın.

Tartışma için bkz. [ASPNET/AspNetCore # 6534](https://github.com/aspnet/AspNetCore/issues/6534).

#### <a name="version-introduced"></a>Sunulan sürüm

3.0

#### <a name="old-behavior"></a>Eski davranış

Sınıflar `DefaultHttpContext` ' dan türetilebilir.

#### <a name="new-behavior"></a>Yeni davranış

Sınıflar `DefaultHttpContext` ' dan türetilemez.

#### <a name="reason-for-change"></a>Değişiklik nedeni

Genişletilebilirlik başlangıçta `HttpContext` ' a havuza izin vermek için sağlanmış, ancak gereksiz karmaşıklık ve daha önce diğer iyileştirmeler getirmiştir.

#### <a name="recommended-action"></a>Önerilen eylem

Birim testlerinizde `Mock<DefaultHttpContext>` kullanıyorsanız, bunun yerine `Mock<HttpContext>` ' i kullanmaya başlayın.

#### <a name="category"></a>Kategori

ASP.NET Core

#### <a name="affected-apis"></a>Etkilenen API’ler

<xref:Microsoft.AspNetCore.Http.DefaultHttpContext?displayProperty=nameWithType>

<!--

#### Affected APIs

`T:Microsoft.AspNetCore.Http.DefaultHttpContext`

-->
