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
ms.openlocfilehash: 7f9bf0e309ec8c77d4b1d6afbf111e7eeae629ac
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59149740"
---
# <a name="garbage-collection-etw-events"></a><span data-ttu-id="0b797-102">Çöp Toplama ETW Olayları</span><span class="sxs-lookup"><span data-stu-id="0b797-102">Garbage Collection ETW Events</span></span>
<a name="top"></a> <span data-ttu-id="0b797-103">Bu olaylar, çöp toplama hakkında bilgi toplayın.</span><span class="sxs-lookup"><span data-stu-id="0b797-103">These events collect information pertaining to garbage collection.</span></span> <span data-ttu-id="0b797-104">Bunlar Tanılama'da yardımcı olur ve hata ayıklama, çöp toplama kaç kez belirleme de dahil olmak üzere gerçekleştirildiyse, ne kadar bellek çöp toplama ve benzeri sırasında bırakılmış.</span><span class="sxs-lookup"><span data-stu-id="0b797-104">They help in diagnostics and debugging, including determining how many times garbage collection was performed, how much memory was freed during garbage collection, and so on.</span></span>  
  
 <span data-ttu-id="0b797-105">Bu kategori aşağıdaki olaylar oluşur:</span><span class="sxs-lookup"><span data-stu-id="0b797-105">This category consists of the following events:</span></span>  
  
