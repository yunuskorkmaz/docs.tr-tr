---
title: Çöp Toplama ETW Olayları
ms.date: 03/30/2017
helpviewer_keywords:
- GC events
- garbage collection events [.NET Framework]
- ETW, garbage collection events (CLR)
ms.assetid: f14b6fd7-0966-4d87-bc89-54ef3a44a94a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ec90d022a0c72782f413a84b6fbd2c1b8d663a73
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71046505"
---
# <a name="garbage-collection-etw-events"></a><span data-ttu-id="2905f-102">Çöp Toplama ETW Olayları</span><span class="sxs-lookup"><span data-stu-id="2905f-102">Garbage Collection ETW Events</span></span>
<a name="top"></a><span data-ttu-id="2905f-103">Bu olaylar çöp koleksiyonuyla ilgili bilgiler toplar.</span><span class="sxs-lookup"><span data-stu-id="2905f-103">These events collect information pertaining to garbage collection.</span></span> <span data-ttu-id="2905f-104">Çöp toplamanın kaç kez gerçekleştirildiğini, çöp toplama sırasında ne kadar bellek serbest olduğunu ve bu şekilde ne kadar bellek kaldığını belirleme dahil, tanılama ve hata ayıklamada yardımcı olurlar.</span><span class="sxs-lookup"><span data-stu-id="2905f-104">They help in diagnostics and debugging, including determining how many times garbage collection was performed, how much memory was freed during garbage collection, and so on.</span></span>  
  
 <span data-ttu-id="2905f-105">Bu kategori aşağıdaki olaylardan oluşur:</span><span class="sxs-lookup"><span data-stu-id="2905f-105">This category consists of the following events:</span></span>  
  
