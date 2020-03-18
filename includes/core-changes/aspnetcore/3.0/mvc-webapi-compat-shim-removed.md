---
ms.openlocfilehash: 75945e7ff26c1c6db891d12cef4c16ed210da6af
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394405"
---
### <a name="mvc-web-api-compatibility-shim-removed"></a>MVC: Web API uyumluluk şim kaldırıldı

core 3.0 ASP.NET ile `Microsoft.AspNetCore.Mvc.WebApiCompatShim` başlayarak, paket artık kullanılamaz.

#### <a name="change-description"></a>Açıklamayı değiştir

`Microsoft.AspNetCore.Mvc.WebApiCompatShim` (WebApiCompatShim) paketi, mevcut Web API uygulamalarını ASP.NET Core'a geçirmeyi kolaylaştırmak için ASP.NET Core'da ASP.NET 4.x Web API 2 ile kısmi uyumluluk sağlar. Ancak, WebApiCompatShim kullanan uygulamalar, son ASP.NET Core sürümlerinde API ile ilgili özelliklerden yararlanamaz. Bu özellikler arasında geliştirilmiş Açık API belirtimi oluşturma, standartlaştırılmış hata işleme ve istemci kodu oluşturma yer alır. 3.0'daki API çabalarını daha iyi odaklamak için WebApiCompatShim kaldırıldı. WebApiCompatShim'i kullanan varolan uygulamalar yeni `[ApiController]` modele geçmelidir.

#### <a name="version-introduced"></a>Sürüm tanıtıldı

3,0

#### <a name="reason-for-change"></a>Değişiklik nedeni

Web API uyumluluk şim bir geçiş aracıydı. Kullanıcı erişimini ASP.NET Core'a eklenen yeni işlevlere kısıtlamar.

#### <a name="recommended-action"></a>Önerilen eylem

Bu şim kullanımını kaldırın ve doğrudan ASP.NET Core'daki benzer işlevsellik için geçiş yapmak.

#### <a name="category"></a>Kategori

ASP.NET Çekirdeği

#### <a name="affected-apis"></a>Etkilenen API’ler

<xref:Microsoft.AspNetCore.Mvc.WebApiCompatShim?displayProperty=fullName>

<!--

#### Affected APIs

N:Microsoft.AspNetCore.Mvc.WebApiCompatShim

-->
