---
ms.openlocfilehash: f202b39f1a45f740625827be25e72df0e403d605
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901831"
---
### <a name="signalr-javascript-client-package-name-changed"></a><span data-ttu-id="40011-101">SignalR: JavaScript istemci paketi adı değiştirildi</span><span class="sxs-lookup"><span data-stu-id="40011-101">SignalR: JavaScript client package name changed</span></span>

<span data-ttu-id="40011-102">ASP.NET Core 3,0 Preview 7 ' de, SignalR JavaScript istemci paketi adı `@aspnet/signalr` `@microsoft/signalr`olarak değiştirildi.</span><span class="sxs-lookup"><span data-stu-id="40011-102">In ASP.NET Core 3.0 Preview 7, the SignalR JavaScript client package name changed from `@aspnet/signalr` to `@microsoft/signalr`.</span></span> <span data-ttu-id="40011-103">Ad değişikliği, SignalR 'nin Azure SignalR hizmeti sayesinde yalnızca ASP.NET Core uygulamalardan daha fazla yararlı olduğunu yansıtır.</span><span class="sxs-lookup"><span data-stu-id="40011-103">The name change reflects the fact that SignalR is useful in more than just ASP.NET Core apps, thanks to the Azure SignalR Service.</span></span>

<span data-ttu-id="40011-104">Bu değişikliğe tepki vermek için *Package. JSON* dosyalarınızda, `require` deyimlerinizin ve ECMAScript `import` deyiminizdeki başvuruları değiştirin.</span><span class="sxs-lookup"><span data-stu-id="40011-104">To react to this change, change references in your *package.json* files, `require` statements, and ECMAScript `import` statements.</span></span> <span data-ttu-id="40011-105">Bu yeniden adlandırma kapsamında hiçbir API değişmeyecektir.</span><span class="sxs-lookup"><span data-stu-id="40011-105">No API will change as part of this rename.</span></span>

<span data-ttu-id="40011-106">Tartışma için bkz. [DotNet/aspnetcore # 11637](https://github.com/dotnet/aspnetcore/issues/11637).</span><span class="sxs-lookup"><span data-stu-id="40011-106">For discussion, see [dotnet/aspnetcore#11637](https://github.com/dotnet/aspnetcore/issues/11637).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="40011-107">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="40011-107">Version introduced</span></span>

<span data-ttu-id="40011-108">3.0</span><span class="sxs-lookup"><span data-stu-id="40011-108">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="40011-109">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="40011-109">Old behavior</span></span>

<span data-ttu-id="40011-110">İstemci paketi `@aspnet/signalr`olarak adlandırılmıştı.</span><span class="sxs-lookup"><span data-stu-id="40011-110">The client package was named `@aspnet/signalr`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="40011-111">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="40011-111">New behavior</span></span>

<span data-ttu-id="40011-112">İstemci paketine `@microsoft/signalr`adı verilir.</span><span class="sxs-lookup"><span data-stu-id="40011-112">The client package is named `@microsoft/signalr`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="40011-113">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="40011-113">Reason for change</span></span>

<span data-ttu-id="40011-114">Ad değişikliği, SignalR 'nin Azure SignalR hizmeti için teşekkürler ASP.NET Core uygulamalar ötesinde yararlı olduğunu açıklığa kavuşturar.</span><span class="sxs-lookup"><span data-stu-id="40011-114">The name change clarifies that SignalR is useful beyond ASP.NET Core apps, thanks to the Azure SignalR Service.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="40011-115">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="40011-115">Recommended action</span></span>

<span data-ttu-id="40011-116">Yeni pakete geçiş `@microsoft/signalr`.</span><span class="sxs-lookup"><span data-stu-id="40011-116">Switch to the new package `@microsoft/signalr`.</span></span>

#### <a name="category"></a><span data-ttu-id="40011-117">Kategori</span><span class="sxs-lookup"><span data-stu-id="40011-117">Category</span></span>

<span data-ttu-id="40011-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="40011-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="40011-119">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="40011-119">Affected APIs</span></span>

<span data-ttu-id="40011-120">Yok.</span><span class="sxs-lookup"><span data-stu-id="40011-120">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
