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
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59149740"
---
# <a name="garbage-collection-etw-events"></a><span data-ttu-id="90e6b-102">Çöp Toplama ETW Olayları</span><span class="sxs-lookup"><span data-stu-id="90e6b-102">Garbage Collection ETW Events</span></span>
<a name="top"></a> <span data-ttu-id="90e6b-103">Bu olaylar, çöp toplama hakkında bilgi toplayın.</span><span class="sxs-lookup"><span data-stu-id="90e6b-103">These events collect information pertaining to garbage collection.</span></span> <span data-ttu-id="90e6b-104">Bunlar Tanılama'da yardımcı olur ve hata ayıklama, çöp toplama kaç kez belirleme de dahil olmak üzere gerçekleştirildiyse, ne kadar bellek çöp toplama ve benzeri sırasında bırakılmış.</span><span class="sxs-lookup"><span data-stu-id="90e6b-104">They help in diagnostics and debugging, including determining how many times garbage collection was performed, how much memory was freed during garbage collection, and so on.</span></span>  
  
 <span data-ttu-id="90e6b-105">Bu kategori aşağıdaki olaylar oluşur:</span><span class="sxs-lookup"><span data-stu-id="90e6b-105">This category consists of the following events:</span></span>  
  
-   [<span data-ttu-id="90e6b-106">GCStart_V1 olay</span><span class="sxs-lookup"><span data-stu-id="90e6b-106">GCStart_V1 Event</span></span>](#gcstart_v1_event)  
  
-   [<span data-ttu-id="90e6b-107">GCEnd_V1 Event</span><span class="sxs-lookup"><span data-stu-id="90e6b-107">GCEnd_V1 Event</span></span>](#gcend_v1_event)  
  
-   [<span data-ttu-id="90e6b-108">GCHeapStats_V1 olay</span><span class="sxs-lookup"><span data-stu-id="90e6b-108">GCHeapStats_V1 Event</span></span>](#gcheapstats_v1_event)  
  
-   [<span data-ttu-id="90e6b-109">GCCreateSegment_V1 Event</span><span class="sxs-lookup"><span data-stu-id="90e6b-109">GCCreateSegment_V1 Event</span></span>](#gccreatesegment_v1_event)  
  
-   [<span data-ttu-id="90e6b-110">GCFreeSegment_V1 Event</span><span class="sxs-lookup"><span data-stu-id="90e6b-110">GCFreeSegment_V1 Event</span></span>](#gcfreesegment_v1_event)  
  
-   [<span data-ttu-id="90e6b-111">GCRestartEEBegin_V1 olay</span><span class="sxs-lookup"><span data-stu-id="90e6b-111">GCRestartEEBegin_V1 Event</span></span>](#gcrestarteebegin_v1_event)  
  
-   [<span data-ttu-id="90e6b-112">GCRestartEEEnd_V1 olay</span><span class="sxs-lookup"><span data-stu-id="90e6b-112">GCRestartEEEnd_V1 Event</span></span>](#gcrestarteeend_v1_event)  
  
-   [<span data-ttu-id="90e6b-113">GCSuspendEE_V1 Event</span><span class="sxs-lookup"><span data-stu-id="90e6b-113">GCSuspendEE_V1 Event</span></span>](#gcsuspendee_v1_event)  
  
-   [<span data-ttu-id="90e6b-114">GCSuspendEEEnd_V1 Event</span><span class="sxs-lookup"><span data-stu-id="90e6b-114">GCSuspendEEEnd_V1 Event</span></span>](#gcsuspendeeend_v1_event)  
  
-   [<span data-ttu-id="90e6b-115">GCAllocationTick_V2 olay</span><span class="sxs-lookup"><span data-stu-id="90e6b-115">GCAllocationTick_V2 Event</span></span>](#gcallocationtick_v2_event)  
  
-   [<span data-ttu-id="90e6b-116">GCFinalizersBegin_V1 Event</span><span class="sxs-lookup"><span data-stu-id="90e6b-116">GCFinalizersBegin_V1 Event</span></span>](#gcfinalizersbegin_v1_event)  
  
-   [<span data-ttu-id="90e6b-117">GCFinalizersEnd_V1 olay</span><span class="sxs-lookup"><span data-stu-id="90e6b-117">GCFinalizersEnd_V1 Event</span></span>](#gcfinalizersend_v1_event)  
  
-   [<span data-ttu-id="90e6b-118">GCCreateConcurrentThread_V1 olay</span><span class="sxs-lookup"><span data-stu-id="90e6b-118">GCCreateConcurrentThread_V1 Event</span></span>](#gccreateconcurrentthread_v1_event)  
  
-   [<span data-ttu-id="90e6b-119">GCTerminateConcurrentThread_V1 olay</span><span class="sxs-lookup"><span data-stu-id="90e6b-119">GCTerminateConcurrentThread_V1 Event</span></span>](#gcterminateconcurrentthread_v1_event)  
  
<a name="gcstart_v1_event"></a>   
## <a name="gcstartv1-event"></a><span data-ttu-id="90e6b-120">GCStart_V1 olay</span><span class="sxs-lookup"><span data-stu-id="90e6b-120">GCStart_V1 Event</span></span>  
 <span data-ttu-id="90e6b-121">Aşağıdaki tabloda, düzeyi ve anahtar sözcüğü gösterir.</span><span class="sxs-lookup"><span data-stu-id="90e6b-121">The following table shows the keyword and level.</span></span> <span data-ttu-id="90e6b-122">(Daha fazla bilgi için [CLR ETW anahtar sözcükleri ve Düzeyler](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="90e6b-122">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="90e6b-123">Olayı için anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="90e6b-123">Keyword for raising the event</span></span>|<span data-ttu-id="90e6b-124">Düzey</span><span class="sxs-lookup"><span data-stu-id="90e6b-124">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="90e6b-125">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="90e6b-125">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="90e6b-126">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="90e6b-126">Informational (4)</span></span>|  
  
 <span data-ttu-id="90e6b-127">Aşağıdaki tabloda, olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="90e6b-127">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="90e6b-128">Olay</span><span class="sxs-lookup"><span data-stu-id="90e6b-128">Event</span></span>|<span data-ttu-id="90e6b-129">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="90e6b-129">Event ID</span></span>|<span data-ttu-id="90e6b-130">Ne zaman gerçekleşti</span><span class="sxs-lookup"><span data-stu-id="90e6b-130">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCStart_V1`|<span data-ttu-id="90e6b-131">1.</span><span class="sxs-lookup"><span data-stu-id="90e6b-131">1</span></span>|<span data-ttu-id="90e6b-132">Bir çöp toplama başlatıldı.</span><span class="sxs-lookup"><span data-stu-id="90e6b-132">A garbage collection has started.</span></span>|  
  
 <span data-ttu-id="90e6b-133">Aşağıdaki tabloda, olay verilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="90e6b-133">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="90e6b-134">Alan adı</span><span class="sxs-lookup"><span data-stu-id="90e6b-134">Field name</span></span>|<span data-ttu-id="90e6b-135">Veri türü</span><span class="sxs-lookup"><span data-stu-id="90e6b-135">Data type</span></span>|<span data-ttu-id="90e6b-136">Açıklama</span><span class="sxs-lookup"><span data-stu-id="90e6b-136">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="90e6b-137">Sayı</span><span class="sxs-lookup"><span data-stu-id="90e6b-137">Count</span></span>|<span data-ttu-id="90e6b-138">Kazanma: UInt32</span><span class="sxs-lookup"><span data-stu-id="90e6b-138">win:UInt32</span></span>|<span data-ttu-id="90e6b-139">*n*th çöp toplama.</span><span class="sxs-lookup"><span data-stu-id="90e6b-139">The *n*th garbage collection.</span></span>|  
|<span data-ttu-id="90e6b-140">Derinliği</span><span class="sxs-lookup"><span data-stu-id="90e6b-140">Depth</span></span>|<span data-ttu-id="90e6b-141">Kazanma: UInt32</span><span class="sxs-lookup"><span data-stu-id="90e6b-141">win:UInt32</span></span>|<span data-ttu-id="90e6b-142">Toplanmakta olan oluşturma.</span><span class="sxs-lookup"><span data-stu-id="90e6b-142">The generation that is being collected.</span></span>|  
|<span data-ttu-id="90e6b-143">Neden</span><span class="sxs-lookup"><span data-stu-id="90e6b-143">Reason</span></span>|<span data-ttu-id="90e6b-144">Kazanma: UInt32</span><span class="sxs-lookup"><span data-stu-id="90e6b-144">win:UInt32</span></span>|<span data-ttu-id="90e6b-145">Çöp toplama işlemine neden tetiklendi:</span><span class="sxs-lookup"><span data-stu-id="90e6b-145">Why the garbage collection was triggered:</span></span><br /><br /> <span data-ttu-id="90e6b-146">0x0 - küçük nesne yığını ayırması.</span><span class="sxs-lookup"><span data-stu-id="90e6b-146">0x0 - Small object heap allocation.</span></span><br /><br /> <span data-ttu-id="90e6b-147">0x1 - başlattı.</span><span class="sxs-lookup"><span data-stu-id="90e6b-147">0x1 - Induced.</span></span><br /><br /> <span data-ttu-id="90e6b-148">0x2 - bellek yetersiz.</span><span class="sxs-lookup"><span data-stu-id="90e6b-148">0x2 - Low memory.</span></span><br /><br /> <span data-ttu-id="90e6b-149">0x3 - boş.</span><span class="sxs-lookup"><span data-stu-id="90e6b-149">0x3 - Empty.</span></span><br /><br /> <span data-ttu-id="90e6b-150">0x4 - büyük nesne yığını ayırması.</span><span class="sxs-lookup"><span data-stu-id="90e6b-150">0x4 - Large object heap allocation.</span></span><br /><br /> <span data-ttu-id="90e6b-151">0x5 - yetersiz alan (küçük nesne yığını için).</span><span class="sxs-lookup"><span data-stu-id="90e6b-151">0x5 - Out of space (for small object heap).</span></span><br /><br /> <span data-ttu-id="90e6b-152">0x6 - yetersiz alan (büyük nesne yığını için).</span><span class="sxs-lookup"><span data-stu-id="90e6b-152">0x6 - Out of space (for large object heap).</span></span><br /><br /> <span data-ttu-id="90e6b-153">0x7 - başlattığı ancak engelleme olarak zorunlu değildir.</span><span class="sxs-lookup"><span data-stu-id="90e6b-153">0x7 - Induced but not forced as blocking.</span></span>|  
|<span data-ttu-id="90e6b-154">Tür</span><span class="sxs-lookup"><span data-stu-id="90e6b-154">Type</span></span>|<span data-ttu-id="90e6b-155">Kazanma: UInt32</span><span class="sxs-lookup"><span data-stu-id="90e6b-155">win:UInt32</span></span>|<span data-ttu-id="90e6b-156">0x0 - arka plan atık toplamanın dışında atık toplamayı engelleme oluştu.</span><span class="sxs-lookup"><span data-stu-id="90e6b-156">0x0 - Blocking garbage collection occurred outside background garbage collection.</span></span><br /><br /> <span data-ttu-id="90e6b-157">0x1 - arka plan çöp toplama.</span><span class="sxs-lookup"><span data-stu-id="90e6b-157">0x1 - Background garbage collection.</span></span><br /><br /> <span data-ttu-id="90e6b-158">0x2 - arka plan çöp toplama sırasında atık toplamayı engelleme oluştu.</span><span class="sxs-lookup"><span data-stu-id="90e6b-158">0x2 - Blocking garbage collection occurred during background garbage collection.</span></span>|  
|<span data-ttu-id="90e6b-159">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="90e6b-159">ClrInstanceID</span></span>|<span data-ttu-id="90e6b-160">Kazanma: UInt16</span><span class="sxs-lookup"><span data-stu-id="90e6b-160">win:UInt16</span></span>|<span data-ttu-id="90e6b-161">CLR veya CoreCLR örneği için benzersiz kimlik.</span><span class="sxs-lookup"><span data-stu-id="90e6b-161">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="90e6b-162">Başa dön</span><span class="sxs-lookup"><span data-stu-id="90e6b-162">Back to top</span></span>](#top)  
  
<a name="gcend_v1_event"></a>   
## <a name="gcendv1-event"></a><span data-ttu-id="90e6b-163">GCEnd_V1 olay</span><span class="sxs-lookup"><span data-stu-id="90e6b-163">GCEnd_V1 Event</span></span>  
 <span data-ttu-id="90e6b-164">Aşağıdaki tabloda, düzeyi ve anahtar sözcüğü gösterir.</span><span class="sxs-lookup"><span data-stu-id="90e6b-164">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="90e6b-165">Olayı için anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="90e6b-165">Keyword for raising the event</span></span>|<span data-ttu-id="90e6b-166">Düzey</span><span class="sxs-lookup"><span data-stu-id="90e6b-166">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="90e6b-167">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="90e6b-167">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="90e6b-168">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="90e6b-168">Informational (4)</span></span>|  
  
 <span data-ttu-id="90e6b-169">Aşağıdaki tabloda, olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="90e6b-169">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="90e6b-170">Olay</span><span class="sxs-lookup"><span data-stu-id="90e6b-170">Event</span></span>|<span data-ttu-id="90e6b-171">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="90e6b-171">Event ID</span></span>|<span data-ttu-id="90e6b-172">Ne zaman gerçekleşti</span><span class="sxs-lookup"><span data-stu-id="90e6b-172">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCEnd_V1`|<span data-ttu-id="90e6b-173">2</span><span class="sxs-lookup"><span data-stu-id="90e6b-173">2</span></span>|<span data-ttu-id="90e6b-174">Çöp toplama sona erdi.</span><span class="sxs-lookup"><span data-stu-id="90e6b-174">The garbage collection has ended.</span></span>|  
  
 <span data-ttu-id="90e6b-175">Aşağıdaki tabloda, olay verilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="90e6b-175">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="90e6b-176">Alan adı</span><span class="sxs-lookup"><span data-stu-id="90e6b-176">Field name</span></span>|<span data-ttu-id="90e6b-177">Veri türü</span><span class="sxs-lookup"><span data-stu-id="90e6b-177">Data type</span></span>|<span data-ttu-id="90e6b-178">Açıklama</span><span class="sxs-lookup"><span data-stu-id="90e6b-178">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="90e6b-179">Sayı</span><span class="sxs-lookup"><span data-stu-id="90e6b-179">Count</span></span>|<span data-ttu-id="90e6b-180">Kazanma: UInt32</span><span class="sxs-lookup"><span data-stu-id="90e6b-180">win:UInt32</span></span>|<span data-ttu-id="90e6b-181">*n*th çöp toplama.</span><span class="sxs-lookup"><span data-stu-id="90e6b-181">The *n*th garbage collection.</span></span>|  
|<span data-ttu-id="90e6b-182">Derinliği</span><span class="sxs-lookup"><span data-stu-id="90e6b-182">Depth</span></span>|<span data-ttu-id="90e6b-183">Kazanma: UInt32</span><span class="sxs-lookup"><span data-stu-id="90e6b-183">win:UInt32</span></span>|<span data-ttu-id="90e6b-184">Toplanan oluşturma.</span><span class="sxs-lookup"><span data-stu-id="90e6b-184">The generation that was collected.</span></span>|  
|<span data-ttu-id="90e6b-185">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="90e6b-185">ClrInstanceID</span></span>|<span data-ttu-id="90e6b-186">Kazanma: UInt16</span><span class="sxs-lookup"><span data-stu-id="90e6b-186">win:UInt16</span></span>|<span data-ttu-id="90e6b-187">CLR veya CoreCLR örneği için benzersiz kimlik.</span><span class="sxs-lookup"><span data-stu-id="90e6b-187">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="90e6b-188">Başa dön</span><span class="sxs-lookup"><span data-stu-id="90e6b-188">Back to top</span></span>](#top)  
  
<a name="gcheapstats_v1_event"></a>   
## <a name="gcheapstatsv1-event"></a><span data-ttu-id="90e6b-189">GCHeapStats_V1 olay</span><span class="sxs-lookup"><span data-stu-id="90e6b-189">GCHeapStats_V1 Event</span></span>  
 <span data-ttu-id="90e6b-190">Aşağıdaki tabloda, düzeyi ve anahtar sözcüğü gösterir.</span><span class="sxs-lookup"><span data-stu-id="90e6b-190">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="90e6b-191">Olayı için anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="90e6b-191">Keyword for raising the event</span></span>|<span data-ttu-id="90e6b-192">Düzey</span><span class="sxs-lookup"><span data-stu-id="90e6b-192">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="90e6b-193">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="90e6b-193">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="90e6b-194">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="90e6b-194">Informational (4)</span></span>|  
  
 <span data-ttu-id="90e6b-195">Aşağıdaki tabloda, olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="90e6b-195">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="90e6b-196">Olay</span><span class="sxs-lookup"><span data-stu-id="90e6b-196">Event</span></span>|<span data-ttu-id="90e6b-197">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="90e6b-197">Event ID</span></span>|<span data-ttu-id="90e6b-198">Açıklama</span><span class="sxs-lookup"><span data-stu-id="90e6b-198">Description</span></span>|  
|-----------|--------------|-----------------|  
|`GCHeapStats_V1`|<span data-ttu-id="90e6b-199">4</span><span class="sxs-lookup"><span data-stu-id="90e6b-199">4</span></span>|<span data-ttu-id="90e6b-200">Her çöp toplama sonunda yığında istatistiklerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="90e6b-200">Shows the heap statistics at the end of each garbage collection.</span></span>|  
  
 <span data-ttu-id="90e6b-201">Aşağıdaki tabloda, olay verilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="90e6b-201">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="90e6b-202">Alan adı</span><span class="sxs-lookup"><span data-stu-id="90e6b-202">Field name</span></span>|<span data-ttu-id="90e6b-203">Veri türü</span><span class="sxs-lookup"><span data-stu-id="90e6b-203">Data type</span></span>|<span data-ttu-id="90e6b-204">Açıklama</span><span class="sxs-lookup"><span data-stu-id="90e6b-204">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="90e6b-205">GenerationSize0</span><span class="sxs-lookup"><span data-stu-id="90e6b-205">GenerationSize0</span></span>|<span data-ttu-id="90e6b-206">Kazanma: UInt64</span><span class="sxs-lookup"><span data-stu-id="90e6b-206">win:UInt64</span></span>|<span data-ttu-id="90e6b-207">Nesil 0 belleğin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="90e6b-207">The size, in bytes, of generation 0 memory.</span></span>|  
|<span data-ttu-id="90e6b-208">TotalPromotedSize0</span><span class="sxs-lookup"><span data-stu-id="90e6b-208">TotalPromotedSize0</span></span>|<span data-ttu-id="90e6b-209">Kazanma: UInt64</span><span class="sxs-lookup"><span data-stu-id="90e6b-209">win:UInt64</span></span>|<span data-ttu-id="90e6b-210">1. nesil için nesil 0 ' yükseltilen bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="90e6b-210">The number of bytes that are promoted from generation 0 to generation 1.</span></span>|  
|<span data-ttu-id="90e6b-211">GenerationSize1</span><span class="sxs-lookup"><span data-stu-id="90e6b-211">GenerationSize1</span></span>|<span data-ttu-id="90e6b-212">Kazanma: UInt64</span><span class="sxs-lookup"><span data-stu-id="90e6b-212">win:UInt64</span></span>|<span data-ttu-id="90e6b-213">1. kuşak belleğin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="90e6b-213">The size, in bytes, of generation 1 memory.</span></span>|  
|<span data-ttu-id="90e6b-214">TotalPromotedSize1</span><span class="sxs-lookup"><span data-stu-id="90e6b-214">TotalPromotedSize1</span></span>|<span data-ttu-id="90e6b-215">Kazanma: UInt64</span><span class="sxs-lookup"><span data-stu-id="90e6b-215">win:UInt64</span></span>|<span data-ttu-id="90e6b-216">Nesil 1 ' 2 yeni nesle yükseltilir bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="90e6b-216">The number of bytes that are promoted from generation 1 to generation 2.</span></span>|  
|<span data-ttu-id="90e6b-217">GenerationSize2</span><span class="sxs-lookup"><span data-stu-id="90e6b-217">GenerationSize2</span></span>|<span data-ttu-id="90e6b-218">Kazanma: UInt64</span><span class="sxs-lookup"><span data-stu-id="90e6b-218">win:UInt64</span></span>|<span data-ttu-id="90e6b-219">2. nesil belleğin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="90e6b-219">The size, in bytes, of generation 2 memory.</span></span>|  
|<span data-ttu-id="90e6b-220">TotalPromotedSize2</span><span class="sxs-lookup"><span data-stu-id="90e6b-220">TotalPromotedSize2</span></span>|<span data-ttu-id="90e6b-221">Kazanma: UInt64</span><span class="sxs-lookup"><span data-stu-id="90e6b-221">win:UInt64</span></span>|<span data-ttu-id="90e6b-222">2. nesil son toplamadan sonra içinde kurtulan bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="90e6b-222">The number of bytes that survived in generation 2 after the last collection.</span></span>|  
|<span data-ttu-id="90e6b-223">GenerationSize3</span><span class="sxs-lookup"><span data-stu-id="90e6b-223">GenerationSize3</span></span>|<span data-ttu-id="90e6b-224">Kazanma: UInt64</span><span class="sxs-lookup"><span data-stu-id="90e6b-224">win:UInt64</span></span>|<span data-ttu-id="90e6b-225">Büyük nesne yığını bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="90e6b-225">The size, in bytes, of the large object heap.</span></span>|  
|<span data-ttu-id="90e6b-226">TotalPromotedSize3</span><span class="sxs-lookup"><span data-stu-id="90e6b-226">TotalPromotedSize3</span></span>|<span data-ttu-id="90e6b-227">Kazanma: UInt64</span><span class="sxs-lookup"><span data-stu-id="90e6b-227">win:UInt64</span></span>|<span data-ttu-id="90e6b-228">Büyük nesne yığınında sonra son toplamadan kurtulan bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="90e6b-228">The number of bytes that survived in the large object heap after the last collection.</span></span>|  
|<span data-ttu-id="90e6b-229">FinalizationPromotedSize</span><span class="sxs-lookup"><span data-stu-id="90e6b-229">FinalizationPromotedSize</span></span>|<span data-ttu-id="90e6b-230">Kazanma: UInt64</span><span class="sxs-lookup"><span data-stu-id="90e6b-230">win:UInt64</span></span>|<span data-ttu-id="90e6b-231">Baytlarında sonlandırma için hazır olan nesneleri toplam boyutu.</span><span class="sxs-lookup"><span data-stu-id="90e6b-231">The total size, in bytes, of the objects that are ready for finalization.</span></span>|  
|<span data-ttu-id="90e6b-232">FinalizationPromotedCount</span><span class="sxs-lookup"><span data-stu-id="90e6b-232">FinalizationPromotedCount</span></span>|<span data-ttu-id="90e6b-233">Kazanma: UInt64</span><span class="sxs-lookup"><span data-stu-id="90e6b-233">win:UInt64</span></span>|<span data-ttu-id="90e6b-234">Sonlandırma için hazır olan nesnelerinin sayısı.</span><span class="sxs-lookup"><span data-stu-id="90e6b-234">The number of objects that are ready for finalization.</span></span>|  
|<span data-ttu-id="90e6b-235">PinnedObjectCount</span><span class="sxs-lookup"><span data-stu-id="90e6b-235">PinnedObjectCount</span></span>|<span data-ttu-id="90e6b-236">Kazanma: UInt32</span><span class="sxs-lookup"><span data-stu-id="90e6b-236">win:UInt32</span></span>|<span data-ttu-id="90e6b-237">Sabitlenen (taşınamayan) nesne sayısı.</span><span class="sxs-lookup"><span data-stu-id="90e6b-237">The number of pinned (unmovable) objects.</span></span>|  
|<span data-ttu-id="90e6b-238">SinkBlockCount</span><span class="sxs-lookup"><span data-stu-id="90e6b-238">SinkBlockCount</span></span>|<span data-ttu-id="90e6b-239">Kazanma: UInt32</span><span class="sxs-lookup"><span data-stu-id="90e6b-239">win:UInt32</span></span>|<span data-ttu-id="90e6b-240">Kullanımdaki eşitleme blokların sayısı.</span><span class="sxs-lookup"><span data-stu-id="90e6b-240">The number of synchronization blocks in use.</span></span>|  
|<span data-ttu-id="90e6b-241">GCHandleCount</span><span class="sxs-lookup"><span data-stu-id="90e6b-241">GCHandleCount</span></span>|<span data-ttu-id="90e6b-242">Kazanma: UInt32</span><span class="sxs-lookup"><span data-stu-id="90e6b-242">win:UInt32</span></span>|<span data-ttu-id="90e6b-243">Kullanımda olan çöp toplama sayısı.</span><span class="sxs-lookup"><span data-stu-id="90e6b-243">The number of garbage collection handles in use.</span></span>|  
|<span data-ttu-id="90e6b-244">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="90e6b-244">ClrInstanceID</span></span>|<span data-ttu-id="90e6b-245">Kazanma: UInt16</span><span class="sxs-lookup"><span data-stu-id="90e6b-245">win:UInt16</span></span>|<span data-ttu-id="90e6b-246">CLR veya CoreCLR örneği için benzersiz kimlik.</span><span class="sxs-lookup"><span data-stu-id="90e6b-246">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="90e6b-247">Başa dön</span><span class="sxs-lookup"><span data-stu-id="90e6b-247">Back to top</span></span>](#top)  
  
<a name="gccreatesegment_v1_event"></a>   
## <a name="gccreatesegmentv1-event"></a><span data-ttu-id="90e6b-248">GCCreateSegment_V1 Event</span><span class="sxs-lookup"><span data-stu-id="90e6b-248">GCCreateSegment_V1 Event</span></span>  
 <span data-ttu-id="90e6b-249">Aşağıdaki tabloda, düzeyi ve anahtar sözcüğü gösterir.</span><span class="sxs-lookup"><span data-stu-id="90e6b-249">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="90e6b-250">Olayı için anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="90e6b-250">Keyword for raising the event</span></span>|<span data-ttu-id="90e6b-251">Düzey</span><span class="sxs-lookup"><span data-stu-id="90e6b-251">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="90e6b-252">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="90e6b-252">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="90e6b-253">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="90e6b-253">Informational (4)</span></span>|  
  
 <span data-ttu-id="90e6b-254">Aşağıdaki tabloda, olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="90e6b-254">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="90e6b-255">Olay</span><span class="sxs-lookup"><span data-stu-id="90e6b-255">Event</span></span>|<span data-ttu-id="90e6b-256">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="90e6b-256">Event ID</span></span>|<span data-ttu-id="90e6b-257">Ne zaman gerçekleşti</span><span class="sxs-lookup"><span data-stu-id="90e6b-257">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCCreateSegment_V1`|<span data-ttu-id="90e6b-258">5</span><span class="sxs-lookup"><span data-stu-id="90e6b-258">5</span></span>|<span data-ttu-id="90e6b-259">Yeni bir çöp toplama segment oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="90e6b-259">A new garbage collection segment has been created.</span></span> <span data-ttu-id="90e6b-260">Ayrıca, zaten çalışan bir işlemde izleme etkin olduğunda, var olan her segment için bu olay oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="90e6b-260">In addition, when tracing is enabled on a process that is already running, this event is raised for each existing segment.</span></span>|  
  
 <span data-ttu-id="90e6b-261">Aşağıdaki tabloda, olay verilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="90e6b-261">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="90e6b-262">Alan adı</span><span class="sxs-lookup"><span data-stu-id="90e6b-262">Field name</span></span>|<span data-ttu-id="90e6b-263">Veri türü</span><span class="sxs-lookup"><span data-stu-id="90e6b-263">Data type</span></span>|<span data-ttu-id="90e6b-264">Açıklama</span><span class="sxs-lookup"><span data-stu-id="90e6b-264">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="90e6b-265">Adres</span><span class="sxs-lookup"><span data-stu-id="90e6b-265">Address</span></span>|<span data-ttu-id="90e6b-266">Kazanma: UInt64</span><span class="sxs-lookup"><span data-stu-id="90e6b-266">win:UInt64</span></span>|<span data-ttu-id="90e6b-267">Segment adresi.</span><span class="sxs-lookup"><span data-stu-id="90e6b-267">The address of the segment.</span></span>|  
|<span data-ttu-id="90e6b-268">Boyut</span><span class="sxs-lookup"><span data-stu-id="90e6b-268">Size</span></span>|<span data-ttu-id="90e6b-269">Kazanma: UInt64</span><span class="sxs-lookup"><span data-stu-id="90e6b-269">win:UInt64</span></span>|<span data-ttu-id="90e6b-270">Kesim boyutu.</span><span class="sxs-lookup"><span data-stu-id="90e6b-270">The size of the segment.</span></span>|  
|<span data-ttu-id="90e6b-271">Tür</span><span class="sxs-lookup"><span data-stu-id="90e6b-271">Type</span></span>|<span data-ttu-id="90e6b-272">Kazanma: UInt32</span><span class="sxs-lookup"><span data-stu-id="90e6b-272">win:UInt32</span></span>|<span data-ttu-id="90e6b-273">0x0 - küçük nesne yığını.</span><span class="sxs-lookup"><span data-stu-id="90e6b-273">0x0 - Small object heap.</span></span><br /><br /> <span data-ttu-id="90e6b-274">0x1 - büyük nesne yığını.</span><span class="sxs-lookup"><span data-stu-id="90e6b-274">0x1 - Large object heap.</span></span><br /><br /> <span data-ttu-id="90e6b-275">0x2 - yığın salt okunur.</span><span class="sxs-lookup"><span data-stu-id="90e6b-275">0x2 - Read-only heap.</span></span>|  
|<span data-ttu-id="90e6b-276">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="90e6b-276">ClrInstanceID</span></span>|<span data-ttu-id="90e6b-277">Kazanma: UInt16</span><span class="sxs-lookup"><span data-stu-id="90e6b-277">win:UInt16</span></span>|<span data-ttu-id="90e6b-278">CLR veya CoreCLR örneği için benzersiz kimlik.</span><span class="sxs-lookup"><span data-stu-id="90e6b-278">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 <span data-ttu-id="90e6b-279">Boyutu çöp toplayıcısının ayrılan parçaları uygulama özgü olan ve düzenli güncelleştirmeleri dahil olmak üzere dilediğiniz zaman değiştirilebilir unutmayın.</span><span class="sxs-lookup"><span data-stu-id="90e6b-279">Note that the size of segments allocated by the garbage collector is implementation-specific and is subject to change at any time, including in periodic updates.</span></span> <span data-ttu-id="90e6b-280">Uygulamanız hiçbir zaman hakkında varsayımlar veya belirli bir segment boyutuna göre değişir ve segment ayırma için kullanılabilir bellek miktarını yapılandırmak için denemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="90e6b-280">Your app should never make assumptions about or depend on a particular segment size, nor should it attempt to configure the amount of memory available for segment allocations.</span></span>  
  
 [<span data-ttu-id="90e6b-281">Başa dön</span><span class="sxs-lookup"><span data-stu-id="90e6b-281">Back to top</span></span>](#top)  
  
<a name="gcfreesegment_v1_event"></a>   
## <a name="gcfreesegmentv1-event"></a><span data-ttu-id="90e6b-282">GCFreeSegment_V1 Event</span><span class="sxs-lookup"><span data-stu-id="90e6b-282">GCFreeSegment_V1 Event</span></span>  
 <span data-ttu-id="90e6b-283">Aşağıdaki tabloda, düzeyi ve anahtar sözcüğü gösterir.</span><span class="sxs-lookup"><span data-stu-id="90e6b-283">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="90e6b-284">Olayı için anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="90e6b-284">Keyword for raising the event</span></span>|<span data-ttu-id="90e6b-285">Düzey</span><span class="sxs-lookup"><span data-stu-id="90e6b-285">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="90e6b-286">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="90e6b-286">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="90e6b-287">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="90e6b-287">Informational (4)</span></span>|  
  
 <span data-ttu-id="90e6b-288">Aşağıdaki tabloda, olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="90e6b-288">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="90e6b-289">Olay</span><span class="sxs-lookup"><span data-stu-id="90e6b-289">Event</span></span>|<span data-ttu-id="90e6b-290">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="90e6b-290">Event ID</span></span>|<span data-ttu-id="90e6b-291">Ne zaman gerçekleşti</span><span class="sxs-lookup"><span data-stu-id="90e6b-291">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCFreeSegment_V1`|<span data-ttu-id="90e6b-292">6</span><span class="sxs-lookup"><span data-stu-id="90e6b-292">6</span></span>|<span data-ttu-id="90e6b-293">Bir çöp toplama segment piyasaya Sürüldü.</span><span class="sxs-lookup"><span data-stu-id="90e6b-293">A garbage collection segment has been released.</span></span>|  
  
 <span data-ttu-id="90e6b-294">Aşağıdaki tabloda, olay verilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="90e6b-294">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="90e6b-295">Alan adı</span><span class="sxs-lookup"><span data-stu-id="90e6b-295">Field name</span></span>|<span data-ttu-id="90e6b-296">Veri türü</span><span class="sxs-lookup"><span data-stu-id="90e6b-296">Data type</span></span>|<span data-ttu-id="90e6b-297">Açıklama</span><span class="sxs-lookup"><span data-stu-id="90e6b-297">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="90e6b-298">Adres</span><span class="sxs-lookup"><span data-stu-id="90e6b-298">Address</span></span>|<span data-ttu-id="90e6b-299">Kazanma: UInt64</span><span class="sxs-lookup"><span data-stu-id="90e6b-299">win:UInt64</span></span>|<span data-ttu-id="90e6b-300">Segment adresi.</span><span class="sxs-lookup"><span data-stu-id="90e6b-300">The address of the segment.</span></span>|  
|<span data-ttu-id="90e6b-301">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="90e6b-301">ClrInstanceID</span></span>|<span data-ttu-id="90e6b-302">Kazanma: UInt16</span><span class="sxs-lookup"><span data-stu-id="90e6b-302">win:UInt16</span></span>|<span data-ttu-id="90e6b-303">CLR veya CoreCLR örneği için benzersiz kimlik.</span><span class="sxs-lookup"><span data-stu-id="90e6b-303">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="90e6b-304">Başa dön</span><span class="sxs-lookup"><span data-stu-id="90e6b-304">Back to top</span></span>](#top)  
  
<a name="gcrestarteebegin_v1_event"></a>   
## <a name="gcrestarteebeginv1-event"></a><span data-ttu-id="90e6b-305">GCRestartEEBegin_V1 olay</span><span class="sxs-lookup"><span data-stu-id="90e6b-305">GCRestartEEBegin_V1 Event</span></span>  
 <span data-ttu-id="90e6b-306">Aşağıdaki tabloda, düzeyi ve anahtar sözcüğü gösterir.</span><span class="sxs-lookup"><span data-stu-id="90e6b-306">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="90e6b-307">Olayı için anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="90e6b-307">Keyword for raising the event</span></span>|<span data-ttu-id="90e6b-308">Düzey</span><span class="sxs-lookup"><span data-stu-id="90e6b-308">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="90e6b-309">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="90e6b-309">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="90e6b-310">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="90e6b-310">Informational (4)</span></span>|  
  
 <span data-ttu-id="90e6b-311">Aşağıdaki tabloda, olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="90e6b-311">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="90e6b-312">Olay</span><span class="sxs-lookup"><span data-stu-id="90e6b-312">Event</span></span>|<span data-ttu-id="90e6b-313">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="90e6b-313">Event ID</span></span>|<span data-ttu-id="90e6b-314">Ne zaman gerçekleşti</span><span class="sxs-lookup"><span data-stu-id="90e6b-314">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCRestartEEBegin_V1`|<span data-ttu-id="90e6b-315">7</span><span class="sxs-lookup"><span data-stu-id="90e6b-315">7</span></span>|<span data-ttu-id="90e6b-316">Ortak dil çalışma zamanı askıya alma gelen sürdürme başladı.</span><span class="sxs-lookup"><span data-stu-id="90e6b-316">Resumption from common language runtime suspension has begun.</span></span>|  
  
 <span data-ttu-id="90e6b-317">Hiçbir olay verileri.</span><span class="sxs-lookup"><span data-stu-id="90e6b-317">No event data.</span></span>  
  
 [<span data-ttu-id="90e6b-318">Başa dön</span><span class="sxs-lookup"><span data-stu-id="90e6b-318">Back to top</span></span>](#top)  
  
<a name="gcrestarteeend_v1_event"></a>   
## <a name="gcrestarteeendv1-event"></a><span data-ttu-id="90e6b-319">GCRestartEEEnd_V1 olay</span><span class="sxs-lookup"><span data-stu-id="90e6b-319">GCRestartEEEnd_V1 Event</span></span>  
 <span data-ttu-id="90e6b-320">Aşağıdaki tabloda, düzeyi ve anahtar sözcüğü gösterir.</span><span class="sxs-lookup"><span data-stu-id="90e6b-320">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="90e6b-321">Olayı için anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="90e6b-321">Keyword for raising the event</span></span>|<span data-ttu-id="90e6b-322">Düzey</span><span class="sxs-lookup"><span data-stu-id="90e6b-322">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="90e6b-323">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="90e6b-323">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="90e6b-324">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="90e6b-324">Informational (4)</span></span>|  
  
 <span data-ttu-id="90e6b-325">Aşağıdaki tabloda, olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="90e6b-325">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="90e6b-326">Olay</span><span class="sxs-lookup"><span data-stu-id="90e6b-326">Event</span></span>|<span data-ttu-id="90e6b-327">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="90e6b-327">Event Id</span></span>|<span data-ttu-id="90e6b-328">Ne zaman gerçekleşti</span><span class="sxs-lookup"><span data-stu-id="90e6b-328">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCRestartEEEnd_V1`|<span data-ttu-id="90e6b-329">3</span><span class="sxs-lookup"><span data-stu-id="90e6b-329">3</span></span>|<span data-ttu-id="90e6b-330">Ortak dil çalışma zamanı askıya alma gelen sürdürme sona erdi.</span><span class="sxs-lookup"><span data-stu-id="90e6b-330">Resumption from common language runtime suspension has ended.</span></span>|  
  
 <span data-ttu-id="90e6b-331">Hiçbir olay verileri.</span><span class="sxs-lookup"><span data-stu-id="90e6b-331">No event data.</span></span>  
  
 [<span data-ttu-id="90e6b-332">Başa dön</span><span class="sxs-lookup"><span data-stu-id="90e6b-332">Back to top</span></span>](#top)  
  
<a name="gcsuspendee_v1_event"></a>   
## <a name="gcsuspendeev1-event"></a><span data-ttu-id="90e6b-333">GCSuspendEE_V1 Event</span><span class="sxs-lookup"><span data-stu-id="90e6b-333">GCSuspendEE_V1 Event</span></span>  
 <span data-ttu-id="90e6b-334">Aşağıdaki tabloda, düzeyi ve anahtar sözcüğü gösterir.</span><span class="sxs-lookup"><span data-stu-id="90e6b-334">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="90e6b-335">Olayı için anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="90e6b-335">Keyword for raising the event</span></span>|<span data-ttu-id="90e6b-336">Düzey</span><span class="sxs-lookup"><span data-stu-id="90e6b-336">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="90e6b-337">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="90e6b-337">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="90e6b-338">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="90e6b-338">Informational (4)</span></span>|  
  
 <span data-ttu-id="90e6b-339">Aşağıdaki tabloda, olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="90e6b-339">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="90e6b-340">Olay</span><span class="sxs-lookup"><span data-stu-id="90e6b-340">Event</span></span>|<span data-ttu-id="90e6b-341">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="90e6b-341">Event ID</span></span>|<span data-ttu-id="90e6b-342">Ne zaman gerçekleşti</span><span class="sxs-lookup"><span data-stu-id="90e6b-342">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCSuspendEE_V1`|<span data-ttu-id="90e6b-343">9</span><span class="sxs-lookup"><span data-stu-id="90e6b-343">9</span></span>|<span data-ttu-id="90e6b-344">Çöp toplama işlemi için yürütme altyapısının askıya alma başlangıcı.</span><span class="sxs-lookup"><span data-stu-id="90e6b-344">Start of suspension of the execution engine for garbage collection.</span></span>|  
  
 <span data-ttu-id="90e6b-345">Aşağıdaki tabloda, olay verilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="90e6b-345">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="90e6b-346">Alan adı</span><span class="sxs-lookup"><span data-stu-id="90e6b-346">Field name</span></span>|<span data-ttu-id="90e6b-347">Veri türü</span><span class="sxs-lookup"><span data-stu-id="90e6b-347">Data type</span></span>|<span data-ttu-id="90e6b-348">Açıklama</span><span class="sxs-lookup"><span data-stu-id="90e6b-348">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="90e6b-349">Neden</span><span class="sxs-lookup"><span data-stu-id="90e6b-349">Reason</span></span>|<span data-ttu-id="90e6b-350">Kazanma: UInt16</span><span class="sxs-lookup"><span data-stu-id="90e6b-350">win:UInt16</span></span>|<span data-ttu-id="90e6b-351">0x0 - diğer.</span><span class="sxs-lookup"><span data-stu-id="90e6b-351">0x0 - Other.</span></span><br /><br /> <span data-ttu-id="90e6b-352">0x1 - çöp toplama.</span><span class="sxs-lookup"><span data-stu-id="90e6b-352">0x1 - Garbage collection.</span></span><br /><br /> <span data-ttu-id="90e6b-353">0x2 - uygulama etki alanı kapatma.</span><span class="sxs-lookup"><span data-stu-id="90e6b-353">0x2 - Application domain shutdown.</span></span><br /><br /> <span data-ttu-id="90e6b-354">0x3 - kod pitching.</span><span class="sxs-lookup"><span data-stu-id="90e6b-354">0x3 - Code pitching.</span></span><br /><br /> <span data-ttu-id="90e6b-355">0x4 - kapatma.</span><span class="sxs-lookup"><span data-stu-id="90e6b-355">0x4 - Shutdown.</span></span><br /><br /> <span data-ttu-id="90e6b-356">0x5 - Hata Ayıklayıcısı'nı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="90e6b-356">0x5 - Debugger.</span></span><br /><br /> <span data-ttu-id="90e6b-357">0x6 - çöp toplama için hazırlama.</span><span class="sxs-lookup"><span data-stu-id="90e6b-357">0x6 - Preparation for garbage collection.</span></span>|  
|<span data-ttu-id="90e6b-358">Sayı</span><span class="sxs-lookup"><span data-stu-id="90e6b-358">Count</span></span>|<span data-ttu-id="90e6b-359">Kazanma: UInt32</span><span class="sxs-lookup"><span data-stu-id="90e6b-359">win:UInt32</span></span>|<span data-ttu-id="90e6b-360">GC sayısı zaman.</span><span class="sxs-lookup"><span data-stu-id="90e6b-360">The GC count at the time.</span></span> <span data-ttu-id="90e6b-361">Genellikle, bundan sonra bir sonraki GC başlangıç olayı görür ve biz GC dizini çöp toplama sırasında arttıkça sayımına bu sayı + 1 olur.</span><span class="sxs-lookup"><span data-stu-id="90e6b-361">Usually, you would see a subsequent GC Start event after this, and its Count would be this Count + 1 as we increase the GC index during a garbage collection.</span></span>|  
|<span data-ttu-id="90e6b-362">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="90e6b-362">ClrInstanceID</span></span>|<span data-ttu-id="90e6b-363">Kazanma: UInt16</span><span class="sxs-lookup"><span data-stu-id="90e6b-363">win:UInt16</span></span>|<span data-ttu-id="90e6b-364">CLR veya CoreCLR örneği için benzersiz kimlik.</span><span class="sxs-lookup"><span data-stu-id="90e6b-364">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="90e6b-365">Başa dön</span><span class="sxs-lookup"><span data-stu-id="90e6b-365">Back to top</span></span>](#top)  
  
<a name="gcsuspendeeend_v1_event"></a>   
## <a name="gcsuspendeeendv1-event"></a><span data-ttu-id="90e6b-366">GCSuspendEEEnd_V1 Event</span><span class="sxs-lookup"><span data-stu-id="90e6b-366">GCSuspendEEEnd_V1 Event</span></span>  
 <span data-ttu-id="90e6b-367">Aşağıdaki tablo düzeyi ve anahtar sözcüğü gösterir:</span><span class="sxs-lookup"><span data-stu-id="90e6b-367">The following table shows the keyword and level:</span></span>  
  
|<span data-ttu-id="90e6b-368">Olayı için anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="90e6b-368">Keyword for raising the event</span></span>|<span data-ttu-id="90e6b-369">Düzey</span><span class="sxs-lookup"><span data-stu-id="90e6b-369">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="90e6b-370">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="90e6b-370">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="90e6b-371">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="90e6b-371">Informational (4)</span></span>|  
  
 <span data-ttu-id="90e6b-372">Aşağıdaki tablo, olay bilgileri gösterir:</span><span class="sxs-lookup"><span data-stu-id="90e6b-372">The following table shows the event information:</span></span>  
  
|<span data-ttu-id="90e6b-373">Olay</span><span class="sxs-lookup"><span data-stu-id="90e6b-373">Event</span></span>|<span data-ttu-id="90e6b-374">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="90e6b-374">Event ID</span></span>|<span data-ttu-id="90e6b-375">Ne zaman gerçekleşti</span><span class="sxs-lookup"><span data-stu-id="90e6b-375">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCSuspendEEEnd_V1`|<span data-ttu-id="90e6b-376">8</span><span class="sxs-lookup"><span data-stu-id="90e6b-376">8</span></span>|<span data-ttu-id="90e6b-377">Çöp toplama işlemi için yürütme altyapısının askıya alma sonu.</span><span class="sxs-lookup"><span data-stu-id="90e6b-377">End of suspension of the execution engine for garbage collection.</span></span>|  
  
 <span data-ttu-id="90e6b-378">Hiçbir olay verileri.</span><span class="sxs-lookup"><span data-stu-id="90e6b-378">No event data.</span></span>  
  
 [<span data-ttu-id="90e6b-379">Başa dön</span><span class="sxs-lookup"><span data-stu-id="90e6b-379">Back to top</span></span>](#top)  
  
<a name="gcallocationtick_v2_event"></a>   
## <a name="gcallocationtickv2-event"></a><span data-ttu-id="90e6b-380">GCAllocationTick_V2 olay</span><span class="sxs-lookup"><span data-stu-id="90e6b-380">GCAllocationTick_V2 Event</span></span>  
 <span data-ttu-id="90e6b-381">Aşağıdaki tabloda, düzeyi ve anahtar sözcüğü gösterir.</span><span class="sxs-lookup"><span data-stu-id="90e6b-381">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="90e6b-382">Olayı için anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="90e6b-382">Keyword for raising the event</span></span>|<span data-ttu-id="90e6b-383">Düzey</span><span class="sxs-lookup"><span data-stu-id="90e6b-383">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="90e6b-384">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="90e6b-384">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="90e6b-385">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="90e6b-385">Informational (4)</span></span>|  
  
 <span data-ttu-id="90e6b-386">Aşağıdaki tabloda, olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="90e6b-386">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="90e6b-387">Olay</span><span class="sxs-lookup"><span data-stu-id="90e6b-387">Event</span></span>|<span data-ttu-id="90e6b-388">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="90e6b-388">Event ID</span></span>|<span data-ttu-id="90e6b-389">Ne zaman gerçekleşti</span><span class="sxs-lookup"><span data-stu-id="90e6b-389">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCAllocationTick_V2`|<span data-ttu-id="90e6b-390">10</span><span class="sxs-lookup"><span data-stu-id="90e6b-390">10</span></span>|<span data-ttu-id="90e6b-391">Her seferinde yaklaşık 100 KB ayrılır.</span><span class="sxs-lookup"><span data-stu-id="90e6b-391">Each time approximately 100 KB is allocated.</span></span>|  
  
 <span data-ttu-id="90e6b-392">Aşağıdaki tabloda, olay verilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="90e6b-392">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="90e6b-393">Alan adı</span><span class="sxs-lookup"><span data-stu-id="90e6b-393">Field name</span></span>|<span data-ttu-id="90e6b-394">Veri türü</span><span class="sxs-lookup"><span data-stu-id="90e6b-394">Data type</span></span>|<span data-ttu-id="90e6b-395">Açıklama</span><span class="sxs-lookup"><span data-stu-id="90e6b-395">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="90e6b-396">AllocationAmount</span><span class="sxs-lookup"><span data-stu-id="90e6b-396">AllocationAmount</span></span>|<span data-ttu-id="90e6b-397">Kazanma: UInt32</span><span class="sxs-lookup"><span data-stu-id="90e6b-397">win:UInt32</span></span>|<span data-ttu-id="90e6b-398">Ayırma bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="90e6b-398">The allocation size, in bytes.</span></span> <span data-ttu-id="90e6b-399">Bu değer, küçük bir ULONG (4,294,967,295 bayt), uzunluğundan ayırmalar için doğru olur.</span><span class="sxs-lookup"><span data-stu-id="90e6b-399">This value is accurate for allocations that are less than the length of a ULONG (4,294,967,295 bytes).</span></span> <span data-ttu-id="90e6b-400">Ayırma büyükse, bu alan kesilmiş değer içerir.</span><span class="sxs-lookup"><span data-stu-id="90e6b-400">If the allocation is greater, this field contains a truncated value.</span></span> <span data-ttu-id="90e6b-401">Kullanım `AllocationAmount64` çok büyük ayırmalar için.</span><span class="sxs-lookup"><span data-stu-id="90e6b-401">Use `AllocationAmount64` for very large allocations.</span></span>|  
|<span data-ttu-id="90e6b-402">AllocationKind</span><span class="sxs-lookup"><span data-stu-id="90e6b-402">AllocationKind</span></span>|<span data-ttu-id="90e6b-403">Kazanma: UInt32</span><span class="sxs-lookup"><span data-stu-id="90e6b-403">win:UInt32</span></span>|<span data-ttu-id="90e6b-404">0x0 - küçük nesne ayırma (içinde küçük nesne yığını ayırma'dir).</span><span class="sxs-lookup"><span data-stu-id="90e6b-404">0x0 - Small object allocation (allocation is in small object heap).</span></span><br /><br /> <span data-ttu-id="90e6b-405">0x1 - büyük nesne ayırma (büyük nesne yığınında ayırma'dir).</span><span class="sxs-lookup"><span data-stu-id="90e6b-405">0x1 - Large object allocation (allocation is in large object heap).</span></span>|  
|<span data-ttu-id="90e6b-406">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="90e6b-406">ClrInstanceID</span></span>|<span data-ttu-id="90e6b-407">Kazanma: UInt16</span><span class="sxs-lookup"><span data-stu-id="90e6b-407">win:UInt16</span></span>|<span data-ttu-id="90e6b-408">CLR veya CoreCLR örneği için benzersiz kimlik.</span><span class="sxs-lookup"><span data-stu-id="90e6b-408">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
|<span data-ttu-id="90e6b-409">AllocationAmount64</span><span class="sxs-lookup"><span data-stu-id="90e6b-409">AllocationAmount64</span></span>|<span data-ttu-id="90e6b-410">Kazanma: UInt64</span><span class="sxs-lookup"><span data-stu-id="90e6b-410">win:UInt64</span></span>|<span data-ttu-id="90e6b-411">Ayırma bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="90e6b-411">The allocation size, in bytes.</span></span> <span data-ttu-id="90e6b-412">Bu değer çok büyük ayırmalarını doğru olur.</span><span class="sxs-lookup"><span data-stu-id="90e6b-412">This value is accurate for very large allocations.</span></span>|  
|<span data-ttu-id="90e6b-413">typeId</span><span class="sxs-lookup"><span data-stu-id="90e6b-413">TypeId</span></span>|<span data-ttu-id="90e6b-414">Kazanma: işaretçi</span><span class="sxs-lookup"><span data-stu-id="90e6b-414">win:Pointer</span></span>|<span data-ttu-id="90e6b-415">MethodTable adresi.</span><span class="sxs-lookup"><span data-stu-id="90e6b-415">The address of the MethodTable.</span></span> <span data-ttu-id="90e6b-416">Bu olayı sırasında ayrılan nesnelerin birkaç türü olduğunda, bu son (100 KB eşiği olması nedeniyle nesne) ayrılmış nesne karşılık gelen MethodTable adresidir.</span><span class="sxs-lookup"><span data-stu-id="90e6b-416">When there are several types of objects that were allocated during this event, this is the address of the MethodTable that corresponds to the last object allocated (the object that caused the 100 KB threshold to be exceeded).</span></span>|  
|<span data-ttu-id="90e6b-417">TypeName</span><span class="sxs-lookup"><span data-stu-id="90e6b-417">TypeName</span></span>|<span data-ttu-id="90e6b-418">Kazanma: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="90e6b-418">win:UnicodeString</span></span>|<span data-ttu-id="90e6b-419">Ayrılmış olan tür adı.</span><span class="sxs-lookup"><span data-stu-id="90e6b-419">The name of the type that was allocated.</span></span> <span data-ttu-id="90e6b-420">Bu olayı sırasında ayrılan nesnelerin birkaç türü olduğunda, (100 KB eşiği olması nedeniyle nesne) ayrılan son nesnenin türü budur.</span><span class="sxs-lookup"><span data-stu-id="90e6b-420">When there are several types of objects that were allocated during this event, this is the type of the last object allocated (the object that caused the 100 KB threshold to be exceeded).</span></span>|  
|<span data-ttu-id="90e6b-421">HeapIndex</span><span class="sxs-lookup"><span data-stu-id="90e6b-421">HeapIndex</span></span>|<span data-ttu-id="90e6b-422">Kazanma: UInt32</span><span class="sxs-lookup"><span data-stu-id="90e6b-422">win:UInt32</span></span>|<span data-ttu-id="90e6b-423">Nesne ayrıldığı yığında.</span><span class="sxs-lookup"><span data-stu-id="90e6b-423">The heap where the object was allocated.</span></span> <span data-ttu-id="90e6b-424">İş istasyonu çöp toplama ile çalışırken, bu değer 0 (sıfır) olur.</span><span class="sxs-lookup"><span data-stu-id="90e6b-424">This value is 0 (zero) when running with workstation garbage collection.</span></span>|  
  
 [<span data-ttu-id="90e6b-425">Başa dön</span><span class="sxs-lookup"><span data-stu-id="90e6b-425">Back to top</span></span>](#top)  
  
<a name="gcfinalizersbegin_v1_event"></a>   
## <a name="gcfinalizersbeginv1-event"></a><span data-ttu-id="90e6b-426">GCFinalizersBegin_V1 olay</span><span class="sxs-lookup"><span data-stu-id="90e6b-426">GCFinalizersBegin_V1 Event</span></span>  
 <span data-ttu-id="90e6b-427">Aşağıdaki tabloda, düzeyi ve anahtar sözcüğü gösterir.</span><span class="sxs-lookup"><span data-stu-id="90e6b-427">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="90e6b-428">Olayı için anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="90e6b-428">Keyword for raising the event</span></span>|<span data-ttu-id="90e6b-429">Düzey</span><span class="sxs-lookup"><span data-stu-id="90e6b-429">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="90e6b-430">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="90e6b-430">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="90e6b-431">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="90e6b-431">Informational (4)</span></span>|  
  
 <span data-ttu-id="90e6b-432">Aşağıdaki tabloda, olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="90e6b-432">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="90e6b-433">Olay</span><span class="sxs-lookup"><span data-stu-id="90e6b-433">Event</span></span>|<span data-ttu-id="90e6b-434">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="90e6b-434">Event ID</span></span>|<span data-ttu-id="90e6b-435">Ne zaman gerçekleşti</span><span class="sxs-lookup"><span data-stu-id="90e6b-435">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCFinalizersBegin_V1`|<span data-ttu-id="90e6b-436">14</span><span class="sxs-lookup"><span data-stu-id="90e6b-436">14</span></span>|<span data-ttu-id="90e6b-437">Sonlandırıcılar çalıştırma başlangıcı.</span><span class="sxs-lookup"><span data-stu-id="90e6b-437">The start of running finalizers.</span></span>|  
  
 <span data-ttu-id="90e6b-438">Hiçbir olay verileri.</span><span class="sxs-lookup"><span data-stu-id="90e6b-438">No event data.</span></span>  
  
 [<span data-ttu-id="90e6b-439">Başa dön</span><span class="sxs-lookup"><span data-stu-id="90e6b-439">Back to top</span></span>](#top)  
  
<a name="gcfinalizersend_v1_event"></a>   
## <a name="gcfinalizersendv1-event"></a><span data-ttu-id="90e6b-440">GCFinalizersEnd_V1 olay</span><span class="sxs-lookup"><span data-stu-id="90e6b-440">GCFinalizersEnd_V1 Event</span></span>  
 <span data-ttu-id="90e6b-441">Aşağıdaki tabloda, düzeyi ve anahtar sözcüğü gösterir.</span><span class="sxs-lookup"><span data-stu-id="90e6b-441">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="90e6b-442">Olayı için anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="90e6b-442">Keyword for raising the event</span></span>|<span data-ttu-id="90e6b-443">Düzey</span><span class="sxs-lookup"><span data-stu-id="90e6b-443">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="90e6b-444">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="90e6b-444">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="90e6b-445">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="90e6b-445">Informational (4)</span></span>|  
  
 <span data-ttu-id="90e6b-446">Aşağıdaki tabloda, olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="90e6b-446">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="90e6b-447">Olay</span><span class="sxs-lookup"><span data-stu-id="90e6b-447">Event</span></span>|<span data-ttu-id="90e6b-448">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="90e6b-448">Event ID</span></span>|<span data-ttu-id="90e6b-449">Ne zaman gerçekleşti</span><span class="sxs-lookup"><span data-stu-id="90e6b-449">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCFinalizersEnd_V1`|<span data-ttu-id="90e6b-450">13</span><span class="sxs-lookup"><span data-stu-id="90e6b-450">13</span></span>|<span data-ttu-id="90e6b-451">Sonlandırıcılar çalıştırma bitiş olayı.</span><span class="sxs-lookup"><span data-stu-id="90e6b-451">The end of running finalizers.</span></span>|  
  
 <span data-ttu-id="90e6b-452">Aşağıdaki tabloda, olay verilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="90e6b-452">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="90e6b-453">Alan adı</span><span class="sxs-lookup"><span data-stu-id="90e6b-453">Field name</span></span>|<span data-ttu-id="90e6b-454">Veri türü</span><span class="sxs-lookup"><span data-stu-id="90e6b-454">Data type</span></span>|<span data-ttu-id="90e6b-455">Açıklama</span><span class="sxs-lookup"><span data-stu-id="90e6b-455">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="90e6b-456">Sayı</span><span class="sxs-lookup"><span data-stu-id="90e6b-456">Count</span></span>|<span data-ttu-id="90e6b-457">Kazanma: UInt32</span><span class="sxs-lookup"><span data-stu-id="90e6b-457">win:UInt32</span></span>|<span data-ttu-id="90e6b-458">Çalıştırılan bir sonlandırıcı sayısı.</span><span class="sxs-lookup"><span data-stu-id="90e6b-458">The number of finalizers that were run.</span></span>|  
|<span data-ttu-id="90e6b-459">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="90e6b-459">ClrInstanceID</span></span>|<span data-ttu-id="90e6b-460">Kazanma: UInt16</span><span class="sxs-lookup"><span data-stu-id="90e6b-460">win:UInt16</span></span>|<span data-ttu-id="90e6b-461">CLR veya CoreCLR örneği için benzersiz kimlik.</span><span class="sxs-lookup"><span data-stu-id="90e6b-461">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="90e6b-462">Başa dön</span><span class="sxs-lookup"><span data-stu-id="90e6b-462">Back to top</span></span>](#top)  
  
<a name="gccreateconcurrentthread_v1_event"></a>   
## <a name="gccreateconcurrentthreadv1-event"></a><span data-ttu-id="90e6b-463">GCCreateConcurrentThread_V1 olay</span><span class="sxs-lookup"><span data-stu-id="90e6b-463">GCCreateConcurrentThread_V1 Event</span></span>  
 <span data-ttu-id="90e6b-464">Aşağıdaki tabloda, düzeyi ve anahtar sözcüğü gösterir.</span><span class="sxs-lookup"><span data-stu-id="90e6b-464">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="90e6b-465">Olayı için anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="90e6b-465">Keyword for raising the event</span></span>|<span data-ttu-id="90e6b-466">Düzey</span><span class="sxs-lookup"><span data-stu-id="90e6b-466">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="90e6b-467">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="90e6b-467">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="90e6b-468">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="90e6b-468">Informational (4)</span></span>|  
|<span data-ttu-id="90e6b-469">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="90e6b-469">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="90e6b-470">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="90e6b-470">Informational (4)</span></span>|  
  
 <span data-ttu-id="90e6b-471">Aşağıdaki tabloda, olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="90e6b-471">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="90e6b-472">Olay</span><span class="sxs-lookup"><span data-stu-id="90e6b-472">Event</span></span>|<span data-ttu-id="90e6b-473">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="90e6b-473">Event ID</span></span>|<span data-ttu-id="90e6b-474">Ne zaman gerçekleşti</span><span class="sxs-lookup"><span data-stu-id="90e6b-474">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCCreateConcurrentThread_V1`|<span data-ttu-id="90e6b-475">11</span><span class="sxs-lookup"><span data-stu-id="90e6b-475">11</span></span>|<span data-ttu-id="90e6b-476">Eş zamanlı çöp toplama iş parçacığı oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="90e6b-476">Concurrent garbage collection thread was created.</span></span>|  
  
 <span data-ttu-id="90e6b-477">Hiçbir olay verileri.</span><span class="sxs-lookup"><span data-stu-id="90e6b-477">No event data.</span></span>  
  
 [<span data-ttu-id="90e6b-478">Başa dön</span><span class="sxs-lookup"><span data-stu-id="90e6b-478">Back to top</span></span>](#top)  
  
<a name="gcterminateconcurrentthread_v1_event"></a>   
## <a name="gcterminateconcurrentthreadv1-event"></a><span data-ttu-id="90e6b-479">GCTerminateConcurrentThread_V1 olay</span><span class="sxs-lookup"><span data-stu-id="90e6b-479">GCTerminateConcurrentThread_V1 Event</span></span>  
 <span data-ttu-id="90e6b-480">Aşağıdaki tabloda, düzeyi ve anahtar sözcüğü gösterir.</span><span class="sxs-lookup"><span data-stu-id="90e6b-480">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="90e6b-481">Olayı için anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="90e6b-481">Keyword for raising the event</span></span>|<span data-ttu-id="90e6b-482">Düzey</span><span class="sxs-lookup"><span data-stu-id="90e6b-482">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="90e6b-483">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="90e6b-483">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="90e6b-484">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="90e6b-484">Informational (4)</span></span>|  
|<span data-ttu-id="90e6b-485">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="90e6b-485">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="90e6b-486">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="90e6b-486">Informational (4)</span></span>|  
  
 <span data-ttu-id="90e6b-487">Aşağıdaki tabloda, olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="90e6b-487">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="90e6b-488">Olay</span><span class="sxs-lookup"><span data-stu-id="90e6b-488">Event</span></span>|<span data-ttu-id="90e6b-489">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="90e6b-489">Event ID</span></span>|<span data-ttu-id="90e6b-490">Ne zaman gerçekleşti</span><span class="sxs-lookup"><span data-stu-id="90e6b-490">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCTerminateConcurrentThread_V1`|<span data-ttu-id="90e6b-491">12</span><span class="sxs-lookup"><span data-stu-id="90e6b-491">12</span></span>|<span data-ttu-id="90e6b-492">Eş zamanlı çöp toplama iş parçacığı sonlandırıldı.</span><span class="sxs-lookup"><span data-stu-id="90e6b-492">Concurrent garbage collection thread was terminated.</span></span>|  
  
 <span data-ttu-id="90e6b-493">Hiçbir olay verileri.</span><span class="sxs-lookup"><span data-stu-id="90e6b-493">No event data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90e6b-494">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="90e6b-494">See also</span></span>

- [<span data-ttu-id="90e6b-495">CLR ETW Olayları</span><span class="sxs-lookup"><span data-stu-id="90e6b-495">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
