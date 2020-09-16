---
ms.openlocfilehash: ca0792a3fd05d28cecceac1d644e3e4bf64722bc
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80345210"
---
### <a name="signalr-messagepack-hub-protocol-moved-to-messagepack-2x-package"></a><span data-ttu-id="4aa96-101">SignalR: MessagePack 2. x paketine taşınan MessagePack hub Protokolü</span><span class="sxs-lookup"><span data-stu-id="4aa96-101">SignalR: MessagePack Hub Protocol moved to MessagePack 2.x package</span></span>

<span data-ttu-id="4aa96-102">ASP.NET Core SignalR [MessagePack hub Protokolü](/aspnet/core/signalr/messagepackhubprotocol) MessagePack serileştirme Için [MessagePack NuGet paketini](https://www.nuget.org/packages/MessagePack) kullanır.</span><span class="sxs-lookup"><span data-stu-id="4aa96-102">The ASP.NET Core SignalR [MessagePack Hub Protocol](/aspnet/core/signalr/messagepackhubprotocol) uses the [MessagePack NuGet package](https://www.nuget.org/packages/MessagePack) for MessagePack serialization.</span></span> <span data-ttu-id="4aa96-103">ASP.NET Core 5,0 paketi 1. x sürümünden en son 2. x paketi sürümüne yükseltir.</span><span class="sxs-lookup"><span data-stu-id="4aa96-103">ASP.NET Core 5.0 upgrades the package from 1.x to the latest 2.x package version.</span></span>

<span data-ttu-id="4aa96-104">Bu sorunla ilgili tartışmak için bkz. [DotNet/aspnetcore # 18692](https://github.com/dotnet/aspnetcore/issues/18692).</span><span class="sxs-lookup"><span data-stu-id="4aa96-104">For discussion on this issue, see [dotnet/aspnetcore#18692](https://github.com/dotnet/aspnetcore/issues/18692).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="4aa96-105">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="4aa96-105">Version introduced</span></span>

<span data-ttu-id="4aa96-106">5,0 Preview 1</span><span class="sxs-lookup"><span data-stu-id="4aa96-106">5.0 Preview 1</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="4aa96-107">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="4aa96-107">Old behavior</span></span>

<span data-ttu-id="4aa96-108">ASP.NET Core SignalR, MessagePack iletilerini seri hale getirmek ve seri durumdan çıkarmak için MessagePack 1. x paketini kullandı.</span><span class="sxs-lookup"><span data-stu-id="4aa96-108">ASP.NET Core SignalR used the MessagePack 1.x package to serialize and deserialize MessagePack messages.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="4aa96-109">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="4aa96-109">New behavior</span></span>

<span data-ttu-id="4aa96-110">ASP.NET Core SignalR, MessagePack iletilerinin serileştirilmek ve serisini kaldırmak için MessagePack 2. x paketini kullanır.</span><span class="sxs-lookup"><span data-stu-id="4aa96-110">ASP.NET Core SignalR uses the MessagePack 2.x package to serialize and deserialize MessagePack messages.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="4aa96-111">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="4aa96-111">Reason for change</span></span>

<span data-ttu-id="4aa96-112">MessagePack 2. x paketindeki en son geliştirmeler yararlı işlevsellik ekler.</span><span class="sxs-lookup"><span data-stu-id="4aa96-112">The latest improvements in the MessagePack 2.x package add useful functionality.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="4aa96-113">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="4aa96-113">Recommended action</span></span>

<span data-ttu-id="4aa96-114">Bu son değişiklik şu durumlarda geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="4aa96-114">This breaking change applies when:</span></span>

* <span data-ttu-id="4aa96-115">Değerleri ayarlama veya yapılandırma <xref:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions> .</span><span class="sxs-lookup"><span data-stu-id="4aa96-115">Setting or configuring values on <xref:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions>.</span></span>
* <span data-ttu-id="4aa96-116">MessagePack API 'Lerini doğrudan kullanarak ve aynı projede ASP.NET Core SignalR MessagePack hub protokolünü kullanarak.</span><span class="sxs-lookup"><span data-stu-id="4aa96-116">Using the MessagePack APIs directly and using the ASP.NET Core SignalR MessagePack Hub Protocol in the same project.</span></span> <span data-ttu-id="4aa96-117">Önceki sürüm yerine daha yeni bir sürüm yüklenecektir.</span><span class="sxs-lookup"><span data-stu-id="4aa96-117">The newer version will be loaded instead of the previous version.</span></span>

<span data-ttu-id="4aa96-118">Paket yazarlarından geçiş kılavuzu için bkz. [MessagePack v1. x 'Ten MessagePack v2. x 'e](https://github.com/neuecc/MessagePack-CSharp/blob/master/doc/migration.md)geçiş.</span><span class="sxs-lookup"><span data-stu-id="4aa96-118">For migration guidance from the package authors, see [Migrating from MessagePack v1.x to MessagePack v2.x](https://github.com/neuecc/MessagePack-CSharp/blob/master/doc/migration.md).</span></span> <span data-ttu-id="4aa96-119">İleti serileştirme ve seri durumdan çıkarma özelliklerinin bazı yönleri etkilenir.</span><span class="sxs-lookup"><span data-stu-id="4aa96-119">Some aspects of message serialization and deserialization are affected.</span></span> <span data-ttu-id="4aa96-120">Özellikle, [DateTime değerlerinin serileştirilme şekli için davranış değişiklikleri](https://github.com/neuecc/MessagePack-CSharp/blob/master/doc/migration.md#behavioral-changes)vardır.</span><span class="sxs-lookup"><span data-stu-id="4aa96-120">Specifically, there are [behavioral changes to how DateTime values are serialized](https://github.com/neuecc/MessagePack-CSharp/blob/master/doc/migration.md#behavioral-changes).</span></span>

#### <a name="category"></a><span data-ttu-id="4aa96-121">Kategori</span><span class="sxs-lookup"><span data-stu-id="4aa96-121">Category</span></span>

<span data-ttu-id="4aa96-122">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="4aa96-122">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="4aa96-123">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="4aa96-123">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions?displayProperty=nameWithType>

<!--

#### Affected APIs

`T:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions`

-->
