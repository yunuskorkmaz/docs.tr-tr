---
ms.openlocfilehash: de06825f1031d05bc83183a83bae165e2f9512ff
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032881"
---
### <a name="signalr-hubconnection-resetsendping-and-resettimeout-methods-removed"></a><span data-ttu-id="abf42-101">SignalR: HubConnection ResetSendPing ve ResetTimeout yöntemleri kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="abf42-101">SignalR: HubConnection ResetSendPing and ResetTimeout methods removed</span></span>

<span data-ttu-id="abf42-102">`ResetSendPing`Ve `ResetTimeout` yöntemleri, SignalR API 'sinden kaldırılmıştır `HubConnection` .</span><span class="sxs-lookup"><span data-stu-id="abf42-102">The `ResetSendPing` and `ResetTimeout` methods were removed from the SignalR `HubConnection` API.</span></span> <span data-ttu-id="abf42-103">Bu yöntemler başlangıçta yalnızca iç kullanıma yöneliktir, ancak ASP.NET Core 2,2 ' de genel kullanıma sunulmuştur.</span><span class="sxs-lookup"><span data-stu-id="abf42-103">These methods were originally intended only for internal use but were made public in ASP.NET Core 2.2.</span></span> <span data-ttu-id="abf42-104">Bu yöntemler ASP.NET Core 3,0 Preview 4 sürümünden itibaren kullanılabilir olmayacaktır.</span><span class="sxs-lookup"><span data-stu-id="abf42-104">These methods won't be available starting in the ASP.NET Core 3.0 Preview 4 release.</span></span> <span data-ttu-id="abf42-105">Tartışma için bkz. [DotNet/aspnetcore # 8543](https://github.com/dotnet/aspnetcore/issues/8543).</span><span class="sxs-lookup"><span data-stu-id="abf42-105">For discussion, see [dotnet/aspnetcore#8543](https://github.com/dotnet/aspnetcore/issues/8543).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="abf42-106">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="abf42-106">Version introduced</span></span>

<span data-ttu-id="abf42-107">3,0</span><span class="sxs-lookup"><span data-stu-id="abf42-107">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="abf42-108">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="abf42-108">Old behavior</span></span>

<span data-ttu-id="abf42-109">API 'Ler kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="abf42-109">APIs were available.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="abf42-110">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="abf42-110">New behavior</span></span>

<span data-ttu-id="abf42-111">API 'Ler kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="abf42-111">APIs are removed.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="abf42-112">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="abf42-112">Reason for change</span></span>

<span data-ttu-id="abf42-113">Bu yöntemler başlangıçta yalnızca iç kullanıma yöneliktir, ancak ASP.NET Core 2,2 ' de genel kullanıma sunulmuştur.</span><span class="sxs-lookup"><span data-stu-id="abf42-113">These methods were originally intended only for internal use but were made public in ASP.NET Core 2.2.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="abf42-114">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="abf42-114">Recommended action</span></span>

<span data-ttu-id="abf42-115">Bu yöntemleri kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="abf42-115">Don't use these methods.</span></span>

#### <a name="category"></a><span data-ttu-id="abf42-116">Kategori</span><span class="sxs-lookup"><span data-stu-id="abf42-116">Category</span></span>

<span data-ttu-id="abf42-117">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="abf42-117">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="abf42-118">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="abf42-118">Affected APIs</span></span>

- <xref:Microsoft.AspNetCore.SignalR.Client.HubConnection.ResetSendPing?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.SignalR.Client.HubConnection.ResetTimeout?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:Microsoft.AspNetCore.SignalR.Client.HubConnection.ResetSendPing`
- `M:Microsoft.AspNetCore.SignalR.Client.HubConnection.ResetTimeout`

-->
