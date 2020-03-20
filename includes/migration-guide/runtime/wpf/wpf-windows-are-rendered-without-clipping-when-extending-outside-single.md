---
ms.openlocfilehash: 3b7309347c643d89a28331c6ef3cac36085a969a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67858471"
---
### <a name="wpf-windows-are-rendered-without-clipping-when-extending-outside-a-single-monitor"></a><span data-ttu-id="30b31-101">WPF pencereler, tek bir monitörün dışına uzatıldığında kırpma olmadan işlenir</span><span class="sxs-lookup"><span data-stu-id="30b31-101">WPF windows are rendered without clipping when extending outside a single monitor</span></span>

|   |   |
|---|---|
|<span data-ttu-id="30b31-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="30b31-102">Details</span></span>|<span data-ttu-id="30b31-103">Windows 8 ve üzeri üzerinde çalışan .NET Framework 4.6'da, çoklu monitör senaryosunda tek ekranın dışına uzandığında tüm pencere kırpma olmadan işlenir.</span><span class="sxs-lookup"><span data-stu-id="30b31-103">In the .NET Framework 4.6 running on Windows 8 and above, the entire window is rendered without clipping when it extends outside of single display in a multi-monitor scenario.</span></span> <span data-ttu-id="30b31-104">Bu, .NET Framework'ün tek bir ekranın ötesine uzanan WPF pencerelerini kesecek önceki sürümlerinden farklıdır.</span><span class="sxs-lookup"><span data-stu-id="30b31-104">This is different from previous versions of the .NET Framework which would clip WPF windows that extended beyond a single display.</span></span>|
|<span data-ttu-id="30b31-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="30b31-105">Suggestion</span></span>|<span data-ttu-id="30b31-106">Bu davranış (klip le şaşmasın veya <code>&lt;EnableMultiMonitorDisplayClipping&gt;</code> kesilmesin), bir uygulamanın yapılandırma <code>&lt;appSettings&gt;</code> <code>EnableMultiMonitorDisplayClipping</code> dosyasındaki öğe kullanılarak veya uygulama başlangıcında özelliği ayarlayarak açıkça ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="30b31-106">This behavior (whether to clip or not) can be explicitly set using the <code>&lt;EnableMultiMonitorDisplayClipping&gt;</code> element in <code>&lt;appSettings&gt;</code> in an application's configuration file, or by setting the <code>EnableMultiMonitorDisplayClipping</code> property at app startup.</span></span>|
|<span data-ttu-id="30b31-107">Kapsam</span><span class="sxs-lookup"><span data-stu-id="30b31-107">Scope</span></span>|<span data-ttu-id="30b31-108">İkincil</span><span class="sxs-lookup"><span data-stu-id="30b31-108">Minor</span></span>|
|<span data-ttu-id="30b31-109">Sürüm</span><span class="sxs-lookup"><span data-stu-id="30b31-109">Version</span></span>|<span data-ttu-id="30b31-110">4.6</span><span class="sxs-lookup"><span data-stu-id="30b31-110">4.6</span></span>|
|<span data-ttu-id="30b31-111">Tür</span><span class="sxs-lookup"><span data-stu-id="30b31-111">Type</span></span>|<span data-ttu-id="30b31-112">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="30b31-112">Runtime</span></span>|
