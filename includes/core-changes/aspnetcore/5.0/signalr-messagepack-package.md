---
ms.openlocfilehash: ca0792a3fd05d28cecceac1d644e3e4bf64722bc
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80345210"
---
### <a name="signalr-messagepack-hub-protocol-moved-to-messagepack-2x-package"></a>SignalR: MessagePack Hub Protokolü MessagePack 2.x paketine taşındı

Core SignalR [MessagePack Hub Protokolü](/aspnet/core/signalr/messagepackhubprotocol) ASP.NET MessagePack Serileştirme için [MessagePack NuGet paketini](https://www.nuget.org/packages/MessagePack) kullanır. ASP.NET Core 5.0 paketi 1.x'ten en son 2.x paket sürümüne yükseltiyor.

Bu konuda tartışma için [dotnet/aspnetcore#18692'ye](https://github.com/dotnet/aspnetcore/issues/18692)bakın.

#### <a name="version-introduced"></a>Sürüm tanıtıldı

5.0 Önizleme 1

#### <a name="old-behavior"></a>Eski davranış

ASP.NET Core SignalR MessagePack mesajlarını seri hale getirmek ve deserialize etmek için MessagePack 1.x paketini kullandı.

#### <a name="new-behavior"></a>Yeni davranış

ASP.NET Core SignalR MessagePack mesajlarını seri hale getirmek ve deserialize etmek için MessagePack 2.x paketini kullanır.

#### <a name="reason-for-change"></a>Değişiklik nedeni

MessagePack 2.x paketindeki en son geliştirmeler yararlı işlevsellik ekler.

#### <a name="recommended-action"></a>Önerilen eylem

Bu kesme değişikliği aşağıdaki anda geçerlidir:

* <xref:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions>Değerleri ayarlama veya yapılandırma.
* MessagePack API'lerini doğrudan ve aynı projede ASP.NET Core SignalR MessagePack Hub Protokolü'nü kullanmak. Önceki sürüm yerine yeni sürüm yüklenir.

Paket yazarlarının geçiş kılavuzu için [messagepack v1.x'ten MessagePack v2.x'e geçiş](https://github.com/neuecc/MessagePack-CSharp/blob/master/doc/migration.md)e bakın. İleti serileştirme ve deserialization bazı yönleri etkilenir. Özellikle, [DateTime değerlerinin serihale nasıl verildiğine dair davranış değişiklikleri](https://github.com/neuecc/MessagePack-CSharp/blob/master/doc/migration.md#behavioral-changes)vardır.

#### <a name="category"></a>Kategori

ASP.NET Core

#### <a name="affected-apis"></a>Etkilenen API’ler

<xref:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions?displayProperty=nameWithType>

<!--

#### Affected APIs

`T:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions`

-->
