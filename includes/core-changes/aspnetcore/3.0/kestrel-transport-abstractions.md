---
ms.openlocfilehash: f95c3916f4da8164cf927344f60f2845f04ddc5c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72393985"
---
### <a name="kestrel-transport-abstractions-removed-and-made-public"></a>Kerkenez: Ulaşım soyutlamaları kaldırıldı ve kamuya açıklandı

"Pubternal" API'lerden uzaklaşmanın bir parçası olarak, Kerkenez aktarım katmanı `Microsoft.AspNetCore.Connections.Abstractions` API'leri kütüphanede genel bir arayüz olarak ortaya çıkar.

#### <a name="version-introduced"></a>Sürüm tanıtıldı

3,0

#### <a name="old-behavior"></a>Eski davranış

- Taşımayla ilgili soyutlamalar kütüphanede `Microsoft.AspNetCore.Server.Kestrel.Transport.Abstractions` mevcuttü.
- Tesis `ListenOptions.NoDelay` müsaitti.

#### <a name="new-behavior"></a>Yeni davranış

- Arabirim, `IConnectionListener` `Microsoft.AspNetCore.Connections.Abstractions` `...Transport.Abstractions` kitaplıktan en çok kullanılan işlevselliği ortaya çıkarmak için kitaplıkta tanıtıldı.
- Şimdi `NoDelay` taşıma seçenekleri mevcuttur`LibuvTransportOptions` ( `SocketTransportOptions`ve ).
- `SchedulingMode`artık kullanılamıyor.

#### <a name="reason-for-change"></a>Değişiklik nedeni

ASP.NET Core 3.0 uzak "pubternal" API'ler taşındı.

#### <a name="recommended-action"></a>Önerilen eylem

#### <a name="category"></a>Kategori

ASP.NET Çekirdeği

#### <a name="affected-apis"></a>Etkilenen API’ler

None

<!-- 

### Affected APIs

Not detectable via API analysis

-->
