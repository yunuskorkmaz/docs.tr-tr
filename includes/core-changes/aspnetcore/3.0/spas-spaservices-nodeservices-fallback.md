---
ms.openlocfilehash: 1017801346e65940e4dc075ef72f7a00d7e6bcd9
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394216"
---
### <a name="spas-spaservices-and-nodeservices-no-longer-fall-back-to-console-logger"></a><span data-ttu-id="bd0c6-101">Maça 'Lar: Spaservice ve NodeServices artık konsol günlükçüsü 'e geri düşmüyor</span><span class="sxs-lookup"><span data-stu-id="bd0c6-101">SPAs: SpaServices and NodeServices no longer fall back to console logger</span></span>

<span data-ttu-id="bd0c6-102"><xref:Microsoft.AspNetCore.SpaServices?displayProperty=nameWithType> ve <xref:Microsoft.AspNetCore.NodeServices?displayProperty=nameWithType>, günlüğe kaydetme yapılandırılmadığı takdirde konsol günlüklerini görüntülemez.</span><span class="sxs-lookup"><span data-stu-id="bd0c6-102"><xref:Microsoft.AspNetCore.SpaServices?displayProperty=nameWithType> and <xref:Microsoft.AspNetCore.NodeServices?displayProperty=nameWithType> won't display console logs unless logging is configured.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="bd0c6-103">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="bd0c6-103">Version introduced</span></span>

<span data-ttu-id="bd0c6-104">3.0</span><span class="sxs-lookup"><span data-stu-id="bd0c6-104">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="bd0c6-105">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="bd0c6-105">Old behavior</span></span>

<span data-ttu-id="bd0c6-106">`Microsoft.AspNetCore.SpaServices` ve `Microsoft.AspNetCore.NodeServices` günlük yapılandırılmadığı zaman otomatik olarak bir konsol günlükçüsü oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="bd0c6-106">`Microsoft.AspNetCore.SpaServices` and `Microsoft.AspNetCore.NodeServices` used to automatically create a console logger when logging isn't configured.</span></span> 

#### <a name="new-behavior"></a><span data-ttu-id="bd0c6-107">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="bd0c6-107">New behavior</span></span>

<span data-ttu-id="bd0c6-108">`Microsoft.AspNetCore.SpaServices` ve `Microsoft.AspNetCore.NodeServices`, günlüğe kaydetme yapılandırılmadığı takdirde konsol günlüklerini görüntülemez.</span><span class="sxs-lookup"><span data-stu-id="bd0c6-108">`Microsoft.AspNetCore.SpaServices` and `Microsoft.AspNetCore.NodeServices` won't display console logs unless logging is configured.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="bd0c6-109">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="bd0c6-109">Reason for change</span></span>

<span data-ttu-id="bd0c6-110">Diğer ASP.NET Core paketlerinin günlüğe kaydetme işleminin nasıl uygulanacağını hizalamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="bd0c6-110">There's a need to align with how other ASP.NET Core packages implement logging.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="bd0c6-111">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="bd0c6-111">Recommended action</span></span>

<span data-ttu-id="bd0c6-112">Eski davranış gerekliyse konsol günlüğünü yapılandırmak için `services.AddLogging(builder => builder.AddConsole())` ' ı `Setup.ConfigureServices` yöntemine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="bd0c6-112">If the old behavior is required, to configure console logging, add `services.AddLogging(builder => builder.AddConsole())` to your `Setup.ConfigureServices` method.</span></span>

#### <a name="category"></a><span data-ttu-id="bd0c6-113">Kategori</span><span class="sxs-lookup"><span data-stu-id="bd0c6-113">Category</span></span>

<span data-ttu-id="bd0c6-114">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="bd0c6-114">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="bd0c6-115">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="bd0c6-115">Affected APIs</span></span>

<span data-ttu-id="bd0c6-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="bd0c6-116">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