- [<span data-ttu-id="2905f-106">GCStart_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="2905f-106">GCStart_V1 Event</span></span>](#gcstart_v1_event)  
  
- [<span data-ttu-id="2905f-107">GCEnd_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="2905f-107">GCEnd_V1 Event</span></span>](#gcend_v1_event)  
  
- [<span data-ttu-id="2905f-108">GCHeapStats_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="2905f-108">GCHeapStats_V1 Event</span></span>](#gcheapstats_v1_event)  
  
- [<span data-ttu-id="2905f-109">GCCreateSegment_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="2905f-109">GCCreateSegment_V1 Event</span></span>](#gccreatesegment_v1_event)  
  
- [<span data-ttu-id="2905f-110">GCFreeSegment_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="2905f-110">GCFreeSegment_V1 Event</span></span>](#gcfreesegment_v1_event)  
  
- [<span data-ttu-id="2905f-111">GCRestartEEBegin_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="2905f-111">GCRestartEEBegin_V1 Event</span></span>](#gcrestarteebegin_v1_event)  
  
- [<span data-ttu-id="2905f-112">GCRestartEEEnd_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="2905f-112">GCRestartEEEnd_V1 Event</span></span>](#gcrestarteeend_v1_event)  
  
- [<span data-ttu-id="2905f-113">GCSuspendEE_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="2905f-113">GCSuspendEE_V1 Event</span></span>](#gcsuspendee_v1_event)  
  
- [<span data-ttu-id="2905f-114">GCSuspendEEEnd_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="2905f-114">GCSuspendEEEnd_V1 Event</span></span>](#gcsuspendeeend_v1_event)  
  
- [<span data-ttu-id="2905f-115">GCAllocationTick_V2 olayı</span><span class="sxs-lookup"><span data-stu-id="2905f-115">GCAllocationTick_V2 Event</span></span>](#gcallocationtick_v2_event)  
  
- [<span data-ttu-id="2905f-116">GCFinalizersBegin_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="2905f-116">GCFinalizersBegin_V1 Event</span></span>](#gcfinalizersbegin_v1_event)  
  
- [<span data-ttu-id="2905f-117">GCFinalizersEnd_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="2905f-117">GCFinalizersEnd_V1 Event</span></span>](#gcfinalizersend_v1_event)  
  
- [<span data-ttu-id="2905f-118">GCCreateConcurrentThread_V1 Olayı</span><span class="sxs-lookup"><span data-stu-id="2905f-118">GCCreateConcurrentThread_V1 Event</span></span>](#gccreateconcurrentthread_v1_event)  
  
- [<span data-ttu-id="2905f-119">GCTerminateConcurrentThread_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="2905f-119">GCTerminateConcurrentThread_V1 Event</span></span>](#gcterminateconcurrentthread_v1_event)  
  
<a name="gcstart_v1_event"></a>   
## <a name="gcstart_v1-event"></a><span data-ttu-id="2905f-120">GCStart_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="2905f-120">GCStart_V1 Event</span></span>  
 <span data-ttu-id="2905f-121">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="2905f-121">The following table shows the keyword and level.</span></span> <span data-ttu-id="2905f-122">(Daha fazla bilgi için bkz. [CLR ETW anahtar sözcükleri ve düzeyleri](clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="2905f-122">(For more information, see [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="2905f-123">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="2905f-123">Keyword for raising the event</span></span>|<span data-ttu-id="2905f-124">Düzey</span><span class="sxs-lookup"><span data-stu-id="2905f-124">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="2905f-125">`GCKeyword`0x1</span><span class="sxs-lookup"><span data-stu-id="2905f-125">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="2905f-126">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="2905f-126">Informational (4)</span></span>|  
  
 <span data-ttu-id="2905f-127">Aşağıdaki tabloda olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="2905f-127">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="2905f-128">Olay</span><span class="sxs-lookup"><span data-stu-id="2905f-128">Event</span></span>|<span data-ttu-id="2905f-129">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="2905f-129">Event ID</span></span>|<span data-ttu-id="2905f-130">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="2905f-130">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCStart_V1`|<span data-ttu-id="2905f-131">1\.</span><span class="sxs-lookup"><span data-stu-id="2905f-131">1</span></span>|<span data-ttu-id="2905f-132">Çöp toplama işlemi başlatıldı.</span><span class="sxs-lookup"><span data-stu-id="2905f-132">A garbage collection has started.</span></span>|  
  
 <span data-ttu-id="2905f-133">Aşağıdaki tabloda olay verileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="2905f-133">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="2905f-134">Alan adı</span><span class="sxs-lookup"><span data-stu-id="2905f-134">Field name</span></span>|<span data-ttu-id="2905f-135">Veri türü</span><span class="sxs-lookup"><span data-stu-id="2905f-135">Data type</span></span>|<span data-ttu-id="2905f-136">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2905f-136">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="2905f-137">Count</span><span class="sxs-lookup"><span data-stu-id="2905f-137">Count</span></span>|<span data-ttu-id="2905f-138">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="2905f-138">win:UInt32</span></span>|<span data-ttu-id="2905f-139">*N*. çöp toplama.</span><span class="sxs-lookup"><span data-stu-id="2905f-139">The *n*th garbage collection.</span></span>|  
|<span data-ttu-id="2905f-140">Derinliğini</span><span class="sxs-lookup"><span data-stu-id="2905f-140">Depth</span></span>|<span data-ttu-id="2905f-141">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="2905f-141">win:UInt32</span></span>|<span data-ttu-id="2905f-142">Toplanmakta olan oluşturma.</span><span class="sxs-lookup"><span data-stu-id="2905f-142">The generation that is being collected.</span></span>|  
|<span data-ttu-id="2905f-143">Neden</span><span class="sxs-lookup"><span data-stu-id="2905f-143">Reason</span></span>|<span data-ttu-id="2905f-144">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="2905f-144">win:UInt32</span></span>|<span data-ttu-id="2905f-145">Çöp toplamanın neden tetiklendiği:</span><span class="sxs-lookup"><span data-stu-id="2905f-145">Why the garbage collection was triggered:</span></span><br /><br /> <span data-ttu-id="2905f-146">0x0-küçük nesne yığını ayırması.</span><span class="sxs-lookup"><span data-stu-id="2905f-146">0x0 - Small object heap allocation.</span></span><br /><br /> <span data-ttu-id="2905f-147">0x1-alınmış.</span><span class="sxs-lookup"><span data-stu-id="2905f-147">0x1 - Induced.</span></span><br /><br /> <span data-ttu-id="2905f-148">0x2-düşük bellek.</span><span class="sxs-lookup"><span data-stu-id="2905f-148">0x2 - Low memory.</span></span><br /><br /> <span data-ttu-id="2905f-149">0x3-boş.</span><span class="sxs-lookup"><span data-stu-id="2905f-149">0x3 - Empty.</span></span><br /><br /> <span data-ttu-id="2905f-150">0x4-büyük nesne yığını ayırması.</span><span class="sxs-lookup"><span data-stu-id="2905f-150">0x4 - Large object heap allocation.</span></span><br /><br /> <span data-ttu-id="2905f-151">0x5-alan kalmadı (küçük nesne yığını için).</span><span class="sxs-lookup"><span data-stu-id="2905f-151">0x5 - Out of space (for small object heap).</span></span><br /><br /> <span data-ttu-id="2905f-152">0x6-alan kalmadı (büyük nesne yığını için).</span><span class="sxs-lookup"><span data-stu-id="2905f-152">0x6 - Out of space (for large object heap).</span></span><br /><br /> <span data-ttu-id="2905f-153">0x7-alınmış ancak engelleme olarak zorlanmadı.</span><span class="sxs-lookup"><span data-stu-id="2905f-153">0x7 - Induced but not forced as blocking.</span></span>|  
|<span data-ttu-id="2905f-154">Tür</span><span class="sxs-lookup"><span data-stu-id="2905f-154">Type</span></span>|<span data-ttu-id="2905f-155">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="2905f-155">win:UInt32</span></span>|<span data-ttu-id="2905f-156">0x0-arka plan atık toplama dışında bir çöp toplama engelleme gerçekleşti.</span><span class="sxs-lookup"><span data-stu-id="2905f-156">0x0 - Blocking garbage collection occurred outside background garbage collection.</span></span><br /><br /> <span data-ttu-id="2905f-157">0x1-arka plan atık toplama.</span><span class="sxs-lookup"><span data-stu-id="2905f-157">0x1 - Background garbage collection.</span></span><br /><br /> <span data-ttu-id="2905f-158">0x2-arka plan atık toplama sırasında atık toplamayı engelleme oluştu.</span><span class="sxs-lookup"><span data-stu-id="2905f-158">0x2 - Blocking garbage collection occurred during background garbage collection.</span></span>|  
|<span data-ttu-id="2905f-159">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="2905f-159">ClrInstanceID</span></span>|<span data-ttu-id="2905f-160">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="2905f-160">win:UInt16</span></span>|<span data-ttu-id="2905f-161">CLR veya CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="2905f-161">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="2905f-162">Başa dön</span><span class="sxs-lookup"><span data-stu-id="2905f-162">Back to top</span></span>](#top)  
  
<a name="gcend_v1_event"></a>   
## <a name="gcend_v1-event"></a><span data-ttu-id="2905f-163">GCEnd_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="2905f-163">GCEnd_V1 Event</span></span>  
 <span data-ttu-id="2905f-164">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="2905f-164">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="2905f-165">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="2905f-165">Keyword for raising the event</span></span>|<span data-ttu-id="2905f-166">Düzey</span><span class="sxs-lookup"><span data-stu-id="2905f-166">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="2905f-167">`GCKeyword`0x1</span><span class="sxs-lookup"><span data-stu-id="2905f-167">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="2905f-168">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="2905f-168">Informational (4)</span></span>|  
  
 <span data-ttu-id="2905f-169">Aşağıdaki tabloda olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="2905f-169">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="2905f-170">Olay</span><span class="sxs-lookup"><span data-stu-id="2905f-170">Event</span></span>|<span data-ttu-id="2905f-171">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="2905f-171">Event ID</span></span>|<span data-ttu-id="2905f-172">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="2905f-172">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCEnd_V1`|<span data-ttu-id="2905f-173">2</span><span class="sxs-lookup"><span data-stu-id="2905f-173">2</span></span>|<span data-ttu-id="2905f-174">Çöp toplama sona erdi.</span><span class="sxs-lookup"><span data-stu-id="2905f-174">The garbage collection has ended.</span></span>|  
  
 <span data-ttu-id="2905f-175">Aşağıdaki tabloda olay verileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="2905f-175">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="2905f-176">Alan adı</span><span class="sxs-lookup"><span data-stu-id="2905f-176">Field name</span></span>|<span data-ttu-id="2905f-177">Veri türü</span><span class="sxs-lookup"><span data-stu-id="2905f-177">Data type</span></span>|<span data-ttu-id="2905f-178">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2905f-178">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="2905f-179">Count</span><span class="sxs-lookup"><span data-stu-id="2905f-179">Count</span></span>|<span data-ttu-id="2905f-180">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="2905f-180">win:UInt32</span></span>|<span data-ttu-id="2905f-181">*N*. çöp toplama.</span><span class="sxs-lookup"><span data-stu-id="2905f-181">The *n*th garbage collection.</span></span>|  
|<span data-ttu-id="2905f-182">Derinliğini</span><span class="sxs-lookup"><span data-stu-id="2905f-182">Depth</span></span>|<span data-ttu-id="2905f-183">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="2905f-183">win:UInt32</span></span>|<span data-ttu-id="2905f-184">Toplanan nesil.</span><span class="sxs-lookup"><span data-stu-id="2905f-184">The generation that was collected.</span></span>|  
|<span data-ttu-id="2905f-185">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="2905f-185">ClrInstanceID</span></span>|<span data-ttu-id="2905f-186">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="2905f-186">win:UInt16</span></span>|<span data-ttu-id="2905f-187">CLR veya CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="2905f-187">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="2905f-188">Başa dön</span><span class="sxs-lookup"><span data-stu-id="2905f-188">Back to top</span></span>](#top)  
  
<a name="gcheapstats_v1_event"></a>   
## <a name="gcheapstats_v1-event"></a><span data-ttu-id="2905f-189">GCHeapStats_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="2905f-189">GCHeapStats_V1 Event</span></span>  
 <span data-ttu-id="2905f-190">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="2905f-190">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="2905f-191">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="2905f-191">Keyword for raising the event</span></span>|<span data-ttu-id="2905f-192">Düzey</span><span class="sxs-lookup"><span data-stu-id="2905f-192">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="2905f-193">`GCKeyword`0x1</span><span class="sxs-lookup"><span data-stu-id="2905f-193">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="2905f-194">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="2905f-194">Informational (4)</span></span>|  
  
 <span data-ttu-id="2905f-195">Aşağıdaki tabloda olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="2905f-195">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="2905f-196">Olay</span><span class="sxs-lookup"><span data-stu-id="2905f-196">Event</span></span>|<span data-ttu-id="2905f-197">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="2905f-197">Event ID</span></span>|<span data-ttu-id="2905f-198">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2905f-198">Description</span></span>|  
|-----------|--------------|-----------------|  
|`GCHeapStats_V1`|<span data-ttu-id="2905f-199">4</span><span class="sxs-lookup"><span data-stu-id="2905f-199">4</span></span>|<span data-ttu-id="2905f-200">Her çöp toplamanın sonundaki yığın istatistiklerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="2905f-200">Shows the heap statistics at the end of each garbage collection.</span></span>|  
  
 <span data-ttu-id="2905f-201">Aşağıdaki tabloda olay verileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="2905f-201">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="2905f-202">Alan adı</span><span class="sxs-lookup"><span data-stu-id="2905f-202">Field name</span></span>|<span data-ttu-id="2905f-203">Veri türü</span><span class="sxs-lookup"><span data-stu-id="2905f-203">Data type</span></span>|<span data-ttu-id="2905f-204">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2905f-204">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="2905f-205">GenerationSize0</span><span class="sxs-lookup"><span data-stu-id="2905f-205">GenerationSize0</span></span>|<span data-ttu-id="2905f-206">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="2905f-206">win:UInt64</span></span>|<span data-ttu-id="2905f-207">0\. nesil belleğin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="2905f-207">The size, in bytes, of generation 0 memory.</span></span>|  
|<span data-ttu-id="2905f-208">TotalPromotedSize0</span><span class="sxs-lookup"><span data-stu-id="2905f-208">TotalPromotedSize0</span></span>|<span data-ttu-id="2905f-209">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="2905f-209">win:UInt64</span></span>|<span data-ttu-id="2905f-210">Nesil 0 ' dan 1 ' e yükseltilen bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="2905f-210">The number of bytes that are promoted from generation 0 to generation 1.</span></span>|  
|<span data-ttu-id="2905f-211">GenerationSize1</span><span class="sxs-lookup"><span data-stu-id="2905f-211">GenerationSize1</span></span>|<span data-ttu-id="2905f-212">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="2905f-212">win:UInt64</span></span>|<span data-ttu-id="2905f-213">1\. nesil belleğin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="2905f-213">The size, in bytes, of generation 1 memory.</span></span>|  
|<span data-ttu-id="2905f-214">TotalPromotedSize1</span><span class="sxs-lookup"><span data-stu-id="2905f-214">TotalPromotedSize1</span></span>|<span data-ttu-id="2905f-215">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="2905f-215">win:UInt64</span></span>|<span data-ttu-id="2905f-216">1\. nesil 2 ' ye kadar yükseltilen bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="2905f-216">The number of bytes that are promoted from generation 1 to generation 2.</span></span>|  
|<span data-ttu-id="2905f-217">GenerationSize2</span><span class="sxs-lookup"><span data-stu-id="2905f-217">GenerationSize2</span></span>|<span data-ttu-id="2905f-218">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="2905f-218">win:UInt64</span></span>|<span data-ttu-id="2905f-219">2\. nesil belleğin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="2905f-219">The size, in bytes, of generation 2 memory.</span></span>|  
|<span data-ttu-id="2905f-220">TotalPromotedSize2</span><span class="sxs-lookup"><span data-stu-id="2905f-220">TotalPromotedSize2</span></span>|<span data-ttu-id="2905f-221">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="2905f-221">win:UInt64</span></span>|<span data-ttu-id="2905f-222">Son koleksiyondan sonra 2. nesil üzerinde kalan bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="2905f-222">The number of bytes that survived in generation 2 after the last collection.</span></span>|  
|<span data-ttu-id="2905f-223">GenerationSize3</span><span class="sxs-lookup"><span data-stu-id="2905f-223">GenerationSize3</span></span>|<span data-ttu-id="2905f-224">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="2905f-224">win:UInt64</span></span>|<span data-ttu-id="2905f-225">Büyük nesne yığınının bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="2905f-225">The size, in bytes, of the large object heap.</span></span>|  
|<span data-ttu-id="2905f-226">TotalPromotedSize3</span><span class="sxs-lookup"><span data-stu-id="2905f-226">TotalPromotedSize3</span></span>|<span data-ttu-id="2905f-227">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="2905f-227">win:UInt64</span></span>|<span data-ttu-id="2905f-228">Son koleksiyondan sonra büyük nesne yığınında kalan bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="2905f-228">The number of bytes that survived in the large object heap after the last collection.</span></span>|  
|<span data-ttu-id="2905f-229">Sonlandırizationpromotedsize</span><span class="sxs-lookup"><span data-stu-id="2905f-229">FinalizationPromotedSize</span></span>|<span data-ttu-id="2905f-230">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="2905f-230">win:UInt64</span></span>|<span data-ttu-id="2905f-231">Sonlandırma için hazırlanma nesnelerinin bayt cinsinden toplam boyutu.</span><span class="sxs-lookup"><span data-stu-id="2905f-231">The total size, in bytes, of the objects that are ready for finalization.</span></span>|  
|<span data-ttu-id="2905f-232">Sonlandırizationpromotedcount</span><span class="sxs-lookup"><span data-stu-id="2905f-232">FinalizationPromotedCount</span></span>|<span data-ttu-id="2905f-233">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="2905f-233">win:UInt64</span></span>|<span data-ttu-id="2905f-234">Sonlandırmaya hazırlanma nesne sayısı.</span><span class="sxs-lookup"><span data-stu-id="2905f-234">The number of objects that are ready for finalization.</span></span>|  
|<span data-ttu-id="2905f-235">PinnedObjectCount</span><span class="sxs-lookup"><span data-stu-id="2905f-235">PinnedObjectCount</span></span>|<span data-ttu-id="2905f-236">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="2905f-236">win:UInt32</span></span>|<span data-ttu-id="2905f-237">Sabitlenmiş (taşınamaz) nesne sayısı.</span><span class="sxs-lookup"><span data-stu-id="2905f-237">The number of pinned (unmovable) objects.</span></span>|  
|<span data-ttu-id="2905f-238">SinkBlockCount</span><span class="sxs-lookup"><span data-stu-id="2905f-238">SinkBlockCount</span></span>|<span data-ttu-id="2905f-239">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="2905f-239">win:UInt32</span></span>|<span data-ttu-id="2905f-240">Kullanımdaki eşitleme bloklarının sayısı.</span><span class="sxs-lookup"><span data-stu-id="2905f-240">The number of synchronization blocks in use.</span></span>|  
|<span data-ttu-id="2905f-241">Gchandlet sayısı</span><span class="sxs-lookup"><span data-stu-id="2905f-241">GCHandleCount</span></span>|<span data-ttu-id="2905f-242">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="2905f-242">win:UInt32</span></span>|<span data-ttu-id="2905f-243">Kullanımdaki çöp toplama tanıtıcılarının sayısı.</span><span class="sxs-lookup"><span data-stu-id="2905f-243">The number of garbage collection handles in use.</span></span>|  
|<span data-ttu-id="2905f-244">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="2905f-244">ClrInstanceID</span></span>|<span data-ttu-id="2905f-245">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="2905f-245">win:UInt16</span></span>|<span data-ttu-id="2905f-246">CLR veya CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="2905f-246">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="2905f-247">Başa dön</span><span class="sxs-lookup"><span data-stu-id="2905f-247">Back to top</span></span>](#top)  
  
<a name="gccreatesegment_v1_event"></a>   
## <a name="gccreatesegment_v1-event"></a><span data-ttu-id="2905f-248">GCCreateSegment_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="2905f-248">GCCreateSegment_V1 Event</span></span>  
 <span data-ttu-id="2905f-249">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="2905f-249">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="2905f-250">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="2905f-250">Keyword for raising the event</span></span>|<span data-ttu-id="2905f-251">Düzey</span><span class="sxs-lookup"><span data-stu-id="2905f-251">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="2905f-252">`GCKeyword`0x1</span><span class="sxs-lookup"><span data-stu-id="2905f-252">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="2905f-253">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="2905f-253">Informational (4)</span></span>|  
  
 <span data-ttu-id="2905f-254">Aşağıdaki tabloda olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="2905f-254">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="2905f-255">Olay</span><span class="sxs-lookup"><span data-stu-id="2905f-255">Event</span></span>|<span data-ttu-id="2905f-256">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="2905f-256">Event ID</span></span>|<span data-ttu-id="2905f-257">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="2905f-257">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCCreateSegment_V1`|<span data-ttu-id="2905f-258">5</span><span class="sxs-lookup"><span data-stu-id="2905f-258">5</span></span>|<span data-ttu-id="2905f-259">Yeni bir atık toplama segmenti oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="2905f-259">A new garbage collection segment has been created.</span></span> <span data-ttu-id="2905f-260">Ayrıca, izleme zaten çalışmakta olan bir işlemde etkinleştirildiğinde, bu olay varolan her segment için oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="2905f-260">In addition, when tracing is enabled on a process that is already running, this event is raised for each existing segment.</span></span>|  
  
 <span data-ttu-id="2905f-261">Aşağıdaki tabloda olay verileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="2905f-261">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="2905f-262">Alan adı</span><span class="sxs-lookup"><span data-stu-id="2905f-262">Field name</span></span>|<span data-ttu-id="2905f-263">Veri türü</span><span class="sxs-lookup"><span data-stu-id="2905f-263">Data type</span></span>|<span data-ttu-id="2905f-264">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2905f-264">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="2905f-265">Adres</span><span class="sxs-lookup"><span data-stu-id="2905f-265">Address</span></span>|<span data-ttu-id="2905f-266">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="2905f-266">win:UInt64</span></span>|<span data-ttu-id="2905f-267">Segmentin adresi.</span><span class="sxs-lookup"><span data-stu-id="2905f-267">The address of the segment.</span></span>|  
|<span data-ttu-id="2905f-268">Boyut</span><span class="sxs-lookup"><span data-stu-id="2905f-268">Size</span></span>|<span data-ttu-id="2905f-269">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="2905f-269">win:UInt64</span></span>|<span data-ttu-id="2905f-270">Segmentin boyutu.</span><span class="sxs-lookup"><span data-stu-id="2905f-270">The size of the segment.</span></span>|  
|<span data-ttu-id="2905f-271">Tür</span><span class="sxs-lookup"><span data-stu-id="2905f-271">Type</span></span>|<span data-ttu-id="2905f-272">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="2905f-272">win:UInt32</span></span>|<span data-ttu-id="2905f-273">0x0-küçük nesne yığını.</span><span class="sxs-lookup"><span data-stu-id="2905f-273">0x0 - Small object heap.</span></span><br /><br /> <span data-ttu-id="2905f-274">0x1-büyük nesne yığını.</span><span class="sxs-lookup"><span data-stu-id="2905f-274">0x1 - Large object heap.</span></span><br /><br /> <span data-ttu-id="2905f-275">0x2-salt okunurdur yığın.</span><span class="sxs-lookup"><span data-stu-id="2905f-275">0x2 - Read-only heap.</span></span>|  
|<span data-ttu-id="2905f-276">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="2905f-276">ClrInstanceID</span></span>|<span data-ttu-id="2905f-277">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="2905f-277">win:UInt16</span></span>|<span data-ttu-id="2905f-278">CLR veya CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="2905f-278">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 <span data-ttu-id="2905f-279">Çöp toplayıcı tarafından ayrılan parçaların boyutunun uygulamaya özgü olduğunu ve düzenli güncelleştirmeler de dahil olmak üzere herhangi bir zamanda değişikliğe tabi olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="2905f-279">Note that the size of segments allocated by the garbage collector is implementation-specific and is subject to change at any time, including in periodic updates.</span></span> <span data-ttu-id="2905f-280">Uygulamanız, belirli bir kesim boyutuna ilişkin varsayımları asla belirtmemelidir veya buna bağlı olarak, kesim ayırmaları için kullanılabilir bellek miktarını yapılandırmayı denemelidir.</span><span class="sxs-lookup"><span data-stu-id="2905f-280">Your app should never make assumptions about or depend on a particular segment size, nor should it attempt to configure the amount of memory available for segment allocations.</span></span>  
  
 [<span data-ttu-id="2905f-281">Başa dön</span><span class="sxs-lookup"><span data-stu-id="2905f-281">Back to top</span></span>](#top)  
  
<a name="gcfreesegment_v1_event"></a>   
## <a name="gcfreesegment_v1-event"></a><span data-ttu-id="2905f-282">GCFreeSegment_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="2905f-282">GCFreeSegment_V1 Event</span></span>  
 <span data-ttu-id="2905f-283">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="2905f-283">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="2905f-284">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="2905f-284">Keyword for raising the event</span></span>|<span data-ttu-id="2905f-285">Düzey</span><span class="sxs-lookup"><span data-stu-id="2905f-285">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="2905f-286">`GCKeyword`0x1</span><span class="sxs-lookup"><span data-stu-id="2905f-286">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="2905f-287">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="2905f-287">Informational (4)</span></span>|  
  
 <span data-ttu-id="2905f-288">Aşağıdaki tabloda olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="2905f-288">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="2905f-289">Olay</span><span class="sxs-lookup"><span data-stu-id="2905f-289">Event</span></span>|<span data-ttu-id="2905f-290">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="2905f-290">Event ID</span></span>|<span data-ttu-id="2905f-291">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="2905f-291">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCFreeSegment_V1`|<span data-ttu-id="2905f-292">6</span><span class="sxs-lookup"><span data-stu-id="2905f-292">6</span></span>|<span data-ttu-id="2905f-293">Çöp toplama segmenti yayınlandı.</span><span class="sxs-lookup"><span data-stu-id="2905f-293">A garbage collection segment has been released.</span></span>|  
  
 <span data-ttu-id="2905f-294">Aşağıdaki tabloda olay verileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="2905f-294">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="2905f-295">Alan adı</span><span class="sxs-lookup"><span data-stu-id="2905f-295">Field name</span></span>|<span data-ttu-id="2905f-296">Veri türü</span><span class="sxs-lookup"><span data-stu-id="2905f-296">Data type</span></span>|<span data-ttu-id="2905f-297">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2905f-297">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="2905f-298">Adres</span><span class="sxs-lookup"><span data-stu-id="2905f-298">Address</span></span>|<span data-ttu-id="2905f-299">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="2905f-299">win:UInt64</span></span>|<span data-ttu-id="2905f-300">Segmentin adresi.</span><span class="sxs-lookup"><span data-stu-id="2905f-300">The address of the segment.</span></span>|  
|<span data-ttu-id="2905f-301">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="2905f-301">ClrInstanceID</span></span>|<span data-ttu-id="2905f-302">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="2905f-302">win:UInt16</span></span>|<span data-ttu-id="2905f-303">CLR veya CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="2905f-303">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="2905f-304">Başa dön</span><span class="sxs-lookup"><span data-stu-id="2905f-304">Back to top</span></span>](#top)  
  
<a name="gcrestarteebegin_v1_event"></a>   
## <a name="gcrestarteebegin_v1-event"></a><span data-ttu-id="2905f-305">GCRestartEEBegin_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="2905f-305">GCRestartEEBegin_V1 Event</span></span>  
 <span data-ttu-id="2905f-306">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="2905f-306">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="2905f-307">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="2905f-307">Keyword for raising the event</span></span>|<span data-ttu-id="2905f-308">Düzey</span><span class="sxs-lookup"><span data-stu-id="2905f-308">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="2905f-309">`GCKeyword`0x1</span><span class="sxs-lookup"><span data-stu-id="2905f-309">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="2905f-310">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="2905f-310">Informational (4)</span></span>|  
  
 <span data-ttu-id="2905f-311">Aşağıdaki tabloda olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="2905f-311">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="2905f-312">Olay</span><span class="sxs-lookup"><span data-stu-id="2905f-312">Event</span></span>|<span data-ttu-id="2905f-313">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="2905f-313">Event ID</span></span>|<span data-ttu-id="2905f-314">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="2905f-314">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCRestartEEBegin_V1`|<span data-ttu-id="2905f-315">7</span><span class="sxs-lookup"><span data-stu-id="2905f-315">7</span></span>|<span data-ttu-id="2905f-316">Ortak dil çalışma zamanı askıya alma işleminden sürdürme başladı.</span><span class="sxs-lookup"><span data-stu-id="2905f-316">Resumption from common language runtime suspension has begun.</span></span>|  
  
 <span data-ttu-id="2905f-317">Olay verisi yok.</span><span class="sxs-lookup"><span data-stu-id="2905f-317">No event data.</span></span>  
  
 [<span data-ttu-id="2905f-318">Başa dön</span><span class="sxs-lookup"><span data-stu-id="2905f-318">Back to top</span></span>](#top)  
  
<a name="gcrestarteeend_v1_event"></a>   
## <a name="gcrestarteeend_v1-event"></a><span data-ttu-id="2905f-319">GCRestartEEEnd_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="2905f-319">GCRestartEEEnd_V1 Event</span></span>  
 <span data-ttu-id="2905f-320">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="2905f-320">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="2905f-321">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="2905f-321">Keyword for raising the event</span></span>|<span data-ttu-id="2905f-322">Düzey</span><span class="sxs-lookup"><span data-stu-id="2905f-322">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="2905f-323">`GCKeyword`0x1</span><span class="sxs-lookup"><span data-stu-id="2905f-323">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="2905f-324">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="2905f-324">Informational (4)</span></span>|  
  
 <span data-ttu-id="2905f-325">Aşağıdaki tabloda olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="2905f-325">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="2905f-326">Olay</span><span class="sxs-lookup"><span data-stu-id="2905f-326">Event</span></span>|<span data-ttu-id="2905f-327">Olay kimliği</span><span class="sxs-lookup"><span data-stu-id="2905f-327">Event Id</span></span>|<span data-ttu-id="2905f-328">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="2905f-328">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCRestartEEEnd_V1`|<span data-ttu-id="2905f-329">3</span><span class="sxs-lookup"><span data-stu-id="2905f-329">3</span></span>|<span data-ttu-id="2905f-330">Ortak dil çalışma zamanı askıya alma işleminden sürdürme sonlandı.</span><span class="sxs-lookup"><span data-stu-id="2905f-330">Resumption from common language runtime suspension has ended.</span></span>|  
  
 <span data-ttu-id="2905f-331">Olay verisi yok.</span><span class="sxs-lookup"><span data-stu-id="2905f-331">No event data.</span></span>  
  
 [<span data-ttu-id="2905f-332">Başa dön</span><span class="sxs-lookup"><span data-stu-id="2905f-332">Back to top</span></span>](#top)  
  
<a name="gcsuspendee_v1_event"></a>   
## <a name="gcsuspendee_v1-event"></a><span data-ttu-id="2905f-333">GCSuspendEE_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="2905f-333">GCSuspendEE_V1 Event</span></span>  
 <span data-ttu-id="2905f-334">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="2905f-334">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="2905f-335">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="2905f-335">Keyword for raising the event</span></span>|<span data-ttu-id="2905f-336">Düzey</span><span class="sxs-lookup"><span data-stu-id="2905f-336">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="2905f-337">`GCKeyword`0x1</span><span class="sxs-lookup"><span data-stu-id="2905f-337">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="2905f-338">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="2905f-338">Informational (4)</span></span>|  
  
 <span data-ttu-id="2905f-339">Aşağıdaki tabloda olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="2905f-339">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="2905f-340">Olay</span><span class="sxs-lookup"><span data-stu-id="2905f-340">Event</span></span>|<span data-ttu-id="2905f-341">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="2905f-341">Event ID</span></span>|<span data-ttu-id="2905f-342">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="2905f-342">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCSuspendEE_V1`|<span data-ttu-id="2905f-343">9</span><span class="sxs-lookup"><span data-stu-id="2905f-343">9</span></span>|<span data-ttu-id="2905f-344">Çöp toplama için yürütme altyapısının askıya alınma başlangıcı.</span><span class="sxs-lookup"><span data-stu-id="2905f-344">Start of suspension of the execution engine for garbage collection.</span></span>|  
  
 <span data-ttu-id="2905f-345">Aşağıdaki tabloda olay verileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="2905f-345">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="2905f-346">Alan adı</span><span class="sxs-lookup"><span data-stu-id="2905f-346">Field name</span></span>|<span data-ttu-id="2905f-347">Veri türü</span><span class="sxs-lookup"><span data-stu-id="2905f-347">Data type</span></span>|<span data-ttu-id="2905f-348">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2905f-348">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="2905f-349">Neden</span><span class="sxs-lookup"><span data-stu-id="2905f-349">Reason</span></span>|<span data-ttu-id="2905f-350">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="2905f-350">win:UInt16</span></span>|<span data-ttu-id="2905f-351">0x0-diğer.</span><span class="sxs-lookup"><span data-stu-id="2905f-351">0x0 - Other.</span></span><br /><br /> <span data-ttu-id="2905f-352">0x1-çöp toplama.</span><span class="sxs-lookup"><span data-stu-id="2905f-352">0x1 - Garbage collection.</span></span><br /><br /> <span data-ttu-id="2905f-353">0x2-Uygulama etki alanı kapanıyor.</span><span class="sxs-lookup"><span data-stu-id="2905f-353">0x2 - Application domain shutdown.</span></span><br /><br /> <span data-ttu-id="2905f-354">0x3-kod yeniden getiriliyor.</span><span class="sxs-lookup"><span data-stu-id="2905f-354">0x3 - Code pitching.</span></span><br /><br /> <span data-ttu-id="2905f-355">0x4-kapanıyor.</span><span class="sxs-lookup"><span data-stu-id="2905f-355">0x4 - Shutdown.</span></span><br /><br /> <span data-ttu-id="2905f-356">0x5-Debugger.</span><span class="sxs-lookup"><span data-stu-id="2905f-356">0x5 - Debugger.</span></span><br /><br /> <span data-ttu-id="2905f-357">çöp toplama için 0x6 hazırlığı.</span><span class="sxs-lookup"><span data-stu-id="2905f-357">0x6 - Preparation for garbage collection.</span></span>|  
|<span data-ttu-id="2905f-358">Count</span><span class="sxs-lookup"><span data-stu-id="2905f-358">Count</span></span>|<span data-ttu-id="2905f-359">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="2905f-359">win:UInt32</span></span>|<span data-ttu-id="2905f-360">GC sayısı (saat).</span><span class="sxs-lookup"><span data-stu-id="2905f-360">The GC count at the time.</span></span> <span data-ttu-id="2905f-361">Genellikle, bundan sonra sonraki bir GC başlangıç olayını görürsünüz ve çöp toplama sırasında GC dizinini artırdıkça bu sayı + 1 olur.</span><span class="sxs-lookup"><span data-stu-id="2905f-361">Usually, you would see a subsequent GC Start event after this, and its Count would be this Count + 1 as we increase the GC index during a garbage collection.</span></span>|  
|<span data-ttu-id="2905f-362">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="2905f-362">ClrInstanceID</span></span>|<span data-ttu-id="2905f-363">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="2905f-363">win:UInt16</span></span>|<span data-ttu-id="2905f-364">CLR veya CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="2905f-364">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="2905f-365">Başa dön</span><span class="sxs-lookup"><span data-stu-id="2905f-365">Back to top</span></span>](#top)  
  
<a name="gcsuspendeeend_v1_event"></a>   
## <a name="gcsuspendeeend_v1-event"></a><span data-ttu-id="2905f-366">GCSuspendEEEnd_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="2905f-366">GCSuspendEEEnd_V1 Event</span></span>  
 <span data-ttu-id="2905f-367">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="2905f-367">The following table shows the keyword and level:</span></span>  
  
|<span data-ttu-id="2905f-368">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="2905f-368">Keyword for raising the event</span></span>|<span data-ttu-id="2905f-369">Düzey</span><span class="sxs-lookup"><span data-stu-id="2905f-369">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="2905f-370">`GCKeyword`0x1</span><span class="sxs-lookup"><span data-stu-id="2905f-370">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="2905f-371">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="2905f-371">Informational (4)</span></span>|  
  
 <span data-ttu-id="2905f-372">Aşağıdaki tabloda olay bilgileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="2905f-372">The following table shows the event information:</span></span>  
  
|<span data-ttu-id="2905f-373">Olay</span><span class="sxs-lookup"><span data-stu-id="2905f-373">Event</span></span>|<span data-ttu-id="2905f-374">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="2905f-374">Event ID</span></span>|<span data-ttu-id="2905f-375">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="2905f-375">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCSuspendEEEnd_V1`|<span data-ttu-id="2905f-376">8</span><span class="sxs-lookup"><span data-stu-id="2905f-376">8</span></span>|<span data-ttu-id="2905f-377">Çöp toplama için yürütme altyapısının askıya alınma sonu.</span><span class="sxs-lookup"><span data-stu-id="2905f-377">End of suspension of the execution engine for garbage collection.</span></span>|  
  
 <span data-ttu-id="2905f-378">Olay verisi yok.</span><span class="sxs-lookup"><span data-stu-id="2905f-378">No event data.</span></span>  
  
 [<span data-ttu-id="2905f-379">Başa dön</span><span class="sxs-lookup"><span data-stu-id="2905f-379">Back to top</span></span>](#top)  
  
<a name="gcallocationtick_v2_event"></a>   
## <a name="gcallocationtick_v2-event"></a><span data-ttu-id="2905f-380">GCAllocationTick_V2 olayı</span><span class="sxs-lookup"><span data-stu-id="2905f-380">GCAllocationTick_V2 Event</span></span>  
 <span data-ttu-id="2905f-381">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="2905f-381">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="2905f-382">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="2905f-382">Keyword for raising the event</span></span>|<span data-ttu-id="2905f-383">Düzey</span><span class="sxs-lookup"><span data-stu-id="2905f-383">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="2905f-384">`GCKeyword`0x1</span><span class="sxs-lookup"><span data-stu-id="2905f-384">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="2905f-385">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="2905f-385">Informational (4)</span></span>|  
  
 <span data-ttu-id="2905f-386">Aşağıdaki tabloda olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="2905f-386">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="2905f-387">Olay</span><span class="sxs-lookup"><span data-stu-id="2905f-387">Event</span></span>|<span data-ttu-id="2905f-388">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="2905f-388">Event ID</span></span>|<span data-ttu-id="2905f-389">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="2905f-389">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCAllocationTick_V2`|<span data-ttu-id="2905f-390">10</span><span class="sxs-lookup"><span data-stu-id="2905f-390">10</span></span>|<span data-ttu-id="2905f-391">Yaklaşık 100 KB ayrıldığı her seferinde.</span><span class="sxs-lookup"><span data-stu-id="2905f-391">Each time approximately 100 KB is allocated.</span></span>|  
  
 <span data-ttu-id="2905f-392">Aşağıdaki tabloda olay verileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="2905f-392">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="2905f-393">Alan adı</span><span class="sxs-lookup"><span data-stu-id="2905f-393">Field name</span></span>|<span data-ttu-id="2905f-394">Veri türü</span><span class="sxs-lookup"><span data-stu-id="2905f-394">Data type</span></span>|<span data-ttu-id="2905f-395">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2905f-395">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="2905f-396">AllocationAmount</span><span class="sxs-lookup"><span data-stu-id="2905f-396">AllocationAmount</span></span>|<span data-ttu-id="2905f-397">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="2905f-397">win:UInt32</span></span>|<span data-ttu-id="2905f-398">Bayt cinsinden ayırma boyutu.</span><span class="sxs-lookup"><span data-stu-id="2905f-398">The allocation size, in bytes.</span></span> <span data-ttu-id="2905f-399">Bu değer, ULONG 'un uzunluğundan (4.294.967.295 bayt) daha az olan ayırmalar için doğrudur.</span><span class="sxs-lookup"><span data-stu-id="2905f-399">This value is accurate for allocations that are less than the length of a ULONG (4,294,967,295 bytes).</span></span> <span data-ttu-id="2905f-400">Ayırma daha büyükse, bu alan kesilmiş bir değer içerir.</span><span class="sxs-lookup"><span data-stu-id="2905f-400">If the allocation is greater, this field contains a truncated value.</span></span> <span data-ttu-id="2905f-401">Çok `AllocationAmount64` büyük ayırmalar için kullanın.</span><span class="sxs-lookup"><span data-stu-id="2905f-401">Use `AllocationAmount64` for very large allocations.</span></span>|  
|<span data-ttu-id="2905f-402">AllocationKind</span><span class="sxs-lookup"><span data-stu-id="2905f-402">AllocationKind</span></span>|<span data-ttu-id="2905f-403">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="2905f-403">win:UInt32</span></span>|<span data-ttu-id="2905f-404">0x0-küçük nesne ayırma (ayırma küçük nesne yığınında).</span><span class="sxs-lookup"><span data-stu-id="2905f-404">0x0 - Small object allocation (allocation is in small object heap).</span></span><br /><br /> <span data-ttu-id="2905f-405">0x1-büyük nesne ayırma (ayırma büyük nesne yığınında).</span><span class="sxs-lookup"><span data-stu-id="2905f-405">0x1 - Large object allocation (allocation is in large object heap).</span></span>|  
|<span data-ttu-id="2905f-406">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="2905f-406">ClrInstanceID</span></span>|<span data-ttu-id="2905f-407">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="2905f-407">win:UInt16</span></span>|<span data-ttu-id="2905f-408">CLR veya CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="2905f-408">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
|<span data-ttu-id="2905f-409">AllocationAmount64</span><span class="sxs-lookup"><span data-stu-id="2905f-409">AllocationAmount64</span></span>|<span data-ttu-id="2905f-410">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="2905f-410">win:UInt64</span></span>|<span data-ttu-id="2905f-411">Bayt cinsinden ayırma boyutu.</span><span class="sxs-lookup"><span data-stu-id="2905f-411">The allocation size, in bytes.</span></span> <span data-ttu-id="2905f-412">Bu değer, çok büyük ayırmalar için doğrudur.</span><span class="sxs-lookup"><span data-stu-id="2905f-412">This value is accurate for very large allocations.</span></span>|  
|<span data-ttu-id="2905f-413">Türü</span><span class="sxs-lookup"><span data-stu-id="2905f-413">TypeId</span></span>|<span data-ttu-id="2905f-414">Win: Işaretçi</span><span class="sxs-lookup"><span data-stu-id="2905f-414">win:Pointer</span></span>|<span data-ttu-id="2905f-415">MethodTable 'ın adresi.</span><span class="sxs-lookup"><span data-stu-id="2905f-415">The address of the MethodTable.</span></span> <span data-ttu-id="2905f-416">Bu olay sırasında ayrılan çeşitli nesne türleri olduğunda, bu, ayrılan son nesneye (100 KB eşiğinin aşılmasına neden olan nesne) karşılık gelen MethodTable 'ın adresidir.</span><span class="sxs-lookup"><span data-stu-id="2905f-416">When there are several types of objects that were allocated during this event, this is the address of the MethodTable that corresponds to the last object allocated (the object that caused the 100 KB threshold to be exceeded).</span></span>|  
|<span data-ttu-id="2905f-417">TypeName</span><span class="sxs-lookup"><span data-stu-id="2905f-417">TypeName</span></span>|<span data-ttu-id="2905f-418">Win: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="2905f-418">win:UnicodeString</span></span>|<span data-ttu-id="2905f-419">Ayrılan türün adı.</span><span class="sxs-lookup"><span data-stu-id="2905f-419">The name of the type that was allocated.</span></span> <span data-ttu-id="2905f-420">Bu olay sırasında ayrılan çeşitli nesne türleri varsa, bu, ayrılan son nesnenin türüdür (100 KB eşiğinin aşılmasına neden olan nesne).</span><span class="sxs-lookup"><span data-stu-id="2905f-420">When there are several types of objects that were allocated during this event, this is the type of the last object allocated (the object that caused the 100 KB threshold to be exceeded).</span></span>|  
|<span data-ttu-id="2905f-421">Heapındex</span><span class="sxs-lookup"><span data-stu-id="2905f-421">HeapIndex</span></span>|<span data-ttu-id="2905f-422">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="2905f-422">win:UInt32</span></span>|<span data-ttu-id="2905f-423">Nesnenin ayrıldığı yığın.</span><span class="sxs-lookup"><span data-stu-id="2905f-423">The heap where the object was allocated.</span></span> <span data-ttu-id="2905f-424">Bu değer, iş istasyonu atık toplama ile çalıştırılırken 0 (sıfır) değeridir.</span><span class="sxs-lookup"><span data-stu-id="2905f-424">This value is 0 (zero) when running with workstation garbage collection.</span></span>|  
  
 [<span data-ttu-id="2905f-425">Başa dön</span><span class="sxs-lookup"><span data-stu-id="2905f-425">Back to top</span></span>](#top)  
  
<a name="gcfinalizersbegin_v1_event"></a>   
## <a name="gcfinalizersbegin_v1-event"></a><span data-ttu-id="2905f-426">GCFinalizersBegin_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="2905f-426">GCFinalizersBegin_V1 Event</span></span>  
 <span data-ttu-id="2905f-427">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="2905f-427">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="2905f-428">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="2905f-428">Keyword for raising the event</span></span>|<span data-ttu-id="2905f-429">Düzey</span><span class="sxs-lookup"><span data-stu-id="2905f-429">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="2905f-430">`GCKeyword`0x1</span><span class="sxs-lookup"><span data-stu-id="2905f-430">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="2905f-431">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="2905f-431">Informational (4)</span></span>|  
  
 <span data-ttu-id="2905f-432">Aşağıdaki tabloda olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="2905f-432">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="2905f-433">Olay</span><span class="sxs-lookup"><span data-stu-id="2905f-433">Event</span></span>|<span data-ttu-id="2905f-434">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="2905f-434">Event ID</span></span>|<span data-ttu-id="2905f-435">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="2905f-435">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCFinalizersBegin_V1`|<span data-ttu-id="2905f-436">14</span><span class="sxs-lookup"><span data-stu-id="2905f-436">14</span></span>|<span data-ttu-id="2905f-437">Sonlandırıcıları çalıştırmanın başlangıcı.</span><span class="sxs-lookup"><span data-stu-id="2905f-437">The start of running finalizers.</span></span>|  
  
 <span data-ttu-id="2905f-438">Olay verisi yok.</span><span class="sxs-lookup"><span data-stu-id="2905f-438">No event data.</span></span>  
  
 [<span data-ttu-id="2905f-439">Başa dön</span><span class="sxs-lookup"><span data-stu-id="2905f-439">Back to top</span></span>](#top)  
  
<a name="gcfinalizersend_v1_event"></a>   
## <a name="gcfinalizersend_v1-event"></a><span data-ttu-id="2905f-440">GCFinalizersEnd_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="2905f-440">GCFinalizersEnd_V1 Event</span></span>  
 <span data-ttu-id="2905f-441">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="2905f-441">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="2905f-442">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="2905f-442">Keyword for raising the event</span></span>|<span data-ttu-id="2905f-443">Düzey</span><span class="sxs-lookup"><span data-stu-id="2905f-443">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="2905f-444">`GCKeyword`0x1</span><span class="sxs-lookup"><span data-stu-id="2905f-444">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="2905f-445">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="2905f-445">Informational (4)</span></span>|  
  
 <span data-ttu-id="2905f-446">Aşağıdaki tabloda olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="2905f-446">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="2905f-447">Olay</span><span class="sxs-lookup"><span data-stu-id="2905f-447">Event</span></span>|<span data-ttu-id="2905f-448">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="2905f-448">Event ID</span></span>|<span data-ttu-id="2905f-449">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="2905f-449">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCFinalizersEnd_V1`|<span data-ttu-id="2905f-450">13</span><span class="sxs-lookup"><span data-stu-id="2905f-450">13</span></span>|<span data-ttu-id="2905f-451">Sonlandırıcılardan çalıştırmanın sonu.</span><span class="sxs-lookup"><span data-stu-id="2905f-451">The end of running finalizers.</span></span>|  
  
 <span data-ttu-id="2905f-452">Aşağıdaki tabloda olay verileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="2905f-452">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="2905f-453">Alan adı</span><span class="sxs-lookup"><span data-stu-id="2905f-453">Field name</span></span>|<span data-ttu-id="2905f-454">Veri türü</span><span class="sxs-lookup"><span data-stu-id="2905f-454">Data type</span></span>|<span data-ttu-id="2905f-455">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2905f-455">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="2905f-456">Count</span><span class="sxs-lookup"><span data-stu-id="2905f-456">Count</span></span>|<span data-ttu-id="2905f-457">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="2905f-457">win:UInt32</span></span>|<span data-ttu-id="2905f-458">Çalıştırılan sonlandırıcılar sayısı.</span><span class="sxs-lookup"><span data-stu-id="2905f-458">The number of finalizers that were run.</span></span>|  
|<span data-ttu-id="2905f-459">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="2905f-459">ClrInstanceID</span></span>|<span data-ttu-id="2905f-460">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="2905f-460">win:UInt16</span></span>|<span data-ttu-id="2905f-461">CLR veya CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="2905f-461">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="2905f-462">Başa dön</span><span class="sxs-lookup"><span data-stu-id="2905f-462">Back to top</span></span>](#top)  
  
<a name="gccreateconcurrentthread_v1_event"></a>   
## <a name="gccreateconcurrentthread_v1-event"></a><span data-ttu-id="2905f-463">GCCreateConcurrentThread_V1 Olayı</span><span class="sxs-lookup"><span data-stu-id="2905f-463">GCCreateConcurrentThread_V1 Event</span></span>  
 <span data-ttu-id="2905f-464">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="2905f-464">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="2905f-465">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="2905f-465">Keyword for raising the event</span></span>|<span data-ttu-id="2905f-466">Düzey</span><span class="sxs-lookup"><span data-stu-id="2905f-466">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="2905f-467">`GCKeyword`0x1</span><span class="sxs-lookup"><span data-stu-id="2905f-467">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="2905f-468">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="2905f-468">Informational (4)</span></span>|  
|<span data-ttu-id="2905f-469">`ThreadingKeyword`(0x10000)</span><span class="sxs-lookup"><span data-stu-id="2905f-469">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="2905f-470">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="2905f-470">Informational (4)</span></span>|  
  
 <span data-ttu-id="2905f-471">Aşağıdaki tabloda olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="2905f-471">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="2905f-472">Olay</span><span class="sxs-lookup"><span data-stu-id="2905f-472">Event</span></span>|<span data-ttu-id="2905f-473">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="2905f-473">Event ID</span></span>|<span data-ttu-id="2905f-474">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="2905f-474">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCCreateConcurrentThread_V1`|<span data-ttu-id="2905f-475">11</span><span class="sxs-lookup"><span data-stu-id="2905f-475">11</span></span>|<span data-ttu-id="2905f-476">Eşzamanlı atık toplama iş parçacığı oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="2905f-476">Concurrent garbage collection thread was created.</span></span>|  
  
 <span data-ttu-id="2905f-477">Olay verisi yok.</span><span class="sxs-lookup"><span data-stu-id="2905f-477">No event data.</span></span>  
  
 [<span data-ttu-id="2905f-478">Başa dön</span><span class="sxs-lookup"><span data-stu-id="2905f-478">Back to top</span></span>](#top)  
  
<a name="gcterminateconcurrentthread_v1_event"></a>   
## <a name="gcterminateconcurrentthread_v1-event"></a><span data-ttu-id="2905f-479">GCTerminateConcurrentThread_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="2905f-479">GCTerminateConcurrentThread_V1 Event</span></span>  
 <span data-ttu-id="2905f-480">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="2905f-480">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="2905f-481">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="2905f-481">Keyword for raising the event</span></span>|<span data-ttu-id="2905f-482">Düzey</span><span class="sxs-lookup"><span data-stu-id="2905f-482">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="2905f-483">`GCKeyword`0x1</span><span class="sxs-lookup"><span data-stu-id="2905f-483">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="2905f-484">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="2905f-484">Informational (4)</span></span>|  
|<span data-ttu-id="2905f-485">`ThreadingKeyword`(0x10000)</span><span class="sxs-lookup"><span data-stu-id="2905f-485">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="2905f-486">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="2905f-486">Informational (4)</span></span>|  
  
 <span data-ttu-id="2905f-487">Aşağıdaki tabloda olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="2905f-487">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="2905f-488">Olay</span><span class="sxs-lookup"><span data-stu-id="2905f-488">Event</span></span>|<span data-ttu-id="2905f-489">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="2905f-489">Event ID</span></span>|<span data-ttu-id="2905f-490">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="2905f-490">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCTerminateConcurrentThread_V1`|<span data-ttu-id="2905f-491">12</span><span class="sxs-lookup"><span data-stu-id="2905f-491">12</span></span>|<span data-ttu-id="2905f-492">Eşzamanlı atık toplama iş parçacığı sonlandırıldı.</span><span class="sxs-lookup"><span data-stu-id="2905f-492">Concurrent garbage collection thread was terminated.</span></span>|  
  
 <span data-ttu-id="2905f-493">Olay verisi yok.</span><span class="sxs-lookup"><span data-stu-id="2905f-493">No event data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2905f-494">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2905f-494">See also</span></span>

- [<span data-ttu-id="2905f-495">CLR ETW Olayları</span><span class="sxs-lookup"><span data-stu-id="2905f-495">CLR ETW Events</span></span>](clr-etw-events.md)
