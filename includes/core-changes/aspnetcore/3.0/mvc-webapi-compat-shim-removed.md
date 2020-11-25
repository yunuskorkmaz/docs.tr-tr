---
ms.openlocfilehash: 75945e7ff26c1c6db891d12cef4c16ed210da6af
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032843"
---
### <a name="mvc-web-api-compatibility-shim-removed"></a>MVC: Web API 'SI uyumluluk dolgusu kaldırıldı

ASP.NET Core 3,0 ' den başlayarak, `Microsoft.AspNetCore.Mvc.WebApiCompatShim` paket artık kullanılamıyor.

#### <a name="change-description"></a>Açıklamayı Değiştir

`Microsoft.AspNetCore.Mvc.WebApiCompatShim`(WebApiCompatShim) paketi, mevcut Web API uygulamalarının ASP.NET Core geçişini kolaylaştırmak için ASP.NET 4. x Web API 2 ile ASP.NET Core kısmi uyumluluk sağlar. Ancak, WebApiCompatShim kullanan uygulamalar, son ASP.NET Core sürümlerindeki API ile ilgili özelliklerden faydalanmalarından yararlanabilir. Bu tür özellikler, geliştirilmiş açık API belirtim oluşturma, standartlaştırılmış hata işleme ve istemci kodu oluşturma özelliklerini içerir. API çabalarını 3,0 ' de daha iyi odaklamak için WebApiCompatShim kaldırılmıştır. WebApiCompatShim kullanan mevcut uygulamalar, daha yeni modele geçirilmesi gerekir `[ApiController]` .

#### <a name="version-introduced"></a>Sunulan sürüm

3,0

#### <a name="reason-for-change"></a>Değişiklik nedeni

Web API 'SI uyumluluk dolgusu bir geçiş aracıdır. ASP.NET Core eklenen yeni işlevlere Kullanıcı erişimini kısıtlar.

#### <a name="recommended-action"></a>Önerilen eylem

Bu dolgunun kullanımını kaldırın ve ASP.NET Core kendi kendine benzer işlevlere doğrudan geçirin.

#### <a name="category"></a>Kategori

ASP.NET Core

#### <a name="affected-apis"></a>Etkilenen API’ler

<xref:Microsoft.AspNetCore.Mvc.WebApiCompatShim?displayProperty=fullName>

<!--

#### Affected APIs

N:Microsoft.AspNetCore.Mvc.WebApiCompatShim

-->
