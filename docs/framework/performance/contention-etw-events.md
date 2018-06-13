---
title: Çekişme ETW Olayları
ms.date: 03/30/2017
helpviewer_keywords:
- contention events [.NET Framework]
- ETW, contention events (CLR)
ms.assetid: 6933e753-2f2a-425b-ae84-42138c957d76
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3487b67ea49cecfd0da2b5b3f993ea54d562145d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33397526"
---
# <a name="contention-etw-events"></a><span data-ttu-id="23035-102">Çekişme ETW Olayları</span><span class="sxs-lookup"><span data-stu-id="23035-102">Contention ETW Events</span></span>
<span data-ttu-id="23035-103">Çekişme olayları için Çekişme olduğunda ortaya <xref:System.Threading.Monitor?displayProperty=nameWithType> kilitleri ya da çalışma zamanı tarafından kullanılan yerel kilitler.</span><span class="sxs-lookup"><span data-stu-id="23035-103">Contention events are raised whenever there is contention for <xref:System.Threading.Monitor?displayProperty=nameWithType> locks or native locks used by the runtime.</span></span> <span data-ttu-id="23035-104">Çakışma, başka bir iş parçacığı kilidi sahip olduğu sırada bir kilidi için bekleyen bir iş parçacığı oluşur.</span><span class="sxs-lookup"><span data-stu-id="23035-104">Contention occurs when a thread is waiting for a lock while another thread possesses the lock.</span></span>  
  
 <span data-ttu-id="23035-105">Aşağıdaki tabloda altında Çekişme olayları yükseltildiği anahtar sözcüğü ve olayları düzeyini gösterir.</span><span class="sxs-lookup"><span data-stu-id="23035-105">The following table shows the keyword under which contention events are raised, and the level of the events.</span></span> <span data-ttu-id="23035-106">(Daha fazla bilgi için bkz: [CLR ETW anahtar sözcükleri ve Düzeyler](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="23035-106">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="23035-107">Olay oluşturma için anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="23035-107">Keyword for raising the event</span></span>|<span data-ttu-id="23035-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="23035-108">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="23035-109">`ContentionKeyword` (0x4000)</span><span class="sxs-lookup"><span data-stu-id="23035-109">`ContentionKeyword` (0x4000)</span></span>|<span data-ttu-id="23035-110">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="23035-110">Informational (4)</span></span>|  
  
 <span data-ttu-id="23035-111">Aşağıdaki tabloda olay bilgilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="23035-111">The following table shows event information.</span></span>  
  
|<span data-ttu-id="23035-112">Olay</span><span class="sxs-lookup"><span data-stu-id="23035-112">Event</span></span>|<span data-ttu-id="23035-113">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="23035-113">Event ID</span></span>|<span data-ttu-id="23035-114">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="23035-114">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ContentionStart_V1`|<span data-ttu-id="23035-115">81</span><span class="sxs-lookup"><span data-stu-id="23035-115">81</span></span>|<span data-ttu-id="23035-116">Çekişme başlatır.</span><span class="sxs-lookup"><span data-stu-id="23035-116">Contention starts.</span></span> <span data-ttu-id="23035-117">Bu olay, bir iş parçacığı bir kilidi bekler önce geçen süre dönmesini miktarını içermez; yalnızca bir kilit edinmeye iş parçacığı bekler yapıldığında oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="23035-117">This event does not include the amount of spinning time before a thread waits to acquire a lock; it is raised only when the thread waits to acquire a lock.</span></span>|  
|`ContentionStop`|<span data-ttu-id="23035-118">81</span><span class="sxs-lookup"><span data-stu-id="23035-118">81</span></span>|<span data-ttu-id="23035-119">Çekişme sona erer.</span><span class="sxs-lookup"><span data-stu-id="23035-119">Contention ends.</span></span>|  
  
 <span data-ttu-id="23035-120">Aşağıdaki tabloda olay verilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="23035-120">The following table shows event data.</span></span>  
  
|<span data-ttu-id="23035-121">Alan adı</span><span class="sxs-lookup"><span data-stu-id="23035-121">Field name</span></span>|<span data-ttu-id="23035-122">Veri türü</span><span class="sxs-lookup"><span data-stu-id="23035-122">Data type</span></span>|<span data-ttu-id="23035-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="23035-123">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="23035-124">Bayraklar</span><span class="sxs-lookup"><span data-stu-id="23035-124">Flags</span></span>|<span data-ttu-id="23035-125">Win: UInt8</span><span class="sxs-lookup"><span data-stu-id="23035-125">win:UInt8</span></span>|<span data-ttu-id="23035-126">için 0 yönetilen; Yerel için 1.</span><span class="sxs-lookup"><span data-stu-id="23035-126">0 for managed; 1 for native.</span></span>|  
|<span data-ttu-id="23035-127">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="23035-127">ClrInstanceID</span></span>|<span data-ttu-id="23035-128">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="23035-128">win:UInt16</span></span>|<span data-ttu-id="23035-129">CLR örneği için benzersiz kimlik.</span><span class="sxs-lookup"><span data-stu-id="23035-129">Unique ID for the instance of CLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="23035-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="23035-130">See Also</span></span>  
 [<span data-ttu-id="23035-131">CLR ETW Olayları</span><span class="sxs-lookup"><span data-stu-id="23035-131">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
