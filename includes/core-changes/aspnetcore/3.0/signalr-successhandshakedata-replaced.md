---
ms.openlocfilehash: 1d8bcaf68d44f27642048c1c207b52c55b604690
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75902042"
---
### <a name="signalr-handshakeprotocolsuccesshandshakedata-replaced"></a>SignalR: HandshakeProtocol.SuccessHandshakeData değiştirildi

[HandshakeProtocol.SuccessHandshakeData](https://github.com/dotnet/aspnetcore/blob/c5b2bc0df2a0027832bf7d01dfb19ca39cd08ae6/src/SignalR/common/SignalR.Common/src/Protocol/HandshakeProtocol.cs#L27) alanı kaldırıldı ve belirli `IHubProtocol`bir verilen başarılı bir el sıkışma yanıtı üreten bir yardımcı yöntemi ile değiştirildi .

#### <a name="version-introduced"></a>Sürüm tanıtıldı

3,0

#### <a name="old-behavior"></a>Eski davranış

`HandshakeProtocol.SuccessHandshakeData`bir `public static ReadOnlyMemory<byte>` alandı.

#### <a name="new-behavior"></a>Yeni davranış

`HandshakeProtocol.SuccessHandshakeData`belirtilen protokole dayalı `static` `GetSuccessfulHandshake(IHubProtocol protocol)` bir `ReadOnlyMemory<byte>` döndürür bir yöntem ile değiştirilmiştir.

#### <a name="reason-for-change"></a>Değişiklik nedeni

El sıkışma _yanıtına,_ seçili protokole bağlı olarak sabit olmayan ve değişen ek alanlar eklendi.

#### <a name="recommended-action"></a>Önerilen eylem

Yok. Bu tür, kullanıcı kodundan kullanım için tasarlanmıyor. SignalR `public`sunucusu ve istemcisi arasında paylaşılabilsin diye. .NET'te yazılı müşteri SignalR istemcileri tarafından da kullanılabilir. SignalR **kullanıcıları** bu değişikliktan etkilenmemelidir.

#### <a name="category"></a>Kategori

ASP.NET Çekirdeği

#### <a name="affected-apis"></a>Etkilenen API’ler

<xref:Microsoft.AspNetCore.SignalR.Protocol.HandshakeProtocol.SuccessHandshakeData?displayProperty=namewithType>

<!--

#### Affected APIs

`F:Microsoft.AspNetCore.SignalR.Protocol.HandshakeProtocol.SuccessHandshakeData`

-->
