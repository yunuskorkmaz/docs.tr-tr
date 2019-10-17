---
ms.openlocfilehash: 1c9c899d77dd69e185281d98bfec18ce73d80815
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394105"
---
### <a name="kestrel-empty-https-assembly-removed"></a>Kestrel: boş HTTPS derlemesi kaldırıldı

@No__t-0 derleme kaldırıldı.

#### <a name="version-introduced"></a>Sunulan sürüm

3.0

#### <a name="reason-for-change"></a>Değişiklik nedeni

ASP.NET Core 2,1 ' de, `Microsoft.AspNetCore.Server.Kestrel.Https` ' ın içerikleri <xref:Microsoft.AspNetCore.Server.Kestrel.Core?displayProperty=fullName> ' e taşındı. Bu değişiklik, `[TypeForwardedTo]` öznitelikleri kullanılarak kırılmamış bir şekilde gerçekleştirildi.

#### <a name="recommended-action"></a>Önerilen eylem

- @No__t-0 2,0 'e başvuran Kitaplıklar tüm ASP.NET Core bağımlılıklarını 2,1 veya sonraki bir sürüme güncelleştirmeniz gerekir. Aksi takdirde, ASP.NET Core 3,0 uygulamasına yüklendiğinde bu uygulamalar kesintiye uğrabilirler.
- ASP.NET Core 2,1 ve üzeri hedefleme uygulamaları ve kitaplıkları `Microsoft.AspNetCore.Server.Kestrel.Https` NuGet paketine doğrudan başvuruları kaldırmalıdır.

#### <a name="category"></a>Kategori

ASP.NET Core

#### <a name="affected-apis"></a>Etkilenen API’ler

Yok.

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
