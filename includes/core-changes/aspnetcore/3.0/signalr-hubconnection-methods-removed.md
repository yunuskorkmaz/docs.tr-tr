---
ms.openlocfilehash: de06825f1031d05bc83183a83bae165e2f9512ff
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901717"
---
### <a name="signalr-hubconnection-resetsendping-and-resettimeout-methods-removed"></a>SignalR: HubConnection ResetSendPing ve ResetTimeout yöntemleri kaldırıldı

Ve `ResetSendPing` `ResetTimeout` yöntemler SignalR `HubConnection` API kaldırıldı. Bu yöntemler başlangıçta sadece dahili kullanım için tasarlanmıştır ancak ASP.NET Core 2.2'de kamuya açıklanmıştır. Bu yöntemler, ASP.NET Core 3.0 Preview 4 sürümünden başlayarak kullanılamaz. Tartışma için [dotnet/aspnetcore#8543'e](https://github.com/dotnet/aspnetcore/issues/8543)bakın.

#### <a name="version-introduced"></a>Sürüm tanıtıldı

3,0

#### <a name="old-behavior"></a>Eski davranış

API'ler mevcuttü.

#### <a name="new-behavior"></a>Yeni davranış

API'ler kaldırılır.

#### <a name="reason-for-change"></a>Değişiklik nedeni

Bu yöntemler başlangıçta sadece dahili kullanım için tasarlanmıştır ancak ASP.NET Core 2.2'de kamuya açıklanmıştır.

#### <a name="recommended-action"></a>Önerilen eylem

Bu yöntemleri kullanmayın.

#### <a name="category"></a>Kategori

ASP.NET Çekirdeği

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:Microsoft.AspNetCore.SignalR.Client.HubConnection.ResetSendPing?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.SignalR.Client.HubConnection.ResetTimeout?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:Microsoft.AspNetCore.SignalR.Client.HubConnection.ResetSendPing`
- `M:Microsoft.AspNetCore.SignalR.Client.HubConnection.ResetTimeout`

-->
