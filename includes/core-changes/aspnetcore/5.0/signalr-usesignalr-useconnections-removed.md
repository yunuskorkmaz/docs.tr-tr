---
ms.openlocfilehash: 329ef39c7626ecd743577f336a4c8cd4a38fb082
ms.sourcegitcommit: e48a54ebe62e874500a7043f6ee0b77a744d55b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/26/2020
ms.locfileid: "80291668"
---
### <a name="signalr-usesignalr-and-useconnections-methods-removed"></a><span data-ttu-id="8bc6e-101">SignalR: UseSignalR ve UseConnections yöntemleri kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="8bc6e-101">SignalR: UseSignalR and UseConnections methods removed</span></span>

<span data-ttu-id="8bc6e-102">ASP.NET Core 3,0 ' de, SignalR bir uç nokta yönlendirme benimsemiştir.</span><span class="sxs-lookup"><span data-stu-id="8bc6e-102">In ASP.NET Core 3.0, SignalR adopted endpoint routing.</span></span> <span data-ttu-id="8bc6e-103">Bu değişikliğin bir parçası olarak,, <xref:Microsoft.AspNetCore.Builder.SignalRAppBuilderExtensions.UseSignalR%2A> <xref:Microsoft.AspNetCore.Builder.ConnectionsAppBuilderExtensions.UseConnections%2A> ve bazı ilgili yöntemler artık kullanılmıyor olarak işaretlendi.</span><span class="sxs-lookup"><span data-stu-id="8bc6e-103">As part of that change, the <xref:Microsoft.AspNetCore.Builder.SignalRAppBuilderExtensions.UseSignalR%2A>, <xref:Microsoft.AspNetCore.Builder.ConnectionsAppBuilderExtensions.UseConnections%2A>, and some related methods were marked as obsolete.</span></span> <span data-ttu-id="8bc6e-104">ASP.NET Core 5,0 ' de, eski yöntemler kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="8bc6e-104">In ASP.NET Core 5.0, those obsolete methods were removed.</span></span> <span data-ttu-id="8bc6e-105">Yöntemlerin tam listesi için bkz. [etkilenen API 'ler](#affected-apis).</span><span class="sxs-lookup"><span data-stu-id="8bc6e-105">For the full list of methods, see [Affected APIs](#affected-apis).</span></span>

<span data-ttu-id="8bc6e-106">Bu sorunla ilgili tartışmak için bkz. [DotNet/aspnetcore # 20082](https://github.com/dotnet/aspnetcore/issues/20082).</span><span class="sxs-lookup"><span data-stu-id="8bc6e-106">For discussion on this issue, see [dotnet/aspnetcore#20082](https://github.com/dotnet/aspnetcore/issues/20082).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="8bc6e-107">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="8bc6e-107">Version introduced</span></span>

<span data-ttu-id="8bc6e-108">5,0 Preview 3</span><span class="sxs-lookup"><span data-stu-id="8bc6e-108">5.0 Preview 3</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="8bc6e-109">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="8bc6e-109">Old behavior</span></span>

<span data-ttu-id="8bc6e-110">SignalR hub 'ları ve bağlantı işleyicileri, veya yöntemlerini kullanarak ara yazılım ardışık düzenine `UseSignalR` kaydedilebilir `UseConnections` .</span><span class="sxs-lookup"><span data-stu-id="8bc6e-110">SignalR hubs and connection handlers could be registered in the middleware pipeline using the `UseSignalR` or `UseConnections` methods.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="8bc6e-111">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="8bc6e-111">New behavior</span></span>

<span data-ttu-id="8bc6e-112">SignalR hub 'ları ve bağlantı işleyicileri <xref:Microsoft.AspNetCore.Builder.EndpointRoutingApplicationBuilderExtensions.UseEndpoints%2A> , <xref:Microsoft.AspNetCore.SignalR.HubRouteBuilder.MapHub%2A> <xref:Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder.MapConnectionHandler%2A> üzerinde ve genişletme yöntemleri kullanılarak kaydedilmelidir <xref:Microsoft.AspNetCore.Routing.IEndpointRouteBuilder> .</span><span class="sxs-lookup"><span data-stu-id="8bc6e-112">SignalR hubs and connection handlers should be registered within <xref:Microsoft.AspNetCore.Builder.EndpointRoutingApplicationBuilderExtensions.UseEndpoints%2A> using the <xref:Microsoft.AspNetCore.SignalR.HubRouteBuilder.MapHub%2A> and <xref:Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder.MapConnectionHandler%2A> extension methods on <xref:Microsoft.AspNetCore.Routing.IEndpointRouteBuilder>.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="8bc6e-113">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="8bc6e-113">Reason for change</span></span>

<span data-ttu-id="8bc6e-114">Eski yöntemlerde, ASP.NET Core diğer yönlendirme bileşenleriyle etkileşime girmediğiniz özel yönlendirme mantığı vardı.</span><span class="sxs-lookup"><span data-stu-id="8bc6e-114">The old methods had custom routing logic that didn't interact with other routing components in ASP.NET Core.</span></span> <span data-ttu-id="8bc6e-115">ASP.NET Core 3,0 ' de, uç nokta yönlendirme olarak adlandırılan yeni bir genel amaçlı yönlendirme sistemi tanıtılmıştı.</span><span class="sxs-lookup"><span data-stu-id="8bc6e-115">In ASP.NET Core 3.0, a new general-purpose routing system, called endpoint routing, was introduced.</span></span> <span data-ttu-id="8bc6e-116">Uç nokta yönlendirme özelliği, diğer yönlendirme bileşenleriyle etkileşim kurmak için SignalR.</span><span class="sxs-lookup"><span data-stu-id="8bc6e-116">Endpoint routing enabled SignalR to interact with other routing components.</span></span> <span data-ttu-id="8bc6e-117">Bu modele geçiş yapmak, kullanıcıların Endpoint Routing 'in tüm avantajlarını belirlemesine olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="8bc6e-117">Switching to this model allows users to realize the full benefits of endpoint routing.</span></span> <span data-ttu-id="8bc6e-118">Sonuç olarak, eski yöntemler kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="8bc6e-118">Consequently, the old methods have been removed.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="8bc6e-119">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="8bc6e-119">Recommended action</span></span>

<span data-ttu-id="8bc6e-120">`UseSignalR`Projenizin yönteminden veya öğesini çağıran kodu kaldırın `UseConnections` `Startup.Configure` .</span><span class="sxs-lookup"><span data-stu-id="8bc6e-120">Remove code that calls `UseSignalR` or `UseConnections` from your project's `Startup.Configure` method.</span></span> <span data-ttu-id="8bc6e-121">Bunu `MapHub` `MapConnectionHandler` , bir çağrısının gövdesinde, sırasıyla veya olan çağrılarıyla değiştirin `UseEndpoints` .</span><span class="sxs-lookup"><span data-stu-id="8bc6e-121">Replace it with calls to `MapHub` or `MapConnectionHandler`, respectively, within the body of a call to `UseEndpoints`.</span></span> <span data-ttu-id="8bc6e-122">Örnek:</span><span class="sxs-lookup"><span data-stu-id="8bc6e-122">For example:</span></span>

<span data-ttu-id="8bc6e-123">**Eski kod:**</span><span class="sxs-lookup"><span data-stu-id="8bc6e-123">**Old code:**</span></span>

```csharp
app.UseSignalR(routes =>
{
    routes.MapHub<SomeHub>("/path");
});
```

<span data-ttu-id="8bc6e-124">**Yeni kod:**</span><span class="sxs-lookup"><span data-stu-id="8bc6e-124">**New code:**</span></span>

```csharp
app.UseEndpoints(endpoints =>
{
    endpoints.MapHub<SomeHub>("/path");
});
```

<span data-ttu-id="8bc6e-125">Genel olarak, önceki `MapHub` ve `MapConnectionHandler` çağrılarınız, ' ın gövdesinden `UseSignalR` ve en az bir `UseConnections` değişikliğe gerek kalmadan doğrudan aktarılabilir `UseEndpoints` .</span><span class="sxs-lookup"><span data-stu-id="8bc6e-125">In general, your previous `MapHub` and `MapConnectionHandler` calls can be transferred directly from the body of `UseSignalR` and `UseConnections` to `UseEndpoints` with little-to-no change needed.</span></span>

#### <a name="category"></a><span data-ttu-id="8bc6e-126">Kategori</span><span class="sxs-lookup"><span data-stu-id="8bc6e-126">Category</span></span>

<span data-ttu-id="8bc6e-127">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="8bc6e-127">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="8bc6e-128">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="8bc6e-128">Affected APIs</span></span>

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
