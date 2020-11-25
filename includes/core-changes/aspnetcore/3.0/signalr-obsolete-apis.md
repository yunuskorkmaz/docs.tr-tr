---
ms.openlocfilehash: 2a65caedea2af65796267aa145e275ebff814bf8
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032891"
---
### <a name="signalr-usesignalr-and-useconnections-methods-marked-obsolete"></a><span data-ttu-id="56e70-101">SignalR: UseSignalR ve UseConnections yöntemleri kullanılmıyor olarak işaretlendi</span><span class="sxs-lookup"><span data-stu-id="56e70-101">SignalR: UseSignalR and UseConnections methods marked obsolete</span></span>

<span data-ttu-id="56e70-102">Yöntemler `UseConnections` ve `UseSignalR` ve sınıflar `ConnectionsRouteBuilder` ve `HubRouteBuilder` ASP.NET Core 3,0 ' de eski olarak işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="56e70-102">The methods `UseConnections` and `UseSignalR` and the classes `ConnectionsRouteBuilder` and `HubRouteBuilder` are marked as obsolete in ASP.NET Core 3.0.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="56e70-103">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="56e70-103">Version introduced</span></span>

<span data-ttu-id="56e70-104">3,0</span><span class="sxs-lookup"><span data-stu-id="56e70-104">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="56e70-105">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="56e70-105">Old behavior</span></span>

<span data-ttu-id="56e70-106">SignalR hub yönlendirmesi veya kullanılarak yapılandırıldı `UseSignalR` `UseConnections` .</span><span class="sxs-lookup"><span data-stu-id="56e70-106">SignalR hub routing was configured using `UseSignalR` or `UseConnections`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="56e70-107">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="56e70-107">New behavior</span></span>

<span data-ttu-id="56e70-108">Yönlendirmeyi yapılandırmanın eski yolu kullanımdan kaldırılmıştır ve uç nokta yönlendirme ile değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="56e70-108">The old way of configuring routing has been obsoleted and replaced with endpoint routing.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="56e70-109">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="56e70-109">Reason for change</span></span>

<span data-ttu-id="56e70-110">Ara yazılım yeni uç nokta yönlendirme sistemine taşınıyor.</span><span class="sxs-lookup"><span data-stu-id="56e70-110">Middleware is being moved to the new endpoint routing system.</span></span> <span data-ttu-id="56e70-111">Ara yazılım eklemenin eski yolu kullanımdan kaldırılıyor.</span><span class="sxs-lookup"><span data-stu-id="56e70-111">The old way of adding middleware is being obsoleted.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="56e70-112">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="56e70-112">Recommended action</span></span>

<span data-ttu-id="56e70-113">Değiştir `UseSignalR` `UseEndpoints` :</span><span class="sxs-lookup"><span data-stu-id="56e70-113">Replace `UseSignalR` with `UseEndpoints`:</span></span>

<span data-ttu-id="56e70-114">**Eski kod:**</span><span class="sxs-lookup"><span data-stu-id="56e70-114">**Old code:**</span></span>

```csharp
app.UseSignalR(routes =>
{
    routes.MapHub<SomeHub>("/path");
});
```

<span data-ttu-id="56e70-115">**Yeni kod:**</span><span class="sxs-lookup"><span data-stu-id="56e70-115">**New code:**</span></span>

```csharp
app.UseEndpoints(endpoints =>
{
    endpoints.MapHub<SomeHub>("/path");
});
```

#### <a name="category"></a><span data-ttu-id="56e70-116">Kategori</span><span class="sxs-lookup"><span data-stu-id="56e70-116">Category</span></span>

<span data-ttu-id="56e70-117">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="56e70-117">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="56e70-118">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="56e70-118">Affected APIs</span></span>

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
