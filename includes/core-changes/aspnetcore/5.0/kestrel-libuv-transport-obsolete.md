---
ms.openlocfilehash: 203d75f5858c8ff039cf579c0539efda0c5c9f02
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/20/2020
ms.locfileid: "86474390"
---
### <a name="kestrel-libuv-transport-marked-as-obsolete"></a><span data-ttu-id="b1061-101">Kestrel: libuv taşıması eski olarak işaretlendi</span><span class="sxs-lookup"><span data-stu-id="b1061-101">Kestrel: Libuv transport marked as obsolete</span></span>

<span data-ttu-id="b1061-102">Önceki ASP.NET Core sürümleri, zaman uyumsuz giriş ve çıktının nasıl gerçekleştirildiği hakkında bir uygulama ayrıntısı olarak libuv kullandı.</span><span class="sxs-lookup"><span data-stu-id="b1061-102">Earlier versions of ASP.NET Core used Libuv as an implementation detail of how asynchronous input and output was performed.</span></span> <span data-ttu-id="b1061-103">ASP.NET Core 2,0 ' de, alternatif bir <xref:System.Net.Sockets.Socket> tabanlı Aktarım geliştirdik.</span><span class="sxs-lookup"><span data-stu-id="b1061-103">In ASP.NET Core 2.0, an alternative, <xref:System.Net.Sockets.Socket>-based transport was developed.</span></span> <span data-ttu-id="b1061-104">ASP.NET Core 2,1 ' de, Kestrel `Socket` Varsayılan olarak tabanlı aktarımı kullanmaya geçti.</span><span class="sxs-lookup"><span data-stu-id="b1061-104">In ASP.NET Core 2.1, Kestrel switched to using the `Socket`-based transport by default.</span></span> <span data-ttu-id="b1061-105">Uyumluluk nedenleriyle libuv desteği korunmıştı.</span><span class="sxs-lookup"><span data-stu-id="b1061-105">Libuv support was maintained for compatibility reasons.</span></span>

<span data-ttu-id="b1061-106">Bu noktada, tabanlı `Socket` taşımanın kullanımı libuv aktarımından çok daha yaygındır.</span><span class="sxs-lookup"><span data-stu-id="b1061-106">At this point, use of the `Socket`-based transport is far more common than the Libuv transport.</span></span> <span data-ttu-id="b1061-107">Bu nedenle, libuv desteği .NET 5,0 ' de kullanılmıyor olarak işaretlenir ve tamamen .NET 6,0 ' de kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="b1061-107">Consequently, Libuv support is marked as obsolete in .NET 5.0 and will be removed entirely in .NET 6.0.</span></span>

<span data-ttu-id="b1061-108">Bu değişikliğin bir parçası olarak, .NET 5,0 zaman diliminde yeni işletim sistemi platformları (Windows ARM64 gibi) için libuv desteği eklenmez.</span><span class="sxs-lookup"><span data-stu-id="b1061-108">As part of this change, Libuv support for new operating system platforms (like Windows ARM64) won't be added in the .NET 5.0 timeframe.</span></span>

