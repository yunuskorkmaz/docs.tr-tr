---
ms.openlocfilehash: de06825f1031d05bc83183a83bae165e2f9512ff
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901717"
---
### <a name="signalr-hubconnection-resetsendping-and-resettimeout-methods-removed"></a><span data-ttu-id="0d9d0-101">SignalR: HubConnection ResetSendPing ve ResetTimeout yöntemleri kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="0d9d0-101">SignalR: HubConnection ResetSendPing and ResetTimeout methods removed</span></span>

<span data-ttu-id="0d9d0-102">Ve `ResetSendPing` `ResetTimeout` yöntemler SignalR `HubConnection` API kaldırıldı.</span><span class="sxs-lookup"><span data-stu-id="0d9d0-102">The `ResetSendPing` and `ResetTimeout` methods were removed from the SignalR `HubConnection` API.</span></span> <span data-ttu-id="0d9d0-103">Bu yöntemler başlangıçta sadece dahili kullanım için tasarlanmıştır ancak ASP.NET Core 2.2'de kamuya açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="0d9d0-103">These methods were originally intended only for internal use but were made public in ASP.NET Core 2.2.</span></span> <span data-ttu-id="0d9d0-104">Bu yöntemler, ASP.NET Core 3.0 Preview 4 sürümünden başlayarak kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="0d9d0-104">These methods won't be available starting in the ASP.NET Core 3.0 Preview 4 release.</span></span> <span data-ttu-id="0d9d0-105">Tartışma için [dotnet/aspnetcore#8543'e](https://github.com/dotnet/aspnetcore/issues/8543)bakın.</span><span class="sxs-lookup"><span data-stu-id="0d9d0-105">For discussion, see [dotnet/aspnetcore#8543](https://github.com/dotnet/aspnetcore/issues/8543).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="0d9d0-106">Sürüm tanıtıldı</span><span class="sxs-lookup"><span data-stu-id="0d9d0-106">Version introduced</span></span>

<span data-ttu-id="0d9d0-107">3,0</span><span class="sxs-lookup"><span data-stu-id="0d9d0-107">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="0d9d0-108">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="0d9d0-108">Old behavior</span></span>

<span data-ttu-id="0d9d0-109">API'ler mevcuttü.</span><span class="sxs-lookup"><span data-stu-id="0d9d0-109">APIs were available.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="0d9d0-110">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="0d9d0-110">New behavior</span></span>

<span data-ttu-id="0d9d0-111">API'ler kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="0d9d0-111">APIs are removed.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="0d9d0-112">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="0d9d0-112">Reason for change</span></span>

<span data-ttu-id="0d9d0-113">Bu yöntemler başlangıçta sadece dahili kullanım için tasarlanmıştır ancak ASP.NET Core 2.2'de kamuya açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="0d9d0-113">These methods were originally intended only for internal use but were made public in ASP.NET Core 2.2.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="0d9d0-114">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="0d9d0-114">Recommended action</span></span>

<span data-ttu-id="0d9d0-115">Bu yöntemleri kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="0d9d0-115">Don't use these methods.</span></span>

#### <a name="category"></a><span data-ttu-id="0d9d0-116">Kategori</span><span class="sxs-lookup"><span data-stu-id="0d9d0-116">Category</span></span>

<span data-ttu-id="0d9d0-117">ASP.NET Çekirdeği</span><span class="sxs-lookup"><span data-stu-id="0d9d0-117">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="0d9d0-118">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="0d9d0-118">Affected APIs</span></span>

- <xref:Microsoft.AspNetCore.SignalR.Client.HubConnection.ResetSendPing?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.SignalR.Client.HubConnection.ResetTimeout?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:Microsoft.AspNetCore.SignalR.Client.HubConnection.ResetSendPing`
- `M:Microsoft.AspNetCore.SignalR.Client.HubConnection.ResetTimeout`

-->
