---
ms.openlocfilehash: fb23418816abcae125106c93b339a546aa9bc2ee
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032804"
---
### <a name="kestrel-transport-abstractions-removed-and-made-public"></a><span data-ttu-id="26fed-101">Kestrel: kaldırılan ve genel kullanıma açık olan taşıma soyutlamaları</span><span class="sxs-lookup"><span data-stu-id="26fed-101">Kestrel: Transport abstractions removed and made public</span></span>

<span data-ttu-id="26fed-102">"Pubternal" API 'lerinden uzaklaşma kapsamında, Kestrel aktarım katmanı API 'Leri kitaplıkta ortak bir arabirim olarak sunulur `Microsoft.AspNetCore.Connections.Abstractions` .</span><span class="sxs-lookup"><span data-stu-id="26fed-102">As part of moving away from "pubternal" APIs, the Kestrel transport layer APIs are exposed as a public interface in the `Microsoft.AspNetCore.Connections.Abstractions` library.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="26fed-103">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="26fed-103">Version introduced</span></span>

<span data-ttu-id="26fed-104">3,0</span><span class="sxs-lookup"><span data-stu-id="26fed-104">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="26fed-105">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="26fed-105">Old behavior</span></span>

- <span data-ttu-id="26fed-106">Taşıma ile ilgili soyutlamalar `Microsoft.AspNetCore.Server.Kestrel.Transport.Abstractions` kitaplıkta kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="26fed-106">Transport-related abstractions were available in the `Microsoft.AspNetCore.Server.Kestrel.Transport.Abstractions` library.</span></span>
- <span data-ttu-id="26fed-107">`ListenOptions.NoDelay`Özellik kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="26fed-107">The `ListenOptions.NoDelay` property was available.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="26fed-108">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="26fed-108">New behavior</span></span>

- <span data-ttu-id="26fed-109">Arabirim, kitaplıkta `IConnectionListener` `Microsoft.AspNetCore.Connections.Abstractions` en çok kullanılan işlevselliği kullanıma sunmak için kitaplıkta tanıtılmıştı `...Transport.Abstractions` .</span><span class="sxs-lookup"><span data-stu-id="26fed-109">The `IConnectionListener` interface was introduced in the `Microsoft.AspNetCore.Connections.Abstractions` library to expose the most used functionality from the `...Transport.Abstractions` library.</span></span>
- <span data-ttu-id="26fed-110">`NoDelay`Artık aktarım seçeneklerinde ( `LibuvTransportOptions` ve `SocketTransportOptions` ) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="26fed-110">The `NoDelay` is now available in transport options (`LibuvTransportOptions` and `SocketTransportOptions`).</span></span>
- <span data-ttu-id="26fed-111">`SchedulingMode` artık kullanılamıyor.</span><span class="sxs-lookup"><span data-stu-id="26fed-111">`SchedulingMode` is no longer available.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="26fed-112">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="26fed-112">Reason for change</span></span>

<span data-ttu-id="26fed-113">ASP.NET Core 3,0, "pubternal" API 'Lerinden uzağa taşındı.</span><span class="sxs-lookup"><span data-stu-id="26fed-113">ASP.NET Core 3.0 has moved away from "pubternal" APIs.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="26fed-114">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="26fed-114">Recommended action</span></span>

#### <a name="category"></a><span data-ttu-id="26fed-115">Kategori</span><span class="sxs-lookup"><span data-stu-id="26fed-115">Category</span></span>

<span data-ttu-id="26fed-116">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="26fed-116">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="26fed-117">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="26fed-117">Affected APIs</span></span>

<span data-ttu-id="26fed-118">Yok</span><span class="sxs-lookup"><span data-stu-id="26fed-118">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
