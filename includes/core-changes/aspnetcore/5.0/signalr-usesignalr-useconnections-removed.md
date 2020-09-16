---
ms.openlocfilehash: 329ef39c7626ecd743577f336a4c8cd4a38fb082
ms.sourcegitcommit: e48a54ebe62e874500a7043f6ee0b77a744d55b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/26/2020
ms.locfileid: "80291668"
---
### <a name="signalr-usesignalr-and-useconnections-methods-removed"></a>SignalR: UseSignalR ve UseConnections yöntemleri kaldırıldı

ASP.NET Core 3,0 ' de, SignalR bir uç nokta yönlendirme benimsemiştir. Bu değişikliğin bir parçası olarak,, <xref:Microsoft.AspNetCore.Builder.SignalRAppBuilderExtensions.UseSignalR%2A> <xref:Microsoft.AspNetCore.Builder.ConnectionsAppBuilderExtensions.UseConnections%2A> ve bazı ilgili yöntemler artık kullanılmıyor olarak işaretlendi. ASP.NET Core 5,0 ' de, eski yöntemler kaldırılmıştır. Yöntemlerin tam listesi için bkz. [etkilenen API 'ler](#affected-apis).

Bu sorunla ilgili tartışmak için bkz. [DotNet/aspnetcore # 20082](https://github.com/dotnet/aspnetcore/issues/20082).

#### <a name="version-introduced"></a>Sunulan sürüm

5,0 Preview 3

#### <a name="old-behavior"></a>Eski davranış

SignalR hub 'ları ve bağlantı işleyicileri, veya yöntemlerini kullanarak ara yazılım ardışık düzenine `UseSignalR` kaydedilebilir `UseConnections` .

#### <a name="new-behavior"></a>Yeni davranış

SignalR hub 'ları ve bağlantı işleyicileri <xref:Microsoft.AspNetCore.Builder.EndpointRoutingApplicationBuilderExtensions.UseEndpoints%2A> , <xref:Microsoft.AspNetCore.SignalR.HubRouteBuilder.MapHub%2A> <xref:Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder.MapConnectionHandler%2A> üzerinde ve genişletme yöntemleri kullanılarak kaydedilmelidir <xref:Microsoft.AspNetCore.Routing.IEndpointRouteBuilder> .

#### <a name="reason-for-change"></a>Değişiklik nedeni

Eski yöntemlerde, ASP.NET Core diğer yönlendirme bileşenleriyle etkileşime girmediğiniz özel yönlendirme mantığı vardı. ASP.NET Core 3,0 ' de, uç nokta yönlendirme olarak adlandırılan yeni bir genel amaçlı yönlendirme sistemi tanıtılmıştı. Uç nokta yönlendirme özelliği, diğer yönlendirme bileşenleriyle etkileşim kurmak için SignalR. Bu modele geçiş yapmak, kullanıcıların Endpoint Routing 'in tüm avantajlarını belirlemesine olanak sağlar. Sonuç olarak, eski yöntemler kaldırılmıştır.

#### <a name="recommended-action"></a>Önerilen eylem

`UseSignalR`Projenizin yönteminden veya öğesini çağıran kodu kaldırın `UseConnections` `Startup.Configure` . Bunu `MapHub` `MapConnectionHandler` , bir çağrısının gövdesinde, sırasıyla veya olan çağrılarıyla değiştirin `UseEndpoints` . Örnek:

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

Genel olarak, önceki `MapHub` ve `MapConnectionHandler` çağrılarınız, ' ın gövdesinden `UseSignalR` ve en az bir `UseConnections` değişikliğe gerek kalmadan doğrudan aktarılabilir `UseEndpoints` .

#### <a name="category"></a>Kategori

ASP.NET Core

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:Microsoft.AspNetCore.Builder.ConnectionsAppBuilderExtensions.UseConnections%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Builder.SignalRAppBuilderExtensions.UseSignalR%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder.MapConnections%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder.MapConnectionHandler%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.SignalR.HubRouteBuilder.MapHub%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:Microsoft.AspNetCore.Builder.ConnectionsAppBuilderExtensions.UseConnections`
- `Overload:Microsoft.AspNetCore.Builder.SignalRAppBuilderExtensions.UseSignalR`
- `Overload:Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder.MapConnections`
- `Overload:Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder.MapConnectionHandler`
- `Overload:Microsoft.AspNetCore.SignalR.HubRouteBuilder.MapHub`

-->
