---
ms.openlocfilehash: d276e2bbf24c8b2389a0a8078c62c327c3729d50
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621447"
---
### <a name="wpf-windows-are-rendered-without-clipping-when-extending-outside-a-single-monitor"></a><span data-ttu-id="caab9-101">WPF pencereleri, tek bir izleyicinin dışında genişledikleri zaman kırpmadan işlenir</span><span class="sxs-lookup"><span data-stu-id="caab9-101">WPF windows are rendered without clipping when extending outside a single monitor</span></span>

#### <a name="details"></a><span data-ttu-id="caab9-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="caab9-102">Details</span></span>

<span data-ttu-id="caab9-103">Windows 8 ve üzeri sürümlerde çalışan .NET Framework 4,6 ' de, tüm pencere, birden çok izleyici senaryosunda tek bir görüntü dışına genişlemediğinde kırpma olmadan işlenir.</span><span class="sxs-lookup"><span data-stu-id="caab9-103">In the .NET Framework 4.6 running on Windows 8 and above, the entire window is rendered without clipping when it extends outside of single display in a multi-monitor scenario.</span></span> <span data-ttu-id="caab9-104">Bu, tek bir görüntüleme ötesinde Genişletilebilir WPF pencerelerini Clip .NET Framework önceki sürümlerinden farklıdır.</span><span class="sxs-lookup"><span data-stu-id="caab9-104">This is different from previous versions of the .NET Framework which would clip WPF windows that extended beyond a single display.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="caab9-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="caab9-105">Suggestion</span></span>

<span data-ttu-id="caab9-106">Bu davranış (klip veya Not) <code>&lt;EnableMultiMonitorDisplayClipping&gt;</code> <code>&lt;appSettings&gt;</code> , bir uygulamanın yapılandırma dosyasındaki öğesini kullanarak veya uygulama başlangıcında özelliği ayarlayarak açıkça ayarlanabilir <code>EnableMultiMonitorDisplayClipping</code> .</span><span class="sxs-lookup"><span data-stu-id="caab9-106">This behavior (whether to clip or not) can be explicitly set using the <code>&lt;EnableMultiMonitorDisplayClipping&gt;</code> element in <code>&lt;appSettings&gt;</code> in an application's configuration file, or by setting the <code>EnableMultiMonitorDisplayClipping</code> property at app startup.</span></span>

| <span data-ttu-id="caab9-107">Name</span><span class="sxs-lookup"><span data-stu-id="caab9-107">Name</span></span>    | <span data-ttu-id="caab9-108">Değer</span><span class="sxs-lookup"><span data-stu-id="caab9-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="caab9-109">Kapsam</span><span class="sxs-lookup"><span data-stu-id="caab9-109">Scope</span></span>   |<span data-ttu-id="caab9-110">İkincil</span><span class="sxs-lookup"><span data-stu-id="caab9-110">Minor</span></span>|
|<span data-ttu-id="caab9-111">Sürüm</span><span class="sxs-lookup"><span data-stu-id="caab9-111">Version</span></span>|<span data-ttu-id="caab9-112">4.6</span><span class="sxs-lookup"><span data-stu-id="caab9-112">4.6</span></span>|
|<span data-ttu-id="caab9-113">Tür</span><span class="sxs-lookup"><span data-stu-id="caab9-113">Type</span></span>|<span data-ttu-id="caab9-114">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="caab9-114">Runtime</span></span>|
