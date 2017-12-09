---
title: "Çöp Toplama ETW Olayları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- GC events
- garbage collection events [.NET Framework]
- ETW, garbage collection events (CLR)
ms.assetid: f14b6fd7-0966-4d87-bc89-54ef3a44a94a
caps.latest.revision: "21"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 06fc335e4b8011afd92e698b20e4b84572b153c3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="garbage-collection-etw-events"></a><span data-ttu-id="b6f46-102">Çöp Toplama ETW Olayları</span><span class="sxs-lookup"><span data-stu-id="b6f46-102">Garbage Collection ETW Events</span></span>
<a name="top"></a><span data-ttu-id="b6f46-103">Bu olaylar çöp toplama ilgili bilgi toplayın.</span><span class="sxs-lookup"><span data-stu-id="b6f46-103">These events collect information pertaining to garbage collection.</span></span> <span data-ttu-id="b6f46-104">Tanılamada yardımcı olurlar ve hata ayıklama, atık toplama kaç kez belirleme dahil olmak üzere gerçekleştirildiyse, ne kadar bellek çöp toplama ve benzeri sırasında bırakılmış.</span><span class="sxs-lookup"><span data-stu-id="b6f46-104">They help in diagnostics and debugging, including determining how many times garbage collection was performed, how much memory was freed during garbage collection, and so on.</span></span>  
  
 <span data-ttu-id="b6f46-105">Bu kategori aşağıdaki olaylar oluşur:</span><span class="sxs-lookup"><span data-stu-id="b6f46-105">This category consists of the following events:</span></span>  
  
