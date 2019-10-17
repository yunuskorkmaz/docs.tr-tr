---
ms.openlocfilehash: f95c3916f4da8164cf927344f60f2845f04ddc5c
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72393985"
---
### <a name="kestrel-transport-abstractions-removed-and-made-public"></a>Kestrel: kaldırılan ve genel kullanıma açık olan taşıma soyutlamaları

"Pubternal" API 'lerinden uzaklaşma kapsamında, Kestrel aktarım katmanı API 'Leri `Microsoft.AspNetCore.Connections.Abstractions` kitaplığında ortak arabirim olarak sunulur.

#### <a name="version-introduced"></a>Sunulan sürüm

3.0

#### <a name="old-behavior"></a>Eski davranış

- Taşıma ile ilgili soyutlamalar `Microsoft.AspNetCore.Server.Kestrel.Transport.Abstractions` kitaplığı 'nda mevcuttur.
- @No__t-0 özelliği kullanılabilir.

#### <a name="new-behavior"></a>Yeni davranış

- @No__t-0 arabirimi, `...Transport.Abstractions` kitaplığından en çok kullanılan işlevselliği göstermek için `Microsoft.AspNetCore.Connections.Abstractions` kitaplığında tanıtılmıştı.
- @No__t-0 artık aktarım seçeneklerinde (`LibuvTransportOptions` ve `SocketTransportOptions`) kullanılabilir.
- `SchedulingMode` artık kullanılamıyor.

#### <a name="reason-for-change"></a>Değişiklik nedeni

ASP.NET Core 3,0, "pubternal" API 'Lerinden uzağa taşındı.

#### <a name="recommended-action"></a>Önerilen eylem

#### <a name="category"></a>Kategori

ASP.NET Core

#### <a name="affected-apis"></a>Etkilenen API’ler

Yok.

<!-- 

### Affected APIs

Not detectable via API analysis

-->
