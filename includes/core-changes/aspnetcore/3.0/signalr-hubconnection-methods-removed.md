---
ms.openlocfilehash: a56c5fc32b5fd274d5da0d9b295918f5ea3b345e
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394116"
---
### <a name="signalr-hubconnection-resetsendping-and-resettimeout-methods-removed"></a>SignalR: HubConnection ResetSendPing ve ResetTimeout yöntemleri kaldırıldı

@No__t-0 ve `ResetTimeout` yöntemleri, SignalR `HubConnection` API 'sinden kaldırılmıştır. Bu yöntemler başlangıçta yalnızca iç kullanıma yöneliktir, ancak ASP.NET Core 2,2 ' de genel kullanıma sunulmuştur. Bu yöntemler ASP.NET Core 3,0 Preview 4 sürümünden itibaren kullanılabilir olmayacaktır. Tartışma için bkz. [ASPNET/AspNetCore # 8543](https://github.com/aspnet/AspNetCore/issues/8543).

#### <a name="version-introduced"></a>Sunulan sürüm

3.0

#### <a name="old-behavior"></a>Eski davranış

API 'Ler kullanılabilir.

#### <a name="new-behavior"></a>Yeni davranış

API 'Ler kaldırılır.

#### <a name="reason-for-change"></a>Değişiklik nedeni

Bu yöntemler başlangıçta yalnızca iç kullanıma yöneliktir, ancak ASP.NET Core 2,2 ' de genel kullanıma sunulmuştur.

#### <a name="recommended-action"></a>Önerilen eylem

Bu yöntemleri kullanmayın.

#### <a name="category"></a>Kategori

ASP.NET Core

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:Microsoft.AspNetCore.SignalR.Client.HubConnection.ResetSendPing?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.SignalR.Client.HubConnection.ResetTimeout?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:Microsoft.AspNetCore.SignalR.Client.HubConnection.ResetSendPing`
- `M:Microsoft.AspNetCore.SignalR.Client.HubConnection.ResetTimeout`

-->
