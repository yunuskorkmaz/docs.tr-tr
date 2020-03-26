---
ms.openlocfilehash: 329ef39c7626ecd743577f336a4c8cd4a38fb082
ms.sourcegitcommit: e48a54ebe62e874500a7043f6ee0b77a744d55b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/26/2020
ms.locfileid: "80291668"
---
### <a name="signalr-usesignalr-and-useconnections-methods-removed"></a><span data-ttu-id="19b6d-101">SignalR: UseSignalR ve UseConnections yöntemleri kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="19b6d-101">SignalR: UseSignalR and UseConnections methods removed</span></span>

<span data-ttu-id="19b6d-102">ASP.NET Core 3.0'da SignalR uç nokta yönlendirmeyi benimsedi.</span><span class="sxs-lookup"><span data-stu-id="19b6d-102">In ASP.NET Core 3.0, SignalR adopted endpoint routing.</span></span> <span data-ttu-id="19b6d-103">Bu değişikliğin bir parçası <xref:Microsoft.AspNetCore.Builder.SignalRAppBuilderExtensions.UseSignalR%2A> <xref:Microsoft.AspNetCore.Builder.ConnectionsAppBuilderExtensions.UseConnections%2A>olarak, , , ve bazı ilgili yöntemler eski olarak işaretlenmiştir.</span><span class="sxs-lookup"><span data-stu-id="19b6d-103">As part of that change, the <xref:Microsoft.AspNetCore.Builder.SignalRAppBuilderExtensions.UseSignalR%2A>, <xref:Microsoft.AspNetCore.Builder.ConnectionsAppBuilderExtensions.UseConnections%2A>, and some related methods were marked as obsolete.</span></span> <span data-ttu-id="19b6d-104">Core 5.0ASP.NET, bu eski yöntemler kaldırıldı.</span><span class="sxs-lookup"><span data-stu-id="19b6d-104">In ASP.NET Core 5.0, those obsolete methods were removed.</span></span> <span data-ttu-id="19b6d-105">Yöntemlerin tam listesi için [Etkilenen API'ler'e](#affected-apis)bakın.</span><span class="sxs-lookup"><span data-stu-id="19b6d-105">For the full list of methods, see [Affected APIs](#affected-apis).</span></span>

