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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61722945"
---
# <a name="garbage-collection-etw-events"></a><span data-ttu-id="77739-102">Çöp Toplama ETW Olayları</span><span class="sxs-lookup"><span data-stu-id="77739-102">Garbage Collection ETW Events</span></span>
<a name="top"></a> <span data-ttu-id="77739-103">Bu olaylar, çöp toplama hakkında bilgi toplayın.</span><span class="sxs-lookup"><span data-stu-id="77739-103">These events collect information pertaining to garbage collection.</span></span> <span data-ttu-id="77739-104">Bunlar Tanılama'da yardımcı olur ve hata ayıklama, çöp toplama kaç kez belirleme de dahil olmak üzere gerçekleştirildiyse, ne kadar bellek çöp toplama ve benzeri sırasında bırakılmış.</span><span class="sxs-lookup"><span data-stu-id="77739-104">They help in diagnostics and debugging, including determining how many times garbage collection was performed, how much memory was freed during garbage collection, and so on.</span></span>  
  
 <span data-ttu-id="77739-105">Bu kategori aşağıdaki olaylar oluşur:</span><span class="sxs-lookup"><span data-stu-id="77739-105">This category consists of the following events:</span></span>  
  
- [<span data-ttu-id="77739-106">GCStart_V1 olay</span><span class="sxs-lookup"><span data-stu-id="77739-106">GCStart_V1 Event</span></span>](#gcstart_v1_event)  
  
- [<span data-ttu-id="77739-107">GCEnd_V1 Event</span><span class="sxs-lookup"><span data-stu-id="77739-107">GCEnd_V1 Event</span></span>](#gcend_v1_event)  
  
- [<span data-ttu-id="77739-108">GCHeapStats_V1 olay</span><span class="sxs-lookup"><span data-stu-id="77739-108">GCHeapStats_V1 Event</span></span>](#gcheapstats_v1_event)  
  
- [<span data-ttu-id="77739-109">GCCreateSegment_V1 Event</span><span class="sxs-lookup"><span data-stu-id="77739-109">GCCreateSegment_V1 Event</span></span>](#gccreatesegment_v1_event)  
  
- [<span data-ttu-id="77739-110">GCFreeSegment_V1 Event</span><span class="sxs-lookup"><span data-stu-id="77739-110">GCFreeSegment_V1 Event</span></span>](#gcfreesegment_v1_event)  
  
- [<span data-ttu-id="77739-111">GCRestartEEBegin_V1 olay</span><span class="sxs-lookup"><span data-stu-id="77739-111">GCRestartEEBegin_V1 Event</span></span>](#gcrestarteebegin_v1_event)  
  
- [<span data-ttu-id="77739-112">GCRestartEEEnd_V1 olay</span><span class="sxs-lookup"><span data-stu-id="77739-112">GCRestartEEEnd_V1 Event</span></span>](#gcrestarteeend_v1_event)  
  
- [<span data-ttu-id="77739-113">GCSuspendEE_V1 Event</span><span class="sxs-lookup"><span data-stu-id="77739-113">GCSuspendEE_V1 Event</span></span>](#gcsuspendee_v1_event)  
  
- [<span data-ttu-id="77739-114">GCSuspendEEEnd_V1 Event</span><span class="sxs-lookup"><span data-stu-id="77739-114">GCSuspendEEEnd_V1 Event</span></span>](#gcsuspendeeend_v1_event)  
  
- [<span data-ttu-id="77739-115">GCAllocationTick_V2 olay</span><span class="sxs-lookup"><span data-stu-id="77739-115">GCAllocationTick_V2 Event</span></span>](#gcallocationtick_v2_event)  
  
- [<span data-ttu-id="77739-116">GCFinalizersBegin_V1 Event</span><span class="sxs-lookup"><span data-stu-id="77739-116">GCFinalizersBegin_V1 Event</span></span>](#gcfinalizersbegin_v1_event)  
  
- [<span data-ttu-id="77739-117">GCFinalizersEnd_V1 olay</span><span class="sxs-lookup"><span data-stu-id="77739-117">GCFinalizersEnd_V1 Event</span></span>](#gcfinalizersend_v1_event)  
  
- [<span data-ttu-id="77739-118">GCCreateConcurrentThread_V1 olay</span><span class="sxs-lookup"><span data-stu-id="77739-118">GCCreateConcurrentThread_V1 Event</span></span>](#gccreateconcurrentthread_v1_event)  
  
- [<span data-ttu-id="77739-119">GCTerminateConcurrentThread_V1 olay</span><span class="sxs-lookup"><span data-stu-id="77739-119">GCTerminateConcurrentThread_V1 Event</span></span>](#gcterminateconcurrentthread_v1_event)  
  
<a name="gcstart_v1_event"></a>   
## <a name="gcstartv1-event"></a><span data-ttu-id="77739-120">GCStart_V1 olay</span><span class="sxs-lookup"><span data-stu-id="77739-120">GCStart_V1 Event</span></span>  
 <span data-ttu-id="77739-121">Aşağıdaki tabloda, düzeyi ve anahtar sözcüğü gösterir.</span><span class="sxs-lookup"><span data-stu-id="77739-121">The following table shows the keyword and level.</span></span> <span data-ttu-id="77739-122">(Daha fazla bilgi için [CLR ETW anahtar sözcükleri ve Düzeyler](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="77739-122">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="77739-123">Olayı için anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="77739-123">Keyword for raising the event</span></span>|<span data-ttu-id="77739-124">Düzey</span><span class="sxs-lookup"><span data-stu-id="77739-124">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="77739-125">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="77739-125">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="77739-126">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="77739-126">Informational (4)</span></span>|  
  
 <span data-ttu-id="77739-127">Aşağıdaki tabloda, olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="77739-127">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="77739-128">Olay</span><span class="sxs-lookup"><span data-stu-id="77739-128">Event</span></span>|<span data-ttu-id="77739-129">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="77739-129">Event ID</span></span>|<span data-ttu-id="77739-130">Ne zaman gerçekleşti</span><span class="sxs-lookup"><span data-stu-id="77739-130">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCStart_V1`|<span data-ttu-id="77739-131">1.</span><span class="sxs-lookup"><span data-stu-id="77739-131">1</span></span>|<span data-ttu-id="77739-132">Bir çöp toplama başlatıldı.</span><span class="sxs-lookup"><span data-stu-id="77739-132">A garbage collection has started.</span></span>|  
  
 <span data-ttu-id="77739-133">Aşağıdaki tabloda, olay verilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="77739-133">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="77739-134">Alan adı</span><span class="sxs-lookup"><span data-stu-id="77739-134">Field name</span></span>|<span data-ttu-id="77739-135">Veri türü</span><span class="sxs-lookup"><span data-stu-id="77739-135">Data type</span></span>|<span data-ttu-id="77739-136">Açıklama</span><span class="sxs-lookup"><span data-stu-id="77739-136">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="77739-137">Count</span><span class="sxs-lookup"><span data-stu-id="77739-137">Count</span></span>|<span data-ttu-id="77739-138">Kazanma: UInt32</span><span class="sxs-lookup"><span data-stu-id="77739-138">win:UInt32</span></span>|<span data-ttu-id="77739-139">*n*th çöp toplama.</span><span class="sxs-lookup"><span data-stu-id="77739-139">The *n*th garbage collection.</span></span>|  
|<span data-ttu-id="77739-140">Derinliği</span><span class="sxs-lookup"><span data-stu-id="77739-140">Depth</span></span>|<span data-ttu-id="77739-141">Kazanma: UInt32</span><span class="sxs-lookup"><span data-stu-id="77739-141">win:UInt32</span></span>|<span data-ttu-id="77739-142">Toplanmakta olan oluşturma.</span><span class="sxs-lookup"><span data-stu-id="77739-142">The generation that is being collected.</span></span>|  
|<span data-ttu-id="77739-143">Neden</span><span class="sxs-lookup"><span data-stu-id="77739-143">Reason</span></span>|<span data-ttu-id="77739-144">Kazanma: UInt32</span><span class="sxs-lookup"><span data-stu-id="77739-144">win:UInt32</span></span>|<span data-ttu-id="77739-145">Çöp toplama işlemine neden tetiklendi:</span><span class="sxs-lookup"><span data-stu-id="77739-145">Why the garbage collection was triggered:</span></span><br /><br /> <span data-ttu-id="77739-146">0x0 - küçük nesne yığını ayırması.</span><span class="sxs-lookup"><span data-stu-id="77739-146">0x0 - Small object heap allocation.</span></span><br /><br /> <span data-ttu-id="77739-147">0x1 - başlattı.</span><span class="sxs-lookup"><span data-stu-id="77739-147">0x1 - Induced.</span></span><br /><br /> <span data-ttu-id="77739-148">0x2 - bellek yetersiz.</span><span class="sxs-lookup"><span data-stu-id="77739-148">0x2 - Low memory.</span></span><br /><br /> <span data-ttu-id="77739-149">0x3 - boş.</span><span class="sxs-lookup"><span data-stu-id="77739-149">0x3 - Empty.</span></span><br /><br /> <span data-ttu-id="77739-150">0x4 - büyük nesne yığını ayırması.</span><span class="sxs-lookup"><span data-stu-id="77739-150">0x4 - Large object heap allocation.</span></span><br /><br /> <span data-ttu-id="77739-151">0x5 - yetersiz alan (küçük nesne yığını için).</span><span class="sxs-lookup"><span data-stu-id="77739-151">0x5 - Out of space (for small object heap).</span></span><br /><br /> <span data-ttu-id="77739-152">0x6 - yetersiz alan (büyük nesne yığını için).</span><span class="sxs-lookup"><span data-stu-id="77739-152">0x6 - Out of space (for large object heap).</span></span><br /><br /> <span data-ttu-id="77739-153">0x7 - başlattığı ancak engelleme olarak zorunlu değildir.</span><span class="sxs-lookup"><span data-stu-id="77739-153">0x7 - Induced but not forced as blocking.</span></span>|  
|<span data-ttu-id="77739-154">Tür</span><span class="sxs-lookup"><span data-stu-id="77739-154">Type</span></span>|<span data-ttu-id="77739-155">Kazanma: UInt32</span><span class="sxs-lookup"><span data-stu-id="77739-155">win:UInt32</span></span>|<span data-ttu-id="77739-156">0x0 - arka plan atık toplamanın dışında atık toplamayı engelleme oluştu.</span><span class="sxs-lookup"><span data-stu-id="77739-156">0x0 - Blocking garbage collection occurred outside background garbage collection.</span></span><br /><br /> <span data-ttu-id="77739-157">0x1 - arka plan çöp toplama.</span><span class="sxs-lookup"><span data-stu-id="77739-157">0x1 - Background garbage collection.</span></span><br /><br /> <span data-ttu-id="77739-158">0x2 - arka plan çöp toplama sırasında atık toplamayı engelleme oluştu.</span><span class="sxs-lookup"><span data-stu-id="77739-158">0x2 - Blocking garbage collection occurred during background garbage collection.</span></span>|  
|<span data-ttu-id="77739-159">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="77739-159">ClrInstanceID</span></span>|<span data-ttu-id="77739-160">Kazanma: UInt16</span><span class="sxs-lookup"><span data-stu-id="77739-160">win:UInt16</span></span>|<span data-ttu-id="77739-161">CLR veya CoreCLR örneği için benzersiz kimlik.</span><span class="sxs-lookup"><span data-stu-id="77739-161">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="77739-162">Başa dön</span><span class="sxs-lookup"><span data-stu-id="77739-162">Back to top</span></span>](#top)  
  
<a name="gcend_v1_event"></a>   
## <a name="gcendv1-event"></a><span data-ttu-id="77739-163">GCEnd_V1 olay</span><span class="sxs-lookup"><span data-stu-id="77739-163">GCEnd_V1 Event</span></span>  
 <span data-ttu-id="77739-164">Aşağıdaki tabloda, düzeyi ve anahtar sözcüğü gösterir.</span><span class="sxs-lookup"><span data-stu-id="77739-164">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="77739-165">Olayı için anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="77739-165">Keyword for raising the event</span></span>|<span data-ttu-id="77739-166">Düzey</span><span class="sxs-lookup"><span data-stu-id="77739-166">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="77739-167">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="77739-167">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="77739-168">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="77739-168">Informational (4)</span></span>|  
  
 <span data-ttu-id="77739-169">Aşağıdaki tabloda, olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="77739-169">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="77739-170">Olay</span><span class="sxs-lookup"><span data-stu-id="77739-170">Event</span></span>|<span data-ttu-id="77739-171">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="77739-171">Event ID</span></span>|<span data-ttu-id="77739-172">Ne zaman gerçekleşti</span><span class="sxs-lookup"><span data-stu-id="77739-172">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCEnd_V1`|<span data-ttu-id="77739-173">2</span><span class="sxs-lookup"><span data-stu-id="77739-173">2</span></span>|<span data-ttu-id="77739-174">Çöp toplama sona erdi.</span><span class="sxs-lookup"><span data-stu-id="77739-174">The garbage collection has ended.</span></span>|  
  
 <span data-ttu-id="77739-175">Aşağıdaki tabloda, olay verilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="77739-175">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="77739-176">Alan adı</span><span class="sxs-lookup"><span data-stu-id="77739-176">Field name</span></span>|<span data-ttu-id="77739-177">Veri türü</span><span class="sxs-lookup"><span data-stu-id="77739-177">Data type</span></span>|<span data-ttu-id="77739-178">Açıklama</span><span class="sxs-lookup"><span data-stu-id="77739-178">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="77739-179">Count</span><span class="sxs-lookup"><span data-stu-id="77739-179">Count</span></span>|<span data-ttu-id="77739-180">Kazanma: UInt32</span><span class="sxs-lookup"><span data-stu-id="77739-180">win:UInt32</span></span>|<span data-ttu-id="77739-181">*n*th çöp toplama.</span><span class="sxs-lookup"><span data-stu-id="77739-181">The *n*th garbage collection.</span></span>|  
|<span data-ttu-id="77739-182">Derinliği</span><span class="sxs-lookup"><span data-stu-id="77739-182">Depth</span></span>|<span data-ttu-id="77739-183">Kazanma: UInt32</span><span class="sxs-lookup"><span data-stu-id="77739-183">win:UInt32</span></span>|<span data-ttu-id="77739-184">Toplanan oluşturma.</span><span class="sxs-lookup"><span data-stu-id="77739-184">The generation that was collected.</span></span>|  
|<span data-ttu-id="77739-185">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="77739-185">ClrInstanceID</span></span>|<span data-ttu-id="77739-186">Kazanma: UInt16</span><span class="sxs-lookup"><span data-stu-id="77739-186">win:UInt16</span></span>|<span data-ttu-id="77739-187">CLR veya CoreCLR örneği için benzersiz kimlik.</span><span class="sxs-lookup"><span data-stu-id="77739-187">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="77739-188">Başa dön</span><span class="sxs-lookup"><span data-stu-id="77739-188">Back to top</span></span>](#top)  
  
<a name="gcheapstats_v1_event"></a>   
## <a name="gcheapstatsv1-event"></a><span data-ttu-id="77739-189">GCHeapStats_V1 olay</span><span class="sxs-lookup"><span data-stu-id="77739-189">GCHeapStats_V1 Event</span></span>  
 <span data-ttu-id="77739-190">Aşağıdaki tabloda, düzeyi ve anahtar sözcüğü gösterir.</span><span class="sxs-lookup"><span data-stu-id="77739-190">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="77739-191">Olayı için anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="77739-191">Keyword for raising the event</span></span>|<span data-ttu-id="77739-192">Düzey</span><span class="sxs-lookup"><span data-stu-id="77739-192">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="77739-193">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="77739-193">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="77739-194">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="77739-194">Informational (4)</span></span>|  
  
 <span data-ttu-id="77739-195">Aşağıdaki tabloda, olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="77739-195">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="77739-196">Olay</span><span class="sxs-lookup"><span data-stu-id="77739-196">Event</span></span>|<span data-ttu-id="77739-197">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="77739-197">Event ID</span></span>|<span data-ttu-id="77739-198">Açıklama</span><span class="sxs-lookup"><span data-stu-id="77739-198">Description</span></span>|  
|-----------|--------------|-----------------|  
|`GCHeapStats_V1`|<span data-ttu-id="77739-199">4</span><span class="sxs-lookup"><span data-stu-id="77739-199">4</span></span>|<span data-ttu-id="77739-200">Her çöp toplama sonunda yığında istatistiklerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="77739-200">Shows the heap statistics at the end of each garbage collection.</span></span>|  
  
 <span data-ttu-id="77739-201">Aşağıdaki tabloda, olay verilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="77739-201">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="77739-202">Alan adı</span><span class="sxs-lookup"><span data-stu-id="77739-202">Field name</span></span>|<span data-ttu-id="77739-203">Veri türü</span><span class="sxs-lookup"><span data-stu-id="77739-203">Data type</span></span>|<span data-ttu-id="77739-204">Açıklama</span><span class="sxs-lookup"><span data-stu-id="77739-204">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="77739-205">GenerationSize0</span><span class="sxs-lookup"><span data-stu-id="77739-205">GenerationSize0</span></span>|<span data-ttu-id="77739-206">Kazanma: UInt64</span><span class="sxs-lookup"><span data-stu-id="77739-206">win:UInt64</span></span>|<span data-ttu-id="77739-207">Nesil 0 belleğin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="77739-207">The size, in bytes, of generation 0 memory.</span></span>|  
|<span data-ttu-id="77739-208">TotalPromotedSize0</span><span class="sxs-lookup"><span data-stu-id="77739-208">TotalPromotedSize0</span></span>|<span data-ttu-id="77739-209">Kazanma: UInt64</span><span class="sxs-lookup"><span data-stu-id="77739-209">win:UInt64</span></span>|<span data-ttu-id="77739-210">1. nesil için nesil 0 ' yükseltilen bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="77739-210">The number of bytes that are promoted from generation 0 to generation 1.</span></span>|  
|<span data-ttu-id="77739-211">GenerationSize1</span><span class="sxs-lookup"><span data-stu-id="77739-211">GenerationSize1</span></span>|<span data-ttu-id="77739-212">Kazanma: UInt64</span><span class="sxs-lookup"><span data-stu-id="77739-212">win:UInt64</span></span>|<span data-ttu-id="77739-213">1. kuşak belleğin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="77739-213">The size, in bytes, of generation 1 memory.</span></span>|  
|<span data-ttu-id="77739-214">TotalPromotedSize1</span><span class="sxs-lookup"><span data-stu-id="77739-214">TotalPromotedSize1</span></span>|<span data-ttu-id="77739-215">Kazanma: UInt64</span><span class="sxs-lookup"><span data-stu-id="77739-215">win:UInt64</span></span>|<span data-ttu-id="77739-216">Nesil 1 ' 2 yeni nesle yükseltilir bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="77739-216">The number of bytes that are promoted from generation 1 to generation 2.</span></span>|  
|<span data-ttu-id="77739-217">GenerationSize2</span><span class="sxs-lookup"><span data-stu-id="77739-217">GenerationSize2</span></span>|<span data-ttu-id="77739-218">Kazanma: UInt64</span><span class="sxs-lookup"><span data-stu-id="77739-218">win:UInt64</span></span>|<span data-ttu-id="77739-219">2. nesil belleğin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="77739-219">The size, in bytes, of generation 2 memory.</span></span>|  
|<span data-ttu-id="77739-220">TotalPromotedSize2</span><span class="sxs-lookup"><span data-stu-id="77739-220">TotalPromotedSize2</span></span>|<span data-ttu-id="77739-221">Kazanma: UInt64</span><span class="sxs-lookup"><span data-stu-id="77739-221">win:UInt64</span></span>|<span data-ttu-id="77739-222">2. nesil son toplamadan sonra içinde kurtulan bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="77739-222">The number of bytes that survived in generation 2 after the last collection.</span></span>|  
|<span data-ttu-id="77739-223">GenerationSize3</span><span class="sxs-lookup"><span data-stu-id="77739-223">GenerationSize3</span></span>|<span data-ttu-id="77739-224">Kazanma: UInt64</span><span class="sxs-lookup"><span data-stu-id="77739-224">win:UInt64</span></span>|<span data-ttu-id="77739-225">Büyük nesne yığını bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="77739-225">The size, in bytes, of the large object heap.</span></span>|  
|<span data-ttu-id="77739-226">TotalPromotedSize3</span><span class="sxs-lookup"><span data-stu-id="77739-226">TotalPromotedSize3</span></span>|<span data-ttu-id="77739-227">Kazanma: UInt64</span><span class="sxs-lookup"><span data-stu-id="77739-227">win:UInt64</span></span>|<span data-ttu-id="77739-228">Büyük nesne yığınında sonra son toplamadan kurtulan bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="77739-228">The number of bytes that survived in the large object heap after the last collection.</span></span>|  
|<span data-ttu-id="77739-229">FinalizationPromotedSize</span><span class="sxs-lookup"><span data-stu-id="77739-229">FinalizationPromotedSize</span></span>|<span data-ttu-id="77739-230">Kazanma: UInt64</span><span class="sxs-lookup"><span data-stu-id="77739-230">win:UInt64</span></span>|<span data-ttu-id="77739-231">Baytlarında sonlandırma için hazır olan nesneleri toplam boyutu.</span><span class="sxs-lookup"><span data-stu-id="77739-231">The total size, in bytes, of the objects that are ready for finalization.</span></span>|  
|<span data-ttu-id="77739-232">FinalizationPromotedCount</span><span class="sxs-lookup"><span data-stu-id="77739-232">FinalizationPromotedCount</span></span>|<span data-ttu-id="77739-233">Kazanma: UInt64</span><span class="sxs-lookup"><span data-stu-id="77739-233">win:UInt64</span></span>|<span data-ttu-id="77739-234">Sonlandırma için hazır olan nesnelerinin sayısı.</span><span class="sxs-lookup"><span data-stu-id="77739-234">The number of objects that are ready for finalization.</span></span>|  
|<span data-ttu-id="77739-235">PinnedObjectCount</span><span class="sxs-lookup"><span data-stu-id="77739-235">PinnedObjectCount</span></span>|<span data-ttu-id="77739-236">Kazanma: UInt32</span><span class="sxs-lookup"><span data-stu-id="77739-236">win:UInt32</span></span>|<span data-ttu-id="77739-237">Sabitlenen (taşınamayan) nesne sayısı.</span><span class="sxs-lookup"><span data-stu-id="77739-237">The number of pinned (unmovable) objects.</span></span>|  
|<span data-ttu-id="77739-238">SinkBlockCount</span><span class="sxs-lookup"><span data-stu-id="77739-238">SinkBlockCount</span></span>|<span data-ttu-id="77739-239">Kazanma: UInt32</span><span class="sxs-lookup"><span data-stu-id="77739-239">win:UInt32</span></span>|<span data-ttu-id="77739-240">Kullanımdaki eşitleme blokların sayısı.</span><span class="sxs-lookup"><span data-stu-id="77739-240">The number of synchronization blocks in use.</span></span>|  
|<span data-ttu-id="77739-241">GCHandleCount</span><span class="sxs-lookup"><span data-stu-id="77739-241">GCHandleCount</span></span>|<span data-ttu-id="77739-242">Kazanma: UInt32</span><span class="sxs-lookup"><span data-stu-id="77739-242">win:UInt32</span></span>|<span data-ttu-id="77739-243">Kullanımda olan çöp toplama sayısı.</span><span class="sxs-lookup"><span data-stu-id="77739-243">The number of garbage collection handles in use.</span></span>|  
|<span data-ttu-id="77739-244">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="77739-244">ClrInstanceID</span></span>|<span data-ttu-id="77739-245">Kazanma: UInt16</span><span class="sxs-lookup"><span data-stu-id="77739-245">win:UInt16</span></span>|<span data-ttu-id="77739-246">CLR veya CoreCLR örneği için benzersiz kimlik.</span><span class="sxs-lookup"><span data-stu-id="77739-246">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="77739-247">Başa dön</span><span class="sxs-lookup"><span data-stu-id="77739-247">Back to top</span></span>](#top)  
  
<a name="gccreatesegment_v1_event"></a>   
## <a name="gccreatesegmentv1-event"></a><span data-ttu-id="77739-248">GCCreateSegment_V1 Event</span><span class="sxs-lookup"><span data-stu-id="77739-248">GCCreateSegment_V1 Event</span></span>  
 <span data-ttu-id="77739-249">Aşağıdaki tabloda, düzeyi ve anahtar sözcüğü gösterir.</span><span class="sxs-lookup"><span data-stu-id="77739-249">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="77739-250">Olayı için anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="77739-250">Keyword for raising the event</span></span>|<span data-ttu-id="77739-251">Düzey</span><span class="sxs-lookup"><span data-stu-id="77739-251">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="77739-252">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="77739-252">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="77739-253">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="77739-253">Informational (4)</span></span>|  
  
 <span data-ttu-id="77739-254">Aşağıdaki tabloda, olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="77739-254">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="77739-255">Olay</span><span class="sxs-lookup"><span data-stu-id="77739-255">Event</span></span>|<span data-ttu-id="77739-256">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="77739-256">Event ID</span></span>|<span data-ttu-id="77739-257">Ne zaman gerçekleşti</span><span class="sxs-lookup"><span data-stu-id="77739-257">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCCreateSegment_V1`|<span data-ttu-id="77739-258">5</span><span class="sxs-lookup"><span data-stu-id="77739-258">5</span></span>|<span data-ttu-id="77739-259">Yeni bir çöp toplama segment oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="77739-259">A new garbage collection segment has been created.</span></span> <span data-ttu-id="77739-260">Ayrıca, zaten çalışan bir işlemde izleme etkin olduğunda, var olan her segment için bu olay oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="77739-260">In addition, when tracing is enabled on a process that is already running, this event is raised for each existing segment.</span></span>|  
  
 <span data-ttu-id="77739-261">Aşağıdaki tabloda, olay verilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="77739-261">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="77739-262">Alan adı</span><span class="sxs-lookup"><span data-stu-id="77739-262">Field name</span></span>|<span data-ttu-id="77739-263">Veri türü</span><span class="sxs-lookup"><span data-stu-id="77739-263">Data type</span></span>|<span data-ttu-id="77739-264">Açıklama</span><span class="sxs-lookup"><span data-stu-id="77739-264">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="77739-265">Adres</span><span class="sxs-lookup"><span data-stu-id="77739-265">Address</span></span>|<span data-ttu-id="77739-266">Kazanma: UInt64</span><span class="sxs-lookup"><span data-stu-id="77739-266">win:UInt64</span></span>|<span data-ttu-id="77739-267">Segment adresi.</span><span class="sxs-lookup"><span data-stu-id="77739-267">The address of the segment.</span></span>|  
|<span data-ttu-id="77739-268">Boyut</span><span class="sxs-lookup"><span data-stu-id="77739-268">Size</span></span>|<span data-ttu-id="77739-269">Kazanma: UInt64</span><span class="sxs-lookup"><span data-stu-id="77739-269">win:UInt64</span></span>|<span data-ttu-id="77739-270">Kesim boyutu.</span><span class="sxs-lookup"><span data-stu-id="77739-270">The size of the segment.</span></span>|  
|<span data-ttu-id="77739-271">Tür</span><span class="sxs-lookup"><span data-stu-id="77739-271">Type</span></span>|<span data-ttu-id="77739-272">Kazanma: UInt32</span><span class="sxs-lookup"><span data-stu-id="77739-272">win:UInt32</span></span>|<span data-ttu-id="77739-273">0x0 - küçük nesne yığını.</span><span class="sxs-lookup"><span data-stu-id="77739-273">0x0 - Small object heap.</span></span><br /><br /> <span data-ttu-id="77739-274">0x1 - büyük nesne yığını.</span><span class="sxs-lookup"><span data-stu-id="77739-274">0x1 - Large object heap.</span></span><br /><br /> <span data-ttu-id="77739-275">0x2 - yığın salt okunur.</span><span class="sxs-lookup"><span data-stu-id="77739-275">0x2 - Read-only heap.</span></span>|  
|<span data-ttu-id="77739-276">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="77739-276">ClrInstanceID</span></span>|<span data-ttu-id="77739-277">Kazanma: UInt16</span><span class="sxs-lookup"><span data-stu-id="77739-277">win:UInt16</span></span>|<span data-ttu-id="77739-278">CLR veya CoreCLR örneği için benzersiz kimlik.</span><span class="sxs-lookup"><span data-stu-id="77739-278">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 <span data-ttu-id="77739-279">Boyutu çöp toplayıcısının ayrılan parçaları uygulama özgü olan ve düzenli güncelleştirmeleri dahil olmak üzere dilediğiniz zaman değiştirilebilir unutmayın.</span><span class="sxs-lookup"><span data-stu-id="77739-279">Note that the size of segments allocated by the garbage collector is implementation-specific and is subject to change at any time, including in periodic updates.</span></span> <span data-ttu-id="77739-280">Uygulamanız hiçbir zaman hakkında varsayımlar veya belirli bir segment boyutuna göre değişir ve segment ayırma için kullanılabilir bellek miktarını yapılandırmak için denemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="77739-280">Your app should never make assumptions about or depend on a particular segment size, nor should it attempt to configure the amount of memory available for segment allocations.</span></span>  
  
 [<span data-ttu-id="77739-281">Başa dön</span><span class="sxs-lookup"><span data-stu-id="77739-281">Back to top</span></span>](#top)  
  
<a name="gcfreesegment_v1_event"></a>   
## <a name="gcfreesegmentv1-event"></a><span data-ttu-id="77739-282">GCFreeSegment_V1 Event</span><span class="sxs-lookup"><span data-stu-id="77739-282">GCFreeSegment_V1 Event</span></span>  
 <span data-ttu-id="77739-283">Aşağıdaki tabloda, düzeyi ve anahtar sözcüğü gösterir.</span><span class="sxs-lookup"><span data-stu-id="77739-283">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="77739-284">Olayı için anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="77739-284">Keyword for raising the event</span></span>|<span data-ttu-id="77739-285">Düzey</span><span class="sxs-lookup"><span data-stu-id="77739-285">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="77739-286">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="77739-286">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="77739-287">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="77739-287">Informational (4)</span></span>|  
  
 <span data-ttu-id="77739-288">Aşağıdaki tabloda, olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="77739-288">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="77739-289">Olay</span><span class="sxs-lookup"><span data-stu-id="77739-289">Event</span></span>|<span data-ttu-id="77739-290">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="77739-290">Event ID</span></span>|<span data-ttu-id="77739-291">Ne zaman gerçekleşti</span><span class="sxs-lookup"><span data-stu-id="77739-291">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCFreeSegment_V1`|<span data-ttu-id="77739-292">6</span><span class="sxs-lookup"><span data-stu-id="77739-292">6</span></span>|<span data-ttu-id="77739-293">Bir çöp toplama segment piyasaya Sürüldü.</span><span class="sxs-lookup"><span data-stu-id="77739-293">A garbage collection segment has been released.</span></span>|  
  
 <span data-ttu-id="77739-294">Aşağıdaki tabloda, olay verilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="77739-294">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="77739-295">Alan adı</span><span class="sxs-lookup"><span data-stu-id="77739-295">Field name</span></span>|<span data-ttu-id="77739-296">Veri türü</span><span class="sxs-lookup"><span data-stu-id="77739-296">Data type</span></span>|<span data-ttu-id="77739-297">Açıklama</span><span class="sxs-lookup"><span data-stu-id="77739-297">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="77739-298">Adres</span><span class="sxs-lookup"><span data-stu-id="77739-298">Address</span></span>|<span data-ttu-id="77739-299">Kazanma: UInt64</span><span class="sxs-lookup"><span data-stu-id="77739-299">win:UInt64</span></span>|<span data-ttu-id="77739-300">Segment adresi.</span><span class="sxs-lookup"><span data-stu-id="77739-300">The address of the segment.</span></span>|  
|<span data-ttu-id="77739-301">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="77739-301">ClrInstanceID</span></span>|<span data-ttu-id="77739-302">Kazanma: UInt16</span><span class="sxs-lookup"><span data-stu-id="77739-302">win:UInt16</span></span>|<span data-ttu-id="77739-303">CLR veya CoreCLR örneği için benzersiz kimlik.</span><span class="sxs-lookup"><span data-stu-id="77739-303">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="77739-304">Başa dön</span><span class="sxs-lookup"><span data-stu-id="77739-304">Back to top</span></span>](#top)  
  
<a name="gcrestarteebegin_v1_event"></a>   
## <a name="gcrestarteebeginv1-event"></a><span data-ttu-id="77739-305">GCRestartEEBegin_V1 olay</span><span class="sxs-lookup"><span data-stu-id="77739-305">GCRestartEEBegin_V1 Event</span></span>  
 <span data-ttu-id="77739-306">Aşağıdaki tabloda, düzeyi ve anahtar sözcüğü gösterir.</span><span class="sxs-lookup"><span data-stu-id="77739-306">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="77739-307">Olayı için anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="77739-307">Keyword for raising the event</span></span>|<span data-ttu-id="77739-308">Düzey</span><span class="sxs-lookup"><span data-stu-id="77739-308">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="77739-309">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="77739-309">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="77739-310">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="77739-310">Informational (4)</span></span>|  
  
 <span data-ttu-id="77739-311">Aşağıdaki tabloda, olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="77739-311">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="77739-312">Olay</span><span class="sxs-lookup"><span data-stu-id="77739-312">Event</span></span>|<span data-ttu-id="77739-313">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="77739-313">Event ID</span></span>|<span data-ttu-id="77739-314">Ne zaman gerçekleşti</span><span class="sxs-lookup"><span data-stu-id="77739-314">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCRestartEEBegin_V1`|<span data-ttu-id="77739-315">7</span><span class="sxs-lookup"><span data-stu-id="77739-315">7</span></span>|<span data-ttu-id="77739-316">Ortak dil çalışma zamanı askıya alma gelen sürdürme başladı.</span><span class="sxs-lookup"><span data-stu-id="77739-316">Resumption from common language runtime suspension has begun.</span></span>|  
  
 <span data-ttu-id="77739-317">Hiçbir olay verileri.</span><span class="sxs-lookup"><span data-stu-id="77739-317">No event data.</span></span>  
  
 [<span data-ttu-id="77739-318">Başa dön</span><span class="sxs-lookup"><span data-stu-id="77739-318">Back to top</span></span>](#top)  
  
<a name="gcrestarteeend_v1_event"></a>   
## <a name="gcrestarteeendv1-event"></a><span data-ttu-id="77739-319">GCRestartEEEnd_V1 olay</span><span class="sxs-lookup"><span data-stu-id="77739-319">GCRestartEEEnd_V1 Event</span></span>  
 <span data-ttu-id="77739-320">Aşağıdaki tabloda, düzeyi ve anahtar sözcüğü gösterir.</span><span class="sxs-lookup"><span data-stu-id="77739-320">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="77739-321">Olayı için anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="77739-321">Keyword for raising the event</span></span>|<span data-ttu-id="77739-322">Düzey</span><span class="sxs-lookup"><span data-stu-id="77739-322">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="77739-323">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="77739-323">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="77739-324">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="77739-324">Informational (4)</span></span>|  
  
 <span data-ttu-id="77739-325">Aşağıdaki tabloda, olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="77739-325">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="77739-326">Olay</span><span class="sxs-lookup"><span data-stu-id="77739-326">Event</span></span>|<span data-ttu-id="77739-327">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="77739-327">Event Id</span></span>|<span data-ttu-id="77739-328">Ne zaman gerçekleşti</span><span class="sxs-lookup"><span data-stu-id="77739-328">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCRestartEEEnd_V1`|<span data-ttu-id="77739-329">3</span><span class="sxs-lookup"><span data-stu-id="77739-329">3</span></span>|<span data-ttu-id="77739-330">Ortak dil çalışma zamanı askıya alma gelen sürdürme sona erdi.</span><span class="sxs-lookup"><span data-stu-id="77739-330">Resumption from common language runtime suspension has ended.</span></span>|  
  
 <span data-ttu-id="77739-331">Hiçbir olay verileri.</span><span class="sxs-lookup"><span data-stu-id="77739-331">No event data.</span></span>  
  
 [<span data-ttu-id="77739-332">Başa dön</span><span class="sxs-lookup"><span data-stu-id="77739-332">Back to top</span></span>](#top)  
  
<a name="gcsuspendee_v1_event"></a>   
## <a name="gcsuspendeev1-event"></a><span data-ttu-id="77739-333">GCSuspendEE_V1 Event</span><span class="sxs-lookup"><span data-stu-id="77739-333">GCSuspendEE_V1 Event</span></span>  
 <span data-ttu-id="77739-334">Aşağıdaki tabloda, düzeyi ve anahtar sözcüğü gösterir.</span><span class="sxs-lookup"><span data-stu-id="77739-334">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="77739-335">Olayı için anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="77739-335">Keyword for raising the event</span></span>|<span data-ttu-id="77739-336">Düzey</span><span class="sxs-lookup"><span data-stu-id="77739-336">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="77739-337">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="77739-337">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="77739-338">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="77739-338">Informational (4)</span></span>|  
  
 <span data-ttu-id="77739-339">Aşağıdaki tabloda, olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="77739-339">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="77739-340">Olay</span><span class="sxs-lookup"><span data-stu-id="77739-340">Event</span></span>|<span data-ttu-id="77739-341">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="77739-341">Event ID</span></span>|<span data-ttu-id="77739-342">Ne zaman gerçekleşti</span><span class="sxs-lookup"><span data-stu-id="77739-342">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCSuspendEE_V1`|<span data-ttu-id="77739-343">9</span><span class="sxs-lookup"><span data-stu-id="77739-343">9</span></span>|<span data-ttu-id="77739-344">Çöp toplama işlemi için yürütme altyapısının askıya alma başlangıcı.</span><span class="sxs-lookup"><span data-stu-id="77739-344">Start of suspension of the execution engine for garbage collection.</span></span>|  
  
 <span data-ttu-id="77739-345">Aşağıdaki tabloda, olay verilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="77739-345">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="77739-346">Alan adı</span><span class="sxs-lookup"><span data-stu-id="77739-346">Field name</span></span>|<span data-ttu-id="77739-347">Veri türü</span><span class="sxs-lookup"><span data-stu-id="77739-347">Data type</span></span>|<span data-ttu-id="77739-348">Açıklama</span><span class="sxs-lookup"><span data-stu-id="77739-348">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="77739-349">Neden</span><span class="sxs-lookup"><span data-stu-id="77739-349">Reason</span></span>|<span data-ttu-id="77739-350">Kazanma: UInt16</span><span class="sxs-lookup"><span data-stu-id="77739-350">win:UInt16</span></span>|<span data-ttu-id="77739-351">0x0 - diğer.</span><span class="sxs-lookup"><span data-stu-id="77739-351">0x0 - Other.</span></span><br /><br /> <span data-ttu-id="77739-352">0x1 - çöp toplama.</span><span class="sxs-lookup"><span data-stu-id="77739-352">0x1 - Garbage collection.</span></span><br /><br /> <span data-ttu-id="77739-353">0x2 - uygulama etki alanı kapatma.</span><span class="sxs-lookup"><span data-stu-id="77739-353">0x2 - Application domain shutdown.</span></span><br /><br /> <span data-ttu-id="77739-354">0x3 - kod pitching.</span><span class="sxs-lookup"><span data-stu-id="77739-354">0x3 - Code pitching.</span></span><br /><br /> <span data-ttu-id="77739-355">0x4 - kapatma.</span><span class="sxs-lookup"><span data-stu-id="77739-355">0x4 - Shutdown.</span></span><br /><br /> <span data-ttu-id="77739-356">0x5 - Hata Ayıklayıcısı'nı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="77739-356">0x5 - Debugger.</span></span><br /><br /> <span data-ttu-id="77739-357">0x6 - çöp toplama için hazırlama.</span><span class="sxs-lookup"><span data-stu-id="77739-357">0x6 - Preparation for garbage collection.</span></span>|  
|<span data-ttu-id="77739-358">Count</span><span class="sxs-lookup"><span data-stu-id="77739-358">Count</span></span>|<span data-ttu-id="77739-359">Kazanma: UInt32</span><span class="sxs-lookup"><span data-stu-id="77739-359">win:UInt32</span></span>|<span data-ttu-id="77739-360">GC sayısı zaman.</span><span class="sxs-lookup"><span data-stu-id="77739-360">The GC count at the time.</span></span> <span data-ttu-id="77739-361">Genellikle, bundan sonra bir sonraki GC başlangıç olayı görür ve biz GC dizini çöp toplama sırasında arttıkça sayımına bu sayı + 1 olur.</span><span class="sxs-lookup"><span data-stu-id="77739-361">Usually, you would see a subsequent GC Start event after this, and its Count would be this Count + 1 as we increase the GC index during a garbage collection.</span></span>|  
|<span data-ttu-id="77739-362">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="77739-362">ClrInstanceID</span></span>|<span data-ttu-id="77739-363">Kazanma: UInt16</span><span class="sxs-lookup"><span data-stu-id="77739-363">win:UInt16</span></span>|<span data-ttu-id="77739-364">CLR veya CoreCLR örneği için benzersiz kimlik.</span><span class="sxs-lookup"><span data-stu-id="77739-364">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="77739-365">Başa dön</span><span class="sxs-lookup"><span data-stu-id="77739-365">Back to top</span></span>](#top)  
  
<a name="gcsuspendeeend_v1_event"></a>   
## <a name="gcsuspendeeendv1-event"></a><span data-ttu-id="77739-366">GCSuspendEEEnd_V1 Event</span><span class="sxs-lookup"><span data-stu-id="77739-366">GCSuspendEEEnd_V1 Event</span></span>  
 <span data-ttu-id="77739-367">Aşağıdaki tablo düzeyi ve anahtar sözcüğü gösterir:</span><span class="sxs-lookup"><span data-stu-id="77739-367">The following table shows the keyword and level:</span></span>  
  
|<span data-ttu-id="77739-368">Olayı için anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="77739-368">Keyword for raising the event</span></span>|<span data-ttu-id="77739-369">Düzey</span><span class="sxs-lookup"><span data-stu-id="77739-369">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="77739-370">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="77739-370">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="77739-371">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="77739-371">Informational (4)</span></span>|  
  
 <span data-ttu-id="77739-372">Aşağıdaki tablo, olay bilgileri gösterir:</span><span class="sxs-lookup"><span data-stu-id="77739-372">The following table shows the event information:</span></span>  
  
|<span data-ttu-id="77739-373">Olay</span><span class="sxs-lookup"><span data-stu-id="77739-373">Event</span></span>|<span data-ttu-id="77739-374">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="77739-374">Event ID</span></span>|<span data-ttu-id="77739-375">Ne zaman gerçekleşti</span><span class="sxs-lookup"><span data-stu-id="77739-375">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCSuspendEEEnd_V1`|<span data-ttu-id="77739-376">8</span><span class="sxs-lookup"><span data-stu-id="77739-376">8</span></span>|<span data-ttu-id="77739-377">Çöp toplama işlemi için yürütme altyapısının askıya alma sonu.</span><span class="sxs-lookup"><span data-stu-id="77739-377">End of suspension of the execution engine for garbage collection.</span></span>|  
  
 <span data-ttu-id="77739-378">Hiçbir olay verileri.</span><span class="sxs-lookup"><span data-stu-id="77739-378">No event data.</span></span>  
  
 [<span data-ttu-id="77739-379">Başa dön</span><span class="sxs-lookup"><span data-stu-id="77739-379">Back to top</span></span>](#top)  
  
<a name="gcallocationtick_v2_event"></a>   
## <a name="gcallocationtickv2-event"></a><span data-ttu-id="77739-380">GCAllocationTick_V2 olay</span><span class="sxs-lookup"><span data-stu-id="77739-380">GCAllocationTick_V2 Event</span></span>  
 <span data-ttu-id="77739-381">Aşağıdaki tabloda, düzeyi ve anahtar sözcüğü gösterir.</span><span class="sxs-lookup"><span data-stu-id="77739-381">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="77739-382">Olayı için anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="77739-382">Keyword for raising the event</span></span>|<span data-ttu-id="77739-383">Düzey</span><span class="sxs-lookup"><span data-stu-id="77739-383">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="77739-384">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="77739-384">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="77739-385">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="77739-385">Informational (4)</span></span>|  
  
 <span data-ttu-id="77739-386">Aşağıdaki tabloda, olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="77739-386">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="77739-387">Olay</span><span class="sxs-lookup"><span data-stu-id="77739-387">Event</span></span>|<span data-ttu-id="77739-388">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="77739-388">Event ID</span></span>|<span data-ttu-id="77739-389">Ne zaman gerçekleşti</span><span class="sxs-lookup"><span data-stu-id="77739-389">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCAllocationTick_V2`|<span data-ttu-id="77739-390">10</span><span class="sxs-lookup"><span data-stu-id="77739-390">10</span></span>|<span data-ttu-id="77739-391">Her seferinde yaklaşık 100 KB ayrılır.</span><span class="sxs-lookup"><span data-stu-id="77739-391">Each time approximately 100 KB is allocated.</span></span>|  
  
 <span data-ttu-id="77739-392">Aşağıdaki tabloda, olay verilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="77739-392">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="77739-393">Alan adı</span><span class="sxs-lookup"><span data-stu-id="77739-393">Field name</span></span>|<span data-ttu-id="77739-394">Veri türü</span><span class="sxs-lookup"><span data-stu-id="77739-394">Data type</span></span>|<span data-ttu-id="77739-395">Açıklama</span><span class="sxs-lookup"><span data-stu-id="77739-395">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="77739-396">AllocationAmount</span><span class="sxs-lookup"><span data-stu-id="77739-396">AllocationAmount</span></span>|<span data-ttu-id="77739-397">Kazanma: UInt32</span><span class="sxs-lookup"><span data-stu-id="77739-397">win:UInt32</span></span>|<span data-ttu-id="77739-398">Ayırma bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="77739-398">The allocation size, in bytes.</span></span> <span data-ttu-id="77739-399">Bu değer, küçük bir ULONG (4,294,967,295 bayt), uzunluğundan ayırmalar için doğru olur.</span><span class="sxs-lookup"><span data-stu-id="77739-399">This value is accurate for allocations that are less than the length of a ULONG (4,294,967,295 bytes).</span></span> <span data-ttu-id="77739-400">Ayırma büyükse, bu alan kesilmiş değer içerir.</span><span class="sxs-lookup"><span data-stu-id="77739-400">If the allocation is greater, this field contains a truncated value.</span></span> <span data-ttu-id="77739-401">Kullanım `AllocationAmount64` çok büyük ayırmalar için.</span><span class="sxs-lookup"><span data-stu-id="77739-401">Use `AllocationAmount64` for very large allocations.</span></span>|  
|<span data-ttu-id="77739-402">AllocationKind</span><span class="sxs-lookup"><span data-stu-id="77739-402">AllocationKind</span></span>|<span data-ttu-id="77739-403">Kazanma: UInt32</span><span class="sxs-lookup"><span data-stu-id="77739-403">win:UInt32</span></span>|<span data-ttu-id="77739-404">0x0 - küçük nesne ayırma (içinde küçük nesne yığını ayırma'dir).</span><span class="sxs-lookup"><span data-stu-id="77739-404">0x0 - Small object allocation (allocation is in small object heap).</span></span><br /><br /> <span data-ttu-id="77739-405">0x1 - büyük nesne ayırma (büyük nesne yığınında ayırma'dir).</span><span class="sxs-lookup"><span data-stu-id="77739-405">0x1 - Large object allocation (allocation is in large object heap).</span></span>|  
|<span data-ttu-id="77739-406">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="77739-406">ClrInstanceID</span></span>|<span data-ttu-id="77739-407">Kazanma: UInt16</span><span class="sxs-lookup"><span data-stu-id="77739-407">win:UInt16</span></span>|<span data-ttu-id="77739-408">CLR veya CoreCLR örneği için benzersiz kimlik.</span><span class="sxs-lookup"><span data-stu-id="77739-408">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
|<span data-ttu-id="77739-409">AllocationAmount64</span><span class="sxs-lookup"><span data-stu-id="77739-409">AllocationAmount64</span></span>|<span data-ttu-id="77739-410">Kazanma: UInt64</span><span class="sxs-lookup"><span data-stu-id="77739-410">win:UInt64</span></span>|<span data-ttu-id="77739-411">Ayırma bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="77739-411">The allocation size, in bytes.</span></span> <span data-ttu-id="77739-412">Bu değer çok büyük ayırmalarını doğru olur.</span><span class="sxs-lookup"><span data-stu-id="77739-412">This value is accurate for very large allocations.</span></span>|  
|<span data-ttu-id="77739-413">typeId</span><span class="sxs-lookup"><span data-stu-id="77739-413">TypeId</span></span>|<span data-ttu-id="77739-414">Kazanma: işaretçi</span><span class="sxs-lookup"><span data-stu-id="77739-414">win:Pointer</span></span>|<span data-ttu-id="77739-415">MethodTable adresi.</span><span class="sxs-lookup"><span data-stu-id="77739-415">The address of the MethodTable.</span></span> <span data-ttu-id="77739-416">Bu olayı sırasında ayrılan nesnelerin birkaç türü olduğunda, bu son (100 KB eşiği olması nedeniyle nesne) ayrılmış nesne karşılık gelen MethodTable adresidir.</span><span class="sxs-lookup"><span data-stu-id="77739-416">When there are several types of objects that were allocated during this event, this is the address of the MethodTable that corresponds to the last object allocated (the object that caused the 100 KB threshold to be exceeded).</span></span>|  
|<span data-ttu-id="77739-417">TypeName</span><span class="sxs-lookup"><span data-stu-id="77739-417">TypeName</span></span>|<span data-ttu-id="77739-418">Kazanma: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="77739-418">win:UnicodeString</span></span>|<span data-ttu-id="77739-419">Ayrılmış olan tür adı.</span><span class="sxs-lookup"><span data-stu-id="77739-419">The name of the type that was allocated.</span></span> <span data-ttu-id="77739-420">Bu olayı sırasında ayrılan nesnelerin birkaç türü olduğunda, (100 KB eşiği olması nedeniyle nesne) ayrılan son nesnenin türü budur.</span><span class="sxs-lookup"><span data-stu-id="77739-420">When there are several types of objects that were allocated during this event, this is the type of the last object allocated (the object that caused the 100 KB threshold to be exceeded).</span></span>|  
|<span data-ttu-id="77739-421">HeapIndex</span><span class="sxs-lookup"><span data-stu-id="77739-421">HeapIndex</span></span>|<span data-ttu-id="77739-422">Kazanma: UInt32</span><span class="sxs-lookup"><span data-stu-id="77739-422">win:UInt32</span></span>|<span data-ttu-id="77739-423">Nesne ayrıldığı yığında.</span><span class="sxs-lookup"><span data-stu-id="77739-423">The heap where the object was allocated.</span></span> <span data-ttu-id="77739-424">İş istasyonu çöp toplama ile çalışırken, bu değer 0 (sıfır) olur.</span><span class="sxs-lookup"><span data-stu-id="77739-424">This value is 0 (zero) when running with workstation garbage collection.</span></span>|  
  
 [<span data-ttu-id="77739-425">Başa dön</span><span class="sxs-lookup"><span data-stu-id="77739-425">Back to top</span></span>](#top)  
  
<a name="gcfinalizersbegin_v1_event"></a>   
## <a name="gcfinalizersbeginv1-event"></a><span data-ttu-id="77739-426">GCFinalizersBegin_V1 olay</span><span class="sxs-lookup"><span data-stu-id="77739-426">GCFinalizersBegin_V1 Event</span></span>  
 <span data-ttu-id="77739-427">Aşağıdaki tabloda, düzeyi ve anahtar sözcüğü gösterir.</span><span class="sxs-lookup"><span data-stu-id="77739-427">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="77739-428">Olayı için anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="77739-428">Keyword for raising the event</span></span>|<span data-ttu-id="77739-429">Düzey</span><span class="sxs-lookup"><span data-stu-id="77739-429">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="77739-430">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="77739-430">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="77739-431">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="77739-431">Informational (4)</span></span>|  
  
 <span data-ttu-id="77739-432">Aşağıdaki tabloda, olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="77739-432">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="77739-433">Olay</span><span class="sxs-lookup"><span data-stu-id="77739-433">Event</span></span>|<span data-ttu-id="77739-434">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="77739-434">Event ID</span></span>|<span data-ttu-id="77739-435">Ne zaman gerçekleşti</span><span class="sxs-lookup"><span data-stu-id="77739-435">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCFinalizersBegin_V1`|<span data-ttu-id="77739-436">14</span><span class="sxs-lookup"><span data-stu-id="77739-436">14</span></span>|<span data-ttu-id="77739-437">Sonlandırıcılar çalıştırma başlangıcı.</span><span class="sxs-lookup"><span data-stu-id="77739-437">The start of running finalizers.</span></span>|  
  
 <span data-ttu-id="77739-438">Hiçbir olay verileri.</span><span class="sxs-lookup"><span data-stu-id="77739-438">No event data.</span></span>  
  
 [<span data-ttu-id="77739-439">Başa dön</span><span class="sxs-lookup"><span data-stu-id="77739-439">Back to top</span></span>](#top)  
  
<a name="gcfinalizersend_v1_event"></a>   
## <a name="gcfinalizersendv1-event"></a><span data-ttu-id="77739-440">GCFinalizersEnd_V1 olay</span><span class="sxs-lookup"><span data-stu-id="77739-440">GCFinalizersEnd_V1 Event</span></span>  
 <span data-ttu-id="77739-441">Aşağıdaki tabloda, düzeyi ve anahtar sözcüğü gösterir.</span><span class="sxs-lookup"><span data-stu-id="77739-441">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="77739-442">Olayı için anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="77739-442">Keyword for raising the event</span></span>|<span data-ttu-id="77739-443">Düzey</span><span class="sxs-lookup"><span data-stu-id="77739-443">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="77739-444">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="77739-444">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="77739-445">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="77739-445">Informational (4)</span></span>|  
  
 <span data-ttu-id="77739-446">Aşağıdaki tabloda, olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="77739-446">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="77739-447">Olay</span><span class="sxs-lookup"><span data-stu-id="77739-447">Event</span></span>|<span data-ttu-id="77739-448">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="77739-448">Event ID</span></span>|<span data-ttu-id="77739-449">Ne zaman gerçekleşti</span><span class="sxs-lookup"><span data-stu-id="77739-449">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCFinalizersEnd_V1`|<span data-ttu-id="77739-450">13</span><span class="sxs-lookup"><span data-stu-id="77739-450">13</span></span>|<span data-ttu-id="77739-451">Sonlandırıcılar çalıştırma bitiş olayı.</span><span class="sxs-lookup"><span data-stu-id="77739-451">The end of running finalizers.</span></span>|  
  
 <span data-ttu-id="77739-452">Aşağıdaki tabloda, olay verilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="77739-452">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="77739-453">Alan adı</span><span class="sxs-lookup"><span data-stu-id="77739-453">Field name</span></span>|<span data-ttu-id="77739-454">Veri türü</span><span class="sxs-lookup"><span data-stu-id="77739-454">Data type</span></span>|<span data-ttu-id="77739-455">Açıklama</span><span class="sxs-lookup"><span data-stu-id="77739-455">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="77739-456">Count</span><span class="sxs-lookup"><span data-stu-id="77739-456">Count</span></span>|<span data-ttu-id="77739-457">Kazanma: UInt32</span><span class="sxs-lookup"><span data-stu-id="77739-457">win:UInt32</span></span>|<span data-ttu-id="77739-458">Çalıştırılan bir sonlandırıcı sayısı.</span><span class="sxs-lookup"><span data-stu-id="77739-458">The number of finalizers that were run.</span></span>|  
|<span data-ttu-id="77739-459">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="77739-459">ClrInstanceID</span></span>|<span data-ttu-id="77739-460">Kazanma: UInt16</span><span class="sxs-lookup"><span data-stu-id="77739-460">win:UInt16</span></span>|<span data-ttu-id="77739-461">CLR veya CoreCLR örneği için benzersiz kimlik.</span><span class="sxs-lookup"><span data-stu-id="77739-461">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="77739-462">Başa dön</span><span class="sxs-lookup"><span data-stu-id="77739-462">Back to top</span></span>](#top)  
  
<a name="gccreateconcurrentthread_v1_event"></a>   
## <a name="gccreateconcurrentthreadv1-event"></a><span data-ttu-id="77739-463">GCCreateConcurrentThread_V1 olay</span><span class="sxs-lookup"><span data-stu-id="77739-463">GCCreateConcurrentThread_V1 Event</span></span>  
 <span data-ttu-id="77739-464">Aşağıdaki tabloda, düzeyi ve anahtar sözcüğü gösterir.</span><span class="sxs-lookup"><span data-stu-id="77739-464">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="77739-465">Olayı için anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="77739-465">Keyword for raising the event</span></span>|<span data-ttu-id="77739-466">Düzey</span><span class="sxs-lookup"><span data-stu-id="77739-466">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="77739-467">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="77739-467">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="77739-468">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="77739-468">Informational (4)</span></span>|  
|<span data-ttu-id="77739-469">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="77739-469">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="77739-470">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="77739-470">Informational (4)</span></span>|  
  
 <span data-ttu-id="77739-471">Aşağıdaki tabloda, olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="77739-471">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="77739-472">Olay</span><span class="sxs-lookup"><span data-stu-id="77739-472">Event</span></span>|<span data-ttu-id="77739-473">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="77739-473">Event ID</span></span>|<span data-ttu-id="77739-474">Ne zaman gerçekleşti</span><span class="sxs-lookup"><span data-stu-id="77739-474">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCCreateConcurrentThread_V1`|<span data-ttu-id="77739-475">11</span><span class="sxs-lookup"><span data-stu-id="77739-475">11</span></span>|<span data-ttu-id="77739-476">Eş zamanlı çöp toplama iş parçacığı oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="77739-476">Concurrent garbage collection thread was created.</span></span>|  
  
 <span data-ttu-id="77739-477">Hiçbir olay verileri.</span><span class="sxs-lookup"><span data-stu-id="77739-477">No event data.</span></span>  
  
 [<span data-ttu-id="77739-478">Başa dön</span><span class="sxs-lookup"><span data-stu-id="77739-478">Back to top</span></span>](#top)  
  
<a name="gcterminateconcurrentthread_v1_event"></a>   
## <a name="gcterminateconcurrentthreadv1-event"></a><span data-ttu-id="77739-479">GCTerminateConcurrentThread_V1 olay</span><span class="sxs-lookup"><span data-stu-id="77739-479">GCTerminateConcurrentThread_V1 Event</span></span>  
 <span data-ttu-id="77739-480">Aşağıdaki tabloda, düzeyi ve anahtar sözcüğü gösterir.</span><span class="sxs-lookup"><span data-stu-id="77739-480">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="77739-481">Olayı için anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="77739-481">Keyword for raising the event</span></span>|<span data-ttu-id="77739-482">Düzey</span><span class="sxs-lookup"><span data-stu-id="77739-482">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="77739-483">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="77739-483">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="77739-484">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="77739-484">Informational (4)</span></span>|  
|<span data-ttu-id="77739-485">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="77739-485">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="77739-486">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="77739-486">Informational (4)</span></span>|  
  
 <span data-ttu-id="77739-487">Aşağıdaki tabloda, olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="77739-487">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="77739-488">Olay</span><span class="sxs-lookup"><span data-stu-id="77739-488">Event</span></span>|<span data-ttu-id="77739-489">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="77739-489">Event ID</span></span>|<span data-ttu-id="77739-490">Ne zaman gerçekleşti</span><span class="sxs-lookup"><span data-stu-id="77739-490">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCTerminateConcurrentThread_V1`|<span data-ttu-id="77739-491">12</span><span class="sxs-lookup"><span data-stu-id="77739-491">12</span></span>|<span data-ttu-id="77739-492">Eş zamanlı çöp toplama iş parçacığı sonlandırıldı.</span><span class="sxs-lookup"><span data-stu-id="77739-492">Concurrent garbage collection thread was terminated.</span></span>|  
  
 <span data-ttu-id="77739-493">Hiçbir olay verileri.</span><span class="sxs-lookup"><span data-stu-id="77739-493">No event data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77739-494">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="77739-494">See also</span></span>

- [<span data-ttu-id="77739-495">CLR ETW Olayları</span><span class="sxs-lookup"><span data-stu-id="77739-495">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
