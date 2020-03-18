---
ms.openlocfilehash: e5355387d5cb6d9e6de89f5b85e64bc100b32ae1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72522662"
---
### <a name="spas-spaservices-and-nodeservices-no-longer-fall-back-to-console-logger"></a><span data-ttu-id="a2013-101">SP'ler: SpaServices ve NodeServices artık konsol logger geri düşmek</span><span class="sxs-lookup"><span data-stu-id="a2013-101">SPAs: SpaServices and NodeServices no longer fall back to console logger</span></span>

<span data-ttu-id="a2013-102"><xref:Microsoft.AspNetCore.SpaServices?displayProperty=nameWithType><xref:Microsoft.AspNetCore.NodeServices?displayProperty=nameWithType> ve günlük yapılandırması yapılmadığı sürece konsol günlüklerini görüntülemez.</span><span class="sxs-lookup"><span data-stu-id="a2013-102"><xref:Microsoft.AspNetCore.SpaServices?displayProperty=nameWithType> and <xref:Microsoft.AspNetCore.NodeServices?displayProperty=nameWithType> won't display console logs unless logging is configured.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="a2013-103">Sürüm tanıtıldı</span><span class="sxs-lookup"><span data-stu-id="a2013-103">Version introduced</span></span>

<span data-ttu-id="a2013-104">3,0</span><span class="sxs-lookup"><span data-stu-id="a2013-104">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="a2013-105">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="a2013-105">Old behavior</span></span>

<span data-ttu-id="a2013-106">`Microsoft.AspNetCore.SpaServices`ve `Microsoft.AspNetCore.NodeServices` günlük yapılandırma olmadığında otomatik olarak bir konsol kaydedici oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a2013-106">`Microsoft.AspNetCore.SpaServices` and `Microsoft.AspNetCore.NodeServices` used to automatically create a console logger when logging isn't configured.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="a2013-107">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="a2013-107">New behavior</span></span>

<span data-ttu-id="a2013-108">`Microsoft.AspNetCore.SpaServices``Microsoft.AspNetCore.NodeServices` ve günlük yapılandırması yapılmadığı sürece konsol günlüklerini görüntülemez.</span><span class="sxs-lookup"><span data-stu-id="a2013-108">`Microsoft.AspNetCore.SpaServices` and `Microsoft.AspNetCore.NodeServices` won't display console logs unless logging is configured.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="a2013-109">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="a2013-109">Reason for change</span></span>

<span data-ttu-id="a2013-110">Diğer ASP.NET Core paketlerinin günlüğe kaydetmeyi nasıl uyguladığıyla uyumlu hale getirmek gerekir.</span><span class="sxs-lookup"><span data-stu-id="a2013-110">There's a need to align with how other ASP.NET Core packages implement logging.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="a2013-111">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="a2013-111">Recommended action</span></span>

<span data-ttu-id="a2013-112">Eski davranış gerekiyorsa, konsol günlüğe yapılandırmak `services.AddLogging(builder => builder.AddConsole())` için, yönteminize `Setup.ConfigureServices` ekleyin.</span><span class="sxs-lookup"><span data-stu-id="a2013-112">If the old behavior is required, to configure console logging, add `services.AddLogging(builder => builder.AddConsole())` to your `Setup.ConfigureServices` method.</span></span>

#### <a name="category"></a><span data-ttu-id="a2013-113">Kategori</span><span class="sxs-lookup"><span data-stu-id="a2013-113">Category</span></span>

<span data-ttu-id="a2013-114">ASP.NET Çekirdeği</span><span class="sxs-lookup"><span data-stu-id="a2013-114">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="a2013-115">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="a2013-115">Affected APIs</span></span>

<span data-ttu-id="a2013-116">None</span><span class="sxs-lookup"><span data-stu-id="a2013-116">None</span></span>

<!--

#### Affected APIs

Not detectable via API analysis

-->
