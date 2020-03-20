---
ms.openlocfilehash: 71c81cf188fa4c2300661f10eb87e7ae00e031f6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67804559"
---
### <a name="etw-event-names-cannot-differ-only-by-a-start-or-stop-suffix"></a><span data-ttu-id="0205c-101">ETW olay adları yalnızca "Başlat" veya "Durdur" sonekiile göre farklı olamaz</span><span class="sxs-lookup"><span data-stu-id="0205c-101">ETW event names cannot differ only by a "Start" or "Stop" suffix</span></span>

|   |   |
|---|---|
|<span data-ttu-id="0205c-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="0205c-102">Details</span></span>|<span data-ttu-id="0205c-103">.NET Framework 4.6 ve 4.6.1'de, çalışma zamanı, Windows için iki Olay İzleme (ETW)&quot; &quot;olay&quot; adının yalnızca Başlangıç &quot;veya Durdur <code>LogUser</code> sonekiyle (bir olay adlandırılmış ve diğerinin adı geçtiğinde) <code>LogUserStart</code>farklı olduğunda bir <xref:System.ArgumentException> zaman atar.</span><span class="sxs-lookup"><span data-stu-id="0205c-103">In the .NET Framework 4.6 and 4.6.1, the runtime throws an <xref:System.ArgumentException> when two Event Tracing for Windows (ETW) event names differ only by a &quot;Start&quot; or &quot;Stop&quot; suffix (as when one event is named <code>LogUser</code> and another is named <code>LogUserStart</code>).</span></span> <span data-ttu-id="0205c-104">Bu durumda, çalışma zamanı, herhangi bir günlüğe kaydetme yemeyen olay kaynağını oluşturamaz.</span><span class="sxs-lookup"><span data-stu-id="0205c-104">In this case, the runtime cannot construct the event source, which cannot emit any logging.</span></span>|
|<span data-ttu-id="0205c-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="0205c-105">Suggestion</span></span>|<span data-ttu-id="0205c-106">Özel durumu önlemek için, iki olay adı &quot;yalnızca&quot; &quot;Başlat&quot; veya Durdur sonekiyle farklılık olmadığından emin olun. Bu gereksinim .NET Framework 4.6.2 ile başlayarak kaldırılır; çalışma süresi, yalnızca &quot;Başlat&quot; ve &quot;Durdur&quot; sonekine göre farklılık gösteren olay adlarını ayrıştırabilir.</span><span class="sxs-lookup"><span data-stu-id="0205c-106">To prevent the exception, ensure that no two event names differ only by a &quot;Start&quot; or &quot;Stop&quot; suffix.This requirement is removed starting with the .NET Framework 4.6.2; the runtime can disambiguate event names that differ only by the &quot;Start&quot; and &quot;Stop&quot; suffix.</span></span>|
|<span data-ttu-id="0205c-107">Kapsam</span><span class="sxs-lookup"><span data-stu-id="0205c-107">Scope</span></span>|<span data-ttu-id="0205c-108">Edge</span><span class="sxs-lookup"><span data-stu-id="0205c-108">Edge</span></span>|
|<span data-ttu-id="0205c-109">Sürüm</span><span class="sxs-lookup"><span data-stu-id="0205c-109">Version</span></span>|<span data-ttu-id="0205c-110">4.6</span><span class="sxs-lookup"><span data-stu-id="0205c-110">4.6</span></span>|
|<span data-ttu-id="0205c-111">Tür</span><span class="sxs-lookup"><span data-stu-id="0205c-111">Type</span></span>|<span data-ttu-id="0205c-112">Yeniden Hedefleme</span><span class="sxs-lookup"><span data-stu-id="0205c-112">Retargeting</span></span>|
