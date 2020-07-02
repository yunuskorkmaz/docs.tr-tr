---
ms.openlocfilehash: 0e25d5d9b545e5cb400cbf701fb13da572fadf10
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614678"
---
### <a name="etw-event-names-cannot-differ-only-by-a-start-or-stop-suffix"></a><span data-ttu-id="9acb4-101">ETW olay adları yalnızca bir "Başlat" veya "Durdur" sonekiyle farklı olamaz</span><span class="sxs-lookup"><span data-stu-id="9acb4-101">ETW event names cannot differ only by a "Start" or "Stop" suffix</span></span>

#### <a name="details"></a><span data-ttu-id="9acb4-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="9acb4-102">Details</span></span>

<span data-ttu-id="9acb4-103">4,6 ve 4.6.1 .NET Framework çalışma zamanı, <xref:System.ArgumentException> Windows için Iki olay izleme (ETW) olay adı yalnızca bir "Başlat" veya "Durdur" sonekiyle farklıysa (bir olay adı `LogUser` ve diğeri adlandırılmışsa olduğu gibi `LogUserStart` ).</span><span class="sxs-lookup"><span data-stu-id="9acb4-103">In the .NET Framework 4.6 and 4.6.1, the runtime throws an <xref:System.ArgumentException> when two Event Tracing for Windows (ETW) event names differ only by a "Start" or "Stop" suffix (as when one event is named `LogUser` and another is named `LogUserStart`).</span></span> <span data-ttu-id="9acb4-104">Bu durumda, çalışma zamanı olay kaynağını oluşturamaz, bu da herhangi bir günlüğe kaydetmeyi yayamaz.</span><span class="sxs-lookup"><span data-stu-id="9acb4-104">In this case, the runtime cannot construct the event source, which cannot emit any logging.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="9acb4-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="9acb4-105">Suggestion</span></span>

<span data-ttu-id="9acb4-106">Özel durumu engellemek için, iki olay adının yalnızca bir "Başlat" veya "Durdur" sonekiyle farklı olmamasını sağlayın. Bu gereksinim, .NET Framework 4.6.2; öğesinden başlayarak kaldırılır; çalışma zamanı, yalnızca "Başlat" ve "Durdur" sonekiyle farklı olay adlarını ayırt edebilir.</span><span class="sxs-lookup"><span data-stu-id="9acb4-106">To prevent the exception, ensure that no two event names differ only by a "Start" or "Stop" suffix.This requirement is removed starting with the .NET Framework 4.6.2; the runtime can disambiguate event names that differ only by the "Start" and "Stop" suffix.</span></span>

| <span data-ttu-id="9acb4-107">Name</span><span class="sxs-lookup"><span data-stu-id="9acb4-107">Name</span></span>    | <span data-ttu-id="9acb4-108">Değer</span><span class="sxs-lookup"><span data-stu-id="9acb4-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="9acb4-109">Kapsam</span><span class="sxs-lookup"><span data-stu-id="9acb4-109">Scope</span></span>   | <span data-ttu-id="9acb4-110">Edge</span><span class="sxs-lookup"><span data-stu-id="9acb4-110">Edge</span></span>        |
| <span data-ttu-id="9acb4-111">Sürüm</span><span class="sxs-lookup"><span data-stu-id="9acb4-111">Version</span></span> | <span data-ttu-id="9acb4-112">4.6</span><span class="sxs-lookup"><span data-stu-id="9acb4-112">4.6</span></span>         |
| <span data-ttu-id="9acb4-113">Tür</span><span class="sxs-lookup"><span data-stu-id="9acb4-113">Type</span></span>    | <span data-ttu-id="9acb4-114">Yeniden Hedefleme</span><span class="sxs-lookup"><span data-stu-id="9acb4-114">Retargeting</span></span> |
