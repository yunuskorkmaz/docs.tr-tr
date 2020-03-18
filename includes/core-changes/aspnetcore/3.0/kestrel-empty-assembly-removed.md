---
ms.openlocfilehash: 1c9c899d77dd69e185281d98bfec18ce73d80815
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394105"
---
### <a name="kestrel-empty-https-assembly-removed"></a>Kerkenez: Boş HTTPS derlemesi kaldırıldı

Derleme <xref:Microsoft.AspNetCore.Server.Kestrel.Https?displayProperty=fullName> kaldırıldı.

#### <a name="version-introduced"></a>Sürüm tanıtıldı

3,0

#### <a name="reason-for-change"></a>Değişiklik nedeni

ASP.NET Core 2.1'de `Microsoft.AspNetCore.Server.Kestrel.Https` içeriği <xref:Microsoft.AspNetCore.Server.Kestrel.Core?displayProperty=fullName>. Bu değişiklik öznitelikleri kullanarak `[TypeForwardedTo]` kırılmayan bir şekilde yapıldı.

#### <a name="recommended-action"></a>Önerilen eylem

- 2.0'a başvuran `Microsoft.AspNetCore.Server.Kestrel.Https` kitaplıklar, Temel bağımlılıkASP.NET tümASP.NET 2.1 veya sonraki güncelleştirmeleri gerekir. Aksi takdirde, ASP.NET Core 3.0 uygulamasına yüklendiklerinde kırılabilirler.
- Core 2.1 ve daha sonra ASP.NET hedefleyen uygulamalar ve `Microsoft.AspNetCore.Server.Kestrel.Https` kütüphaneler NuGet paketine yapılan doğrudan başvuruları kaldırmalıdır.

#### <a name="category"></a>Kategori

ASP.NET Çekirdeği

#### <a name="affected-apis"></a>Etkilenen API’ler

None

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
