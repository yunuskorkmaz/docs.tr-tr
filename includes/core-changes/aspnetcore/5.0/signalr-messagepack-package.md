---
ms.openlocfilehash: ca0792a3fd05d28cecceac1d644e3e4bf64722bc
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80345210"
---
### <a name="signalr-messagepack-hub-protocol-moved-to-messagepack-2x-package"></a><span data-ttu-id="f5949-101">SignalR: MessagePack Hub Protokolü MessagePack 2.x paketine taşındı</span><span class="sxs-lookup"><span data-stu-id="f5949-101">SignalR: MessagePack Hub Protocol moved to MessagePack 2.x package</span></span>

<span data-ttu-id="f5949-102">Core SignalR [MessagePack Hub Protokolü](/aspnet/core/signalr/messagepackhubprotocol) ASP.NET MessagePack Serileştirme için [MessagePack NuGet paketini](https://www.nuget.org/packages/MessagePack) kullanır.</span><span class="sxs-lookup"><span data-stu-id="f5949-102">The ASP.NET Core SignalR [MessagePack Hub Protocol](/aspnet/core/signalr/messagepackhubprotocol) uses the [MessagePack NuGet package](https://www.nuget.org/packages/MessagePack) for MessagePack serialization.</span></span> <span data-ttu-id="f5949-103">ASP.NET Core 5.0 paketi 1.x'ten en son 2.x paket sürümüne yükseltiyor.</span><span class="sxs-lookup"><span data-stu-id="f5949-103">ASP.NET Core 5.0 upgrades the package from 1.x to the latest 2.x package version.</span></span>

<span data-ttu-id="f5949-104">Bu konuda tartışma için [dotnet/aspnetcore#18692'ye](https://github.com/dotnet/aspnetcore/issues/18692)bakın.</span><span class="sxs-lookup"><span data-stu-id="f5949-104">For discussion on this issue, see [dotnet/aspnetcore#18692](https://github.com/dotnet/aspnetcore/issues/18692).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="f5949-105">Sürüm tanıtıldı</span><span class="sxs-lookup"><span data-stu-id="f5949-105">Version introduced</span></span>

<span data-ttu-id="f5949-106">5.0 Önizleme 1</span><span class="sxs-lookup"><span data-stu-id="f5949-106">5.0 Preview 1</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="f5949-107">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="f5949-107">Old behavior</span></span>

<span data-ttu-id="f5949-108">ASP.NET Core SignalR MessagePack mesajlarını seri hale getirmek ve deserialize etmek için MessagePack 1.x paketini kullandı.</span><span class="sxs-lookup"><span data-stu-id="f5949-108">ASP.NET Core SignalR used the MessagePack 1.x package to serialize and deserialize MessagePack messages.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="f5949-109">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="f5949-109">New behavior</span></span>

<span data-ttu-id="f5949-110">ASP.NET Core SignalR MessagePack mesajlarını seri hale getirmek ve deserialize etmek için MessagePack 2.x paketini kullanır.</span><span class="sxs-lookup"><span data-stu-id="f5949-110">ASP.NET Core SignalR uses the MessagePack 2.x package to serialize and deserialize MessagePack messages.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="f5949-111">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="f5949-111">Reason for change</span></span>

<span data-ttu-id="f5949-112">MessagePack 2.x paketindeki en son geliştirmeler yararlı işlevsellik ekler.</span><span class="sxs-lookup"><span data-stu-id="f5949-112">The latest improvements in the MessagePack 2.x package add useful functionality.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="f5949-113">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="f5949-113">Recommended action</span></span>

<span data-ttu-id="f5949-114">Bu kesme değişikliği aşağıdaki anda geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="f5949-114">This breaking change applies when:</span></span>

* <span data-ttu-id="f5949-115"><xref:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions>Değerleri ayarlama veya yapılandırma.</span><span class="sxs-lookup"><span data-stu-id="f5949-115">Setting or configuring values on <xref:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions>.</span></span>
* <span data-ttu-id="f5949-116">MessagePack API'lerini doğrudan ve aynı projede ASP.NET Core SignalR MessagePack Hub Protokolü'nü kullanmak.</span><span class="sxs-lookup"><span data-stu-id="f5949-116">Using the MessagePack APIs directly and using the ASP.NET Core SignalR MessagePack Hub Protocol in the same project.</span></span> <span data-ttu-id="f5949-117">Önceki sürüm yerine yeni sürüm yüklenir.</span><span class="sxs-lookup"><span data-stu-id="f5949-117">The newer version will be loaded instead of the previous version.</span></span>

<span data-ttu-id="f5949-118">Paket yazarlarının geçiş kılavuzu için [messagepack v1.x'ten MessagePack v2.x'e geçiş](https://github.com/neuecc/MessagePack-CSharp/blob/master/doc/migration.md)e bakın.</span><span class="sxs-lookup"><span data-stu-id="f5949-118">For migration guidance from the package authors, see [Migrating from MessagePack v1.x to MessagePack v2.x](https://github.com/neuecc/MessagePack-CSharp/blob/master/doc/migration.md).</span></span> <span data-ttu-id="f5949-119">İleti serileştirme ve deserialization bazı yönleri etkilenir.</span><span class="sxs-lookup"><span data-stu-id="f5949-119">Some aspects of message serialization and deserialization are affected.</span></span> <span data-ttu-id="f5949-120">Özellikle, [DateTime değerlerinin serihale nasıl verildiğine dair davranış değişiklikleri](https://github.com/neuecc/MessagePack-CSharp/blob/master/doc/migration.md#behavioral-changes)vardır.</span><span class="sxs-lookup"><span data-stu-id="f5949-120">Specifically, there are [behavioral changes to how DateTime values are serialized](https://github.com/neuecc/MessagePack-CSharp/blob/master/doc/migration.md#behavioral-changes).</span></span>

#### <a name="category"></a><span data-ttu-id="f5949-121">Kategori</span><span class="sxs-lookup"><span data-stu-id="f5949-121">Category</span></span>

<span data-ttu-id="f5949-122">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="f5949-122">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="f5949-123">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="f5949-123">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions?displayProperty=nameWithType>

<!--

#### Affected APIs

`T:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions`

-->
