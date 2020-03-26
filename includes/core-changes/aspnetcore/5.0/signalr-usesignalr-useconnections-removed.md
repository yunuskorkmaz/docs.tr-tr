---
ms.openlocfilehash: 329ef39c7626ecd743577f336a4c8cd4a38fb082
ms.sourcegitcommit: e48a54ebe62e874500a7043f6ee0b77a744d55b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/26/2020
ms.locfileid: "80291668"
---
### <a name="signalr-usesignalr-and-useconnections-methods-removed"></a>SignalR: UseSignalR ve UseConnections yöntemleri kaldırıldı

ASP.NET Core 3.0'da SignalR uç nokta yönlendirmeyi benimsedi. Bu değişikliğin bir parçası <xref:Microsoft.AspNetCore.Builder.SignalRAppBuilderExtensions.UseSignalR%2A> <xref:Microsoft.AspNetCore.Builder.ConnectionsAppBuilderExtensions.UseConnections%2A>olarak, , , ve bazı ilgili yöntemler eski olarak işaretlenmiştir. Core 5.0ASP.NET, bu eski yöntemler kaldırıldı. Yöntemlerin tam listesi için [Etkilenen API'ler'e](#affected-apis)bakın.

Bu konuda tartışma için [dotnet/aspnetcore#20082'ye](https://github.com/dotnet/aspnetcore/issues/20082)bakın.

#### <a name="version-introduced"></a>Sürüm tanıtıldı

5.0 Önizleme 3

#### <a name="old-behavior"></a>Eski davranış

SignalR hub'ları ve bağlantı işleyicileri, ara yazılım `UseSignalR` `UseConnections` ardışık hatlarına veya yöntemleri kullanılarak kaydedilebilir.

#### <a name="new-behavior"></a>Yeni davranış

SignalR hub'ları ve bağlantı işleyicileri <xref:Microsoft.AspNetCore.SignalR.HubRouteBuilder.MapHub%2A> içinde <xref:Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder.MapConnectionHandler%2A> 'deki <xref:Microsoft.AspNetCore.Routing.IEndpointRouteBuilder>uzantı yöntemleri <xref:Microsoft.AspNetCore.Builder.EndpointRoutingApplicationBuilderExtensions.UseEndpoints%2A> kullanılarak kaydedilmelidir.

#### <a name="reason-for-change"></a>Değişiklik nedeni

Eski yöntemler, ASP.NET Core'daki diğer yönlendirme bileşenleriyle etkileşime girmemiş özel yönlendirme mantığına sahipti. Core 3.0ASP.NETde, uç nokta yönlendirme adı verilen yeni bir genel amaçlı yönlendirme sistemi tanıtıldı. Uç nokta yönlendirme, SignalR'ın diğer yönlendirme bileşenleriyle etkileşimkurmasını sağladı. Bu modele geçiş, kullanıcıların uç nokta yönlendirmenin tüm avantajlarını fark etmesini sağlar. Sonuç olarak, eski yöntemler kaldırıldı.

#### <a name="recommended-action"></a>Önerilen eylem

Çağıran `UseSignalR` kodu veya `UseConnections` projenizin `Startup.Configure` yönteminden kaldırın. Veya, sırasıyla, bir çağrının gövdesi içinde yapılan `UseEndpoints`çağrılarla `MapHub` değiştirin. `MapConnectionHandler` Örnek:

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

Genel olarak, `MapHub` önceki `MapConnectionHandler` ve aramalarınız doğrudan gövdeden `UseConnections` `UseEndpoints` `UseSignalR` ve çok az değişiklik gerekli olan transfer edilebilir.

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