<span data-ttu-id="b1061-109">Libuv aktarımının kullanılması gereken sorunları engelleme hakkında tartışmak için, [DotNet/aspnetcore # 23409](https://github.com/dotnet/aspnetcore/issues/23409)adresindeki GitHub sorununa bakın.</span><span class="sxs-lookup"><span data-stu-id="b1061-109">For discussion on blocking issues that require the use of the Libuv transport, see the GitHub issue at [dotnet/aspnetcore#23409](https://github.com/dotnet/aspnetcore/issues/23409).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="b1061-110">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="b1061-110">Version introduced</span></span>

<span data-ttu-id="b1061-111">5,0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="b1061-111">5.0 Preview 8</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="b1061-112">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="b1061-112">Old behavior</span></span>

<span data-ttu-id="b1061-113">Libuv API 'Leri eski olarak işaretlenmemiş.</span><span class="sxs-lookup"><span data-stu-id="b1061-113">The Libuv APIs aren't marked as obsolete.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="b1061-114">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="b1061-114">New behavior</span></span>

<span data-ttu-id="b1061-115">Libuv API 'Leri eski olarak işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="b1061-115">The Libuv APIs are marked as obsolete.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="b1061-116">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="b1061-116">Reason for change</span></span>

<span data-ttu-id="b1061-117">`Socket`-Tabanlı Aktarım varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="b1061-117">The `Socket`-based transport is the default.</span></span> <span data-ttu-id="b1061-118">Libuv taşımasını kullanmaya devam etmek için etkileyici bir neden yoktur.</span><span class="sxs-lookup"><span data-stu-id="b1061-118">There aren't any compelling reasons to continue using the Libuv transport.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="b1061-119">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="b1061-119">Recommended action</span></span>

<span data-ttu-id="b1061-120">[Libuv paketi](https://www.nuget.org/packages/Libuv) ve genişletme yöntemlerinin kullanımını durdur.</span><span class="sxs-lookup"><span data-stu-id="b1061-120">Discontinue use of the [Libuv package](https://www.nuget.org/packages/Libuv) and extension methods.</span></span>

#### <a name="category"></a><span data-ttu-id="b1061-121">Kategori</span><span class="sxs-lookup"><span data-stu-id="b1061-121">Category</span></span>

<span data-ttu-id="b1061-122">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="b1061-122">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="b1061-123">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="b1061-123">Affected APIs</span></span>

- [<span data-ttu-id="b1061-124">WebHostBuilderLibuvExtensions</span><span class="sxs-lookup"><span data-stu-id="b1061-124">WebHostBuilderLibuvExtensions</span></span>](/dotnet/api/microsoft.aspnetcore.hosting.webhostbuilderlibuvextensions?view=aspnetcore-3.0)
- [<span data-ttu-id="b1061-125">WebHostBuilderLibuvExtensions. UseLibuv</span><span class="sxs-lookup"><span data-stu-id="b1061-125">WebHostBuilderLibuvExtensions.UseLibuv</span></span>](/dotnet/api/microsoft.aspnetcore.hosting.webhostbuilderlibuvextensions.uselibuv?view=aspnetcore-3.0)
- [<span data-ttu-id="b1061-126">Microsoft. AspNetCore. Server. Kestrel. Transport. libuv. LibuvTransportOptions</span><span class="sxs-lookup"><span data-stu-id="b1061-126">Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions</span></span>](/dotnet/api/microsoft.aspnetcore.server.kestrel.transport.libuv.libuvtransportoptions?view=aspnetcore-3.0)
- [<span data-ttu-id="b1061-127">Microsoft. AspNetCore. Server. Kestrel. Transport. libuv. LibuvTransportOptions. ThreadCount</span><span class="sxs-lookup"><span data-stu-id="b1061-127">Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions.ThreadCount</span></span>](/dotnet/api/microsoft.aspnetcore.server.kestrel.transport.libuv.libuvtransportoptions.threadcount?view=aspnetcore-3.0)
- [<span data-ttu-id="b1061-128">Microsoft. AspNetCore. Server. Kestrel. Transport. Lıbuv. LibuvTransportOptions. NoDelay</span><span class="sxs-lookup"><span data-stu-id="b1061-128">Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions.NoDelay</span></span>](/dotnet/api/microsoft.aspnetcore.server.kestrel.transport.libuv.libuvtransportoptions.nodelay?view=aspnetcore-3.0)
- [<span data-ttu-id="b1061-129">Microsoft. AspNetCore. Server. Kestrel. Transport. libuv. LibuvTransportOptions. MaxWriteBufferSize</span><span class="sxs-lookup"><span data-stu-id="b1061-129">Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions.MaxWriteBufferSize</span></span>](/dotnet/api/microsoft.aspnetcore.server.kestrel.transport.libuv.libuvtransportoptions.maxwritebuffersize?view=aspnetcore-3.0)
- [<span data-ttu-id="b1061-130">Microsoft. AspNetCore. Server. Kestrel. Transport. libuv. LibuvTransportOptions. MaxReadBufferSize</span><span class="sxs-lookup"><span data-stu-id="b1061-130">Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions.MaxReadBufferSize</span></span>](/dotnet/api/microsoft.aspnetcore.server.kestrel.transport.libuv.libuvtransportoptions.maxreadbuffersize?view=aspnetcore-3.0)
- `Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions.Backlog`

<!-- 

#### Affected APIs

- `T:Microsoft.AspNetCore.Hosting.WebHostBuilderLibuvExtensions`
- `Overload:Microsoft.AspNetCore.Hosting.WebHostBuilderLibuvExtensions.UseLibuv`
- `T:Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions`
- `P:Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions.ThreadCount`
- `P:Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions.NoDelay`
- `P:Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions.MaxWriteBufferSize`
- `P:Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions.MaxReadBufferSize`
- `P:Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions.Backlog`

-->
