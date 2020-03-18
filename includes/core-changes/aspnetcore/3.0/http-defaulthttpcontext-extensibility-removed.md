---
ms.openlocfilehash: 9d138f79fcede4acac837f8d7793aa343ced737c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78290735"
---
### <a name="http-defaulthttpcontext-extensibility-removed"></a>HTTP: VarsayılanHttpContext genişletilebilirlik kaldırıldı

Core 3.0 performans geliştirmelerinin ASP.NET bir parçası olarak, genişletilebilirlik `DefaultHttpContext` kaldırıldı. Sınıf şimdi. `sealed` Daha fazla bilgi için [dotnet/aspnetcore#6504'e](https://github.com/dotnet/aspnetcore/pull/6504)bakın.

Birim testleriniz `Mock<DefaultHttpContext>`kullanıyorsa, kullanın `Mock<HttpContext>` veya `new DefaultHttpContext()` bunun yerine.

Tartışma için [dotnet/aspnetcore#6534'e](https://github.com/dotnet/aspnetcore/issues/6534)bakın.

#### <a name="version-introduced"></a>Sürüm tanıtıldı

3,0

#### <a name="old-behavior"></a>Eski davranış

Sınıflar dan `DefaultHttpContext`türetilebilir.

#### <a name="new-behavior"></a>Yeni davranış

Sınıflar. `DefaultHttpContext`

#### <a name="reason-for-change"></a>Değişiklik nedeni

Genişletilebilirlik başlangıçta havuzlama izin vermek için `HttpContext`sağlanmıştır , ama gereksiz karmaşıklığı tanıttı ve diğer optimizasyonlar engelledi.

#### <a name="recommended-action"></a>Önerilen eylem

Birim testlerinizde `Mock<DefaultHttpContext>` kullanıyorsanız, bunun yerine `Mock<HttpContext>` kullanmaya başlayın.

#### <a name="category"></a>Kategori

ASP.NET Çekirdeği

#### <a name="affected-apis"></a>Etkilenen API’ler

<xref:Microsoft.AspNetCore.Http.DefaultHttpContext?displayProperty=nameWithType>

<!--

#### Affected APIs

`T:Microsoft.AspNetCore.Http.DefaultHttpContext`

-->
