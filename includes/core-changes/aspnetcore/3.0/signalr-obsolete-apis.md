---
ms.openlocfilehash: 2a65caedea2af65796267aa145e275ebff814bf8
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394008"
---
### <a name="signalr-usesignalr-and-useconnections-methods-marked-obsolete"></a>SignalR: UseSignalR ve UseConnections yöntemleri kullanılmıyor olarak işaretlendi

@No__t-0 ve `UseSignalR` yöntemleri ve `ConnectionsRouteBuilder` ve `HubRouteBuilder` sınıfları ASP.NET Core 3,0 ' de kullanılmıyor olarak işaretlenir.

#### <a name="version-introduced"></a>Sunulan sürüm

3.0

#### <a name="old-behavior"></a>Eski davranış

SignalR hub yönlendirmesi `UseSignalR` veya `UseConnections` kullanılarak yapılandırıldı.

#### <a name="new-behavior"></a>Yeni davranış

Yönlendirmeyi yapılandırmanın eski yolu kullanımdan kaldırılmıştır ve uç nokta yönlendirme ile değiştirilmiştir.

#### <a name="reason-for-change"></a>Değişiklik nedeni

Ara yazılım yeni uç nokta yönlendirme sistemine taşınıyor. Ara yazılım eklemenin eski yolu kullanımdan kaldırılıyor.

#### <a name="recommended-action"></a>Önerilen eylem

@No__t-0 ' i `UseEndpoints` ile değiştirin:

**Eski kod:**

```csharp
app.UseSignalR(routes =>
{
    routes.MapHub<SomeHub>("/path");
});
```

**Yeni kod:**

```csharp
app.UseEndpoints(endpoints =>
{
    endpoints.MapHub<SomeHub>("/path");
});
```

#### <a name="category"></a>Kategori

ASP.NET Core

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:Microsoft.AspNetCore.Builder.ConnectionsAppBuilderExtensions.UseConnections(Microsoft.AspNetCore.Builder.IApplicationBuilder,System.Action{Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder})?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Builder.SignalRAppBuilderExtensions.UseSignalR(Microsoft.AspNetCore.Builder.IApplicationBuilder,System.Action{Microsoft.AspNetCore.SignalR.HubRouteBuilder})?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.SignalR.HubRouteBuilder?displayProperty=fullName>

<!-- 

#### Affected APIs

- `M:Microsoft.AspNetCore.Builder.ConnectionsAppBuilderExtensions.UseConnections(Microsoft.AspNetCore.Builder.IApplicationBuilder,System.Action{Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder})`
- `M:Microsoft.AspNetCore.Builder.SignalRAppBuilderExtensions.UseSignalR(Microsoft.AspNetCore.Builder.IApplicationBuilder,System.Action{Microsoft.AspNetCore.SignalR.HubRouteBuilder})`
- `T:Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder`
- `T:Microsoft.AspNetCore.SignalR.HubRouteBuilder`

-->
