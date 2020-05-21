---
ms.openlocfilehash: fb23418816abcae125106c93b339a546aa9bc2ee
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721540"
---
### <a name="kestrel-transport-abstractions-removed-and-made-public"></a>Kestrel: kaldırılan ve genel kullanıma açık olan taşıma soyutlamaları

"Pubternal" API 'lerinden uzaklaşma kapsamında, Kestrel aktarım katmanı API 'Leri kitaplıkta ortak bir arabirim olarak sunulur `Microsoft.AspNetCore.Connections.Abstractions` .

#### <a name="version-introduced"></a>Sunulan sürüm

3.0

#### <a name="old-behavior"></a>Eski davranış

- Taşıma ile ilgili soyutlamalar `Microsoft.AspNetCore.Server.Kestrel.Transport.Abstractions` kitaplıkta kullanılabilir.
- `ListenOptions.NoDelay`Özellik kullanılabilir.

#### <a name="new-behavior"></a>Yeni davranış

- Arabirim, kitaplıkta `IConnectionListener` `Microsoft.AspNetCore.Connections.Abstractions` en çok kullanılan işlevselliği kullanıma sunmak için kitaplıkta tanıtılmıştı `...Transport.Abstractions` .
- `NoDelay`Artık aktarım seçeneklerinde ( `LibuvTransportOptions` ve `SocketTransportOptions` ) kullanılabilir.
- `SchedulingMode`artık kullanılamıyor.

#### <a name="reason-for-change"></a>Değişiklik nedeni

ASP.NET Core 3,0, "pubternal" API 'Lerinden uzağa taşındı.

#### <a name="recommended-action"></a>Önerilen eylem

#### <a name="category"></a>Kategori

ASP.NET Core

#### <a name="affected-apis"></a>Etkilenen API’ler

Yok

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
