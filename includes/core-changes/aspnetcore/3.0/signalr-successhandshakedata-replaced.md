---
ms.openlocfilehash: fa0f54404d1e14afa6ce48a425c984a48498a1ee
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72393904"
---
### <a name="signalr-handshakeprotocolsuccesshandshakedata-replaced"></a>SignalR: HandshakeProtocol. Başarıkıandshakedata değişti

[Handshakeprotocol. Fshandshakedata](https://github.com/aspnet/AspNetCore/blob/c5b2bc0df2a0027832bf7d01dfb19ca39cd08ae6/src/SignalR/common/SignalR.Common/src/Protocol/HandshakeProtocol.cs#L27) alanı kaldırılmıştır ve, belirli bir `IHubProtocol` verilen başarılı bir el sıkışma yanıtı üreten bir yardımcı yöntemle değiştirilmiştir. 

#### <a name="version-introduced"></a>Sunulan sürüm

3.0

#### <a name="old-behavior"></a>Eski davranış

`HandshakeProtocol.SuccessHandshakeData` bir `public static ReadOnlyMemory<byte>` alanıdır.

#### <a name="new-behavior"></a>Yeni davranış

`HandshakeProtocol.SuccessHandshakeData`, belirtilen protokole göre `ReadOnlyMemory<byte>` döndüren bir `static` `GetSuccessfulHandshake(IHubProtocol protocol)` yöntemiyle değiştirilmiştir. 

#### <a name="reason-for-change"></a>Değişiklik nedeni

El sıkışma _yanıtına_ , sabit olmayan ve seçilen protokole bağlı olarak değişen ek alanlar eklenmiştir.

#### <a name="recommended-action"></a>Önerilen eylem

Yok. Bu tür kullanıcı kodundan kullanılmak üzere tasarlanmamıştır. @No__t-0 olduğundan, SignalR sunucusu ve istemcisi arasında paylaşılabilir. Ayrıca, .NET dilinde yazılmış müşteri SignalR istemcileri tarafından da kullanılabilir. SignalR **kullanıcıları** bu değişiklikten etkilenmemelidir.

#### <a name="category"></a>Kategori

ASP.NET Core

#### <a name="affected-apis"></a>Etkilenen API’ler

<xref:Microsoft.AspNetCore.SignalR.Protocol.HandshakeProtocol.SuccessHandshakeData?displayProperty=namewithType>

<!--

#### Affected APIs

`F:Microsoft.AspNetCore.SignalR.Protocol.HandshakeProtocol.SuccessHandshakeData`

-->
