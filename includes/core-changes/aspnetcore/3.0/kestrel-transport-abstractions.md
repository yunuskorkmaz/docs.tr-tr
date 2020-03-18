---
ms.openlocfilehash: f95c3916f4da8164cf927344f60f2845f04ddc5c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72393985"
---
### <a name="kestrel-transport-abstractions-removed-and-made-public"></a><span data-ttu-id="ef10c-101">Kerkenez: Ulaşım soyutlamaları kaldırıldı ve kamuya açıklandı</span><span class="sxs-lookup"><span data-stu-id="ef10c-101">Kestrel: Transport abstractions removed and made public</span></span>

<span data-ttu-id="ef10c-102">"Pubternal" API'lerden uzaklaşmanın bir parçası olarak, Kerkenez aktarım katmanı `Microsoft.AspNetCore.Connections.Abstractions` API'leri kütüphanede genel bir arayüz olarak ortaya çıkar.</span><span class="sxs-lookup"><span data-stu-id="ef10c-102">As part of moving away from "pubternal" APIs, the Kestrel transport layer APIs are exposed as a public interface in the `Microsoft.AspNetCore.Connections.Abstractions` library.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="ef10c-103">Sürüm tanıtıldı</span><span class="sxs-lookup"><span data-stu-id="ef10c-103">Version introduced</span></span>

<span data-ttu-id="ef10c-104">3,0</span><span class="sxs-lookup"><span data-stu-id="ef10c-104">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="ef10c-105">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="ef10c-105">Old behavior</span></span>

- <span data-ttu-id="ef10c-106">Taşımayla ilgili soyutlamalar kütüphanede `Microsoft.AspNetCore.Server.Kestrel.Transport.Abstractions` mevcuttü.</span><span class="sxs-lookup"><span data-stu-id="ef10c-106">Transport-related abstractions were available in the `Microsoft.AspNetCore.Server.Kestrel.Transport.Abstractions` library.</span></span>
- <span data-ttu-id="ef10c-107">Tesis `ListenOptions.NoDelay` müsaitti.</span><span class="sxs-lookup"><span data-stu-id="ef10c-107">The `ListenOptions.NoDelay` property was available.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="ef10c-108">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="ef10c-108">New behavior</span></span>

- <span data-ttu-id="ef10c-109">Arabirim, `IConnectionListener` `Microsoft.AspNetCore.Connections.Abstractions` `...Transport.Abstractions` kitaplıktan en çok kullanılan işlevselliği ortaya çıkarmak için kitaplıkta tanıtıldı.</span><span class="sxs-lookup"><span data-stu-id="ef10c-109">The `IConnectionListener` interface was introduced in the `Microsoft.AspNetCore.Connections.Abstractions` library to expose the most used functionality from the `...Transport.Abstractions` library.</span></span>
- <span data-ttu-id="ef10c-110">Şimdi `NoDelay` taşıma seçenekleri mevcuttur`LibuvTransportOptions` ( `SocketTransportOptions`ve ).</span><span class="sxs-lookup"><span data-stu-id="ef10c-110">The `NoDelay` is now available in transport options (`LibuvTransportOptions` and `SocketTransportOptions`).</span></span>
- <span data-ttu-id="ef10c-111">`SchedulingMode`artık kullanılamıyor.</span><span class="sxs-lookup"><span data-stu-id="ef10c-111">`SchedulingMode` is no longer available.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="ef10c-112">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="ef10c-112">Reason for change</span></span>

<span data-ttu-id="ef10c-113">ASP.NET Core 3.0 uzak "pubternal" API'ler taşındı.</span><span class="sxs-lookup"><span data-stu-id="ef10c-113">ASP.NET Core 3.0 has moved away from "pubternal" APIs.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="ef10c-114">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="ef10c-114">Recommended action</span></span>

#### <a name="category"></a><span data-ttu-id="ef10c-115">Kategori</span><span class="sxs-lookup"><span data-stu-id="ef10c-115">Category</span></span>

<span data-ttu-id="ef10c-116">ASP.NET Çekirdeği</span><span class="sxs-lookup"><span data-stu-id="ef10c-116">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="ef10c-117">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="ef10c-117">Affected APIs</span></span>

<span data-ttu-id="ef10c-118">None</span><span class="sxs-lookup"><span data-stu-id="ef10c-118">None</span></span>

<!-- 

### Affected APIs

Not detectable via API analysis

-->
