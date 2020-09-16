---
ms.openlocfilehash: 05aec429e28ef74515ef6988d5b064e6d16b7c1b
ms.sourcegitcommit: aa6d8a90a4f5d8fe0f6e967980b8c98433f05a44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/16/2020
ms.locfileid: "90680016"
---
### <a name="signalr-handshakeprotocolsuccesshandshakedata-replaced"></a>SignalR: HandshakeProtocol. Başarıkıandshakedata değişti

[Handshakeprotocol. Fshandshakedata](https://github.com/dotnet/aspnetcore/blob/c5b2bc0df2a0027832bf7d01dfb19ca39cd08ae6/src/SignalR/common/SignalR.Common/src/Protocol/HandshakeProtocol.cs#L27) alanı kaldırılmıştır ve belirli bir el sıkışma yanıtı üreten bir yardımcı yöntemle değiştirilmiştir `IHubProtocol` .

#### <a name="version-introduced"></a>Sunulan sürüm

3.0

#### <a name="old-behavior"></a>Eski davranış

`HandshakeProtocol.SuccessHandshakeData` bir `public static ReadOnlyMemory<byte>` alandır.

#### <a name="new-behavior"></a>Yeni davranış

`HandshakeProtocol.SuccessHandshakeData` , `static` `GetSuccessfulHandshake(IHubProtocol protocol)` belirtilen protokole göre döndüren bir yöntemle değiştirilmiştir `ReadOnlyMemory<byte>` .

#### <a name="reason-for-change"></a>Değişiklik nedeni

El sıkışma _yanıtına_ , sabit olmayan ve seçilen protokole bağlı olarak değişen ek alanlar eklenmiştir.

#### <a name="recommended-action"></a>Önerilen eylem

Yok. Bu tür kullanıcı kodundan kullanılmak üzere tasarlanmamıştır. Bu `public` , SignalR sunucusu ve istemcisi arasında paylaşılabilir. Ayrıca, .NET dilinde yazılmış müşteri SignalR istemcileri tarafından da kullanılabilir. SignalR **kullanıcıları** bu değişiklikten etkilenmemelidir.

#### <a name="category"></a>Kategori

ASP.NET Core

#### <a name="affected-apis"></a>Etkilenen API’ler

<xref:Microsoft.AspNetCore.SignalR.Protocol.HandshakeProtocol.SuccessHandshakeData?displayProperty=nameWithType>

<!--

#### Affected APIs

`F:Microsoft.AspNetCore.SignalR.Protocol.HandshakeProtocol.SuccessHandshakeData`

-->
