---
ms.openlocfilehash: f202b39f1a45f740625827be25e72df0e403d605
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901831"
---
### <a name="signalr-javascript-client-package-name-changed"></a><span data-ttu-id="01cc7-101">SignalR: JavaScript istemci paket adı değiştirildi</span><span class="sxs-lookup"><span data-stu-id="01cc7-101">SignalR: JavaScript client package name changed</span></span>

<span data-ttu-id="01cc7-102">Core 3.0 Preview 7ASP.NET, SignalR JavaScript istemci `@aspnet/signalr` `@microsoft/signalr`paket adı .</span><span class="sxs-lookup"><span data-stu-id="01cc7-102">In ASP.NET Core 3.0 Preview 7, the SignalR JavaScript client package name changed from `@aspnet/signalr` to `@microsoft/signalr`.</span></span> <span data-ttu-id="01cc7-103">Ad değişikliği, Azure SignalR Hizmeti sayesinde SignalR'ın ASP.NET Core uygulamasından daha kullanışlı olduğu gerçeğini yansıtır.</span><span class="sxs-lookup"><span data-stu-id="01cc7-103">The name change reflects the fact that SignalR is useful in more than just ASP.NET Core apps, thanks to the Azure SignalR Service.</span></span>

<span data-ttu-id="01cc7-104">Bu değişikliğe tepki vermek *için, paket.json* dosyalarınızdaki, `require` deyimlerinizdeki ve ECMAScript `import` deyimlerinizdeki başvuruları değiştirin.</span><span class="sxs-lookup"><span data-stu-id="01cc7-104">To react to this change, change references in your *package.json* files, `require` statements, and ECMAScript `import` statements.</span></span> <span data-ttu-id="01cc7-105">Bu yeniden adın bir parçası olarak hiçbir API değişmez.</span><span class="sxs-lookup"><span data-stu-id="01cc7-105">No API will change as part of this rename.</span></span>

<span data-ttu-id="01cc7-106">Tartışma için [dotnet/aspnetcore#11637'ye](https://github.com/dotnet/aspnetcore/issues/11637)bakın.</span><span class="sxs-lookup"><span data-stu-id="01cc7-106">For discussion, see [dotnet/aspnetcore#11637](https://github.com/dotnet/aspnetcore/issues/11637).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="01cc7-107">Sürüm tanıtıldı</span><span class="sxs-lookup"><span data-stu-id="01cc7-107">Version introduced</span></span>

<span data-ttu-id="01cc7-108">3,0</span><span class="sxs-lookup"><span data-stu-id="01cc7-108">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="01cc7-109">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="01cc7-109">Old behavior</span></span>

<span data-ttu-id="01cc7-110">İstemci paketi `@aspnet/signalr`nin adı .</span><span class="sxs-lookup"><span data-stu-id="01cc7-110">The client package was named `@aspnet/signalr`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="01cc7-111">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="01cc7-111">New behavior</span></span>

<span data-ttu-id="01cc7-112">İstemci paketi `@microsoft/signalr`nin adı .</span><span class="sxs-lookup"><span data-stu-id="01cc7-112">The client package is named `@microsoft/signalr`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="01cc7-113">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="01cc7-113">Reason for change</span></span>

<span data-ttu-id="01cc7-114">Ad değişikliği, Azure SignalR Hizmeti sayesinde SignalR'ın ASP.NET Core uygulamalarının ötesinde yararlı olduğunu açıklar.</span><span class="sxs-lookup"><span data-stu-id="01cc7-114">The name change clarifies that SignalR is useful beyond ASP.NET Core apps, thanks to the Azure SignalR Service.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="01cc7-115">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="01cc7-115">Recommended action</span></span>

<span data-ttu-id="01cc7-116">Yeni pakete `@microsoft/signalr`geçin.</span><span class="sxs-lookup"><span data-stu-id="01cc7-116">Switch to the new package `@microsoft/signalr`.</span></span>

#### <a name="category"></a><span data-ttu-id="01cc7-117">Kategori</span><span class="sxs-lookup"><span data-stu-id="01cc7-117">Category</span></span>

<span data-ttu-id="01cc7-118">ASP.NET Çekirdeği</span><span class="sxs-lookup"><span data-stu-id="01cc7-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="01cc7-119">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="01cc7-119">Affected APIs</span></span>

<span data-ttu-id="01cc7-120">None</span><span class="sxs-lookup"><span data-stu-id="01cc7-120">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