-   [<span data-ttu-id="b6f46-106">GCStart_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="b6f46-106">GCStart_V1 Event</span></span>](#gcstart_v1_event)  
  
-   [<span data-ttu-id="b6f46-107">GCEnd_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="b6f46-107">GCEnd_V1 Event</span></span>](#gcend_v1_event)  
  
-   [<span data-ttu-id="b6f46-108">GCHeapStats_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="b6f46-108">GCHeapStats_V1 Event</span></span>](#gcheapstats_v1_event)  
  
-   [<span data-ttu-id="b6f46-109">GCCreateSegment_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="b6f46-109">GCCreateSegment_V1 Event</span></span>](#gccreatesegment_v1_event)  
  
-   [<span data-ttu-id="b6f46-110">GCFreeSegment_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="b6f46-110">GCFreeSegment_V1 Event</span></span>](#gcfreesegment_v1_event)  
  
-   [<span data-ttu-id="b6f46-111">GCRestartEEBegin_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="b6f46-111">GCRestartEEBegin_V1 Event</span></span>](#gcrestarteebegin_v1_event)  
  
-   [<span data-ttu-id="b6f46-112">GCRestartEEEnd_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="b6f46-112">GCRestartEEEnd_V1 Event</span></span>](#gcrestarteeend_v1_event)  
  
-   [<span data-ttu-id="b6f46-113">GCSuspendEE_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="b6f46-113">GCSuspendEE_V1 Event</span></span>](#gcsuspendee_v1_event)  
  
-   [<span data-ttu-id="b6f46-114">GCSuspendEEEnd_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="b6f46-114">GCSuspendEEEnd_V1 Event</span></span>](#gcsuspendeeend_v1_event)  
  
-   [<span data-ttu-id="b6f46-115">GCAllocationTick_V2 olayı</span><span class="sxs-lookup"><span data-stu-id="b6f46-115">GCAllocationTick_V2 Event</span></span>](#gcallocationtick_v2_event)  
  
-   [<span data-ttu-id="b6f46-116">GCFinalizersBegin_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="b6f46-116">GCFinalizersBegin_V1 Event</span></span>](#gcfinalizersbegin_v1_event)  
  
-   [<span data-ttu-id="b6f46-117">GCFinalizersEnd_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="b6f46-117">GCFinalizersEnd_V1 Event</span></span>](#gcfinalizersend_v1_event)  
  
-   [<span data-ttu-id="b6f46-118">GCCreateConcurrentThread_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="b6f46-118">GCCreateConcurrentThread_V1 Event</span></span>](#gccreateconcurrentthread_v1_event)  
  
-   [<span data-ttu-id="b6f46-119">GCTerminateConcurrentThread_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="b6f46-119">GCTerminateConcurrentThread_V1 Event</span></span>](#gcterminateconcurrentthread_v1_event)  
  
<a name="gcstart_v1_event"></a>   
## <a name="gcstartv1-event"></a><span data-ttu-id="b6f46-120">GCStart_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="b6f46-120">GCStart_V1 Event</span></span>  
 <span data-ttu-id="b6f46-121">Aşağıdaki tablo düzeyi ve anahtar sözcüğü gösterir.</span><span class="sxs-lookup"><span data-stu-id="b6f46-121">The following table shows the keyword and level.</span></span> <span data-ttu-id="b6f46-122">(Daha fazla bilgi için bkz: [CLR ETW anahtar sözcükleri ve Düzeyler](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="b6f46-122">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="b6f46-123">Olay oluşturma için anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="b6f46-123">Keyword for raising the event</span></span>|<span data-ttu-id="b6f46-124">Düzey</span><span class="sxs-lookup"><span data-stu-id="b6f46-124">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="b6f46-125">`GCKeyword`(0x1)</span><span class="sxs-lookup"><span data-stu-id="b6f46-125">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="b6f46-126">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="b6f46-126">Informational (4)</span></span>|  
  
 <span data-ttu-id="b6f46-127">Aşağıdaki tabloda olay bilgilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="b6f46-127">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="b6f46-128">Olay</span><span class="sxs-lookup"><span data-stu-id="b6f46-128">Event</span></span>|<span data-ttu-id="b6f46-129">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="b6f46-129">Event ID</span></span>|<span data-ttu-id="b6f46-130">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="b6f46-130">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCStart_V1`|<span data-ttu-id="b6f46-131">1.</span><span class="sxs-lookup"><span data-stu-id="b6f46-131">1</span></span>|<span data-ttu-id="b6f46-132">Çöp toplama başlatıldı.</span><span class="sxs-lookup"><span data-stu-id="b6f46-132">A garbage collection has started.</span></span>|  
  
 <span data-ttu-id="b6f46-133">Aşağıdaki tabloda olay verilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="b6f46-133">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="b6f46-134">Alan adı</span><span class="sxs-lookup"><span data-stu-id="b6f46-134">Field name</span></span>|<span data-ttu-id="b6f46-135">Veri türü</span><span class="sxs-lookup"><span data-stu-id="b6f46-135">Data type</span></span>|<span data-ttu-id="b6f46-136">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b6f46-136">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="b6f46-137">Sayısı</span><span class="sxs-lookup"><span data-stu-id="b6f46-137">Count</span></span>|<span data-ttu-id="b6f46-138">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="b6f46-138">win:UInt32</span></span>|<span data-ttu-id="b6f46-139">*n* Th atık toplama.</span><span class="sxs-lookup"><span data-stu-id="b6f46-139">The *n*th garbage collection.</span></span>|  
|<span data-ttu-id="b6f46-140">Derinliği</span><span class="sxs-lookup"><span data-stu-id="b6f46-140">Depth</span></span>|<span data-ttu-id="b6f46-141">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="b6f46-141">win:UInt32</span></span>|<span data-ttu-id="b6f46-142">Toplanacak oluşturma.</span><span class="sxs-lookup"><span data-stu-id="b6f46-142">The generation that is being collected.</span></span>|  
|<span data-ttu-id="b6f46-143">Neden</span><span class="sxs-lookup"><span data-stu-id="b6f46-143">Reason</span></span>|<span data-ttu-id="b6f46-144">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="b6f46-144">win:UInt32</span></span>|<span data-ttu-id="b6f46-145">Çöp toplama neden tetiklendi:</span><span class="sxs-lookup"><span data-stu-id="b6f46-145">Why the garbage collection was triggered:</span></span><br /><br /> <span data-ttu-id="b6f46-146">0x0 - küçük nesne yığın ayırma.</span><span class="sxs-lookup"><span data-stu-id="b6f46-146">0x0 - Small object heap allocation.</span></span><br /><br /> <span data-ttu-id="b6f46-147">0x1 - kopyaladığınızda.</span><span class="sxs-lookup"><span data-stu-id="b6f46-147">0x1 - Induced.</span></span><br /><br /> <span data-ttu-id="b6f46-148">0x2 - bellek yetersiz.</span><span class="sxs-lookup"><span data-stu-id="b6f46-148">0x2 - Low memory.</span></span><br /><br /> <span data-ttu-id="b6f46-149">0x3 - boş.</span><span class="sxs-lookup"><span data-stu-id="b6f46-149">0x3 - Empty.</span></span><br /><br /> <span data-ttu-id="b6f46-150">0x4 - büyük nesne yığın ayırma.</span><span class="sxs-lookup"><span data-stu-id="b6f46-150">0x4 - Large object heap allocation.</span></span><br /><br /> <span data-ttu-id="b6f46-151">0x5 - (için küçük nesne yığın) alanı yetersiz.</span><span class="sxs-lookup"><span data-stu-id="b6f46-151">0x5 - Out of space (for small object heap).</span></span><br /><br /> <span data-ttu-id="b6f46-152">0x6 - (için büyük nesne yığın) alanı yetersiz.</span><span class="sxs-lookup"><span data-stu-id="b6f46-152">0x6 - Out of space (for large object heap).</span></span><br /><br /> <span data-ttu-id="b6f46-153">0x7 - kopyaladığınızda ancak engelleme olarak zorunlu değildir.</span><span class="sxs-lookup"><span data-stu-id="b6f46-153">0x7 - Induced but not forced as blocking.</span></span>|  
|<span data-ttu-id="b6f46-154">Tür</span><span class="sxs-lookup"><span data-stu-id="b6f46-154">Type</span></span>|<span data-ttu-id="b6f46-155">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="b6f46-155">win:UInt32</span></span>|<span data-ttu-id="b6f46-156">0x0 - arka plan çöp toplama dışında engelleme çöp toplama oluştu.</span><span class="sxs-lookup"><span data-stu-id="b6f46-156">0x0 - Blocking garbage collection occurred outside background garbage collection.</span></span><br /><br /> <span data-ttu-id="b6f46-157">0x1 - arka plan çöp toplama.</span><span class="sxs-lookup"><span data-stu-id="b6f46-157">0x1 - Background garbage collection.</span></span><br /><br /> <span data-ttu-id="b6f46-158">0x2 - engelleme çöp toplama arka plan çöp toplama sırasında oluştu.</span><span class="sxs-lookup"><span data-stu-id="b6f46-158">0x2 - Blocking garbage collection occurred during background garbage collection.</span></span>|  
|<span data-ttu-id="b6f46-159">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="b6f46-159">ClrInstanceID</span></span>|<span data-ttu-id="b6f46-160">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="b6f46-160">win:UInt16</span></span>|<span data-ttu-id="b6f46-161">CLR veya CoreCLR örneği için benzersiz kimlik.</span><span class="sxs-lookup"><span data-stu-id="b6f46-161">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="b6f46-162">Başa dön</span><span class="sxs-lookup"><span data-stu-id="b6f46-162">Back to top</span></span>](#top)  
  
<a name="gcend_v1_event"></a>   
## <a name="gcendv1-event"></a><span data-ttu-id="b6f46-163">GCEnd_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="b6f46-163">GCEnd_V1 Event</span></span>  
 <span data-ttu-id="b6f46-164">Aşağıdaki tablo düzeyi ve anahtar sözcüğü gösterir.</span><span class="sxs-lookup"><span data-stu-id="b6f46-164">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="b6f46-165">Olay oluşturma için anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="b6f46-165">Keyword for raising the event</span></span>|<span data-ttu-id="b6f46-166">Düzey</span><span class="sxs-lookup"><span data-stu-id="b6f46-166">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="b6f46-167">`GCKeyword`(0x1)</span><span class="sxs-lookup"><span data-stu-id="b6f46-167">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="b6f46-168">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="b6f46-168">Informational (4)</span></span>|  
  
 <span data-ttu-id="b6f46-169">Aşağıdaki tabloda olay bilgilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="b6f46-169">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="b6f46-170">Olay</span><span class="sxs-lookup"><span data-stu-id="b6f46-170">Event</span></span>|<span data-ttu-id="b6f46-171">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="b6f46-171">Event ID</span></span>|<span data-ttu-id="b6f46-172">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="b6f46-172">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCEnd_V1`|<span data-ttu-id="b6f46-173">2</span><span class="sxs-lookup"><span data-stu-id="b6f46-173">2</span></span>|<span data-ttu-id="b6f46-174">Çöp toplama sona erdi.</span><span class="sxs-lookup"><span data-stu-id="b6f46-174">The garbage collection has ended.</span></span>|  
  
 <span data-ttu-id="b6f46-175">Aşağıdaki tabloda olay verilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="b6f46-175">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="b6f46-176">Alan adı</span><span class="sxs-lookup"><span data-stu-id="b6f46-176">Field name</span></span>|<span data-ttu-id="b6f46-177">Veri türü</span><span class="sxs-lookup"><span data-stu-id="b6f46-177">Data type</span></span>|<span data-ttu-id="b6f46-178">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b6f46-178">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="b6f46-179">Sayısı</span><span class="sxs-lookup"><span data-stu-id="b6f46-179">Count</span></span>|<span data-ttu-id="b6f46-180">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="b6f46-180">win:UInt32</span></span>|<span data-ttu-id="b6f46-181">*n* Th atık toplama.</span><span class="sxs-lookup"><span data-stu-id="b6f46-181">The *n*th garbage collection.</span></span>|  
|<span data-ttu-id="b6f46-182">Derinliği</span><span class="sxs-lookup"><span data-stu-id="b6f46-182">Depth</span></span>|<span data-ttu-id="b6f46-183">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="b6f46-183">win:UInt32</span></span>|<span data-ttu-id="b6f46-184">Toplanan oluşturma.</span><span class="sxs-lookup"><span data-stu-id="b6f46-184">The generation that was collected.</span></span>|  
|<span data-ttu-id="b6f46-185">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="b6f46-185">ClrInstanceID</span></span>|<span data-ttu-id="b6f46-186">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="b6f46-186">win:UInt16</span></span>|<span data-ttu-id="b6f46-187">CLR veya CoreCLR örneği için benzersiz kimlik.</span><span class="sxs-lookup"><span data-stu-id="b6f46-187">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="b6f46-188">Başa dön</span><span class="sxs-lookup"><span data-stu-id="b6f46-188">Back to top</span></span>](#top)  
  
<a name="gcheapstats_v1_event"></a>   
## <a name="gcheapstatsv1-event"></a><span data-ttu-id="b6f46-189">GCHeapStats_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="b6f46-189">GCHeapStats_V1 Event</span></span>  
 <span data-ttu-id="b6f46-190">Aşağıdaki tablo düzeyi ve anahtar sözcüğü gösterir.</span><span class="sxs-lookup"><span data-stu-id="b6f46-190">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="b6f46-191">Olay oluşturma için anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="b6f46-191">Keyword for raising the event</span></span>|<span data-ttu-id="b6f46-192">Düzey</span><span class="sxs-lookup"><span data-stu-id="b6f46-192">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="b6f46-193">`GCKeyword`(0x1)</span><span class="sxs-lookup"><span data-stu-id="b6f46-193">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="b6f46-194">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="b6f46-194">Informational (4)</span></span>|  
  
 <span data-ttu-id="b6f46-195">Aşağıdaki tabloda olay bilgilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="b6f46-195">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="b6f46-196">Olay</span><span class="sxs-lookup"><span data-stu-id="b6f46-196">Event</span></span>|<span data-ttu-id="b6f46-197">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="b6f46-197">Event ID</span></span>|<span data-ttu-id="b6f46-198">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b6f46-198">Description</span></span>|  
|-----------|--------------|-----------------|  
|`GCHeapStats_V1`|<span data-ttu-id="b6f46-199">4</span><span class="sxs-lookup"><span data-stu-id="b6f46-199">4</span></span>|<span data-ttu-id="b6f46-200">Her çöp toplama işleminin sonunda yığın istatistiklerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="b6f46-200">Shows the heap statistics at the end of each garbage collection.</span></span>|  
  
 <span data-ttu-id="b6f46-201">Aşağıdaki tabloda olay verilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="b6f46-201">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="b6f46-202">Alan adı</span><span class="sxs-lookup"><span data-stu-id="b6f46-202">Field name</span></span>|<span data-ttu-id="b6f46-203">Veri türü</span><span class="sxs-lookup"><span data-stu-id="b6f46-203">Data type</span></span>|<span data-ttu-id="b6f46-204">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b6f46-204">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="b6f46-205">GenerationSize0</span><span class="sxs-lookup"><span data-stu-id="b6f46-205">GenerationSize0</span></span>|<span data-ttu-id="b6f46-206">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="b6f46-206">win:UInt64</span></span>|<span data-ttu-id="b6f46-207">Kuşak 0 belleğin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="b6f46-207">The size, in bytes, of generation 0 memory.</span></span>|  
|<span data-ttu-id="b6f46-208">TotalPromotedSize0</span><span class="sxs-lookup"><span data-stu-id="b6f46-208">TotalPromotedSize0</span></span>|<span data-ttu-id="b6f46-209">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="b6f46-209">win:UInt64</span></span>|<span data-ttu-id="b6f46-210">0 kuşaktan 1. nesil için öne çıkar bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="b6f46-210">The number of bytes that are promoted from generation 0 to generation 1.</span></span>|  
|<span data-ttu-id="b6f46-211">GenerationSize1</span><span class="sxs-lookup"><span data-stu-id="b6f46-211">GenerationSize1</span></span>|<span data-ttu-id="b6f46-212">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="b6f46-212">win:UInt64</span></span>|<span data-ttu-id="b6f46-213">1. nesil belleğin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="b6f46-213">The size, in bytes, of generation 1 memory.</span></span>|  
|<span data-ttu-id="b6f46-214">TotalPromotedSize1</span><span class="sxs-lookup"><span data-stu-id="b6f46-214">TotalPromotedSize1</span></span>|<span data-ttu-id="b6f46-215">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="b6f46-215">win:UInt64</span></span>|<span data-ttu-id="b6f46-216">1 kuşaktan 2. nesil için öne çıkar bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="b6f46-216">The number of bytes that are promoted from generation 1 to generation 2.</span></span>|  
|<span data-ttu-id="b6f46-217">GenerationSize2</span><span class="sxs-lookup"><span data-stu-id="b6f46-217">GenerationSize2</span></span>|<span data-ttu-id="b6f46-218">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="b6f46-218">win:UInt64</span></span>|<span data-ttu-id="b6f46-219">2. nesil belleğin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="b6f46-219">The size, in bytes, of generation 2 memory.</span></span>|  
|<span data-ttu-id="b6f46-220">TotalPromotedSize2</span><span class="sxs-lookup"><span data-stu-id="b6f46-220">TotalPromotedSize2</span></span>|<span data-ttu-id="b6f46-221">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="b6f46-221">win:UInt64</span></span>|<span data-ttu-id="b6f46-222">2. nesil son koleksiyon sonra içinde derdi bitti bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="b6f46-222">The number of bytes that survived in generation 2 after the last collection.</span></span>|  
|<span data-ttu-id="b6f46-223">GenerationSize3</span><span class="sxs-lookup"><span data-stu-id="b6f46-223">GenerationSize3</span></span>|<span data-ttu-id="b6f46-224">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="b6f46-224">win:UInt64</span></span>|<span data-ttu-id="b6f46-225">Bayt olarak büyük nesne yığın boyutu.</span><span class="sxs-lookup"><span data-stu-id="b6f46-225">The size, in bytes, of the large object heap.</span></span>|  
|<span data-ttu-id="b6f46-226">TotalPromotedSize3</span><span class="sxs-lookup"><span data-stu-id="b6f46-226">TotalPromotedSize3</span></span>|<span data-ttu-id="b6f46-227">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="b6f46-227">win:UInt64</span></span>|<span data-ttu-id="b6f46-228">Büyük nesne yığın sonra son koleksiyon derdi bitti bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="b6f46-228">The number of bytes that survived in the large object heap after the last collection.</span></span>|  
|<span data-ttu-id="b6f46-229">FinalizationPromotedSize</span><span class="sxs-lookup"><span data-stu-id="b6f46-229">FinalizationPromotedSize</span></span>|<span data-ttu-id="b6f46-230">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="b6f46-230">win:UInt64</span></span>|<span data-ttu-id="b6f46-231">Sonlandırma için hazır olan nesnelerin bayt toplam boyutu.</span><span class="sxs-lookup"><span data-stu-id="b6f46-231">The total size, in bytes, of the objects that are ready for finalization.</span></span>|  
|<span data-ttu-id="b6f46-232">FinalizationPromotedCount</span><span class="sxs-lookup"><span data-stu-id="b6f46-232">FinalizationPromotedCount</span></span>|<span data-ttu-id="b6f46-233">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="b6f46-233">win:UInt64</span></span>|<span data-ttu-id="b6f46-234">Sonlandırma için hazır nesnelerin sayısı.</span><span class="sxs-lookup"><span data-stu-id="b6f46-234">The number of objects that are ready for finalization.</span></span>|  
|<span data-ttu-id="b6f46-235">PinnedObjectCount</span><span class="sxs-lookup"><span data-stu-id="b6f46-235">PinnedObjectCount</span></span>|<span data-ttu-id="b6f46-236">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="b6f46-236">win:UInt32</span></span>|<span data-ttu-id="b6f46-237">Sabitlenmiş (taşınamayan) nesnelerin sayısı.</span><span class="sxs-lookup"><span data-stu-id="b6f46-237">The number of pinned (unmovable) objects.</span></span>|  
|<span data-ttu-id="b6f46-238">SinkBlockCount</span><span class="sxs-lookup"><span data-stu-id="b6f46-238">SinkBlockCount</span></span>|<span data-ttu-id="b6f46-239">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="b6f46-239">win:UInt32</span></span>|<span data-ttu-id="b6f46-240">Kullanımdaki eşitleme bloğu sayısı.</span><span class="sxs-lookup"><span data-stu-id="b6f46-240">The number of synchronization blocks in use.</span></span>|  
|<span data-ttu-id="b6f46-241">GCHandleCount</span><span class="sxs-lookup"><span data-stu-id="b6f46-241">GCHandleCount</span></span>|<span data-ttu-id="b6f46-242">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="b6f46-242">win:UInt32</span></span>|<span data-ttu-id="b6f46-243">Çöp toplama sayısı kullanımda işler.</span><span class="sxs-lookup"><span data-stu-id="b6f46-243">The number of garbage collection handles in use.</span></span>|  
|<span data-ttu-id="b6f46-244">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="b6f46-244">ClrInstanceID</span></span>|<span data-ttu-id="b6f46-245">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="b6f46-245">win:UInt16</span></span>|<span data-ttu-id="b6f46-246">CLR veya CoreCLR örneği için benzersiz kimlik.</span><span class="sxs-lookup"><span data-stu-id="b6f46-246">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="b6f46-247">Başa dön</span><span class="sxs-lookup"><span data-stu-id="b6f46-247">Back to top</span></span>](#top)  
  
<a name="gccreatesegment_v1_event"></a>   
## <a name="gccreatesegmentv1-event"></a><span data-ttu-id="b6f46-248">GCCreateSegment_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="b6f46-248">GCCreateSegment_V1 Event</span></span>  
 <span data-ttu-id="b6f46-249">Aşağıdaki tablo düzeyi ve anahtar sözcüğü gösterir.</span><span class="sxs-lookup"><span data-stu-id="b6f46-249">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="b6f46-250">Olay oluşturma için anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="b6f46-250">Keyword for raising the event</span></span>|<span data-ttu-id="b6f46-251">Düzey</span><span class="sxs-lookup"><span data-stu-id="b6f46-251">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="b6f46-252">`GCKeyword`(0x1)</span><span class="sxs-lookup"><span data-stu-id="b6f46-252">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="b6f46-253">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="b6f46-253">Informational (4)</span></span>|  
  
 <span data-ttu-id="b6f46-254">Aşağıdaki tabloda olay bilgilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="b6f46-254">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="b6f46-255">Olay</span><span class="sxs-lookup"><span data-stu-id="b6f46-255">Event</span></span>|<span data-ttu-id="b6f46-256">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="b6f46-256">Event ID</span></span>|<span data-ttu-id="b6f46-257">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="b6f46-257">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCCreateSegment_V1`|<span data-ttu-id="b6f46-258">5</span><span class="sxs-lookup"><span data-stu-id="b6f46-258">5</span></span>|<span data-ttu-id="b6f46-259">Yeni bir atık toplama segment oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="b6f46-259">A new garbage collection segment has been created.</span></span> <span data-ttu-id="b6f46-260">Ayrıca, izleme zaten çalıştırılan bir işlemde etkinleştirildiğinde, varolan her segment için bu olay tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="b6f46-260">In addition, when tracing is enabled on a process that is already running, this event is raised for each existing segment.</span></span>|  
  
 <span data-ttu-id="b6f46-261">Aşağıdaki tabloda olay verilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="b6f46-261">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="b6f46-262">Alan adı</span><span class="sxs-lookup"><span data-stu-id="b6f46-262">Field name</span></span>|<span data-ttu-id="b6f46-263">Veri türü</span><span class="sxs-lookup"><span data-stu-id="b6f46-263">Data type</span></span>|<span data-ttu-id="b6f46-264">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b6f46-264">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="b6f46-265">Adres</span><span class="sxs-lookup"><span data-stu-id="b6f46-265">Address</span></span>|<span data-ttu-id="b6f46-266">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="b6f46-266">win:UInt64</span></span>|<span data-ttu-id="b6f46-267">Kesim adresi.</span><span class="sxs-lookup"><span data-stu-id="b6f46-267">The address of the segment.</span></span>|  
|<span data-ttu-id="b6f46-268">Boyut</span><span class="sxs-lookup"><span data-stu-id="b6f46-268">Size</span></span>|<span data-ttu-id="b6f46-269">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="b6f46-269">win:UInt64</span></span>|<span data-ttu-id="b6f46-270">Kesim boyutu.</span><span class="sxs-lookup"><span data-stu-id="b6f46-270">The size of the segment.</span></span>|  
|<span data-ttu-id="b6f46-271">Tür</span><span class="sxs-lookup"><span data-stu-id="b6f46-271">Type</span></span>|<span data-ttu-id="b6f46-272">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="b6f46-272">win:UInt32</span></span>|<span data-ttu-id="b6f46-273">0x0 - küçük nesne yığın.</span><span class="sxs-lookup"><span data-stu-id="b6f46-273">0x0 - Small object heap.</span></span><br /><br /> <span data-ttu-id="b6f46-274">0x1 - büyük nesne yığın.</span><span class="sxs-lookup"><span data-stu-id="b6f46-274">0x1 - Large object heap.</span></span><br /><br /> <span data-ttu-id="b6f46-275">0x2 - salt okunur yığın.</span><span class="sxs-lookup"><span data-stu-id="b6f46-275">0x2 - Read-only heap.</span></span>|  
|<span data-ttu-id="b6f46-276">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="b6f46-276">ClrInstanceID</span></span>|<span data-ttu-id="b6f46-277">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="b6f46-277">win:UInt16</span></span>|<span data-ttu-id="b6f46-278">CLR veya CoreCLR örneği için benzersiz kimlik.</span><span class="sxs-lookup"><span data-stu-id="b6f46-278">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 <span data-ttu-id="b6f46-279">Çöp toplayıcı tarafından ayrılan kesimleri boyutunu uygulamasına özeldir ve düzenli güncelleştirmeleri dahil olmak üzere, istediğiniz zaman değiştirilebilir unutmayın.</span><span class="sxs-lookup"><span data-stu-id="b6f46-279">Note that the size of segments allocated by the garbage collector is implementation-specific and is subject to change at any time, including in periodic updates.</span></span> <span data-ttu-id="b6f46-280">Uygulamanız hiçbir zaman hakkında varsayımlar olun veya belirli bir segmentle boyutuna göre değişir ve segment ayırmalarının kullanılabilir bellek miktarını yapılandırmak için denemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="b6f46-280">Your app should never make assumptions about or depend on a particular segment size, nor should it attempt to configure the amount of memory available for segment allocations.</span></span>  
  
 [<span data-ttu-id="b6f46-281">Başa dön</span><span class="sxs-lookup"><span data-stu-id="b6f46-281">Back to top</span></span>](#top)  
  
<a name="gcfreesegment_v1_event"></a>   
## <a name="gcfreesegmentv1-event"></a><span data-ttu-id="b6f46-282">GCFreeSegment_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="b6f46-282">GCFreeSegment_V1 Event</span></span>  
 <span data-ttu-id="b6f46-283">Aşağıdaki tablo düzeyi ve anahtar sözcüğü gösterir.</span><span class="sxs-lookup"><span data-stu-id="b6f46-283">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="b6f46-284">Olay oluşturma için anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="b6f46-284">Keyword for raising the event</span></span>|<span data-ttu-id="b6f46-285">Düzey</span><span class="sxs-lookup"><span data-stu-id="b6f46-285">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="b6f46-286">`GCKeyword`(0x1)</span><span class="sxs-lookup"><span data-stu-id="b6f46-286">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="b6f46-287">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="b6f46-287">Informational (4)</span></span>|  
  
 <span data-ttu-id="b6f46-288">Aşağıdaki tabloda olay bilgilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="b6f46-288">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="b6f46-289">Olay</span><span class="sxs-lookup"><span data-stu-id="b6f46-289">Event</span></span>|<span data-ttu-id="b6f46-290">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="b6f46-290">Event ID</span></span>|<span data-ttu-id="b6f46-291">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="b6f46-291">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCFreeSegment_V1`|<span data-ttu-id="b6f46-292">6</span><span class="sxs-lookup"><span data-stu-id="b6f46-292">6</span></span>|<span data-ttu-id="b6f46-293">Çöp toplama kesimi yayımladı.</span><span class="sxs-lookup"><span data-stu-id="b6f46-293">A garbage collection segment has been released.</span></span>|  
  
 <span data-ttu-id="b6f46-294">Aşağıdaki tabloda olay verilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="b6f46-294">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="b6f46-295">Alan adı</span><span class="sxs-lookup"><span data-stu-id="b6f46-295">Field name</span></span>|<span data-ttu-id="b6f46-296">Veri türü</span><span class="sxs-lookup"><span data-stu-id="b6f46-296">Data type</span></span>|<span data-ttu-id="b6f46-297">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b6f46-297">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="b6f46-298">Adres</span><span class="sxs-lookup"><span data-stu-id="b6f46-298">Address</span></span>|<span data-ttu-id="b6f46-299">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="b6f46-299">win:UInt64</span></span>|<span data-ttu-id="b6f46-300">Kesim adresi.</span><span class="sxs-lookup"><span data-stu-id="b6f46-300">The address of the segment.</span></span>|  
|<span data-ttu-id="b6f46-301">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="b6f46-301">ClrInstanceID</span></span>|<span data-ttu-id="b6f46-302">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="b6f46-302">win:UInt16</span></span>|<span data-ttu-id="b6f46-303">CLR veya CoreCLR örneği için benzersiz kimlik.</span><span class="sxs-lookup"><span data-stu-id="b6f46-303">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="b6f46-304">Başa dön</span><span class="sxs-lookup"><span data-stu-id="b6f46-304">Back to top</span></span>](#top)  
  
<a name="gcrestarteebegin_v1_event"></a>   
## <a name="gcrestarteebeginv1-event"></a><span data-ttu-id="b6f46-305">GCRestartEEBegin_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="b6f46-305">GCRestartEEBegin_V1 Event</span></span>  
 <span data-ttu-id="b6f46-306">Aşağıdaki tablo düzeyi ve anahtar sözcüğü gösterir.</span><span class="sxs-lookup"><span data-stu-id="b6f46-306">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="b6f46-307">Olay oluşturma için anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="b6f46-307">Keyword for raising the event</span></span>|<span data-ttu-id="b6f46-308">Düzey</span><span class="sxs-lookup"><span data-stu-id="b6f46-308">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="b6f46-309">`GCKeyword`(0x1)</span><span class="sxs-lookup"><span data-stu-id="b6f46-309">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="b6f46-310">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="b6f46-310">Informational (4)</span></span>|  
  
 <span data-ttu-id="b6f46-311">Aşağıdaki tabloda olay bilgilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="b6f46-311">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="b6f46-312">Olay</span><span class="sxs-lookup"><span data-stu-id="b6f46-312">Event</span></span>|<span data-ttu-id="b6f46-313">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="b6f46-313">Event ID</span></span>|<span data-ttu-id="b6f46-314">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="b6f46-314">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCRestartEEBegin_V1`|<span data-ttu-id="b6f46-315">7</span><span class="sxs-lookup"><span data-stu-id="b6f46-315">7</span></span>|<span data-ttu-id="b6f46-316">Ortak dil çalışma zamanı askıya gelen sürdürme başladı.</span><span class="sxs-lookup"><span data-stu-id="b6f46-316">Resumption from common language runtime suspension has begun.</span></span>|  
  
 <span data-ttu-id="b6f46-317">Olay verisi yok.</span><span class="sxs-lookup"><span data-stu-id="b6f46-317">No event data.</span></span>  
  
 [<span data-ttu-id="b6f46-318">Başa dön</span><span class="sxs-lookup"><span data-stu-id="b6f46-318">Back to top</span></span>](#top)  
  
<a name="gcrestarteeend_v1_event"></a>   
## <a name="gcrestarteeendv1-event"></a><span data-ttu-id="b6f46-319">GCRestartEEEnd_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="b6f46-319">GCRestartEEEnd_V1 Event</span></span>  
 <span data-ttu-id="b6f46-320">Aşağıdaki tablo düzeyi ve anahtar sözcüğü gösterir.</span><span class="sxs-lookup"><span data-stu-id="b6f46-320">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="b6f46-321">Olay oluşturma için anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="b6f46-321">Keyword for raising the event</span></span>|<span data-ttu-id="b6f46-322">Düzey</span><span class="sxs-lookup"><span data-stu-id="b6f46-322">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="b6f46-323">`GCKeyword`(0x1)</span><span class="sxs-lookup"><span data-stu-id="b6f46-323">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="b6f46-324">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="b6f46-324">Informational (4)</span></span>|  
  
 <span data-ttu-id="b6f46-325">Aşağıdaki tabloda olay bilgilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="b6f46-325">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="b6f46-326">Olay</span><span class="sxs-lookup"><span data-stu-id="b6f46-326">Event</span></span>|<span data-ttu-id="b6f46-327">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="b6f46-327">Event Id</span></span>|<span data-ttu-id="b6f46-328">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="b6f46-328">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCRestartEEEnd_V1`|<span data-ttu-id="b6f46-329">3</span><span class="sxs-lookup"><span data-stu-id="b6f46-329">3</span></span>|<span data-ttu-id="b6f46-330">Ortak dil çalışma zamanı askıya gelen sürdürme sona erdi.</span><span class="sxs-lookup"><span data-stu-id="b6f46-330">Resumption from common language runtime suspension has ended.</span></span>|  
  
 <span data-ttu-id="b6f46-331">Olay verisi yok.</span><span class="sxs-lookup"><span data-stu-id="b6f46-331">No event data.</span></span>  
  
 [<span data-ttu-id="b6f46-332">Başa dön</span><span class="sxs-lookup"><span data-stu-id="b6f46-332">Back to top</span></span>](#top)  
  
<a name="gcsuspendee_v1_event"></a>   
## <a name="gcsuspendeev1-event"></a><span data-ttu-id="b6f46-333">GCSuspendEE_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="b6f46-333">GCSuspendEE_V1 Event</span></span>  
 <span data-ttu-id="b6f46-334">Aşağıdaki tablo düzeyi ve anahtar sözcüğü gösterir.</span><span class="sxs-lookup"><span data-stu-id="b6f46-334">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="b6f46-335">Olay oluşturma için anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="b6f46-335">Keyword for raising the event</span></span>|<span data-ttu-id="b6f46-336">Düzey</span><span class="sxs-lookup"><span data-stu-id="b6f46-336">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="b6f46-337">`GCKeyword`(0x1)</span><span class="sxs-lookup"><span data-stu-id="b6f46-337">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="b6f46-338">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="b6f46-338">Informational (4)</span></span>|  
  
 <span data-ttu-id="b6f46-339">Aşağıdaki tabloda olay bilgilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="b6f46-339">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="b6f46-340">Olay</span><span class="sxs-lookup"><span data-stu-id="b6f46-340">Event</span></span>|<span data-ttu-id="b6f46-341">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="b6f46-341">Event ID</span></span>|<span data-ttu-id="b6f46-342">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="b6f46-342">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCSuspendEE_V1`|<span data-ttu-id="b6f46-343">9</span><span class="sxs-lookup"><span data-stu-id="b6f46-343">9</span></span>|<span data-ttu-id="b6f46-344">Çöp toplama yürütme altyapısı ertelenmesi başlangıcı.</span><span class="sxs-lookup"><span data-stu-id="b6f46-344">Start of suspension of the execution engine for garbage collection.</span></span>|  
  
 <span data-ttu-id="b6f46-345">Aşağıdaki tabloda olay verilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="b6f46-345">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="b6f46-346">Alan adı</span><span class="sxs-lookup"><span data-stu-id="b6f46-346">Field name</span></span>|<span data-ttu-id="b6f46-347">Veri türü</span><span class="sxs-lookup"><span data-stu-id="b6f46-347">Data type</span></span>|<span data-ttu-id="b6f46-348">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b6f46-348">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="b6f46-349">Neden</span><span class="sxs-lookup"><span data-stu-id="b6f46-349">Reason</span></span>|<span data-ttu-id="b6f46-350">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="b6f46-350">win:UInt16</span></span>|<span data-ttu-id="b6f46-351">0x0 - diğer.</span><span class="sxs-lookup"><span data-stu-id="b6f46-351">0x0 - Other.</span></span><br /><br /> <span data-ttu-id="b6f46-352">0x1 - atık toplama.</span><span class="sxs-lookup"><span data-stu-id="b6f46-352">0x1 - Garbage collection.</span></span><br /><br /> <span data-ttu-id="b6f46-353">0x2 - uygulama etki alanı kapatma.</span><span class="sxs-lookup"><span data-stu-id="b6f46-353">0x2 - Application domain shutdown.</span></span><br /><br /> <span data-ttu-id="b6f46-354">0x3 - kod pitching.</span><span class="sxs-lookup"><span data-stu-id="b6f46-354">0x3 - Code pitching.</span></span><br /><br /> <span data-ttu-id="b6f46-355">0x4 - kapatma.</span><span class="sxs-lookup"><span data-stu-id="b6f46-355">0x4 - Shutdown.</span></span><br /><br /> <span data-ttu-id="b6f46-356">0x5 - hata ayıklayıcı.</span><span class="sxs-lookup"><span data-stu-id="b6f46-356">0x5 - Debugger.</span></span><br /><br /> <span data-ttu-id="b6f46-357">0x6 - atık toplama için hazırlama.</span><span class="sxs-lookup"><span data-stu-id="b6f46-357">0x6 - Preparation for garbage collection.</span></span>|  
|<span data-ttu-id="b6f46-358">Sayısı</span><span class="sxs-lookup"><span data-stu-id="b6f46-358">Count</span></span>|<span data-ttu-id="b6f46-359">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="b6f46-359">win:UInt32</span></span>|<span data-ttu-id="b6f46-360">Zaman GC sayısı.</span><span class="sxs-lookup"><span data-stu-id="b6f46-360">The GC count at the time.</span></span> <span data-ttu-id="b6f46-361">Genellikle, bundan sonra bir sonraki GC başlangıç olayı görür ve biz çöp toplama sırasında GC dizin arttıkça sayımına bu sayı + 1 olacaktır.</span><span class="sxs-lookup"><span data-stu-id="b6f46-361">Usually, you would see a subsequent GC Start event after this, and its Count would be this Count + 1 as we increase the GC index during a garbage collection.</span></span>|  
|<span data-ttu-id="b6f46-362">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="b6f46-362">ClrInstanceID</span></span>|<span data-ttu-id="b6f46-363">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="b6f46-363">win:UInt16</span></span>|<span data-ttu-id="b6f46-364">CLR veya CoreCLR örneği için benzersiz kimlik.</span><span class="sxs-lookup"><span data-stu-id="b6f46-364">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="b6f46-365">Başa dön</span><span class="sxs-lookup"><span data-stu-id="b6f46-365">Back to top</span></span>](#top)  
  
<a name="gcsuspendeeend_v1_event"></a>   
## <a name="gcsuspendeeendv1-event"></a><span data-ttu-id="b6f46-366">GCSuspendEEEnd_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="b6f46-366">GCSuspendEEEnd_V1 Event</span></span>  
 <span data-ttu-id="b6f46-367">Aşağıdaki tablo düzeyi ve anahtar sözcüğü gösterir:</span><span class="sxs-lookup"><span data-stu-id="b6f46-367">The following table shows the keyword and level:</span></span>  
  
|<span data-ttu-id="b6f46-368">Olay oluşturma için anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="b6f46-368">Keyword for raising the event</span></span>|<span data-ttu-id="b6f46-369">Düzey</span><span class="sxs-lookup"><span data-stu-id="b6f46-369">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="b6f46-370">`GCKeyword`(0x1)</span><span class="sxs-lookup"><span data-stu-id="b6f46-370">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="b6f46-371">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="b6f46-371">Informational (4)</span></span>|  
  
 <span data-ttu-id="b6f46-372">Aşağıdaki tabloda olay bilgileri gösterir:</span><span class="sxs-lookup"><span data-stu-id="b6f46-372">The following table shows the event information:</span></span>  
  
|<span data-ttu-id="b6f46-373">Olay</span><span class="sxs-lookup"><span data-stu-id="b6f46-373">Event</span></span>|<span data-ttu-id="b6f46-374">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="b6f46-374">Event ID</span></span>|<span data-ttu-id="b6f46-375">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="b6f46-375">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCSuspendEEEnd_V1`|<span data-ttu-id="b6f46-376">8</span><span class="sxs-lookup"><span data-stu-id="b6f46-376">8</span></span>|<span data-ttu-id="b6f46-377">Çöp toplama yürütme altyapısı ertelenmesi sonu.</span><span class="sxs-lookup"><span data-stu-id="b6f46-377">End of suspension of the execution engine for garbage collection.</span></span>|  
  
 <span data-ttu-id="b6f46-378">Olay verisi yok.</span><span class="sxs-lookup"><span data-stu-id="b6f46-378">No event data.</span></span>  
  
 [<span data-ttu-id="b6f46-379">Başa dön</span><span class="sxs-lookup"><span data-stu-id="b6f46-379">Back to top</span></span>](#top)  
  
<a name="gcallocationtick_v2_event"></a>   
## <a name="gcallocationtickv2-event"></a><span data-ttu-id="b6f46-380">GCAllocationTick_V2 olayı</span><span class="sxs-lookup"><span data-stu-id="b6f46-380">GCAllocationTick_V2 Event</span></span>  
 <span data-ttu-id="b6f46-381">Aşağıdaki tablo düzeyi ve anahtar sözcüğü gösterir.</span><span class="sxs-lookup"><span data-stu-id="b6f46-381">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="b6f46-382">Olay oluşturma için anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="b6f46-382">Keyword for raising the event</span></span>|<span data-ttu-id="b6f46-383">Düzey</span><span class="sxs-lookup"><span data-stu-id="b6f46-383">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="b6f46-384">`GCKeyword`(0x1)</span><span class="sxs-lookup"><span data-stu-id="b6f46-384">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="b6f46-385">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="b6f46-385">Informational (4)</span></span>|  
  
 <span data-ttu-id="b6f46-386">Aşağıdaki tabloda olay bilgilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="b6f46-386">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="b6f46-387">Olay</span><span class="sxs-lookup"><span data-stu-id="b6f46-387">Event</span></span>|<span data-ttu-id="b6f46-388">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="b6f46-388">Event ID</span></span>|<span data-ttu-id="b6f46-389">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="b6f46-389">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCAllocationTick_V2`|<span data-ttu-id="b6f46-390">10</span><span class="sxs-lookup"><span data-stu-id="b6f46-390">10</span></span>|<span data-ttu-id="b6f46-391">Her seferinde yaklaşık 100 KB tahsis edilir.</span><span class="sxs-lookup"><span data-stu-id="b6f46-391">Each time approximately 100 KB is allocated.</span></span>|  
  
 <span data-ttu-id="b6f46-392">Aşağıdaki tabloda olay verilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="b6f46-392">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="b6f46-393">Alan adı</span><span class="sxs-lookup"><span data-stu-id="b6f46-393">Field name</span></span>|<span data-ttu-id="b6f46-394">Veri türü</span><span class="sxs-lookup"><span data-stu-id="b6f46-394">Data type</span></span>|<span data-ttu-id="b6f46-395">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b6f46-395">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="b6f46-396">AllocationAmount</span><span class="sxs-lookup"><span data-stu-id="b6f46-396">AllocationAmount</span></span>|<span data-ttu-id="b6f46-397">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="b6f46-397">win:UInt32</span></span>|<span data-ttu-id="b6f46-398">Ayırma bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="b6f46-398">The allocation size, in bytes.</span></span> <span data-ttu-id="b6f46-399">Bu değer, ULONG (4,294,967,295 bayt) uzunluğundan daha küçük olan ayırma için doğrudur.</span><span class="sxs-lookup"><span data-stu-id="b6f46-399">This value is accurate for allocations that are less than the length of a ULONG (4,294,967,295 bytes).</span></span> <span data-ttu-id="b6f46-400">Ayırma büyükse, bu alan kesilmiş değer içerir.</span><span class="sxs-lookup"><span data-stu-id="b6f46-400">If the allocation is greater, this field contains a truncated value.</span></span> <span data-ttu-id="b6f46-401">Kullanım `AllocationAmount64` için çok büyük ayırma.</span><span class="sxs-lookup"><span data-stu-id="b6f46-401">Use `AllocationAmount64` for very large allocations.</span></span>|  
|<span data-ttu-id="b6f46-402">AllocationKind</span><span class="sxs-lookup"><span data-stu-id="b6f46-402">AllocationKind</span></span>|<span data-ttu-id="b6f46-403">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="b6f46-403">win:UInt32</span></span>|<span data-ttu-id="b6f46-404">0x0 - küçük nesne ayırma (küçük nesne yığın ayırma'dir).</span><span class="sxs-lookup"><span data-stu-id="b6f46-404">0x0 - Small object allocation (allocation is in small object heap).</span></span><br /><br /> <span data-ttu-id="b6f46-405">0x1 - büyük nesne ayırma (büyük nesne yığın ayırma'dir).</span><span class="sxs-lookup"><span data-stu-id="b6f46-405">0x1 - Large object allocation (allocation is in large object heap).</span></span>|  
|<span data-ttu-id="b6f46-406">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="b6f46-406">ClrInstanceID</span></span>|<span data-ttu-id="b6f46-407">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="b6f46-407">win:UInt16</span></span>|<span data-ttu-id="b6f46-408">CLR veya CoreCLR örneği için benzersiz kimlik.</span><span class="sxs-lookup"><span data-stu-id="b6f46-408">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
|<span data-ttu-id="b6f46-409">AllocationAmount64</span><span class="sxs-lookup"><span data-stu-id="b6f46-409">AllocationAmount64</span></span>|<span data-ttu-id="b6f46-410">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="b6f46-410">win:UInt64</span></span>|<span data-ttu-id="b6f46-411">Ayırma bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="b6f46-411">The allocation size, in bytes.</span></span> <span data-ttu-id="b6f46-412">Bu değer çok büyük ayırmalarını doğru olur.</span><span class="sxs-lookup"><span data-stu-id="b6f46-412">This value is accurate for very large allocations.</span></span>|  
|<span data-ttu-id="b6f46-413">TypeId</span><span class="sxs-lookup"><span data-stu-id="b6f46-413">TypeId</span></span>|<span data-ttu-id="b6f46-414">Win: işaretçi</span><span class="sxs-lookup"><span data-stu-id="b6f46-414">win:Pointer</span></span>|<span data-ttu-id="b6f46-415">MethodTable adresi.</span><span class="sxs-lookup"><span data-stu-id="b6f46-415">The address of the MethodTable.</span></span> <span data-ttu-id="b6f46-416">Bu olay sırasında ayrılan nesneleri çeşitli olduğunda, bu son (100 KB eşiği aşıldı nedeniyle nesne) ayrılmış nesne karşılık gelen MethodTable adresidir.</span><span class="sxs-lookup"><span data-stu-id="b6f46-416">When there are several types of objects that were allocated during this event, this is the address of the MethodTable that corresponds to the last object allocated (the object that caused the 100 KB threshold to be exceeded).</span></span>|  
|<span data-ttu-id="b6f46-417">TypeName</span><span class="sxs-lookup"><span data-stu-id="b6f46-417">TypeName</span></span>|<span data-ttu-id="b6f46-418">Win: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="b6f46-418">win:UnicodeString</span></span>|<span data-ttu-id="b6f46-419">Ayrıldı türünün adı.</span><span class="sxs-lookup"><span data-stu-id="b6f46-419">The name of the type that was allocated.</span></span> <span data-ttu-id="b6f46-420">Bu olay sırasında ayrılan nesneleri çeşitli olduğunda (100 KB eşiği aşıldı nedeniyle nesne) tahsis son nesnesinin türü budur.</span><span class="sxs-lookup"><span data-stu-id="b6f46-420">When there are several types of objects that were allocated during this event, this is the type of the last object allocated (the object that caused the 100 KB threshold to be exceeded).</span></span>|  
|<span data-ttu-id="b6f46-421">HeapIndex</span><span class="sxs-lookup"><span data-stu-id="b6f46-421">HeapIndex</span></span>|<span data-ttu-id="b6f46-422">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="b6f46-422">win:UInt32</span></span>|<span data-ttu-id="b6f46-423">Burada nesne ayrıldı yığın.</span><span class="sxs-lookup"><span data-stu-id="b6f46-423">The heap where the object was allocated.</span></span> <span data-ttu-id="b6f46-424">Bu değer, iş istasyonu çöp toplama ile çalışırken 0 (sıfır) olur.</span><span class="sxs-lookup"><span data-stu-id="b6f46-424">This value is 0 (zero) when running with workstation garbage collection.</span></span>|  
  
 [<span data-ttu-id="b6f46-425">Başa dön</span><span class="sxs-lookup"><span data-stu-id="b6f46-425">Back to top</span></span>](#top)  
  
<a name="gcfinalizersbegin_v1_event"></a>   
## <a name="gcfinalizersbeginv1-event"></a><span data-ttu-id="b6f46-426">GCFinalizersBegin_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="b6f46-426">GCFinalizersBegin_V1 Event</span></span>  
 <span data-ttu-id="b6f46-427">Aşağıdaki tablo düzeyi ve anahtar sözcüğü gösterir.</span><span class="sxs-lookup"><span data-stu-id="b6f46-427">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="b6f46-428">Olay oluşturma için anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="b6f46-428">Keyword for raising the event</span></span>|<span data-ttu-id="b6f46-429">Düzey</span><span class="sxs-lookup"><span data-stu-id="b6f46-429">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="b6f46-430">`GCKeyword`(0x1)</span><span class="sxs-lookup"><span data-stu-id="b6f46-430">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="b6f46-431">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="b6f46-431">Informational (4)</span></span>|  
  
 <span data-ttu-id="b6f46-432">Aşağıdaki tabloda olay bilgilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="b6f46-432">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="b6f46-433">Olay</span><span class="sxs-lookup"><span data-stu-id="b6f46-433">Event</span></span>|<span data-ttu-id="b6f46-434">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="b6f46-434">Event ID</span></span>|<span data-ttu-id="b6f46-435">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="b6f46-435">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCFinalizersBegin_V1`|<span data-ttu-id="b6f46-436">14</span><span class="sxs-lookup"><span data-stu-id="b6f46-436">14</span></span>|<span data-ttu-id="b6f46-437">Sonlandırıcılar çalıştıran başlangıcı.</span><span class="sxs-lookup"><span data-stu-id="b6f46-437">The start of running finalizers.</span></span>|  
  
 <span data-ttu-id="b6f46-438">Olay verisi yok.</span><span class="sxs-lookup"><span data-stu-id="b6f46-438">No event data.</span></span>  
  
 [<span data-ttu-id="b6f46-439">Başa dön</span><span class="sxs-lookup"><span data-stu-id="b6f46-439">Back to top</span></span>](#top)  
  
<a name="gcfinalizersend_v1_event"></a>   
## <a name="gcfinalizersendv1-event"></a><span data-ttu-id="b6f46-440">GCFinalizersEnd_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="b6f46-440">GCFinalizersEnd_V1 Event</span></span>  
 <span data-ttu-id="b6f46-441">Aşağıdaki tablo düzeyi ve anahtar sözcüğü gösterir.</span><span class="sxs-lookup"><span data-stu-id="b6f46-441">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="b6f46-442">Olay oluşturma için anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="b6f46-442">Keyword for raising the event</span></span>|<span data-ttu-id="b6f46-443">Düzey</span><span class="sxs-lookup"><span data-stu-id="b6f46-443">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="b6f46-444">`GCKeyword`(0x1)</span><span class="sxs-lookup"><span data-stu-id="b6f46-444">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="b6f46-445">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="b6f46-445">Informational (4)</span></span>|  
  
 <span data-ttu-id="b6f46-446">Aşağıdaki tabloda olay bilgilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="b6f46-446">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="b6f46-447">Olay</span><span class="sxs-lookup"><span data-stu-id="b6f46-447">Event</span></span>|<span data-ttu-id="b6f46-448">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="b6f46-448">Event ID</span></span>|<span data-ttu-id="b6f46-449">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="b6f46-449">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCFinalizersEnd_V1`|<span data-ttu-id="b6f46-450">13</span><span class="sxs-lookup"><span data-stu-id="b6f46-450">13</span></span>|<span data-ttu-id="b6f46-451">Sonlandırıcılar çalıştıran sonu.</span><span class="sxs-lookup"><span data-stu-id="b6f46-451">The end of running finalizers.</span></span>|  
  
 <span data-ttu-id="b6f46-452">Aşağıdaki tabloda olay verilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="b6f46-452">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="b6f46-453">Alan adı</span><span class="sxs-lookup"><span data-stu-id="b6f46-453">Field name</span></span>|<span data-ttu-id="b6f46-454">Veri türü</span><span class="sxs-lookup"><span data-stu-id="b6f46-454">Data type</span></span>|<span data-ttu-id="b6f46-455">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b6f46-455">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="b6f46-456">Sayısı</span><span class="sxs-lookup"><span data-stu-id="b6f46-456">Count</span></span>|<span data-ttu-id="b6f46-457">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="b6f46-457">win:UInt32</span></span>|<span data-ttu-id="b6f46-458">Çalıştırılan sonlandırıcılar sayısı.</span><span class="sxs-lookup"><span data-stu-id="b6f46-458">The number of finalizers that were run.</span></span>|  
|<span data-ttu-id="b6f46-459">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="b6f46-459">ClrInstanceID</span></span>|<span data-ttu-id="b6f46-460">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="b6f46-460">win:UInt16</span></span>|<span data-ttu-id="b6f46-461">CLR veya CoreCLR örneği için benzersiz kimlik.</span><span class="sxs-lookup"><span data-stu-id="b6f46-461">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="b6f46-462">Başa dön</span><span class="sxs-lookup"><span data-stu-id="b6f46-462">Back to top</span></span>](#top)  
  
<a name="gccreateconcurrentthread_v1_event"></a>   
## <a name="gccreateconcurrentthreadv1-event"></a><span data-ttu-id="b6f46-463">GCCreateConcurrentThread_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="b6f46-463">GCCreateConcurrentThread_V1 Event</span></span>  
 <span data-ttu-id="b6f46-464">Aşağıdaki tablo düzeyi ve anahtar sözcüğü gösterir.</span><span class="sxs-lookup"><span data-stu-id="b6f46-464">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="b6f46-465">Olay oluşturma için anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="b6f46-465">Keyword for raising the event</span></span>|<span data-ttu-id="b6f46-466">Düzey</span><span class="sxs-lookup"><span data-stu-id="b6f46-466">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="b6f46-467">`GCKeyword`(0x1)</span><span class="sxs-lookup"><span data-stu-id="b6f46-467">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="b6f46-468">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="b6f46-468">Informational (4)</span></span>|  
|<span data-ttu-id="b6f46-469">`ThreadingKeyword`(0x10000)</span><span class="sxs-lookup"><span data-stu-id="b6f46-469">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="b6f46-470">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="b6f46-470">Informational (4)</span></span>|  
  
 <span data-ttu-id="b6f46-471">Aşağıdaki tabloda olay bilgilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="b6f46-471">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="b6f46-472">Olay</span><span class="sxs-lookup"><span data-stu-id="b6f46-472">Event</span></span>|<span data-ttu-id="b6f46-473">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="b6f46-473">Event ID</span></span>|<span data-ttu-id="b6f46-474">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="b6f46-474">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCCreateConcurrentThread_V1`|<span data-ttu-id="b6f46-475">11</span><span class="sxs-lookup"><span data-stu-id="b6f46-475">11</span></span>|<span data-ttu-id="b6f46-476">Eşzamanlı atık toplama iş parçacığı oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="b6f46-476">Concurrent garbage collection thread was created.</span></span>|  
  
 <span data-ttu-id="b6f46-477">Olay verisi yok.</span><span class="sxs-lookup"><span data-stu-id="b6f46-477">No event data.</span></span>  
  
 [<span data-ttu-id="b6f46-478">Başa dön</span><span class="sxs-lookup"><span data-stu-id="b6f46-478">Back to top</span></span>](#top)  
  
<a name="gcterminateconcurrentthread_v1_event"></a>   
## <a name="gcterminateconcurrentthreadv1-event"></a><span data-ttu-id="b6f46-479">GCTerminateConcurrentThread_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="b6f46-479">GCTerminateConcurrentThread_V1 Event</span></span>  
 <span data-ttu-id="b6f46-480">Aşağıdaki tablo düzeyi ve anahtar sözcüğü gösterir.</span><span class="sxs-lookup"><span data-stu-id="b6f46-480">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="b6f46-481">Olay oluşturma için anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="b6f46-481">Keyword for raising the event</span></span>|<span data-ttu-id="b6f46-482">Düzey</span><span class="sxs-lookup"><span data-stu-id="b6f46-482">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="b6f46-483">`GCKeyword`(0x1)</span><span class="sxs-lookup"><span data-stu-id="b6f46-483">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="b6f46-484">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="b6f46-484">Informational (4)</span></span>|  
|<span data-ttu-id="b6f46-485">`ThreadingKeyword`(0x10000)</span><span class="sxs-lookup"><span data-stu-id="b6f46-485">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="b6f46-486">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="b6f46-486">Informational (4)</span></span>|  
  
 <span data-ttu-id="b6f46-487">Aşağıdaki tabloda olay bilgilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="b6f46-487">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="b6f46-488">Olay</span><span class="sxs-lookup"><span data-stu-id="b6f46-488">Event</span></span>|<span data-ttu-id="b6f46-489">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="b6f46-489">Event ID</span></span>|<span data-ttu-id="b6f46-490">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="b6f46-490">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCTerminateConcurrentThread_V1`|<span data-ttu-id="b6f46-491">12</span><span class="sxs-lookup"><span data-stu-id="b6f46-491">12</span></span>|<span data-ttu-id="b6f46-492">Eşzamanlı atık toplama iş parçacığı sona erdirildi.</span><span class="sxs-lookup"><span data-stu-id="b6f46-492">Concurrent garbage collection thread was terminated.</span></span>|  
  
 <span data-ttu-id="b6f46-493">Olay verisi yok.</span><span class="sxs-lookup"><span data-stu-id="b6f46-493">No event data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6f46-494">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b6f46-494">See Also</span></span>  
 [<span data-ttu-id="b6f46-495">CLR ETW olayları</span><span class="sxs-lookup"><span data-stu-id="b6f46-495">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
