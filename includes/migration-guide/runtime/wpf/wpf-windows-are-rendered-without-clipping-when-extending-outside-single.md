---
ms.openlocfilehash: a133c2ea48df11915f8708029c70549e8a1ccefd
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497921"
---
### <a name="wpf-windows-are-rendered-without-clipping-when-extending-outside-a-single-monitor"></a><span data-ttu-id="570f0-101">WPF pencereleri, tek bir izleyicinin dışında genişledikleri zaman kırpmadan işlenir</span><span class="sxs-lookup"><span data-stu-id="570f0-101">WPF windows are rendered without clipping when extending outside a single monitor</span></span>

#### <a name="details"></a><span data-ttu-id="570f0-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="570f0-102">Details</span></span>

<span data-ttu-id="570f0-103">Windows 8 ve üzeri sürümlerde çalışan .NET Framework 4,6 ' de, tüm pencere, birden çok izleyici senaryosunda tek bir görüntü dışına genişlemediğinde kırpma olmadan işlenir.</span><span class="sxs-lookup"><span data-stu-id="570f0-103">In the .NET Framework 4.6 running on Windows 8 and above, the entire window is rendered without clipping when it extends outside of single display in a multi-monitor scenario.</span></span> <span data-ttu-id="570f0-104">Bu, tek bir görüntüleme ötesinde Genişletilebilir WPF pencerelerini Clip .NET Framework önceki sürümlerinden farklıdır.</span><span class="sxs-lookup"><span data-stu-id="570f0-104">This is different from previous versions of the .NET Framework which would clip WPF windows that extended beyond a single display.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="570f0-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="570f0-105">Suggestion</span></span>

<span data-ttu-id="570f0-106">Bu davranış (klip veya Not) <code>&lt;EnableMultiMonitorDisplayClipping&gt;</code> <code>&lt;appSettings&gt;</code> , bir uygulamanın yapılandırma dosyasındaki öğesini kullanarak veya uygulama başlangıcında özelliği ayarlayarak açıkça ayarlanabilir <code>EnableMultiMonitorDisplayClipping</code> .</span><span class="sxs-lookup"><span data-stu-id="570f0-106">This behavior (whether to clip or not) can be explicitly set using the <code>&lt;EnableMultiMonitorDisplayClipping&gt;</code> element in <code>&lt;appSettings&gt;</code> in an application's configuration file, or by setting the <code>EnableMultiMonitorDisplayClipping</code> property at app startup.</span></span>

| <span data-ttu-id="570f0-107">Name</span><span class="sxs-lookup"><span data-stu-id="570f0-107">Name</span></span>    | <span data-ttu-id="570f0-108">Değer</span><span class="sxs-lookup"><span data-stu-id="570f0-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="570f0-109">Kapsam</span><span class="sxs-lookup"><span data-stu-id="570f0-109">Scope</span></span>   |<span data-ttu-id="570f0-110">İkincil</span><span class="sxs-lookup"><span data-stu-id="570f0-110">Minor</span></span>|
|<span data-ttu-id="570f0-111">Sürüm</span><span class="sxs-lookup"><span data-stu-id="570f0-111">Version</span></span>|<span data-ttu-id="570f0-112">4.6</span><span class="sxs-lookup"><span data-stu-id="570f0-112">4.6</span></span>|
|<span data-ttu-id="570f0-113">Tür</span><span class="sxs-lookup"><span data-stu-id="570f0-113">Type</span></span>|<span data-ttu-id="570f0-114">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="570f0-114">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="570f0-115">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="570f0-115">Affected APIs</span></span>

<span data-ttu-id="570f0-116">API analizi aracılığıyla algılanamaz.</span><span class="sxs-lookup"><span data-stu-id="570f0-116">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
