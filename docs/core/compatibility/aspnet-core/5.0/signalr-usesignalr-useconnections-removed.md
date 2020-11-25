---
title: 'Son değişiklik: SignalR: UseSignalR ve UseConnections yöntemleri kaldırıldı'
description: ASP.NET Core 5,0 ' deki ve SignalR başlıklı UseSignalR ve UseConnections yöntemlerinin kaldırıldığı Son değişiklik hakkında bilgi edinin
author: scottaddie
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: 1b1fce04518e69927cdc1650cc1e19107cc81e3b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95761405"
---
# <a name="signalr-usesignalr-and-useconnections-methods-removed"></a>SignalR: UseSignalR ve UseConnections yöntemleri kaldırıldı

ASP.NET Core 3,0 ' de, SignalR bir uç nokta yönlendirme benimsemiştir. Bu değişikliğin bir parçası olarak,, <xref:Microsoft.AspNetCore.Builder.SignalRAppBuilderExtensions.UseSignalR%2A> <xref:Microsoft.AspNetCore.Builder.ConnectionsAppBuilderExtensions.UseConnections%2A> ve bazı ilgili yöntemler artık kullanılmıyor olarak işaretlendi. ASP.NET Core 5,0 ' de, eski yöntemler kaldırılmıştır. Yöntemlerin tam listesi için bkz. [etkilenen API 'ler](#affected-apis).

Bu sorunla ilgili tartışmak için bkz. [DotNet/aspnetcore # 20082](https://github.com/dotnet/aspnetcore/issues/20082).

## <a name="version-introduced"></a>Sunulan sürüm

5,0 Preview 3

## <a name="old-behavior"></a>Eski davranış

SignalR hub 'ları ve bağlantı işleyicileri, veya yöntemlerini kullanarak ara yazılım ardışık düzenine `UseSignalR` kaydedilebilir `UseConnections` .

## <a name="new-behavior"></a>Yeni davranış

SignalR hub 'ları ve bağlantı işleyicileri <xref:Microsoft.AspNetCore.Builder.EndpointRoutingApplicationBuilderExtensions.UseEndpoints%2A> , <xref:Microsoft.AspNetCore.SignalR.HubRouteBuilder.MapHub%2A> <xref:Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder.MapConnectionHandler%2A> üzerinde ve genişletme yöntemleri kullanılarak kaydedilmelidir <xref:Microsoft.AspNetCore.Routing.IEndpointRouteBuilder> .

## <a name="reason-for-change"></a>Değişiklik nedeni

Eski yöntemlerde, ASP.NET Core diğer yönlendirme bileşenleriyle etkileşime girmediğiniz özel yönlendirme mantığı vardı. ASP.NET Core 3,0 ' de, uç nokta yönlendirme olarak adlandırılan yeni bir genel amaçlı yönlendirme sistemi tanıtılmıştı. Uç nokta yönlendirme özelliği, diğer yönlendirme bileşenleriyle etkileşim kurmak için SignalR. Bu modele geçiş yapmak, kullanıcıların Endpoint Routing 'in tüm avantajlarını belirlemesine olanak sağlar. Sonuç olarak, eski yöntemler kaldırılmıştır.

## <a name="recommended-action"></a>Önerilen eylem

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

## <a name="affected-apis"></a>Etkilenen API’ler

- <xref:Microsoft.AspNetCore.Builder.ConnectionsAppBuilderExtensions.UseConnections%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Builder.SignalRAppBuilderExtensions.UseSignalR%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder.MapConnections%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder.MapConnectionHandler%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.SignalR.HubRouteBuilder.MapHub%2A?displayProperty=nameWithType>

<!--

### Category

ASP.NET Core

### Affected APIs

- `Overload:Microsoft.AspNetCore.Builder.ConnectionsAppBuilderExtensions.UseConnections`
- `Overload:Microsoft.AspNetCore.Builder.SignalRAppBuilderExtensions.UseSignalR`
- `Overload:Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder.MapConnections`
- `Overload:Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder.MapConnectionHandler`
- `Overload:Microsoft.AspNetCore.SignalR.HubRouteBuilder.MapHub`

-->
