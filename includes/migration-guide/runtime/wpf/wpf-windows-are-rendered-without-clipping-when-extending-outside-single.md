---
ms.openlocfilehash: 2e974d277d6659aaada321b2a7e7a604df78a7bd
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/01/2019
ms.locfileid: "58761416"
---
### <a name="wpf-windows-are-rendered-without-clipping-when-extending-outside-a-single-monitor"></a><span data-ttu-id="030cf-101">WPF windows tek bir izleyici genişletme olduğunda kırpma olmadan işlenir</span><span class="sxs-lookup"><span data-stu-id="030cf-101">WPF windows are rendered without clipping when extending outside a single monitor</span></span>

|   |   |
|---|---|
|<span data-ttu-id="030cf-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="030cf-102">Details</span></span>|<span data-ttu-id="030cf-103">Bir çoklu monitör senaryosunda tek ekran dışında genişletir, .NET Framework 4.6 çalışır Windows 8 ve üzeri, kırpma olmadan tüm pencere işlenir.</span><span class="sxs-lookup"><span data-stu-id="030cf-103">In the .NET Framework 4.6 running on Windows 8 and above, the entire window is rendered without clipping when it extends outside of single display in a multi-monitor scenario.</span></span> <span data-ttu-id="030cf-104">Bu, tek bir görüntü genişletilmiş WPF windows küçük .NET Framework'ün önceki sürümlerden farklıdır.</span><span class="sxs-lookup"><span data-stu-id="030cf-104">This is different from previous versions of the .NET Framework which would clip WPF windows that extended beyond a single display.</span></span>|
|<span data-ttu-id="030cf-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="030cf-105">Suggestion</span></span>|<span data-ttu-id="030cf-106">Bu davranış (verilip verilmeyeceğini veya küçük) kullanılarak açıkça ayarlanabilir <code>&lt;EnableMultiMonitorDisplayClipping&gt;</code> öğesinde <code>&lt;appSettings&gt;</code> uygulamanın yapılandırma dosyasında veya ayarlayarak <code>EnableMultiMonitorDisplayClipping</code> uygulamanın başlangıcında özelliği.</span><span class="sxs-lookup"><span data-stu-id="030cf-106">This behavior (whether to clip or not) can be explicitly set using the <code>&lt;EnableMultiMonitorDisplayClipping&gt;</code> element in <code>&lt;appSettings&gt;</code> in an application's configuration file, or by setting the <code>EnableMultiMonitorDisplayClipping</code> property at app startup.</span></span>|
|<span data-ttu-id="030cf-107">Kapsam</span><span class="sxs-lookup"><span data-stu-id="030cf-107">Scope</span></span>|<span data-ttu-id="030cf-108">İkincil</span><span class="sxs-lookup"><span data-stu-id="030cf-108">Minor</span></span>|
|<span data-ttu-id="030cf-109">Sürüm</span><span class="sxs-lookup"><span data-stu-id="030cf-109">Version</span></span>|<span data-ttu-id="030cf-110">4.6</span><span class="sxs-lookup"><span data-stu-id="030cf-110">4.6</span></span>|
|<span data-ttu-id="030cf-111">Tür</span><span class="sxs-lookup"><span data-stu-id="030cf-111">Type</span></span>|<span data-ttu-id="030cf-112">Çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="030cf-112">Runtime</span></span>|