<span data-ttu-id="19b6d-106">Bu konuda tartışma için [dotnet/aspnetcore#20082'ye](https://github.com/dotnet/aspnetcore/issues/20082)bakın.</span><span class="sxs-lookup"><span data-stu-id="19b6d-106">For discussion on this issue, see [dotnet/aspnetcore#20082](https://github.com/dotnet/aspnetcore/issues/20082).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="19b6d-107">Sürüm tanıtıldı</span><span class="sxs-lookup"><span data-stu-id="19b6d-107">Version introduced</span></span>

<span data-ttu-id="19b6d-108">5.0 Önizleme 3</span><span class="sxs-lookup"><span data-stu-id="19b6d-108">5.0 Preview 3</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="19b6d-109">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="19b6d-109">Old behavior</span></span>

<span data-ttu-id="19b6d-110">SignalR hub'ları ve bağlantı işleyicileri, ara yazılım `UseSignalR` `UseConnections` ardışık hatlarına veya yöntemleri kullanılarak kaydedilebilir.</span><span class="sxs-lookup"><span data-stu-id="19b6d-110">SignalR hubs and connection handlers could be registered in the middleware pipeline using the `UseSignalR` or `UseConnections` methods.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="19b6d-111">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="19b6d-111">New behavior</span></span>

<span data-ttu-id="19b6d-112">SignalR hub'ları ve bağlantı işleyicileri <xref:Microsoft.AspNetCore.SignalR.HubRouteBuilder.MapHub%2A> içinde <xref:Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder.MapConnectionHandler%2A> 'deki <xref:Microsoft.AspNetCore.Routing.IEndpointRouteBuilder>uzantı yöntemleri <xref:Microsoft.AspNetCore.Builder.EndpointRoutingApplicationBuilderExtensions.UseEndpoints%2A> kullanılarak kaydedilmelidir.</span><span class="sxs-lookup"><span data-stu-id="19b6d-112">SignalR hubs and connection handlers should be registered within <xref:Microsoft.AspNetCore.Builder.EndpointRoutingApplicationBuilderExtensions.UseEndpoints%2A> using the <xref:Microsoft.AspNetCore.SignalR.HubRouteBuilder.MapHub%2A> and <xref:Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder.MapConnectionHandler%2A> extension methods on <xref:Microsoft.AspNetCore.Routing.IEndpointRouteBuilder>.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="19b6d-113">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="19b6d-113">Reason for change</span></span>

<span data-ttu-id="19b6d-114">Eski yöntemler, ASP.NET Core'daki diğer yönlendirme bileşenleriyle etkileşime girmemiş özel yönlendirme mantığına sahipti.</span><span class="sxs-lookup"><span data-stu-id="19b6d-114">The old methods had custom routing logic that didn't interact with other routing components in ASP.NET Core.</span></span> <span data-ttu-id="19b6d-115">Core 3.0ASP.NETde, uç nokta yönlendirme adı verilen yeni bir genel amaçlı yönlendirme sistemi tanıtıldı.</span><span class="sxs-lookup"><span data-stu-id="19b6d-115">In ASP.NET Core 3.0, a new general-purpose routing system, called endpoint routing, was introduced.</span></span> <span data-ttu-id="19b6d-116">Uç nokta yönlendirme, SignalR'ın diğer yönlendirme bileşenleriyle etkileşimkurmasını sağladı.</span><span class="sxs-lookup"><span data-stu-id="19b6d-116">Endpoint routing enabled SignalR to interact with other routing components.</span></span> <span data-ttu-id="19b6d-117">Bu modele geçiş, kullanıcıların uç nokta yönlendirmenin tüm avantajlarını fark etmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="19b6d-117">Switching to this model allows users to realize the full benefits of endpoint routing.</span></span> <span data-ttu-id="19b6d-118">Sonuç olarak, eski yöntemler kaldırıldı.</span><span class="sxs-lookup"><span data-stu-id="19b6d-118">Consequently, the old methods have been removed.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="19b6d-119">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="19b6d-119">Recommended action</span></span>

<span data-ttu-id="19b6d-120">Çağıran `UseSignalR` kodu veya `UseConnections` projenizin `Startup.Configure` yönteminden kaldırın.</span><span class="sxs-lookup"><span data-stu-id="19b6d-120">Remove code that calls `UseSignalR` or `UseConnections` from your project's `Startup.Configure` method.</span></span> <span data-ttu-id="19b6d-121">Veya, sırasıyla, bir çağrının gövdesi içinde yapılan `UseEndpoints`çağrılarla `MapHub` değiştirin. `MapConnectionHandler`</span><span class="sxs-lookup"><span data-stu-id="19b6d-121">Replace it with calls to `MapHub` or `MapConnectionHandler`, respectively, within the body of a call to `UseEndpoints`.</span></span> <span data-ttu-id="19b6d-122">Örnek:</span><span class="sxs-lookup"><span data-stu-id="19b6d-122">For example:</span></span>

<span data-ttu-id="19b6d-123">**Eski kod:**</span><span class="sxs-lookup"><span data-stu-id="19b6d-123">**Old code:**</span></span>

```csharp
app.UseSignalR(routes =>
{
    routes.MapHub<SomeHub>("/path");
});
```

<span data-ttu-id="19b6d-124">**Yeni kod:**</span><span class="sxs-lookup"><span data-stu-id="19b6d-124">**New code:**</span></span>

```csharp
app.UseEndpoints(endpoints =>
{
    endpoints.MapHub<SomeHub>("/path");
});
```

<span data-ttu-id="19b6d-125">Genel olarak, `MapHub` önceki `MapConnectionHandler` ve aramalarınız doğrudan gövdeden `UseConnections` `UseEndpoints` `UseSignalR` ve çok az değişiklik gerekli olan transfer edilebilir.</span><span class="sxs-lookup"><span data-stu-id="19b6d-125">In general, your previous `MapHub` and `MapConnectionHandler` calls can be transferred directly from the body of `UseSignalR` and `UseConnections` to `UseEndpoints` with little-to-no change needed.</span></span>

#### <a name="category"></a><span data-ttu-id="19b6d-126">Kategori</span><span class="sxs-lookup"><span data-stu-id="19b6d-126">Category</span></span>

<span data-ttu-id="19b6d-127">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="19b6d-127">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="19b6d-128">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="19b6d-128">Affected APIs</span></span>

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
