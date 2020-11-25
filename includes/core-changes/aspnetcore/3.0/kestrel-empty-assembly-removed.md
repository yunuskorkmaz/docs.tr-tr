---
ms.openlocfilehash: 1c9c899d77dd69e185281d98bfec18ce73d80815
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032811"
---
### <a name="kestrel-empty-https-assembly-removed"></a>Kestrel: boş HTTPS derlemesi kaldırıldı

Derleme <xref:Microsoft.AspNetCore.Server.Kestrel.Https?displayProperty=fullName> kaldırıldı.

#### <a name="version-introduced"></a>Sunulan sürüm

3,0

#### <a name="reason-for-change"></a>Değişiklik nedeni

ASP.NET Core 2,1 ' de, içeriği `Microsoft.AspNetCore.Server.Kestrel.Https` öğesine taşındı <xref:Microsoft.AspNetCore.Server.Kestrel.Core?displayProperty=fullName> . Bu değişiklik öznitelikler kullanılarak kırılmamış bir şekilde gerçekleştirildi `[TypeForwardedTo]` .

#### <a name="recommended-action"></a>Önerilen eylem

- `Microsoft.AspNetCore.Server.Kestrel.Https`2,0 'ye başvuran Kitaplıklar tüm ASP.NET Core bağımlılıklarını 2,1 veya üzeri olarak güncelleştirmemelidir. Aksi takdirde, ASP.NET Core 3,0 uygulamasına yüklendiğinde bu uygulamalar kesintiye uğrabilirler.
- ASP.NET Core 2,1 ve üstünü hedefleyen uygulamalar ve kitaplıklar, NuGet paketine doğrudan başvuruları kaldırmalıdır `Microsoft.AspNetCore.Server.Kestrel.Https` .

#### <a name="category"></a>Kategori

ASP.NET Core

#### <a name="affected-apis"></a>Etkilenen API’ler

Yok

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
