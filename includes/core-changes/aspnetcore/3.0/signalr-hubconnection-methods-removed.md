---
ms.openlocfilehash: a56c5fc32b5fd274d5da0d9b295918f5ea3b345e
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394116"
---
### <a name="signalr-hubconnection-resetsendping-and-resettimeout-methods-removed"></a><span data-ttu-id="7ae4e-101">SignalR: HubConnection ResetSendPing ve ResetTimeout yöntemleri kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="7ae4e-101">SignalR: HubConnection ResetSendPing and ResetTimeout methods removed</span></span>

<span data-ttu-id="7ae4e-102">@No__t-0 ve `ResetTimeout` yöntemleri, SignalR `HubConnection` API 'sinden kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="7ae4e-102">The `ResetSendPing` and `ResetTimeout` methods were removed from the SignalR `HubConnection` API.</span></span> <span data-ttu-id="7ae4e-103">Bu yöntemler başlangıçta yalnızca iç kullanıma yöneliktir, ancak ASP.NET Core 2,2 ' de genel kullanıma sunulmuştur.</span><span class="sxs-lookup"><span data-stu-id="7ae4e-103">These methods were originally intended only for internal use but were made public in ASP.NET Core 2.2.</span></span> <span data-ttu-id="7ae4e-104">Bu yöntemler ASP.NET Core 3,0 Preview 4 sürümünden itibaren kullanılabilir olmayacaktır.</span><span class="sxs-lookup"><span data-stu-id="7ae4e-104">These methods won't be available starting in the ASP.NET Core 3.0 Preview 4 release.</span></span> <span data-ttu-id="7ae4e-105">Tartışma için bkz. [ASPNET/AspNetCore # 8543](https://github.com/aspnet/AspNetCore/issues/8543).</span><span class="sxs-lookup"><span data-stu-id="7ae4e-105">For discussion, see [aspnet/AspNetCore#8543](https://github.com/aspnet/AspNetCore/issues/8543).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="7ae4e-106">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="7ae4e-106">Version introduced</span></span>

<span data-ttu-id="7ae4e-107">3.0</span><span class="sxs-lookup"><span data-stu-id="7ae4e-107">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="7ae4e-108">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="7ae4e-108">Old behavior</span></span>

<span data-ttu-id="7ae4e-109">API 'Ler kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="7ae4e-109">APIs were available.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="7ae4e-110">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="7ae4e-110">New behavior</span></span>

<span data-ttu-id="7ae4e-111">API 'Ler kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="7ae4e-111">APIs are removed.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="7ae4e-112">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="7ae4e-112">Reason for change</span></span>

<span data-ttu-id="7ae4e-113">Bu yöntemler başlangıçta yalnızca iç kullanıma yöneliktir, ancak ASP.NET Core 2,2 ' de genel kullanıma sunulmuştur.</span><span class="sxs-lookup"><span data-stu-id="7ae4e-113">These methods were originally intended only for internal use but were made public in ASP.NET Core 2.2.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="7ae4e-114">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="7ae4e-114">Recommended action</span></span>

<span data-ttu-id="7ae4e-115">Bu yöntemleri kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="7ae4e-115">Don't use these methods.</span></span>

#### <a name="category"></a><span data-ttu-id="7ae4e-116">Kategori</span><span class="sxs-lookup"><span data-stu-id="7ae4e-116">Category</span></span>

<span data-ttu-id="7ae4e-117">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="7ae4e-117">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="7ae4e-118">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="7ae4e-118">Affected APIs</span></span>

- <xref:Microsoft.AspNetCore.SignalR.Client.HubConnection.ResetSendPing?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.SignalR.Client.HubConnection.ResetTimeout?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:Microsoft.AspNetCore.SignalR.Client.HubConnection.ResetSendPing`
- `M:Microsoft.AspNetCore.SignalR.Client.HubConnection.ResetTimeout`

-->
