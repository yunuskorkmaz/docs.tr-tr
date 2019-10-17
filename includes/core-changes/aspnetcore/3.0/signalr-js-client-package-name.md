---
ms.openlocfilehash: acef6d7177ee5ad7e18dc8ba1e383d6f76263623
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394189"
---
### <a name="signalr-javascript-client-package-name-changed"></a><span data-ttu-id="eca23-101">SignalR: JavaScript istemci paketi adı değiştirildi</span><span class="sxs-lookup"><span data-stu-id="eca23-101">SignalR: JavaScript client package name changed</span></span>

<span data-ttu-id="eca23-102">ASP.NET Core 3,0 Preview 7 ' de, SignalR JavaScript istemci paketi adı `@aspnet/signalr` ' dan `@microsoft/signalr` ' e değişti.</span><span class="sxs-lookup"><span data-stu-id="eca23-102">In ASP.NET Core 3.0 Preview 7, the SignalR JavaScript client package name changed from `@aspnet/signalr` to `@microsoft/signalr`.</span></span> <span data-ttu-id="eca23-103">Ad değişikliği, SignalR 'nin Azure SignalR hizmeti sayesinde yalnızca ASP.NET Core uygulamalardan daha fazla yararlı olduğunu yansıtır.</span><span class="sxs-lookup"><span data-stu-id="eca23-103">The name change reflects the fact that SignalR is useful in more than just ASP.NET Core apps, thanks to the Azure SignalR Service.</span></span>

<span data-ttu-id="eca23-104">Bu değişikliğe tepki vermek için *Package. JSON* dosyalarınızda, `require` deyimlerinizin ve ECMAScript `import` deyiminizdeki başvuruları değiştirin.</span><span class="sxs-lookup"><span data-stu-id="eca23-104">To react to this change, change references in your *package.json* files, `require` statements, and ECMAScript `import` statements.</span></span> <span data-ttu-id="eca23-105">Bu yeniden adlandırma kapsamında hiçbir API değişmeyecektir.</span><span class="sxs-lookup"><span data-stu-id="eca23-105">No API will change as part of this rename.</span></span>

<span data-ttu-id="eca23-106">Tartışma için bkz. [ASPNET/AspNetCore # 11637](https://github.com/aspnet/AspNetCore/issues/11637).</span><span class="sxs-lookup"><span data-stu-id="eca23-106">For discussion, see [aspnet/AspNetCore#11637](https://github.com/aspnet/AspNetCore/issues/11637).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="eca23-107">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="eca23-107">Version introduced</span></span>

<span data-ttu-id="eca23-108">3.0</span><span class="sxs-lookup"><span data-stu-id="eca23-108">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="eca23-109">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="eca23-109">Old behavior</span></span>

<span data-ttu-id="eca23-110">İstemci paketi `@aspnet/signalr` olarak adlandırılmıştı.</span><span class="sxs-lookup"><span data-stu-id="eca23-110">The client package was named `@aspnet/signalr`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="eca23-111">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="eca23-111">New behavior</span></span>

<span data-ttu-id="eca23-112">İstemci paketinin adı `@microsoft/signalr` ' dır.</span><span class="sxs-lookup"><span data-stu-id="eca23-112">The client package is named `@microsoft/signalr`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="eca23-113">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="eca23-113">Reason for change</span></span>

<span data-ttu-id="eca23-114">Ad değişikliği, SignalR 'nin Azure SignalR hizmeti için teşekkürler ASP.NET Core uygulamalar ötesinde yararlı olduğunu açıklığa kavuşturar.</span><span class="sxs-lookup"><span data-stu-id="eca23-114">The name change clarifies that SignalR is useful beyond ASP.NET Core apps, thanks to the Azure SignalR Service.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="eca23-115">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="eca23-115">Recommended action</span></span>

<span data-ttu-id="eca23-116">Yeni pakete geçiş `@microsoft/signalr`.</span><span class="sxs-lookup"><span data-stu-id="eca23-116">Switch to the new package `@microsoft/signalr`.</span></span>

#### <a name="category"></a><span data-ttu-id="eca23-117">Kategori</span><span class="sxs-lookup"><span data-stu-id="eca23-117">Category</span></span>

<span data-ttu-id="eca23-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="eca23-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="eca23-119">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="eca23-119">Affected APIs</span></span>

<span data-ttu-id="eca23-120">Yok.</span><span class="sxs-lookup"><span data-stu-id="eca23-120">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
