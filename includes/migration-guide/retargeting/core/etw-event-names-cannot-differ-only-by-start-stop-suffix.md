---
ms.openlocfilehash: 71c81cf188fa4c2300661f10eb87e7ae00e031f6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59234580"
---
### <a name="etw-event-names-cannot-differ-only-by-a-start-or-stop-suffix"></a><span data-ttu-id="26138-101">ETW olay adları yalnızca "Başlangıç" veya "Durdur" soneki ile farklı olamaz</span><span class="sxs-lookup"><span data-stu-id="26138-101">ETW event names cannot differ only by a "Start" or "Stop" suffix</span></span>

|   |   |
|---|---|
|<span data-ttu-id="26138-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="26138-102">Details</span></span>|<span data-ttu-id="26138-103">.NET Framework 4.6 ve 4.6.1, çalışma zamanı oluşturur bir <xref:System.ArgumentException> iki olay izleme için Windows (ETW) olayı adları farklı yalnızca ne zaman bir &quot;Başlat&quot; veya &quot;Durdur&quot; soneki (bir olay zamanadlıolarak<code>LogUser</code>ve başka adlı <code>LogUserStart</code>).</span><span class="sxs-lookup"><span data-stu-id="26138-103">In the .NET Framework 4.6 and 4.6.1, the runtime throws an <xref:System.ArgumentException> when two Event Tracing for Windows (ETW) event names differ only by a &quot;Start&quot; or &quot;Stop&quot; suffix (as when one event is named <code>LogUser</code> and another is named <code>LogUserStart</code>).</span></span> <span data-ttu-id="26138-104">Bu durumda, çalışma zamanı, tüm günlük yayılamıyor olay kaynağı oluşturulamıyor.</span><span class="sxs-lookup"><span data-stu-id="26138-104">In this case, the runtime cannot construct the event source, which cannot emit any logging.</span></span>|
|<span data-ttu-id="26138-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="26138-105">Suggestion</span></span>|<span data-ttu-id="26138-106">Özel durum önlemek için hiçbir iki olay adları yalnızca farklı olun bir &quot;Başlat&quot; veya &quot;Durdur&quot; soneki. Bu gereksinim, .NET Framework 4.6.2 ile başlayarak kaldırıldı; çalışma zamanı tarafından yalnızca farklı olay adlarını ayırt etmek &quot;Başlat&quot; ve &quot;Durdur&quot; soneki.</span><span class="sxs-lookup"><span data-stu-id="26138-106">To prevent the exception, ensure that no two event names differ only by a &quot;Start&quot; or &quot;Stop&quot; suffix.This requirement is removed starting with the .NET Framework 4.6.2; the runtime can disambiguate event names that differ only by the &quot;Start&quot; and &quot;Stop&quot; suffix.</span></span>|
|<span data-ttu-id="26138-107">Kapsam</span><span class="sxs-lookup"><span data-stu-id="26138-107">Scope</span></span>|<span data-ttu-id="26138-108">Kenar</span><span class="sxs-lookup"><span data-stu-id="26138-108">Edge</span></span>|
|<span data-ttu-id="26138-109">Sürüm</span><span class="sxs-lookup"><span data-stu-id="26138-109">Version</span></span>|<span data-ttu-id="26138-110">4.6</span><span class="sxs-lookup"><span data-stu-id="26138-110">4.6</span></span>|
|<span data-ttu-id="26138-111">Tür</span><span class="sxs-lookup"><span data-stu-id="26138-111">Type</span></span>|<span data-ttu-id="26138-112">Yeniden Hedefleme</span><span class="sxs-lookup"><span data-stu-id="26138-112">Retargeting</span></span>|