-   [<span data-ttu-id="0b797-106">GCStart_V1 olay</span><span class="sxs-lookup"><span data-stu-id="0b797-106">GCStart_V1 Event</span></span>](#gcstart_v1_event)  
  
-   [<span data-ttu-id="0b797-107">GCEnd_V1 olay</span><span class="sxs-lookup"><span data-stu-id="0b797-107">GCEnd_V1 Event</span></span>](#gcend_v1_event)  
  
-   [<span data-ttu-id="0b797-108">GCHeapStats_V1 olay</span><span class="sxs-lookup"><span data-stu-id="0b797-108">GCHeapStats_V1 Event</span></span>](#gcheapstats_v1_event)  
  
-   [<span data-ttu-id="0b797-109">GCCreateSegment_V1 Event</span><span class="sxs-lookup"><span data-stu-id="0b797-109">GCCreateSegment_V1 Event</span></span>](#gccreatesegment_v1_event)  
  
-   [<span data-ttu-id="0b797-110">GCFreeSegment_V1 Event</span><span class="sxs-lookup"><span data-stu-id="0b797-110">GCFreeSegment_V1 Event</span></span>](#gcfreesegment_v1_event)  
  
-   [<span data-ttu-id="0b797-111">GCRestartEEBegin_V1 olay</span><span class="sxs-lookup"><span data-stu-id="0b797-111">GCRestartEEBegin_V1 Event</span></span>](#gcrestarteebegin_v1_event)  
  
-   [<span data-ttu-id="0b797-112">GCRestartEEEnd_V1 olay</span><span class="sxs-lookup"><span data-stu-id="0b797-112">GCRestartEEEnd_V1 Event</span></span>](#gcrestarteeend_v1_event)  
  
-   [<span data-ttu-id="0b797-113">GCSuspendEE_V1 Event</span><span class="sxs-lookup"><span data-stu-id="0b797-113">GCSuspendEE_V1 Event</span></span>](#gcsuspendee_v1_event)  
  
-   [<span data-ttu-id="0b797-114">GCSuspendEEEnd_V1 Event</span><span class="sxs-lookup"><span data-stu-id="0b797-114">GCSuspendEEEnd_V1 Event</span></span>](#gcsuspendeeend_v1_event)  
  
-   [<span data-ttu-id="0b797-115">GCAllocationTick_V2 olay</span><span class="sxs-lookup"><span data-stu-id="0b797-115">GCAllocationTick_V2 Event</span></span>](#gcallocationtick_v2_event)  
  
-   [<span data-ttu-id="0b797-116">GCFinalizersBegin_V1 olay</span><span class="sxs-lookup"><span data-stu-id="0b797-116">GCFinalizersBegin_V1 Event</span></span>](#gcfinalizersbegin_v1_event)  
  
-   [<span data-ttu-id="0b797-117">GCFinalizersEnd_V1 olay</span><span class="sxs-lookup"><span data-stu-id="0b797-117">GCFinalizersEnd_V1 Event</span></span>](#gcfinalizersend_v1_event)  
  
-   [<span data-ttu-id="0b797-118">GCCreateConcurrentThread_V1 olay</span><span class="sxs-lookup"><span data-stu-id="0b797-118">GCCreateConcurrentThread_V1 Event</span></span>](#gccreateconcurrentthread_v1_event)  
  
-   [<span data-ttu-id="0b797-119">GCTerminateConcurrentThread_V1 olay</span><span class="sxs-lookup"><span data-stu-id="0b797-119">GCTerminateConcurrentThread_V1 Event</span></span>](#gcterminateconcurrentthread_v1_event)  
  
<a name="gcstart_v1_event"></a>   
## <a name="gcstartv1-event"></a><span data-ttu-id="0b797-120">GCStart_V1 olay</span><span class="sxs-lookup"><span data-stu-id="0b797-120">GCStart_V1 Event</span></span>  
 <span data-ttu-id="0b797-121">Aşağıdaki tabloda, düzeyi ve anahtar sözcüğü gösterir.</span><span class="sxs-lookup"><span data-stu-id="0b797-121">The following table shows the keyword and level.</span></span> <span data-ttu-id="0b797-122">(Daha fazla bilgi için [CLR ETW anahtar sözcükleri ve Düzeyler](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="0b797-122">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="0b797-123">Olayı için anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="0b797-123">Keyword for raising the event</span></span>|<span data-ttu-id="0b797-124">Düzey</span><span class="sxs-lookup"><span data-stu-id="0b797-124">Level</span></span>|  
|-----------------------------------|-----------|  
|`GCKeyword` <span data-ttu-id="0b797-125">(0x1)</span><span class="sxs-lookup"><span data-stu-id="0b797-125">(0x1)</span></span>|<span data-ttu-id="0b797-126">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="0b797-126">Informational (4)</span></span>|  
  
 <span data-ttu-id="0b797-127">Aşağıdaki tabloda, olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="0b797-127">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="0b797-128">Olay</span><span class="sxs-lookup"><span data-stu-id="0b797-128">Event</span></span>|<span data-ttu-id="0b797-129">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="0b797-129">Event ID</span></span>|<span data-ttu-id="0b797-130">Ne zaman gerçekleşti</span><span class="sxs-lookup"><span data-stu-id="0b797-130">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCStart_V1`|<span data-ttu-id="0b797-131">1.</span><span class="sxs-lookup"><span data-stu-id="0b797-131">1</span></span>|<span data-ttu-id="0b797-132">Bir çöp toplama başlatıldı.</span><span class="sxs-lookup"><span data-stu-id="0b797-132">A garbage collection has started.</span></span>|  
  
 <span data-ttu-id="0b797-133">Aşağıdaki tabloda, olay verilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="0b797-133">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="0b797-134">Alan adı</span><span class="sxs-lookup"><span data-stu-id="0b797-134">Field name</span></span>|<span data-ttu-id="0b797-135">Veri türü</span><span class="sxs-lookup"><span data-stu-id="0b797-135">Data type</span></span>|<span data-ttu-id="0b797-136">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0b797-136">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="0b797-137">Sayı</span><span class="sxs-lookup"><span data-stu-id="0b797-137">Count</span></span>|<span data-ttu-id="0b797-138">Kazanma: UInt32</span><span class="sxs-lookup"><span data-stu-id="0b797-138">win:UInt32</span></span>|<span data-ttu-id="0b797-139">*n*th çöp toplama.</span><span class="sxs-lookup"><span data-stu-id="0b797-139">The *n*th garbage collection.</span></span>|  
|<span data-ttu-id="0b797-140">Derinliği</span><span class="sxs-lookup"><span data-stu-id="0b797-140">Depth</span></span>|<span data-ttu-id="0b797-141">Kazanma: UInt32</span><span class="sxs-lookup"><span data-stu-id="0b797-141">win:UInt32</span></span>|<span data-ttu-id="0b797-142">Toplanmakta olan oluşturma.</span><span class="sxs-lookup"><span data-stu-id="0b797-142">The generation that is being collected.</span></span>|  
|<span data-ttu-id="0b797-143">Neden</span><span class="sxs-lookup"><span data-stu-id="0b797-143">Reason</span></span>|<span data-ttu-id="0b797-144">Kazanma: UInt32</span><span class="sxs-lookup"><span data-stu-id="0b797-144">win:UInt32</span></span>|<span data-ttu-id="0b797-145">Çöp toplama işlemine neden tetiklendi:</span><span class="sxs-lookup"><span data-stu-id="0b797-145">Why the garbage collection was triggered:</span></span><br /><br /> <span data-ttu-id="0b797-146">0x0 - küçük nesne yığını ayırması.</span><span class="sxs-lookup"><span data-stu-id="0b797-146">0x0 - Small object heap allocation.</span></span><br /><br /> <span data-ttu-id="0b797-147">0x1 - başlattı.</span><span class="sxs-lookup"><span data-stu-id="0b797-147">0x1 - Induced.</span></span><br /><br /> <span data-ttu-id="0b797-148">0x2 - bellek yetersiz.</span><span class="sxs-lookup"><span data-stu-id="0b797-148">0x2 - Low memory.</span></span><br /><br /> <span data-ttu-id="0b797-149">0x3 - boş.</span><span class="sxs-lookup"><span data-stu-id="0b797-149">0x3 - Empty.</span></span><br /><br /> <span data-ttu-id="0b797-150">0x4 - büyük nesne yığını ayırması.</span><span class="sxs-lookup"><span data-stu-id="0b797-150">0x4 - Large object heap allocation.</span></span><br /><br /> <span data-ttu-id="0b797-151">0x5 - yetersiz alan (küçük nesne yığını için).</span><span class="sxs-lookup"><span data-stu-id="0b797-151">0x5 - Out of space (for small object heap).</span></span><br /><br /> <span data-ttu-id="0b797-152">0x6 - yetersiz alan (büyük nesne yığını için).</span><span class="sxs-lookup"><span data-stu-id="0b797-152">0x6 - Out of space (for large object heap).</span></span><br /><br /> <span data-ttu-id="0b797-153">0x7 - başlattığı ancak engelleme olarak zorunlu değildir.</span><span class="sxs-lookup"><span data-stu-id="0b797-153">0x7 - Induced but not forced as blocking.</span></span>|  
|<span data-ttu-id="0b797-154">Tür</span><span class="sxs-lookup"><span data-stu-id="0b797-154">Type</span></span>|<span data-ttu-id="0b797-155">Kazanma: UInt32</span><span class="sxs-lookup"><span data-stu-id="0b797-155">win:UInt32</span></span>|<span data-ttu-id="0b797-156">0x0 - arka plan atık toplamanın dışında atık toplamayı engelleme oluştu.</span><span class="sxs-lookup"><span data-stu-id="0b797-156">0x0 - Blocking garbage collection occurred outside background garbage collection.</span></span><br /><br /> <span data-ttu-id="0b797-157">0x1 - arka plan çöp toplama.</span><span class="sxs-lookup"><span data-stu-id="0b797-157">0x1 - Background garbage collection.</span></span><br /><br /> <span data-ttu-id="0b797-158">0x2 - arka plan çöp toplama sırasında atık toplamayı engelleme oluştu.</span><span class="sxs-lookup"><span data-stu-id="0b797-158">0x2 - Blocking garbage collection occurred during background garbage collection.</span></span>|  
|<span data-ttu-id="0b797-159">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="0b797-159">ClrInstanceID</span></span>|<span data-ttu-id="0b797-160">Kazanma: UInt16</span><span class="sxs-lookup"><span data-stu-id="0b797-160">win:UInt16</span></span>|<span data-ttu-id="0b797-161">CLR veya CoreCLR örneği için benzersiz kimlik.</span><span class="sxs-lookup"><span data-stu-id="0b797-161">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="0b797-162">Başa dön</span><span class="sxs-lookup"><span data-stu-id="0b797-162">Back to top</span></span>](#top)  
  
<a name="gcend_v1_event"></a>   
## <a name="gcendv1-event"></a><span data-ttu-id="0b797-163">GCEnd_V1 olay</span><span class="sxs-lookup"><span data-stu-id="0b797-163">GCEnd_V1 Event</span></span>  
 <span data-ttu-id="0b797-164">Aşağıdaki tabloda, düzeyi ve anahtar sözcüğü gösterir.</span><span class="sxs-lookup"><span data-stu-id="0b797-164">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="0b797-165">Olayı için anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="0b797-165">Keyword for raising the event</span></span>|<span data-ttu-id="0b797-166">Düzey</span><span class="sxs-lookup"><span data-stu-id="0b797-166">Level</span></span>|  
|-----------------------------------|-----------|  
|`GCKeyword` <span data-ttu-id="0b797-167">(0x1)</span><span class="sxs-lookup"><span data-stu-id="0b797-167">(0x1)</span></span>|<span data-ttu-id="0b797-168">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="0b797-168">Informational (4)</span></span>|  
  
 <span data-ttu-id="0b797-169">Aşağıdaki tabloda, olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="0b797-169">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="0b797-170">Olay</span><span class="sxs-lookup"><span data-stu-id="0b797-170">Event</span></span>|<span data-ttu-id="0b797-171">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="0b797-171">Event ID</span></span>|<span data-ttu-id="0b797-172">Ne zaman gerçekleşti</span><span class="sxs-lookup"><span data-stu-id="0b797-172">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCEnd_V1`|<span data-ttu-id="0b797-173">2</span><span class="sxs-lookup"><span data-stu-id="0b797-173">2</span></span>|<span data-ttu-id="0b797-174">Çöp toplama sona erdi.</span><span class="sxs-lookup"><span data-stu-id="0b797-174">The garbage collection has ended.</span></span>|  
  
 <span data-ttu-id="0b797-175">Aşağıdaki tabloda, olay verilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="0b797-175">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="0b797-176">Alan adı</span><span class="sxs-lookup"><span data-stu-id="0b797-176">Field name</span></span>|<span data-ttu-id="0b797-177">Veri türü</span><span class="sxs-lookup"><span data-stu-id="0b797-177">Data type</span></span>|<span data-ttu-id="0b797-178">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0b797-178">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="0b797-179">Sayı</span><span class="sxs-lookup"><span data-stu-id="0b797-179">Count</span></span>|<span data-ttu-id="0b797-180">Kazanma: UInt32</span><span class="sxs-lookup"><span data-stu-id="0b797-180">win:UInt32</span></span>|<span data-ttu-id="0b797-181">*n*th çöp toplama.</span><span class="sxs-lookup"><span data-stu-id="0b797-181">The *n*th garbage collection.</span></span>|  
|<span data-ttu-id="0b797-182">Derinliği</span><span class="sxs-lookup"><span data-stu-id="0b797-182">Depth</span></span>|<span data-ttu-id="0b797-183">Kazanma: UInt32</span><span class="sxs-lookup"><span data-stu-id="0b797-183">win:UInt32</span></span>|<span data-ttu-id="0b797-184">Toplanan oluşturma.</span><span class="sxs-lookup"><span data-stu-id="0b797-184">The generation that was collected.</span></span>|  
|<span data-ttu-id="0b797-185">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="0b797-185">ClrInstanceID</span></span>|<span data-ttu-id="0b797-186">Kazanma: UInt16</span><span class="sxs-lookup"><span data-stu-id="0b797-186">win:UInt16</span></span>|<span data-ttu-id="0b797-187">CLR veya CoreCLR örneği için benzersiz kimlik.</span><span class="sxs-lookup"><span data-stu-id="0b797-187">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="0b797-188">Başa dön</span><span class="sxs-lookup"><span data-stu-id="0b797-188">Back to top</span></span>](#top)  
  
<a name="gcheapstats_v1_event"></a>   
## <a name="gcheapstatsv1-event"></a><span data-ttu-id="0b797-189">GCHeapStats_V1 olay</span><span class="sxs-lookup"><span data-stu-id="0b797-189">GCHeapStats_V1 Event</span></span>  
 <span data-ttu-id="0b797-190">Aşağıdaki tabloda, düzeyi ve anahtar sözcüğü gösterir.</span><span class="sxs-lookup"><span data-stu-id="0b797-190">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="0b797-191">Olayı için anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="0b797-191">Keyword for raising the event</span></span>|<span data-ttu-id="0b797-192">Düzey</span><span class="sxs-lookup"><span data-stu-id="0b797-192">Level</span></span>|  
|-----------------------------------|-----------|  
|`GCKeyword` <span data-ttu-id="0b797-193">(0x1)</span><span class="sxs-lookup"><span data-stu-id="0b797-193">(0x1)</span></span>|<span data-ttu-id="0b797-194">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="0b797-194">Informational (4)</span></span>|  
  
 <span data-ttu-id="0b797-195">Aşağıdaki tabloda, olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="0b797-195">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="0b797-196">Olay</span><span class="sxs-lookup"><span data-stu-id="0b797-196">Event</span></span>|<span data-ttu-id="0b797-197">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="0b797-197">Event ID</span></span>|<span data-ttu-id="0b797-198">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0b797-198">Description</span></span>|  
|-----------|--------------|-----------------|  
|`GCHeapStats_V1`|<span data-ttu-id="0b797-199">4</span><span class="sxs-lookup"><span data-stu-id="0b797-199">4</span></span>|<span data-ttu-id="0b797-200">Her çöp toplama sonunda yığında istatistiklerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="0b797-200">Shows the heap statistics at the end of each garbage collection.</span></span>|  
  
 <span data-ttu-id="0b797-201">Aşağıdaki tabloda, olay verilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="0b797-201">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="0b797-202">Alan adı</span><span class="sxs-lookup"><span data-stu-id="0b797-202">Field name</span></span>|<span data-ttu-id="0b797-203">Veri türü</span><span class="sxs-lookup"><span data-stu-id="0b797-203">Data type</span></span>|<span data-ttu-id="0b797-204">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0b797-204">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="0b797-205">GenerationSize0</span><span class="sxs-lookup"><span data-stu-id="0b797-205">GenerationSize0</span></span>|<span data-ttu-id="0b797-206">Kazanma: UInt64</span><span class="sxs-lookup"><span data-stu-id="0b797-206">win:UInt64</span></span>|<span data-ttu-id="0b797-207">Nesil 0 belleğin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="0b797-207">The size, in bytes, of generation 0 memory.</span></span>|  
|<span data-ttu-id="0b797-208">TotalPromotedSize0</span><span class="sxs-lookup"><span data-stu-id="0b797-208">TotalPromotedSize0</span></span>|<span data-ttu-id="0b797-209">Kazanma: UInt64</span><span class="sxs-lookup"><span data-stu-id="0b797-209">win:UInt64</span></span>|<span data-ttu-id="0b797-210">1. nesil için nesil 0 ' yükseltilen bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="0b797-210">The number of bytes that are promoted from generation 0 to generation 1.</span></span>|  
|<span data-ttu-id="0b797-211">GenerationSize1</span><span class="sxs-lookup"><span data-stu-id="0b797-211">GenerationSize1</span></span>|<span data-ttu-id="0b797-212">Kazanma: UInt64</span><span class="sxs-lookup"><span data-stu-id="0b797-212">win:UInt64</span></span>|<span data-ttu-id="0b797-213">1. kuşak belleğin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="0b797-213">The size, in bytes, of generation 1 memory.</span></span>|  
|<span data-ttu-id="0b797-214">TotalPromotedSize1</span><span class="sxs-lookup"><span data-stu-id="0b797-214">TotalPromotedSize1</span></span>|<span data-ttu-id="0b797-215">Kazanma: UInt64</span><span class="sxs-lookup"><span data-stu-id="0b797-215">win:UInt64</span></span>|<span data-ttu-id="0b797-216">Nesil 1 ' 2 yeni nesle yükseltilir bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="0b797-216">The number of bytes that are promoted from generation 1 to generation 2.</span></span>|  
|<span data-ttu-id="0b797-217">GenerationSize2</span><span class="sxs-lookup"><span data-stu-id="0b797-217">GenerationSize2</span></span>|<span data-ttu-id="0b797-218">Kazanma: UInt64</span><span class="sxs-lookup"><span data-stu-id="0b797-218">win:UInt64</span></span>|<span data-ttu-id="0b797-219">2. nesil belleğin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="0b797-219">The size, in bytes, of generation 2 memory.</span></span>|  
|<span data-ttu-id="0b797-220">TotalPromotedSize2</span><span class="sxs-lookup"><span data-stu-id="0b797-220">TotalPromotedSize2</span></span>|<span data-ttu-id="0b797-221">Kazanma: UInt64</span><span class="sxs-lookup"><span data-stu-id="0b797-221">win:UInt64</span></span>|<span data-ttu-id="0b797-222">2. nesil son toplamadan sonra içinde kurtulan bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="0b797-222">The number of bytes that survived in generation 2 after the last collection.</span></span>|  
|<span data-ttu-id="0b797-223">GenerationSize3</span><span class="sxs-lookup"><span data-stu-id="0b797-223">GenerationSize3</span></span>|<span data-ttu-id="0b797-224">Kazanma: UInt64</span><span class="sxs-lookup"><span data-stu-id="0b797-224">win:UInt64</span></span>|<span data-ttu-id="0b797-225">Büyük nesne yığını bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="0b797-225">The size, in bytes, of the large object heap.</span></span>|  
|<span data-ttu-id="0b797-226">TotalPromotedSize3</span><span class="sxs-lookup"><span data-stu-id="0b797-226">TotalPromotedSize3</span></span>|<span data-ttu-id="0b797-227">Kazanma: UInt64</span><span class="sxs-lookup"><span data-stu-id="0b797-227">win:UInt64</span></span>|<span data-ttu-id="0b797-228">Büyük nesne yığınında sonra son toplamadan kurtulan bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="0b797-228">The number of bytes that survived in the large object heap after the last collection.</span></span>|  
|<span data-ttu-id="0b797-229">FinalizationPromotedSize</span><span class="sxs-lookup"><span data-stu-id="0b797-229">FinalizationPromotedSize</span></span>|<span data-ttu-id="0b797-230">Kazanma: UInt64</span><span class="sxs-lookup"><span data-stu-id="0b797-230">win:UInt64</span></span>|<span data-ttu-id="0b797-231">Baytlarında sonlandırma için hazır olan nesneleri toplam boyutu.</span><span class="sxs-lookup"><span data-stu-id="0b797-231">The total size, in bytes, of the objects that are ready for finalization.</span></span>|  
|<span data-ttu-id="0b797-232">FinalizationPromotedCount</span><span class="sxs-lookup"><span data-stu-id="0b797-232">FinalizationPromotedCount</span></span>|<span data-ttu-id="0b797-233">Kazanma: UInt64</span><span class="sxs-lookup"><span data-stu-id="0b797-233">win:UInt64</span></span>|<span data-ttu-id="0b797-234">Sonlandırma için hazır olan nesnelerinin sayısı.</span><span class="sxs-lookup"><span data-stu-id="0b797-234">The number of objects that are ready for finalization.</span></span>|  
|<span data-ttu-id="0b797-235">PinnedObjectCount</span><span class="sxs-lookup"><span data-stu-id="0b797-235">PinnedObjectCount</span></span>|<span data-ttu-id="0b797-236">Kazanma: UInt32</span><span class="sxs-lookup"><span data-stu-id="0b797-236">win:UInt32</span></span>|<span data-ttu-id="0b797-237">Sabitlenen (taşınamayan) nesne sayısı.</span><span class="sxs-lookup"><span data-stu-id="0b797-237">The number of pinned (unmovable) objects.</span></span>|  
|<span data-ttu-id="0b797-238">SinkBlockCount</span><span class="sxs-lookup"><span data-stu-id="0b797-238">SinkBlockCount</span></span>|<span data-ttu-id="0b797-239">Kazanma: UInt32</span><span class="sxs-lookup"><span data-stu-id="0b797-239">win:UInt32</span></span>|<span data-ttu-id="0b797-240">Kullanımdaki eşitleme blokların sayısı.</span><span class="sxs-lookup"><span data-stu-id="0b797-240">The number of synchronization blocks in use.</span></span>|  
|<span data-ttu-id="0b797-241">GCHandleCount</span><span class="sxs-lookup"><span data-stu-id="0b797-241">GCHandleCount</span></span>|<span data-ttu-id="0b797-242">Kazanma: UInt32</span><span class="sxs-lookup"><span data-stu-id="0b797-242">win:UInt32</span></span>|<span data-ttu-id="0b797-243">Kullanımda olan çöp toplama sayısı.</span><span class="sxs-lookup"><span data-stu-id="0b797-243">The number of garbage collection handles in use.</span></span>|  
|<span data-ttu-id="0b797-244">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="0b797-244">ClrInstanceID</span></span>|<span data-ttu-id="0b797-245">Kazanma: UInt16</span><span class="sxs-lookup"><span data-stu-id="0b797-245">win:UInt16</span></span>|<span data-ttu-id="0b797-246">CLR veya CoreCLR örneği için benzersiz kimlik.</span><span class="sxs-lookup"><span data-stu-id="0b797-246">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="0b797-247">Başa dön</span><span class="sxs-lookup"><span data-stu-id="0b797-247">Back to top</span></span>](#top)  
  
<a name="gccreatesegment_v1_event"></a>   
## <a name="gccreatesegmentv1-event"></a><span data-ttu-id="0b797-248">GCCreateSegment_V1 Event</span><span class="sxs-lookup"><span data-stu-id="0b797-248">GCCreateSegment_V1 Event</span></span>  
 <span data-ttu-id="0b797-249">Aşağıdaki tabloda, düzeyi ve anahtar sözcüğü gösterir.</span><span class="sxs-lookup"><span data-stu-id="0b797-249">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="0b797-250">Olayı için anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="0b797-250">Keyword for raising the event</span></span>|<span data-ttu-id="0b797-251">Düzey</span><span class="sxs-lookup"><span data-stu-id="0b797-251">Level</span></span>|  
|-----------------------------------|-----------|  
|`GCKeyword` <span data-ttu-id="0b797-252">(0x1)</span><span class="sxs-lookup"><span data-stu-id="0b797-252">(0x1)</span></span>|<span data-ttu-id="0b797-253">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="0b797-253">Informational (4)</span></span>|  
  
 <span data-ttu-id="0b797-254">Aşağıdaki tabloda, olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="0b797-254">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="0b797-255">Olay</span><span class="sxs-lookup"><span data-stu-id="0b797-255">Event</span></span>|<span data-ttu-id="0b797-256">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="0b797-256">Event ID</span></span>|<span data-ttu-id="0b797-257">Ne zaman gerçekleşti</span><span class="sxs-lookup"><span data-stu-id="0b797-257">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCCreateSegment_V1`|<span data-ttu-id="0b797-258">5</span><span class="sxs-lookup"><span data-stu-id="0b797-258">5</span></span>|<span data-ttu-id="0b797-259">Yeni bir çöp toplama segment oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="0b797-259">A new garbage collection segment has been created.</span></span> <span data-ttu-id="0b797-260">Ayrıca, zaten çalışan bir işlemde izleme etkin olduğunda, var olan her segment için bu olay oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="0b797-260">In addition, when tracing is enabled on a process that is already running, this event is raised for each existing segment.</span></span>|  
  
 <span data-ttu-id="0b797-261">Aşağıdaki tabloda, olay verilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="0b797-261">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="0b797-262">Alan adı</span><span class="sxs-lookup"><span data-stu-id="0b797-262">Field name</span></span>|<span data-ttu-id="0b797-263">Veri türü</span><span class="sxs-lookup"><span data-stu-id="0b797-263">Data type</span></span>|<span data-ttu-id="0b797-264">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0b797-264">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="0b797-265">Adres</span><span class="sxs-lookup"><span data-stu-id="0b797-265">Address</span></span>|<span data-ttu-id="0b797-266">Kazanma: UInt64</span><span class="sxs-lookup"><span data-stu-id="0b797-266">win:UInt64</span></span>|<span data-ttu-id="0b797-267">Segment adresi.</span><span class="sxs-lookup"><span data-stu-id="0b797-267">The address of the segment.</span></span>|  
|<span data-ttu-id="0b797-268">Boyut</span><span class="sxs-lookup"><span data-stu-id="0b797-268">Size</span></span>|<span data-ttu-id="0b797-269">Kazanma: UInt64</span><span class="sxs-lookup"><span data-stu-id="0b797-269">win:UInt64</span></span>|<span data-ttu-id="0b797-270">Kesim boyutu.</span><span class="sxs-lookup"><span data-stu-id="0b797-270">The size of the segment.</span></span>|  
|<span data-ttu-id="0b797-271">Tür</span><span class="sxs-lookup"><span data-stu-id="0b797-271">Type</span></span>|<span data-ttu-id="0b797-272">Kazanma: UInt32</span><span class="sxs-lookup"><span data-stu-id="0b797-272">win:UInt32</span></span>|<span data-ttu-id="0b797-273">0x0 - küçük nesne yığını.</span><span class="sxs-lookup"><span data-stu-id="0b797-273">0x0 - Small object heap.</span></span><br /><br /> <span data-ttu-id="0b797-274">0x1 - büyük nesne yığını.</span><span class="sxs-lookup"><span data-stu-id="0b797-274">0x1 - Large object heap.</span></span><br /><br /> <span data-ttu-id="0b797-275">0x2 - yığın salt okunur.</span><span class="sxs-lookup"><span data-stu-id="0b797-275">0x2 - Read-only heap.</span></span>|  
|<span data-ttu-id="0b797-276">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="0b797-276">ClrInstanceID</span></span>|<span data-ttu-id="0b797-277">Kazanma: UInt16</span><span class="sxs-lookup"><span data-stu-id="0b797-277">win:UInt16</span></span>|<span data-ttu-id="0b797-278">CLR veya CoreCLR örneği için benzersiz kimlik.</span><span class="sxs-lookup"><span data-stu-id="0b797-278">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 <span data-ttu-id="0b797-279">Boyutu çöp toplayıcısının ayrılan parçaları uygulama özgü olan ve düzenli güncelleştirmeleri dahil olmak üzere dilediğiniz zaman değiştirilebilir unutmayın.</span><span class="sxs-lookup"><span data-stu-id="0b797-279">Note that the size of segments allocated by the garbage collector is implementation-specific and is subject to change at any time, including in periodic updates.</span></span> <span data-ttu-id="0b797-280">Uygulamanız hiçbir zaman hakkında varsayımlar veya belirli bir segment boyutuna göre değişir ve segment ayırma için kullanılabilir bellek miktarını yapılandırmak için denemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="0b797-280">Your app should never make assumptions about or depend on a particular segment size, nor should it attempt to configure the amount of memory available for segment allocations.</span></span>  
  
 [<span data-ttu-id="0b797-281">Başa dön</span><span class="sxs-lookup"><span data-stu-id="0b797-281">Back to top</span></span>](#top)  
  
<a name="gcfreesegment_v1_event"></a>   
## <a name="gcfreesegmentv1-event"></a><span data-ttu-id="0b797-282">GCFreeSegment_V1 Event</span><span class="sxs-lookup"><span data-stu-id="0b797-282">GCFreeSegment_V1 Event</span></span>  
 <span data-ttu-id="0b797-283">Aşağıdaki tabloda, düzeyi ve anahtar sözcüğü gösterir.</span><span class="sxs-lookup"><span data-stu-id="0b797-283">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="0b797-284">Olayı için anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="0b797-284">Keyword for raising the event</span></span>|<span data-ttu-id="0b797-285">Düzey</span><span class="sxs-lookup"><span data-stu-id="0b797-285">Level</span></span>|  
|-----------------------------------|-----------|  
|`GCKeyword` <span data-ttu-id="0b797-286">(0x1)</span><span class="sxs-lookup"><span data-stu-id="0b797-286">(0x1)</span></span>|<span data-ttu-id="0b797-287">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="0b797-287">Informational (4)</span></span>|  
  
 <span data-ttu-id="0b797-288">Aşağıdaki tabloda, olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="0b797-288">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="0b797-289">Olay</span><span class="sxs-lookup"><span data-stu-id="0b797-289">Event</span></span>|<span data-ttu-id="0b797-290">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="0b797-290">Event ID</span></span>|<span data-ttu-id="0b797-291">Ne zaman gerçekleşti</span><span class="sxs-lookup"><span data-stu-id="0b797-291">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCFreeSegment_V1`|<span data-ttu-id="0b797-292">6</span><span class="sxs-lookup"><span data-stu-id="0b797-292">6</span></span>|<span data-ttu-id="0b797-293">Bir çöp toplama segment piyasaya Sürüldü.</span><span class="sxs-lookup"><span data-stu-id="0b797-293">A garbage collection segment has been released.</span></span>|  
  
 <span data-ttu-id="0b797-294">Aşağıdaki tabloda, olay verilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="0b797-294">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="0b797-295">Alan adı</span><span class="sxs-lookup"><span data-stu-id="0b797-295">Field name</span></span>|<span data-ttu-id="0b797-296">Veri türü</span><span class="sxs-lookup"><span data-stu-id="0b797-296">Data type</span></span>|<span data-ttu-id="0b797-297">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0b797-297">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="0b797-298">Adres</span><span class="sxs-lookup"><span data-stu-id="0b797-298">Address</span></span>|<span data-ttu-id="0b797-299">Kazanma: UInt64</span><span class="sxs-lookup"><span data-stu-id="0b797-299">win:UInt64</span></span>|<span data-ttu-id="0b797-300">Segment adresi.</span><span class="sxs-lookup"><span data-stu-id="0b797-300">The address of the segment.</span></span>|  
|<span data-ttu-id="0b797-301">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="0b797-301">ClrInstanceID</span></span>|<span data-ttu-id="0b797-302">Kazanma: UInt16</span><span class="sxs-lookup"><span data-stu-id="0b797-302">win:UInt16</span></span>|<span data-ttu-id="0b797-303">CLR veya CoreCLR örneği için benzersiz kimlik.</span><span class="sxs-lookup"><span data-stu-id="0b797-303">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="0b797-304">Başa dön</span><span class="sxs-lookup"><span data-stu-id="0b797-304">Back to top</span></span>](#top)  
  
<a name="gcrestarteebegin_v1_event"></a>   
## <a name="gcrestarteebeginv1-event"></a><span data-ttu-id="0b797-305">GCRestartEEBegin_V1 olay</span><span class="sxs-lookup"><span data-stu-id="0b797-305">GCRestartEEBegin_V1 Event</span></span>  
 <span data-ttu-id="0b797-306">Aşağıdaki tabloda, düzeyi ve anahtar sözcüğü gösterir.</span><span class="sxs-lookup"><span data-stu-id="0b797-306">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="0b797-307">Olayı için anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="0b797-307">Keyword for raising the event</span></span>|<span data-ttu-id="0b797-308">Düzey</span><span class="sxs-lookup"><span data-stu-id="0b797-308">Level</span></span>|  
|-----------------------------------|-----------|  
|`GCKeyword` <span data-ttu-id="0b797-309">(0x1)</span><span class="sxs-lookup"><span data-stu-id="0b797-309">(0x1)</span></span>|<span data-ttu-id="0b797-310">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="0b797-310">Informational (4)</span></span>|  
  
 <span data-ttu-id="0b797-311">Aşağıdaki tabloda, olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="0b797-311">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="0b797-312">Olay</span><span class="sxs-lookup"><span data-stu-id="0b797-312">Event</span></span>|<span data-ttu-id="0b797-313">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="0b797-313">Event ID</span></span>|<span data-ttu-id="0b797-314">Ne zaman gerçekleşti</span><span class="sxs-lookup"><span data-stu-id="0b797-314">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCRestartEEBegin_V1`|<span data-ttu-id="0b797-315">7</span><span class="sxs-lookup"><span data-stu-id="0b797-315">7</span></span>|<span data-ttu-id="0b797-316">Ortak dil çalışma zamanı askıya alma gelen sürdürme başladı.</span><span class="sxs-lookup"><span data-stu-id="0b797-316">Resumption from common language runtime suspension has begun.</span></span>|  
  
 <span data-ttu-id="0b797-317">Hiçbir olay verileri.</span><span class="sxs-lookup"><span data-stu-id="0b797-317">No event data.</span></span>  
  
 [<span data-ttu-id="0b797-318">Başa dön</span><span class="sxs-lookup"><span data-stu-id="0b797-318">Back to top</span></span>](#top)  
  
<a name="gcrestarteeend_v1_event"></a>   
## <a name="gcrestarteeendv1-event"></a><span data-ttu-id="0b797-319">GCRestartEEEnd_V1 olay</span><span class="sxs-lookup"><span data-stu-id="0b797-319">GCRestartEEEnd_V1 Event</span></span>  
 <span data-ttu-id="0b797-320">Aşağıdaki tabloda, düzeyi ve anahtar sözcüğü gösterir.</span><span class="sxs-lookup"><span data-stu-id="0b797-320">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="0b797-321">Olayı için anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="0b797-321">Keyword for raising the event</span></span>|<span data-ttu-id="0b797-322">Düzey</span><span class="sxs-lookup"><span data-stu-id="0b797-322">Level</span></span>|  
|-----------------------------------|-----------|  
|`GCKeyword` <span data-ttu-id="0b797-323">(0x1)</span><span class="sxs-lookup"><span data-stu-id="0b797-323">(0x1)</span></span>|<span data-ttu-id="0b797-324">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="0b797-324">Informational (4)</span></span>|  
  
 <span data-ttu-id="0b797-325">Aşağıdaki tabloda, olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="0b797-325">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="0b797-326">Olay</span><span class="sxs-lookup"><span data-stu-id="0b797-326">Event</span></span>|<span data-ttu-id="0b797-327">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="0b797-327">Event Id</span></span>|<span data-ttu-id="0b797-328">Ne zaman gerçekleşti</span><span class="sxs-lookup"><span data-stu-id="0b797-328">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCRestartEEEnd_V1`|<span data-ttu-id="0b797-329">3</span><span class="sxs-lookup"><span data-stu-id="0b797-329">3</span></span>|<span data-ttu-id="0b797-330">Ortak dil çalışma zamanı askıya alma gelen sürdürme sona erdi.</span><span class="sxs-lookup"><span data-stu-id="0b797-330">Resumption from common language runtime suspension has ended.</span></span>|  
  
 <span data-ttu-id="0b797-331">Hiçbir olay verileri.</span><span class="sxs-lookup"><span data-stu-id="0b797-331">No event data.</span></span>  
  
 [<span data-ttu-id="0b797-332">Başa dön</span><span class="sxs-lookup"><span data-stu-id="0b797-332">Back to top</span></span>](#top)  
  
<a name="gcsuspendee_v1_event"></a>   
## <a name="gcsuspendeev1-event"></a><span data-ttu-id="0b797-333">GCSuspendEE_V1 Event</span><span class="sxs-lookup"><span data-stu-id="0b797-333">GCSuspendEE_V1 Event</span></span>  
 <span data-ttu-id="0b797-334">Aşağıdaki tabloda, düzeyi ve anahtar sözcüğü gösterir.</span><span class="sxs-lookup"><span data-stu-id="0b797-334">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="0b797-335">Olayı için anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="0b797-335">Keyword for raising the event</span></span>|<span data-ttu-id="0b797-336">Düzey</span><span class="sxs-lookup"><span data-stu-id="0b797-336">Level</span></span>|  
|-----------------------------------|-----------|  
|`GCKeyword` <span data-ttu-id="0b797-337">(0x1)</span><span class="sxs-lookup"><span data-stu-id="0b797-337">(0x1)</span></span>|<span data-ttu-id="0b797-338">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="0b797-338">Informational (4)</span></span>|  
  
 <span data-ttu-id="0b797-339">Aşağıdaki tabloda, olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="0b797-339">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="0b797-340">Olay</span><span class="sxs-lookup"><span data-stu-id="0b797-340">Event</span></span>|<span data-ttu-id="0b797-341">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="0b797-341">Event ID</span></span>|<span data-ttu-id="0b797-342">Ne zaman gerçekleşti</span><span class="sxs-lookup"><span data-stu-id="0b797-342">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCSuspendEE_V1`|<span data-ttu-id="0b797-343">9</span><span class="sxs-lookup"><span data-stu-id="0b797-343">9</span></span>|<span data-ttu-id="0b797-344">Çöp toplama işlemi için yürütme altyapısının askıya alma başlangıcı.</span><span class="sxs-lookup"><span data-stu-id="0b797-344">Start of suspension of the execution engine for garbage collection.</span></span>|  
  
 <span data-ttu-id="0b797-345">Aşağıdaki tabloda, olay verilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="0b797-345">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="0b797-346">Alan adı</span><span class="sxs-lookup"><span data-stu-id="0b797-346">Field name</span></span>|<span data-ttu-id="0b797-347">Veri türü</span><span class="sxs-lookup"><span data-stu-id="0b797-347">Data type</span></span>|<span data-ttu-id="0b797-348">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0b797-348">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="0b797-349">Neden</span><span class="sxs-lookup"><span data-stu-id="0b797-349">Reason</span></span>|<span data-ttu-id="0b797-350">Kazanma: UInt16</span><span class="sxs-lookup"><span data-stu-id="0b797-350">win:UInt16</span></span>|<span data-ttu-id="0b797-351">0x0 - diğer.</span><span class="sxs-lookup"><span data-stu-id="0b797-351">0x0 - Other.</span></span><br /><br /> <span data-ttu-id="0b797-352">0x1 - çöp toplama.</span><span class="sxs-lookup"><span data-stu-id="0b797-352">0x1 - Garbage collection.</span></span><br /><br /> <span data-ttu-id="0b797-353">0x2 - uygulama etki alanı kapatma.</span><span class="sxs-lookup"><span data-stu-id="0b797-353">0x2 - Application domain shutdown.</span></span><br /><br /> <span data-ttu-id="0b797-354">0x3 - kod pitching.</span><span class="sxs-lookup"><span data-stu-id="0b797-354">0x3 - Code pitching.</span></span><br /><br /> <span data-ttu-id="0b797-355">0x4 - kapatma.</span><span class="sxs-lookup"><span data-stu-id="0b797-355">0x4 - Shutdown.</span></span><br /><br /> <span data-ttu-id="0b797-356">0x5 - Hata Ayıklayıcısı'nı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="0b797-356">0x5 - Debugger.</span></span><br /><br /> <span data-ttu-id="0b797-357">0x6 - çöp toplama için hazırlama.</span><span class="sxs-lookup"><span data-stu-id="0b797-357">0x6 - Preparation for garbage collection.</span></span>|  
|<span data-ttu-id="0b797-358">Sayı</span><span class="sxs-lookup"><span data-stu-id="0b797-358">Count</span></span>|<span data-ttu-id="0b797-359">Kazanma: UInt32</span><span class="sxs-lookup"><span data-stu-id="0b797-359">win:UInt32</span></span>|<span data-ttu-id="0b797-360">GC sayısı zaman.</span><span class="sxs-lookup"><span data-stu-id="0b797-360">The GC count at the time.</span></span> <span data-ttu-id="0b797-361">Genellikle, bundan sonra bir sonraki GC başlangıç olayı görür ve biz GC dizini çöp toplama sırasında arttıkça sayımına bu sayı + 1 olur.</span><span class="sxs-lookup"><span data-stu-id="0b797-361">Usually, you would see a subsequent GC Start event after this, and its Count would be this Count + 1 as we increase the GC index during a garbage collection.</span></span>|  
|<span data-ttu-id="0b797-362">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="0b797-362">ClrInstanceID</span></span>|<span data-ttu-id="0b797-363">Kazanma: UInt16</span><span class="sxs-lookup"><span data-stu-id="0b797-363">win:UInt16</span></span>|<span data-ttu-id="0b797-364">CLR veya CoreCLR örneği için benzersiz kimlik.</span><span class="sxs-lookup"><span data-stu-id="0b797-364">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="0b797-365">Başa dön</span><span class="sxs-lookup"><span data-stu-id="0b797-365">Back to top</span></span>](#top)  
  
<a name="gcsuspendeeend_v1_event"></a>   
## <a name="gcsuspendeeendv1-event"></a><span data-ttu-id="0b797-366">GCSuspendEEEnd_V1 Event</span><span class="sxs-lookup"><span data-stu-id="0b797-366">GCSuspendEEEnd_V1 Event</span></span>  
 <span data-ttu-id="0b797-367">Aşağıdaki tablo düzeyi ve anahtar sözcüğü gösterir:</span><span class="sxs-lookup"><span data-stu-id="0b797-367">The following table shows the keyword and level:</span></span>  
  
|<span data-ttu-id="0b797-368">Olayı için anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="0b797-368">Keyword for raising the event</span></span>|<span data-ttu-id="0b797-369">Düzey</span><span class="sxs-lookup"><span data-stu-id="0b797-369">Level</span></span>|  
|-----------------------------------|-----------|  
|`GCKeyword` <span data-ttu-id="0b797-370">(0x1)</span><span class="sxs-lookup"><span data-stu-id="0b797-370">(0x1)</span></span>|<span data-ttu-id="0b797-371">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="0b797-371">Informational (4)</span></span>|  
  
 <span data-ttu-id="0b797-372">Aşağıdaki tablo, olay bilgileri gösterir:</span><span class="sxs-lookup"><span data-stu-id="0b797-372">The following table shows the event information:</span></span>  
  
|<span data-ttu-id="0b797-373">Olay</span><span class="sxs-lookup"><span data-stu-id="0b797-373">Event</span></span>|<span data-ttu-id="0b797-374">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="0b797-374">Event ID</span></span>|<span data-ttu-id="0b797-375">Ne zaman gerçekleşti</span><span class="sxs-lookup"><span data-stu-id="0b797-375">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCSuspendEEEnd_V1`|<span data-ttu-id="0b797-376">8</span><span class="sxs-lookup"><span data-stu-id="0b797-376">8</span></span>|<span data-ttu-id="0b797-377">Çöp toplama işlemi için yürütme altyapısının askıya alma sonu.</span><span class="sxs-lookup"><span data-stu-id="0b797-377">End of suspension of the execution engine for garbage collection.</span></span>|  
  
 <span data-ttu-id="0b797-378">Hiçbir olay verileri.</span><span class="sxs-lookup"><span data-stu-id="0b797-378">No event data.</span></span>  
  
 [<span data-ttu-id="0b797-379">Başa dön</span><span class="sxs-lookup"><span data-stu-id="0b797-379">Back to top</span></span>](#top)  
  
<a name="gcallocationtick_v2_event"></a>   
## <a name="gcallocationtickv2-event"></a><span data-ttu-id="0b797-380">GCAllocationTick_V2 olay</span><span class="sxs-lookup"><span data-stu-id="0b797-380">GCAllocationTick_V2 Event</span></span>  
 <span data-ttu-id="0b797-381">Aşağıdaki tabloda, düzeyi ve anahtar sözcüğü gösterir.</span><span class="sxs-lookup"><span data-stu-id="0b797-381">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="0b797-382">Olayı için anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="0b797-382">Keyword for raising the event</span></span>|<span data-ttu-id="0b797-383">Düzey</span><span class="sxs-lookup"><span data-stu-id="0b797-383">Level</span></span>|  
|-----------------------------------|-----------|  
|`GCKeyword` <span data-ttu-id="0b797-384">(0x1)</span><span class="sxs-lookup"><span data-stu-id="0b797-384">(0x1)</span></span>|<span data-ttu-id="0b797-385">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="0b797-385">Informational (4)</span></span>|  
  
 <span data-ttu-id="0b797-386">Aşağıdaki tabloda, olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="0b797-386">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="0b797-387">Olay</span><span class="sxs-lookup"><span data-stu-id="0b797-387">Event</span></span>|<span data-ttu-id="0b797-388">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="0b797-388">Event ID</span></span>|<span data-ttu-id="0b797-389">Ne zaman gerçekleşti</span><span class="sxs-lookup"><span data-stu-id="0b797-389">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCAllocationTick_V2`|<span data-ttu-id="0b797-390">10</span><span class="sxs-lookup"><span data-stu-id="0b797-390">10</span></span>|<span data-ttu-id="0b797-391">Her seferinde yaklaşık 100 KB ayrılır.</span><span class="sxs-lookup"><span data-stu-id="0b797-391">Each time approximately 100 KB is allocated.</span></span>|  
  
 <span data-ttu-id="0b797-392">Aşağıdaki tabloda, olay verilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="0b797-392">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="0b797-393">Alan adı</span><span class="sxs-lookup"><span data-stu-id="0b797-393">Field name</span></span>|<span data-ttu-id="0b797-394">Veri türü</span><span class="sxs-lookup"><span data-stu-id="0b797-394">Data type</span></span>|<span data-ttu-id="0b797-395">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0b797-395">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="0b797-396">AllocationAmount</span><span class="sxs-lookup"><span data-stu-id="0b797-396">AllocationAmount</span></span>|<span data-ttu-id="0b797-397">Kazanma: UInt32</span><span class="sxs-lookup"><span data-stu-id="0b797-397">win:UInt32</span></span>|<span data-ttu-id="0b797-398">Ayırma bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="0b797-398">The allocation size, in bytes.</span></span> <span data-ttu-id="0b797-399">Bu değer, küçük bir ULONG (4,294,967,295 bayt), uzunluğundan ayırmalar için doğru olur.</span><span class="sxs-lookup"><span data-stu-id="0b797-399">This value is accurate for allocations that are less than the length of a ULONG (4,294,967,295 bytes).</span></span> <span data-ttu-id="0b797-400">Ayırma büyükse, bu alan kesilmiş değer içerir.</span><span class="sxs-lookup"><span data-stu-id="0b797-400">If the allocation is greater, this field contains a truncated value.</span></span> <span data-ttu-id="0b797-401">Kullanım `AllocationAmount64` çok büyük ayırmalar için.</span><span class="sxs-lookup"><span data-stu-id="0b797-401">Use `AllocationAmount64` for very large allocations.</span></span>|  
|<span data-ttu-id="0b797-402">AllocationKind</span><span class="sxs-lookup"><span data-stu-id="0b797-402">AllocationKind</span></span>|<span data-ttu-id="0b797-403">Kazanma: UInt32</span><span class="sxs-lookup"><span data-stu-id="0b797-403">win:UInt32</span></span>|<span data-ttu-id="0b797-404">0x0 - küçük nesne ayırma (içinde küçük nesne yığını ayırma'dir).</span><span class="sxs-lookup"><span data-stu-id="0b797-404">0x0 - Small object allocation (allocation is in small object heap).</span></span><br /><br /> <span data-ttu-id="0b797-405">0x1 - büyük nesne ayırma (büyük nesne yığınında ayırma'dir).</span><span class="sxs-lookup"><span data-stu-id="0b797-405">0x1 - Large object allocation (allocation is in large object heap).</span></span>|  
|<span data-ttu-id="0b797-406">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="0b797-406">ClrInstanceID</span></span>|<span data-ttu-id="0b797-407">Kazanma: UInt16</span><span class="sxs-lookup"><span data-stu-id="0b797-407">win:UInt16</span></span>|<span data-ttu-id="0b797-408">CLR veya CoreCLR örneği için benzersiz kimlik.</span><span class="sxs-lookup"><span data-stu-id="0b797-408">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
|<span data-ttu-id="0b797-409">AllocationAmount64</span><span class="sxs-lookup"><span data-stu-id="0b797-409">AllocationAmount64</span></span>|<span data-ttu-id="0b797-410">Kazanma: UInt64</span><span class="sxs-lookup"><span data-stu-id="0b797-410">win:UInt64</span></span>|<span data-ttu-id="0b797-411">Ayırma bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="0b797-411">The allocation size, in bytes.</span></span> <span data-ttu-id="0b797-412">Bu değer çok büyük ayırmalarını doğru olur.</span><span class="sxs-lookup"><span data-stu-id="0b797-412">This value is accurate for very large allocations.</span></span>|  
|<span data-ttu-id="0b797-413">typeId</span><span class="sxs-lookup"><span data-stu-id="0b797-413">TypeId</span></span>|<span data-ttu-id="0b797-414">Kazanma: işaretçi</span><span class="sxs-lookup"><span data-stu-id="0b797-414">win:Pointer</span></span>|<span data-ttu-id="0b797-415">MethodTable adresi.</span><span class="sxs-lookup"><span data-stu-id="0b797-415">The address of the MethodTable.</span></span> <span data-ttu-id="0b797-416">Bu olayı sırasında ayrılan nesnelerin birkaç türü olduğunda, bu son (100 KB eşiği olması nedeniyle nesne) ayrılmış nesne karşılık gelen MethodTable adresidir.</span><span class="sxs-lookup"><span data-stu-id="0b797-416">When there are several types of objects that were allocated during this event, this is the address of the MethodTable that corresponds to the last object allocated (the object that caused the 100 KB threshold to be exceeded).</span></span>|  
|<span data-ttu-id="0b797-417">TypeName</span><span class="sxs-lookup"><span data-stu-id="0b797-417">TypeName</span></span>|<span data-ttu-id="0b797-418">Kazanma: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="0b797-418">win:UnicodeString</span></span>|<span data-ttu-id="0b797-419">Ayrılmış olan tür adı.</span><span class="sxs-lookup"><span data-stu-id="0b797-419">The name of the type that was allocated.</span></span> <span data-ttu-id="0b797-420">Bu olayı sırasında ayrılan nesnelerin birkaç türü olduğunda, (100 KB eşiği olması nedeniyle nesne) ayrılan son nesnenin türü budur.</span><span class="sxs-lookup"><span data-stu-id="0b797-420">When there are several types of objects that were allocated during this event, this is the type of the last object allocated (the object that caused the 100 KB threshold to be exceeded).</span></span>|  
|<span data-ttu-id="0b797-421">HeapIndex</span><span class="sxs-lookup"><span data-stu-id="0b797-421">HeapIndex</span></span>|<span data-ttu-id="0b797-422">Kazanma: UInt32</span><span class="sxs-lookup"><span data-stu-id="0b797-422">win:UInt32</span></span>|<span data-ttu-id="0b797-423">Nesne ayrıldığı yığında.</span><span class="sxs-lookup"><span data-stu-id="0b797-423">The heap where the object was allocated.</span></span> <span data-ttu-id="0b797-424">İş istasyonu çöp toplama ile çalışırken, bu değer 0 (sıfır) olur.</span><span class="sxs-lookup"><span data-stu-id="0b797-424">This value is 0 (zero) when running with workstation garbage collection.</span></span>|  
  
 [<span data-ttu-id="0b797-425">Başa dön</span><span class="sxs-lookup"><span data-stu-id="0b797-425">Back to top</span></span>](#top)  
  
<a name="gcfinalizersbegin_v1_event"></a>   
## <a name="gcfinalizersbeginv1-event"></a><span data-ttu-id="0b797-426">GCFinalizersBegin_V1 olay</span><span class="sxs-lookup"><span data-stu-id="0b797-426">GCFinalizersBegin_V1 Event</span></span>  
 <span data-ttu-id="0b797-427">Aşağıdaki tabloda, düzeyi ve anahtar sözcüğü gösterir.</span><span class="sxs-lookup"><span data-stu-id="0b797-427">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="0b797-428">Olayı için anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="0b797-428">Keyword for raising the event</span></span>|<span data-ttu-id="0b797-429">Düzey</span><span class="sxs-lookup"><span data-stu-id="0b797-429">Level</span></span>|  
|-----------------------------------|-----------|  
|`GCKeyword` <span data-ttu-id="0b797-430">(0x1)</span><span class="sxs-lookup"><span data-stu-id="0b797-430">(0x1)</span></span>|<span data-ttu-id="0b797-431">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="0b797-431">Informational (4)</span></span>|  
  
 <span data-ttu-id="0b797-432">Aşağıdaki tabloda, olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="0b797-432">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="0b797-433">Olay</span><span class="sxs-lookup"><span data-stu-id="0b797-433">Event</span></span>|<span data-ttu-id="0b797-434">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="0b797-434">Event ID</span></span>|<span data-ttu-id="0b797-435">Ne zaman gerçekleşti</span><span class="sxs-lookup"><span data-stu-id="0b797-435">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCFinalizersBegin_V1`|<span data-ttu-id="0b797-436">14</span><span class="sxs-lookup"><span data-stu-id="0b797-436">14</span></span>|<span data-ttu-id="0b797-437">Sonlandırıcılar çalıştırma başlangıcı.</span><span class="sxs-lookup"><span data-stu-id="0b797-437">The start of running finalizers.</span></span>|  
  
 <span data-ttu-id="0b797-438">Hiçbir olay verileri.</span><span class="sxs-lookup"><span data-stu-id="0b797-438">No event data.</span></span>  
  
 [<span data-ttu-id="0b797-439">Başa dön</span><span class="sxs-lookup"><span data-stu-id="0b797-439">Back to top</span></span>](#top)  
  
<a name="gcfinalizersend_v1_event"></a>   
## <a name="gcfinalizersendv1-event"></a><span data-ttu-id="0b797-440">GCFinalizersEnd_V1 olay</span><span class="sxs-lookup"><span data-stu-id="0b797-440">GCFinalizersEnd_V1 Event</span></span>  
 <span data-ttu-id="0b797-441">Aşağıdaki tabloda, düzeyi ve anahtar sözcüğü gösterir.</span><span class="sxs-lookup"><span data-stu-id="0b797-441">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="0b797-442">Olayı için anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="0b797-442">Keyword for raising the event</span></span>|<span data-ttu-id="0b797-443">Düzey</span><span class="sxs-lookup"><span data-stu-id="0b797-443">Level</span></span>|  
|-----------------------------------|-----------|  
|`GCKeyword` <span data-ttu-id="0b797-444">(0x1)</span><span class="sxs-lookup"><span data-stu-id="0b797-444">(0x1)</span></span>|<span data-ttu-id="0b797-445">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="0b797-445">Informational (4)</span></span>|  
  
 <span data-ttu-id="0b797-446">Aşağıdaki tabloda, olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="0b797-446">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="0b797-447">Olay</span><span class="sxs-lookup"><span data-stu-id="0b797-447">Event</span></span>|<span data-ttu-id="0b797-448">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="0b797-448">Event ID</span></span>|<span data-ttu-id="0b797-449">Ne zaman gerçekleşti</span><span class="sxs-lookup"><span data-stu-id="0b797-449">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCFinalizersEnd_V1`|<span data-ttu-id="0b797-450">13</span><span class="sxs-lookup"><span data-stu-id="0b797-450">13</span></span>|<span data-ttu-id="0b797-451">Sonlandırıcılar çalıştırma bitiş olayı.</span><span class="sxs-lookup"><span data-stu-id="0b797-451">The end of running finalizers.</span></span>|  
  
 <span data-ttu-id="0b797-452">Aşağıdaki tabloda, olay verilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="0b797-452">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="0b797-453">Alan adı</span><span class="sxs-lookup"><span data-stu-id="0b797-453">Field name</span></span>|<span data-ttu-id="0b797-454">Veri türü</span><span class="sxs-lookup"><span data-stu-id="0b797-454">Data type</span></span>|<span data-ttu-id="0b797-455">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0b797-455">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="0b797-456">Sayı</span><span class="sxs-lookup"><span data-stu-id="0b797-456">Count</span></span>|<span data-ttu-id="0b797-457">Kazanma: UInt32</span><span class="sxs-lookup"><span data-stu-id="0b797-457">win:UInt32</span></span>|<span data-ttu-id="0b797-458">Çalıştırılan bir sonlandırıcı sayısı.</span><span class="sxs-lookup"><span data-stu-id="0b797-458">The number of finalizers that were run.</span></span>|  
|<span data-ttu-id="0b797-459">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="0b797-459">ClrInstanceID</span></span>|<span data-ttu-id="0b797-460">Kazanma: UInt16</span><span class="sxs-lookup"><span data-stu-id="0b797-460">win:UInt16</span></span>|<span data-ttu-id="0b797-461">CLR veya CoreCLR örneği için benzersiz kimlik.</span><span class="sxs-lookup"><span data-stu-id="0b797-461">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="0b797-462">Başa dön</span><span class="sxs-lookup"><span data-stu-id="0b797-462">Back to top</span></span>](#top)  
  
<a name="gccreateconcurrentthread_v1_event"></a>   
## <a name="gccreateconcurrentthreadv1-event"></a><span data-ttu-id="0b797-463">GCCreateConcurrentThread_V1 olay</span><span class="sxs-lookup"><span data-stu-id="0b797-463">GCCreateConcurrentThread_V1 Event</span></span>  
 <span data-ttu-id="0b797-464">Aşağıdaki tabloda, düzeyi ve anahtar sözcüğü gösterir.</span><span class="sxs-lookup"><span data-stu-id="0b797-464">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="0b797-465">Olayı için anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="0b797-465">Keyword for raising the event</span></span>|<span data-ttu-id="0b797-466">Düzey</span><span class="sxs-lookup"><span data-stu-id="0b797-466">Level</span></span>|  
|-----------------------------------|-----------|  
|`GCKeyword` <span data-ttu-id="0b797-467">(0x1)</span><span class="sxs-lookup"><span data-stu-id="0b797-467">(0x1)</span></span>|<span data-ttu-id="0b797-468">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="0b797-468">Informational (4)</span></span>|  
|`ThreadingKeyword` <span data-ttu-id="0b797-469">(0x10000)</span><span class="sxs-lookup"><span data-stu-id="0b797-469">(0x10000)</span></span>|<span data-ttu-id="0b797-470">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="0b797-470">Informational (4)</span></span>|  
  
 <span data-ttu-id="0b797-471">Aşağıdaki tabloda, olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="0b797-471">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="0b797-472">Olay</span><span class="sxs-lookup"><span data-stu-id="0b797-472">Event</span></span>|<span data-ttu-id="0b797-473">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="0b797-473">Event ID</span></span>|<span data-ttu-id="0b797-474">Ne zaman gerçekleşti</span><span class="sxs-lookup"><span data-stu-id="0b797-474">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCCreateConcurrentThread_V1`|<span data-ttu-id="0b797-475">11</span><span class="sxs-lookup"><span data-stu-id="0b797-475">11</span></span>|<span data-ttu-id="0b797-476">Eş zamanlı çöp toplama iş parçacığı oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="0b797-476">Concurrent garbage collection thread was created.</span></span>|  
  
 <span data-ttu-id="0b797-477">Hiçbir olay verileri.</span><span class="sxs-lookup"><span data-stu-id="0b797-477">No event data.</span></span>  
  
 [<span data-ttu-id="0b797-478">Başa dön</span><span class="sxs-lookup"><span data-stu-id="0b797-478">Back to top</span></span>](#top)  
  
<a name="gcterminateconcurrentthread_v1_event"></a>   
## <a name="gcterminateconcurrentthreadv1-event"></a><span data-ttu-id="0b797-479">GCTerminateConcurrentThread_V1 olay</span><span class="sxs-lookup"><span data-stu-id="0b797-479">GCTerminateConcurrentThread_V1 Event</span></span>  
 <span data-ttu-id="0b797-480">Aşağıdaki tabloda, düzeyi ve anahtar sözcüğü gösterir.</span><span class="sxs-lookup"><span data-stu-id="0b797-480">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="0b797-481">Olayı için anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="0b797-481">Keyword for raising the event</span></span>|<span data-ttu-id="0b797-482">Düzey</span><span class="sxs-lookup"><span data-stu-id="0b797-482">Level</span></span>|  
|-----------------------------------|-----------|  
|`GCKeyword` <span data-ttu-id="0b797-483">(0x1)</span><span class="sxs-lookup"><span data-stu-id="0b797-483">(0x1)</span></span>|<span data-ttu-id="0b797-484">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="0b797-484">Informational (4)</span></span>|  
|`ThreadingKeyword` <span data-ttu-id="0b797-485">(0x10000)</span><span class="sxs-lookup"><span data-stu-id="0b797-485">(0x10000)</span></span>|<span data-ttu-id="0b797-486">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="0b797-486">Informational (4)</span></span>|  
  
 <span data-ttu-id="0b797-487">Aşağıdaki tabloda, olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="0b797-487">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="0b797-488">Olay</span><span class="sxs-lookup"><span data-stu-id="0b797-488">Event</span></span>|<span data-ttu-id="0b797-489">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="0b797-489">Event ID</span></span>|<span data-ttu-id="0b797-490">Ne zaman gerçekleşti</span><span class="sxs-lookup"><span data-stu-id="0b797-490">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCTerminateConcurrentThread_V1`|<span data-ttu-id="0b797-491">12</span><span class="sxs-lookup"><span data-stu-id="0b797-491">12</span></span>|<span data-ttu-id="0b797-492">Eş zamanlı çöp toplama iş parçacığı sonlandırıldı.</span><span class="sxs-lookup"><span data-stu-id="0b797-492">Concurrent garbage collection thread was terminated.</span></span>|  
  
 <span data-ttu-id="0b797-493">Hiçbir olay verileri.</span><span class="sxs-lookup"><span data-stu-id="0b797-493">No event data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b797-494">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0b797-494">See also</span></span>

- [<span data-ttu-id="0b797-495">CLR ETW Olayları</span><span class="sxs-lookup"><span data-stu-id="0b797-495">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
