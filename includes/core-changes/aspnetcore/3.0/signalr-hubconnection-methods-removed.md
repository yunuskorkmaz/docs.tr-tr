---
ms.openlocfilehash: de06825f1031d05bc83183a83bae165e2f9512ff
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901717"
---
### <a name="signalr-hubconnection-resetsendping-and-resettimeout-methods-removed"></a>SignalR: HubConnection ResetSendPing ve ResetTimeout yöntemleri kaldırıldı

`ResetSendPing` ve `ResetTimeout` yöntemleri, SignalR `HubConnection` API 'sinden kaldırılmıştır. Bu yöntemler başlangıçta yalnızca iç kullanıma yöneliktir, ancak ASP.NET Core 2,2 ' de genel kullanıma sunulmuştur. Bu yöntemler ASP.NET Core 3,0 Preview 4 sürümünden itibaren kullanılabilir olmayacaktır. Tartışma için bkz. [DotNet/aspnetcore # 8543](https://github.com/dotnet/aspnetcore/issues/8543).

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
