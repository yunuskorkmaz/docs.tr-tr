---
ms.openlocfilehash: e9278320ee3fdf9e6b89698d187f047c309ea791
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73198591"
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

Yok. Bu tür kullanıcı kodundan kullanılmak üzere tasarlanmamıştır. `public`, bu, SignalR sunucusu ve istemcisi arasında paylaşılabilir. Ayrıca, .NET dilinde yazılmış müşteri SignalR istemcileri tarafından da kullanılabilir. SignalR **kullanıcıları** bu değişiklikten etkilenmemelidir.

#### <a name="category"></a>Kategori

ASP.NET Core

#### <a name="affected-apis"></a>Etkilenen API’ler

<xref:Microsoft.AspNetCore.SignalR.Protocol.HandshakeProtocol.SuccessHandshakeData?displayProperty=namewithType>

<!--

#### Affected APIs

`F:Microsoft.AspNetCore.SignalR.Protocol.HandshakeProtocol.SuccessHandshakeData`

-->
