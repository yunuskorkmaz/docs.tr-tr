---
title: Çekişme ETW Olayları
ms.date: 03/30/2017
helpviewer_keywords:
- contention events [.NET Framework]
- ETW, contention events (CLR)
ms.assetid: 6933e753-2f2a-425b-ae84-42138c957d76
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 90beb1487581ff4c031d6f10fb613430207dc026
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54575573"
---
# <a name="contention-etw-events"></a><span data-ttu-id="1b85d-102">Çekişme ETW Olayları</span><span class="sxs-lookup"><span data-stu-id="1b85d-102">Contention ETW Events</span></span>
<span data-ttu-id="1b85d-103">Çekişme olayları oluştuğunda için Çekişme olduğunda <xref:System.Threading.Monitor?displayProperty=nameWithType> kilitler veya çalışma zamanı tarafından kullanılan yerel kilitler.</span><span class="sxs-lookup"><span data-stu-id="1b85d-103">Contention events are raised whenever there is contention for <xref:System.Threading.Monitor?displayProperty=nameWithType> locks or native locks used by the runtime.</span></span> <span data-ttu-id="1b85d-104">Başka bir iş parçacığı kilit sahip olduğu sırada bir kilit için bekleyen bir iş parçacığı Çekişme gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="1b85d-104">Contention occurs when a thread is waiting for a lock while another thread possesses the lock.</span></span>  
  
 <span data-ttu-id="1b85d-105">Çekişme olayları altında oluşturulan anahtar sözcüğü ve olayları düzeyi aşağıdaki tabloda gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1b85d-105">The following table shows the keyword under which contention events are raised, and the level of the events.</span></span> <span data-ttu-id="1b85d-106">(Daha fazla bilgi için [CLR ETW anahtar sözcükleri ve Düzeyler](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="1b85d-106">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="1b85d-107">Olayı için anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="1b85d-107">Keyword for raising the event</span></span>|<span data-ttu-id="1b85d-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="1b85d-108">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="1b85d-109">`ContentionKeyword` (0x4000)</span><span class="sxs-lookup"><span data-stu-id="1b85d-109">`ContentionKeyword` (0x4000)</span></span>|<span data-ttu-id="1b85d-110">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="1b85d-110">Informational (4)</span></span>|  
  
 <span data-ttu-id="1b85d-111">Aşağıdaki tablo, olay bilgilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="1b85d-111">The following table shows event information.</span></span>  
  
|<span data-ttu-id="1b85d-112">Olay</span><span class="sxs-lookup"><span data-stu-id="1b85d-112">Event</span></span>|<span data-ttu-id="1b85d-113">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="1b85d-113">Event ID</span></span>|<span data-ttu-id="1b85d-114">Ne zaman gerçekleşti</span><span class="sxs-lookup"><span data-stu-id="1b85d-114">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ContentionStart_V1`|<span data-ttu-id="1b85d-115">81</span><span class="sxs-lookup"><span data-stu-id="1b85d-115">81</span></span>|<span data-ttu-id="1b85d-116">Çekişme başlatır.</span><span class="sxs-lookup"><span data-stu-id="1b85d-116">Contention starts.</span></span> <span data-ttu-id="1b85d-117">Bu olay, dönen bir iş parçacığı kilit için bekleyen önceki süre miktarını içermez; yalnızca iş parçacığının bir kilidi bekler olduğunda tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="1b85d-117">This event does not include the amount of spinning time before a thread waits to acquire a lock; it is raised only when the thread waits to acquire a lock.</span></span>|  
|`ContentionStop`|<span data-ttu-id="1b85d-118">81</span><span class="sxs-lookup"><span data-stu-id="1b85d-118">81</span></span>|<span data-ttu-id="1b85d-119">Çekişme sona erer.</span><span class="sxs-lookup"><span data-stu-id="1b85d-119">Contention ends.</span></span>|  
  
 <span data-ttu-id="1b85d-120">Aşağıdaki tabloda, olay verilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="1b85d-120">The following table shows event data.</span></span>  
  
|<span data-ttu-id="1b85d-121">Alan adı</span><span class="sxs-lookup"><span data-stu-id="1b85d-121">Field name</span></span>|<span data-ttu-id="1b85d-122">Veri türü</span><span class="sxs-lookup"><span data-stu-id="1b85d-122">Data type</span></span>|<span data-ttu-id="1b85d-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1b85d-123">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="1b85d-124">Bayraklar</span><span class="sxs-lookup"><span data-stu-id="1b85d-124">Flags</span></span>|<span data-ttu-id="1b85d-125">Kazanma: UInt8</span><span class="sxs-lookup"><span data-stu-id="1b85d-125">win:UInt8</span></span>|<span data-ttu-id="1b85d-126">0 için yönetilen; Yerel için 1.</span><span class="sxs-lookup"><span data-stu-id="1b85d-126">0 for managed; 1 for native.</span></span>|  
|<span data-ttu-id="1b85d-127">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="1b85d-127">ClrInstanceID</span></span>|<span data-ttu-id="1b85d-128">Kazanma: UInt16</span><span class="sxs-lookup"><span data-stu-id="1b85d-128">win:UInt16</span></span>|<span data-ttu-id="1b85d-129">CLR örneği için benzersiz kimliği.</span><span class="sxs-lookup"><span data-stu-id="1b85d-129">Unique ID for the instance of CLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1b85d-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1b85d-130">See also</span></span>
- [<span data-ttu-id="1b85d-131">CLR ETW Olayları</span><span class="sxs-lookup"><span data-stu-id="1b85d-131">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
