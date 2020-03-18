---
ms.openlocfilehash: 2a65caedea2af65796267aa145e275ebff814bf8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394008"
---
### <a name="signalr-usesignalr-and-useconnections-methods-marked-obsolete"></a><span data-ttu-id="9d647-101">SignalR: UseSignalR ve UseConnections yöntemleri eski olarak işaretlenmiş</span><span class="sxs-lookup"><span data-stu-id="9d647-101">SignalR: UseSignalR and UseConnections methods marked obsolete</span></span>

<span data-ttu-id="9d647-102">Yöntemleri `UseConnections` ve `UseSignalR` sınıfları `ConnectionsRouteBuilder` `HubRouteBuilder` ve ASP.NET Core 3.0 eski olarak işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="9d647-102">The methods `UseConnections` and `UseSignalR` and the classes `ConnectionsRouteBuilder` and `HubRouteBuilder` are marked as obsolete in ASP.NET Core 3.0.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="9d647-103">Sürüm tanıtıldı</span><span class="sxs-lookup"><span data-stu-id="9d647-103">Version introduced</span></span>

<span data-ttu-id="9d647-104">3,0</span><span class="sxs-lookup"><span data-stu-id="9d647-104">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="9d647-105">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="9d647-105">Old behavior</span></span>

<span data-ttu-id="9d647-106">SignalR hub yönlendirmesi kullanılarak `UseSignalR` `UseConnections`yapılandırıldı veya .</span><span class="sxs-lookup"><span data-stu-id="9d647-106">SignalR hub routing was configured using `UseSignalR` or `UseConnections`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="9d647-107">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="9d647-107">New behavior</span></span>

<span data-ttu-id="9d647-108">Yönlendirmeyi yapılandırmanın eski yolu obsoleted ve uç nokta yönlendirme ile değiştirildi.</span><span class="sxs-lookup"><span data-stu-id="9d647-108">The old way of configuring routing has been obsoleted and replaced with endpoint routing.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="9d647-109">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="9d647-109">Reason for change</span></span>

<span data-ttu-id="9d647-110">Middleware yeni uç nokta yönlendirme sistemine taşınıyor.</span><span class="sxs-lookup"><span data-stu-id="9d647-110">Middleware is being moved to the new endpoint routing system.</span></span> <span data-ttu-id="9d647-111">Middleware eklemenin eski yolu obsoleted ediliyor.</span><span class="sxs-lookup"><span data-stu-id="9d647-111">The old way of adding middleware is being obsoleted.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="9d647-112">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="9d647-112">Recommended action</span></span>

<span data-ttu-id="9d647-113">`UseSignalR` Değiştir: `UseEndpoints`</span><span class="sxs-lookup"><span data-stu-id="9d647-113">Replace `UseSignalR` with `UseEndpoints`:</span></span>

<span data-ttu-id="9d647-114">**Eski kod:**</span><span class="sxs-lookup"><span data-stu-id="9d647-114">**Old code:**</span></span>

```csharp
app.UseSignalR(routes =>
{
    routes.MapHub<SomeHub>("/path");
});
```

<span data-ttu-id="9d647-115">**Yeni kod:**</span><span class="sxs-lookup"><span data-stu-id="9d647-115">**New code:**</span></span>

```csharp
app.UseEndpoints(endpoints =>
{
    endpoints.MapHub<SomeHub>("/path");
});
```

#### <a name="category"></a><span data-ttu-id="9d647-116">Kategori</span><span class="sxs-lookup"><span data-stu-id="9d647-116">Category</span></span>

<span data-ttu-id="9d647-117">ASP.NET Çekirdeği</span><span class="sxs-lookup"><span data-stu-id="9d647-117">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="9d647-118">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="9d647-118">Affected APIs</span></span>

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
