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
ms.openlocfilehash: 13f7e935ab999ccc3cd3ea1e308e8d686bed4171
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33396941"
---
# <a name="garbage-collection-etw-events"></a><span data-ttu-id="091da-102">Çöp Toplama ETW Olayları</span><span class="sxs-lookup"><span data-stu-id="091da-102">Garbage Collection ETW Events</span></span>
<a name="top"></a> <span data-ttu-id="091da-103">Bu olaylar çöp toplama ilgili bilgi toplayın.</span><span class="sxs-lookup"><span data-stu-id="091da-103">These events collect information pertaining to garbage collection.</span></span> <span data-ttu-id="091da-104">Tanılamada yardımcı olurlar ve hata ayıklama, atık toplama kaç kez belirleme dahil olmak üzere gerçekleştirildiyse, ne kadar bellek çöp toplama ve benzeri sırasında bırakılmış.</span><span class="sxs-lookup"><span data-stu-id="091da-104">They help in diagnostics and debugging, including determining how many times garbage collection was performed, how much memory was freed during garbage collection, and so on.</span></span>  
  
 <span data-ttu-id="091da-105">Bu kategori aşağıdaki olaylar oluşur:</span><span class="sxs-lookup"><span data-stu-id="091da-105">This category consists of the following events:</span></span>  
  
-   [<span data-ttu-id="091da-106">GCStart_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="091da-106">GCStart_V1 Event</span></span>](#gcstart_v1_event)  
  
-   [<span data-ttu-id="091da-107">GCEnd_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="091da-107">GCEnd_V1 Event</span></span>](#gcend_v1_event)  
  
-   [<span data-ttu-id="091da-108">GCHeapStats_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="091da-108">GCHeapStats_V1 Event</span></span>](#gcheapstats_v1_event)  
  
-   [<span data-ttu-id="091da-109">GCCreateSegment_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="091da-109">GCCreateSegment_V1 Event</span></span>](#gccreatesegment_v1_event)  
  
-   [<span data-ttu-id="091da-110">GCFreeSegment_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="091da-110">GCFreeSegment_V1 Event</span></span>](#gcfreesegment_v1_event)  
  
-   [<span data-ttu-id="091da-111">GCRestartEEBegin_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="091da-111">GCRestartEEBegin_V1 Event</span></span>](#gcrestarteebegin_v1_event)  
  
-   [<span data-ttu-id="091da-112">GCRestartEEEnd_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="091da-112">GCRestartEEEnd_V1 Event</span></span>](#gcrestarteeend_v1_event)  
  
-   [<span data-ttu-id="091da-113">GCSuspendEE_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="091da-113">GCSuspendEE_V1 Event</span></span>](#gcsuspendee_v1_event)  
  
-   [<span data-ttu-id="091da-114">GCSuspendEEEnd_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="091da-114">GCSuspendEEEnd_V1 Event</span></span>](#gcsuspendeeend_v1_event)  
  
-   [<span data-ttu-id="091da-115">GCAllocationTick_V2 olayı</span><span class="sxs-lookup"><span data-stu-id="091da-115">GCAllocationTick_V2 Event</span></span>](#gcallocationtick_v2_event)  
  
-   [<span data-ttu-id="091da-116">GCFinalizersBegin_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="091da-116">GCFinalizersBegin_V1 Event</span></span>](#gcfinalizersbegin_v1_event)  
  
-   [<span data-ttu-id="091da-117">GCFinalizersEnd_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="091da-117">GCFinalizersEnd_V1 Event</span></span>](#gcfinalizersend_v1_event)  
  
-   [<span data-ttu-id="091da-118">GCCreateConcurrentThread_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="091da-118">GCCreateConcurrentThread_V1 Event</span></span>](#gccreateconcurrentthread_v1_event)  
  
-   [<span data-ttu-id="091da-119">GCTerminateConcurrentThread_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="091da-119">GCTerminateConcurrentThread_V1 Event</span></span>](#gcterminateconcurrentthread_v1_event)  
  
<a name="gcstart_v1_event"></a>   
## <a name="gcstartv1-event"></a><span data-ttu-id="091da-120">GCStart_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="091da-120">GCStart_V1 Event</span></span>  
 <span data-ttu-id="091da-121">Aşağıdaki tablo düzeyi ve anahtar sözcüğü gösterir.</span><span class="sxs-lookup"><span data-stu-id="091da-121">The following table shows the keyword and level.</span></span> <span data-ttu-id="091da-122">(Daha fazla bilgi için bkz: [CLR ETW anahtar sözcükleri ve Düzeyler](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="091da-122">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="091da-123">Olay oluşturma için anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="091da-123">Keyword for raising the event</span></span>|<span data-ttu-id="091da-124">Düzey</span><span class="sxs-lookup"><span data-stu-id="091da-124">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="091da-125">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="091da-125">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="091da-126">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="091da-126">Informational (4)</span></span>|  
  
 <span data-ttu-id="091da-127">Aşağıdaki tabloda olay bilgilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="091da-127">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="091da-128">Olay</span><span class="sxs-lookup"><span data-stu-id="091da-128">Event</span></span>|<span data-ttu-id="091da-129">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="091da-129">Event ID</span></span>|<span data-ttu-id="091da-130">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="091da-130">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCStart_V1`|<span data-ttu-id="091da-131">1.</span><span class="sxs-lookup"><span data-stu-id="091da-131">1</span></span>|<span data-ttu-id="091da-132">Çöp toplama başlatıldı.</span><span class="sxs-lookup"><span data-stu-id="091da-132">A garbage collection has started.</span></span>|  
  
 <span data-ttu-id="091da-133">Aşağıdaki tabloda olay verilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="091da-133">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="091da-134">Alan adı</span><span class="sxs-lookup"><span data-stu-id="091da-134">Field name</span></span>|<span data-ttu-id="091da-135">Veri türü</span><span class="sxs-lookup"><span data-stu-id="091da-135">Data type</span></span>|<span data-ttu-id="091da-136">Açıklama</span><span class="sxs-lookup"><span data-stu-id="091da-136">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="091da-137">Sayısı</span><span class="sxs-lookup"><span data-stu-id="091da-137">Count</span></span>|<span data-ttu-id="091da-138">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="091da-138">win:UInt32</span></span>|<span data-ttu-id="091da-139">*n*th atık toplama.</span><span class="sxs-lookup"><span data-stu-id="091da-139">The *n*th garbage collection.</span></span>|  
|<span data-ttu-id="091da-140">Derinliği</span><span class="sxs-lookup"><span data-stu-id="091da-140">Depth</span></span>|<span data-ttu-id="091da-141">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="091da-141">win:UInt32</span></span>|<span data-ttu-id="091da-142">Toplanacak oluşturma.</span><span class="sxs-lookup"><span data-stu-id="091da-142">The generation that is being collected.</span></span>|  
|<span data-ttu-id="091da-143">Neden</span><span class="sxs-lookup"><span data-stu-id="091da-143">Reason</span></span>|<span data-ttu-id="091da-144">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="091da-144">win:UInt32</span></span>|<span data-ttu-id="091da-145">Çöp toplama neden tetiklendi:</span><span class="sxs-lookup"><span data-stu-id="091da-145">Why the garbage collection was triggered:</span></span><br /><br /> <span data-ttu-id="091da-146">0x0 - küçük nesne yığın ayırma.</span><span class="sxs-lookup"><span data-stu-id="091da-146">0x0 - Small object heap allocation.</span></span><br /><br /> <span data-ttu-id="091da-147">0x1 - kopyaladığınızda.</span><span class="sxs-lookup"><span data-stu-id="091da-147">0x1 - Induced.</span></span><br /><br /> <span data-ttu-id="091da-148">0x2 - bellek yetersiz.</span><span class="sxs-lookup"><span data-stu-id="091da-148">0x2 - Low memory.</span></span><br /><br /> <span data-ttu-id="091da-149">0x3 - boş.</span><span class="sxs-lookup"><span data-stu-id="091da-149">0x3 - Empty.</span></span><br /><br /> <span data-ttu-id="091da-150">0x4 - büyük nesne yığın ayırma.</span><span class="sxs-lookup"><span data-stu-id="091da-150">0x4 - Large object heap allocation.</span></span><br /><br /> <span data-ttu-id="091da-151">0x5 - (için küçük nesne yığın) alanı yetersiz.</span><span class="sxs-lookup"><span data-stu-id="091da-151">0x5 - Out of space (for small object heap).</span></span><br /><br /> <span data-ttu-id="091da-152">0x6 - (için büyük nesne yığın) alanı yetersiz.</span><span class="sxs-lookup"><span data-stu-id="091da-152">0x6 - Out of space (for large object heap).</span></span><br /><br /> <span data-ttu-id="091da-153">0x7 - kopyaladığınızda ancak engelleme olarak zorunlu değildir.</span><span class="sxs-lookup"><span data-stu-id="091da-153">0x7 - Induced but not forced as blocking.</span></span>|  
|<span data-ttu-id="091da-154">Tür</span><span class="sxs-lookup"><span data-stu-id="091da-154">Type</span></span>|<span data-ttu-id="091da-155">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="091da-155">win:UInt32</span></span>|<span data-ttu-id="091da-156">0x0 - arka plan çöp toplama dışında engelleme çöp toplama oluştu.</span><span class="sxs-lookup"><span data-stu-id="091da-156">0x0 - Blocking garbage collection occurred outside background garbage collection.</span></span><br /><br /> <span data-ttu-id="091da-157">0x1 - arka plan çöp toplama.</span><span class="sxs-lookup"><span data-stu-id="091da-157">0x1 - Background garbage collection.</span></span><br /><br /> <span data-ttu-id="091da-158">0x2 - engelleme çöp toplama arka plan çöp toplama sırasında oluştu.</span><span class="sxs-lookup"><span data-stu-id="091da-158">0x2 - Blocking garbage collection occurred during background garbage collection.</span></span>|  
|<span data-ttu-id="091da-159">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="091da-159">ClrInstanceID</span></span>|<span data-ttu-id="091da-160">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="091da-160">win:UInt16</span></span>|<span data-ttu-id="091da-161">CLR veya CoreCLR örneği için benzersiz kimlik.</span><span class="sxs-lookup"><span data-stu-id="091da-161">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="091da-162">Başa dön</span><span class="sxs-lookup"><span data-stu-id="091da-162">Back to top</span></span>](#top)  
  
<a name="gcend_v1_event"></a>   
## <a name="gcendv1-event"></a><span data-ttu-id="091da-163">GCEnd_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="091da-163">GCEnd_V1 Event</span></span>  
 <span data-ttu-id="091da-164">Aşağıdaki tablo düzeyi ve anahtar sözcüğü gösterir.</span><span class="sxs-lookup"><span data-stu-id="091da-164">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="091da-165">Olay oluşturma için anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="091da-165">Keyword for raising the event</span></span>|<span data-ttu-id="091da-166">Düzey</span><span class="sxs-lookup"><span data-stu-id="091da-166">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="091da-167">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="091da-167">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="091da-168">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="091da-168">Informational (4)</span></span>|  
  
 <span data-ttu-id="091da-169">Aşağıdaki tabloda olay bilgilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="091da-169">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="091da-170">Olay</span><span class="sxs-lookup"><span data-stu-id="091da-170">Event</span></span>|<span data-ttu-id="091da-171">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="091da-171">Event ID</span></span>|<span data-ttu-id="091da-172">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="091da-172">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCEnd_V1`|<span data-ttu-id="091da-173">2</span><span class="sxs-lookup"><span data-stu-id="091da-173">2</span></span>|<span data-ttu-id="091da-174">Çöp toplama sona erdi.</span><span class="sxs-lookup"><span data-stu-id="091da-174">The garbage collection has ended.</span></span>|  
  
 <span data-ttu-id="091da-175">Aşağıdaki tabloda olay verilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="091da-175">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="091da-176">Alan adı</span><span class="sxs-lookup"><span data-stu-id="091da-176">Field name</span></span>|<span data-ttu-id="091da-177">Veri türü</span><span class="sxs-lookup"><span data-stu-id="091da-177">Data type</span></span>|<span data-ttu-id="091da-178">Açıklama</span><span class="sxs-lookup"><span data-stu-id="091da-178">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="091da-179">Sayısı</span><span class="sxs-lookup"><span data-stu-id="091da-179">Count</span></span>|<span data-ttu-id="091da-180">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="091da-180">win:UInt32</span></span>|<span data-ttu-id="091da-181">*n*th atık toplama.</span><span class="sxs-lookup"><span data-stu-id="091da-181">The *n*th garbage collection.</span></span>|  
|<span data-ttu-id="091da-182">Derinliği</span><span class="sxs-lookup"><span data-stu-id="091da-182">Depth</span></span>|<span data-ttu-id="091da-183">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="091da-183">win:UInt32</span></span>|<span data-ttu-id="091da-184">Toplanan oluşturma.</span><span class="sxs-lookup"><span data-stu-id="091da-184">The generation that was collected.</span></span>|  
|<span data-ttu-id="091da-185">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="091da-185">ClrInstanceID</span></span>|<span data-ttu-id="091da-186">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="091da-186">win:UInt16</span></span>|<span data-ttu-id="091da-187">CLR veya CoreCLR örneği için benzersiz kimlik.</span><span class="sxs-lookup"><span data-stu-id="091da-187">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="091da-188">Başa dön</span><span class="sxs-lookup"><span data-stu-id="091da-188">Back to top</span></span>](#top)  
  
<a name="gcheapstats_v1_event"></a>   
## <a name="gcheapstatsv1-event"></a><span data-ttu-id="091da-189">GCHeapStats_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="091da-189">GCHeapStats_V1 Event</span></span>  
 <span data-ttu-id="091da-190">Aşağıdaki tablo düzeyi ve anahtar sözcüğü gösterir.</span><span class="sxs-lookup"><span data-stu-id="091da-190">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="091da-191">Olay oluşturma için anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="091da-191">Keyword for raising the event</span></span>|<span data-ttu-id="091da-192">Düzey</span><span class="sxs-lookup"><span data-stu-id="091da-192">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="091da-193">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="091da-193">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="091da-194">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="091da-194">Informational (4)</span></span>|  
  
 <span data-ttu-id="091da-195">Aşağıdaki tabloda olay bilgilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="091da-195">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="091da-196">Olay</span><span class="sxs-lookup"><span data-stu-id="091da-196">Event</span></span>|<span data-ttu-id="091da-197">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="091da-197">Event ID</span></span>|<span data-ttu-id="091da-198">Açıklama</span><span class="sxs-lookup"><span data-stu-id="091da-198">Description</span></span>|  
|-----------|--------------|-----------------|  
|`GCHeapStats_V1`|<span data-ttu-id="091da-199">4</span><span class="sxs-lookup"><span data-stu-id="091da-199">4</span></span>|<span data-ttu-id="091da-200">Her çöp toplama işleminin sonunda yığın istatistiklerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="091da-200">Shows the heap statistics at the end of each garbage collection.</span></span>|  
  
 <span data-ttu-id="091da-201">Aşağıdaki tabloda olay verilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="091da-201">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="091da-202">Alan adı</span><span class="sxs-lookup"><span data-stu-id="091da-202">Field name</span></span>|<span data-ttu-id="091da-203">Veri türü</span><span class="sxs-lookup"><span data-stu-id="091da-203">Data type</span></span>|<span data-ttu-id="091da-204">Açıklama</span><span class="sxs-lookup"><span data-stu-id="091da-204">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="091da-205">GenerationSize0</span><span class="sxs-lookup"><span data-stu-id="091da-205">GenerationSize0</span></span>|<span data-ttu-id="091da-206">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="091da-206">win:UInt64</span></span>|<span data-ttu-id="091da-207">Kuşak 0 belleğin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="091da-207">The size, in bytes, of generation 0 memory.</span></span>|  
|<span data-ttu-id="091da-208">TotalPromotedSize0</span><span class="sxs-lookup"><span data-stu-id="091da-208">TotalPromotedSize0</span></span>|<span data-ttu-id="091da-209">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="091da-209">win:UInt64</span></span>|<span data-ttu-id="091da-210">0 kuşaktan 1. nesil için öne çıkar bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="091da-210">The number of bytes that are promoted from generation 0 to generation 1.</span></span>|  
|<span data-ttu-id="091da-211">GenerationSize1</span><span class="sxs-lookup"><span data-stu-id="091da-211">GenerationSize1</span></span>|<span data-ttu-id="091da-212">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="091da-212">win:UInt64</span></span>|<span data-ttu-id="091da-213">1. nesil belleğin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="091da-213">The size, in bytes, of generation 1 memory.</span></span>|  
|<span data-ttu-id="091da-214">TotalPromotedSize1</span><span class="sxs-lookup"><span data-stu-id="091da-214">TotalPromotedSize1</span></span>|<span data-ttu-id="091da-215">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="091da-215">win:UInt64</span></span>|<span data-ttu-id="091da-216">1 kuşaktan 2. nesil için öne çıkar bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="091da-216">The number of bytes that are promoted from generation 1 to generation 2.</span></span>|  
|<span data-ttu-id="091da-217">GenerationSize2</span><span class="sxs-lookup"><span data-stu-id="091da-217">GenerationSize2</span></span>|<span data-ttu-id="091da-218">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="091da-218">win:UInt64</span></span>|<span data-ttu-id="091da-219">2. nesil belleğin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="091da-219">The size, in bytes, of generation 2 memory.</span></span>|  
|<span data-ttu-id="091da-220">TotalPromotedSize2</span><span class="sxs-lookup"><span data-stu-id="091da-220">TotalPromotedSize2</span></span>|<span data-ttu-id="091da-221">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="091da-221">win:UInt64</span></span>|<span data-ttu-id="091da-222">2. nesil son koleksiyon sonra içinde derdi bitti bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="091da-222">The number of bytes that survived in generation 2 after the last collection.</span></span>|  
|<span data-ttu-id="091da-223">GenerationSize3</span><span class="sxs-lookup"><span data-stu-id="091da-223">GenerationSize3</span></span>|<span data-ttu-id="091da-224">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="091da-224">win:UInt64</span></span>|<span data-ttu-id="091da-225">Bayt olarak büyük nesne yığın boyutu.</span><span class="sxs-lookup"><span data-stu-id="091da-225">The size, in bytes, of the large object heap.</span></span>|  
|<span data-ttu-id="091da-226">TotalPromotedSize3</span><span class="sxs-lookup"><span data-stu-id="091da-226">TotalPromotedSize3</span></span>|<span data-ttu-id="091da-227">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="091da-227">win:UInt64</span></span>|<span data-ttu-id="091da-228">Büyük nesne yığın sonra son koleksiyon derdi bitti bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="091da-228">The number of bytes that survived in the large object heap after the last collection.</span></span>|  
|<span data-ttu-id="091da-229">FinalizationPromotedSize</span><span class="sxs-lookup"><span data-stu-id="091da-229">FinalizationPromotedSize</span></span>|<span data-ttu-id="091da-230">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="091da-230">win:UInt64</span></span>|<span data-ttu-id="091da-231">Sonlandırma için hazır olan nesnelerin bayt toplam boyutu.</span><span class="sxs-lookup"><span data-stu-id="091da-231">The total size, in bytes, of the objects that are ready for finalization.</span></span>|  
|<span data-ttu-id="091da-232">FinalizationPromotedCount</span><span class="sxs-lookup"><span data-stu-id="091da-232">FinalizationPromotedCount</span></span>|<span data-ttu-id="091da-233">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="091da-233">win:UInt64</span></span>|<span data-ttu-id="091da-234">Sonlandırma için hazır nesnelerin sayısı.</span><span class="sxs-lookup"><span data-stu-id="091da-234">The number of objects that are ready for finalization.</span></span>|  
|<span data-ttu-id="091da-235">PinnedObjectCount</span><span class="sxs-lookup"><span data-stu-id="091da-235">PinnedObjectCount</span></span>|<span data-ttu-id="091da-236">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="091da-236">win:UInt32</span></span>|<span data-ttu-id="091da-237">Sabitlenmiş (taşınamayan) nesnelerin sayısı.</span><span class="sxs-lookup"><span data-stu-id="091da-237">The number of pinned (unmovable) objects.</span></span>|  
|<span data-ttu-id="091da-238">SinkBlockCount</span><span class="sxs-lookup"><span data-stu-id="091da-238">SinkBlockCount</span></span>|<span data-ttu-id="091da-239">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="091da-239">win:UInt32</span></span>|<span data-ttu-id="091da-240">Kullanımdaki eşitleme bloğu sayısı.</span><span class="sxs-lookup"><span data-stu-id="091da-240">The number of synchronization blocks in use.</span></span>|  
|<span data-ttu-id="091da-241">GCHandleCount</span><span class="sxs-lookup"><span data-stu-id="091da-241">GCHandleCount</span></span>|<span data-ttu-id="091da-242">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="091da-242">win:UInt32</span></span>|<span data-ttu-id="091da-243">Çöp toplama sayısı kullanımda işler.</span><span class="sxs-lookup"><span data-stu-id="091da-243">The number of garbage collection handles in use.</span></span>|  
|<span data-ttu-id="091da-244">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="091da-244">ClrInstanceID</span></span>|<span data-ttu-id="091da-245">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="091da-245">win:UInt16</span></span>|<span data-ttu-id="091da-246">CLR veya CoreCLR örneği için benzersiz kimlik.</span><span class="sxs-lookup"><span data-stu-id="091da-246">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="091da-247">Başa dön</span><span class="sxs-lookup"><span data-stu-id="091da-247">Back to top</span></span>](#top)  
  
<a name="gccreatesegment_v1_event"></a>   
## <a name="gccreatesegmentv1-event"></a><span data-ttu-id="091da-248">GCCreateSegment_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="091da-248">GCCreateSegment_V1 Event</span></span>  
 <span data-ttu-id="091da-249">Aşağıdaki tablo düzeyi ve anahtar sözcüğü gösterir.</span><span class="sxs-lookup"><span data-stu-id="091da-249">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="091da-250">Olay oluşturma için anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="091da-250">Keyword for raising the event</span></span>|<span data-ttu-id="091da-251">Düzey</span><span class="sxs-lookup"><span data-stu-id="091da-251">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="091da-252">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="091da-252">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="091da-253">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="091da-253">Informational (4)</span></span>|  
  
 <span data-ttu-id="091da-254">Aşağıdaki tabloda olay bilgilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="091da-254">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="091da-255">Olay</span><span class="sxs-lookup"><span data-stu-id="091da-255">Event</span></span>|<span data-ttu-id="091da-256">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="091da-256">Event ID</span></span>|<span data-ttu-id="091da-257">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="091da-257">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCCreateSegment_V1`|<span data-ttu-id="091da-258">5</span><span class="sxs-lookup"><span data-stu-id="091da-258">5</span></span>|<span data-ttu-id="091da-259">Yeni bir atık toplama segment oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="091da-259">A new garbage collection segment has been created.</span></span> <span data-ttu-id="091da-260">Ayrıca, izleme zaten çalıştırılan bir işlemde etkinleştirildiğinde, varolan her segment için bu olay tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="091da-260">In addition, when tracing is enabled on a process that is already running, this event is raised for each existing segment.</span></span>|  
  
 <span data-ttu-id="091da-261">Aşağıdaki tabloda olay verilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="091da-261">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="091da-262">Alan adı</span><span class="sxs-lookup"><span data-stu-id="091da-262">Field name</span></span>|<span data-ttu-id="091da-263">Veri türü</span><span class="sxs-lookup"><span data-stu-id="091da-263">Data type</span></span>|<span data-ttu-id="091da-264">Açıklama</span><span class="sxs-lookup"><span data-stu-id="091da-264">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="091da-265">Adres</span><span class="sxs-lookup"><span data-stu-id="091da-265">Address</span></span>|<span data-ttu-id="091da-266">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="091da-266">win:UInt64</span></span>|<span data-ttu-id="091da-267">Kesim adresi.</span><span class="sxs-lookup"><span data-stu-id="091da-267">The address of the segment.</span></span>|  
|<span data-ttu-id="091da-268">Boyut</span><span class="sxs-lookup"><span data-stu-id="091da-268">Size</span></span>|<span data-ttu-id="091da-269">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="091da-269">win:UInt64</span></span>|<span data-ttu-id="091da-270">Kesim boyutu.</span><span class="sxs-lookup"><span data-stu-id="091da-270">The size of the segment.</span></span>|  
|<span data-ttu-id="091da-271">Tür</span><span class="sxs-lookup"><span data-stu-id="091da-271">Type</span></span>|<span data-ttu-id="091da-272">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="091da-272">win:UInt32</span></span>|<span data-ttu-id="091da-273">0x0 - küçük nesne yığın.</span><span class="sxs-lookup"><span data-stu-id="091da-273">0x0 - Small object heap.</span></span><br /><br /> <span data-ttu-id="091da-274">0x1 - büyük nesne yığın.</span><span class="sxs-lookup"><span data-stu-id="091da-274">0x1 - Large object heap.</span></span><br /><br /> <span data-ttu-id="091da-275">0x2 - salt okunur yığın.</span><span class="sxs-lookup"><span data-stu-id="091da-275">0x2 - Read-only heap.</span></span>|  
|<span data-ttu-id="091da-276">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="091da-276">ClrInstanceID</span></span>|<span data-ttu-id="091da-277">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="091da-277">win:UInt16</span></span>|<span data-ttu-id="091da-278">CLR veya CoreCLR örneği için benzersiz kimlik.</span><span class="sxs-lookup"><span data-stu-id="091da-278">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 <span data-ttu-id="091da-279">Çöp toplayıcı tarafından ayrılan kesimleri boyutunu uygulamasına özeldir ve düzenli güncelleştirmeleri dahil olmak üzere, istediğiniz zaman değiştirilebilir unutmayın.</span><span class="sxs-lookup"><span data-stu-id="091da-279">Note that the size of segments allocated by the garbage collector is implementation-specific and is subject to change at any time, including in periodic updates.</span></span> <span data-ttu-id="091da-280">Uygulamanız hiçbir zaman hakkında varsayımlar olun veya belirli bir segmentle boyutuna göre değişir ve segment ayırmalarının kullanılabilir bellek miktarını yapılandırmak için denemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="091da-280">Your app should never make assumptions about or depend on a particular segment size, nor should it attempt to configure the amount of memory available for segment allocations.</span></span>  
  
 [<span data-ttu-id="091da-281">Başa dön</span><span class="sxs-lookup"><span data-stu-id="091da-281">Back to top</span></span>](#top)  
  
<a name="gcfreesegment_v1_event"></a>   
## <a name="gcfreesegmentv1-event"></a><span data-ttu-id="091da-282">GCFreeSegment_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="091da-282">GCFreeSegment_V1 Event</span></span>  
 <span data-ttu-id="091da-283">Aşağıdaki tablo düzeyi ve anahtar sözcüğü gösterir.</span><span class="sxs-lookup"><span data-stu-id="091da-283">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="091da-284">Olay oluşturma için anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="091da-284">Keyword for raising the event</span></span>|<span data-ttu-id="091da-285">Düzey</span><span class="sxs-lookup"><span data-stu-id="091da-285">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="091da-286">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="091da-286">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="091da-287">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="091da-287">Informational (4)</span></span>|  
  
 <span data-ttu-id="091da-288">Aşağıdaki tabloda olay bilgilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="091da-288">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="091da-289">Olay</span><span class="sxs-lookup"><span data-stu-id="091da-289">Event</span></span>|<span data-ttu-id="091da-290">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="091da-290">Event ID</span></span>|<span data-ttu-id="091da-291">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="091da-291">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCFreeSegment_V1`|<span data-ttu-id="091da-292">6</span><span class="sxs-lookup"><span data-stu-id="091da-292">6</span></span>|<span data-ttu-id="091da-293">Çöp toplama kesimi yayımladı.</span><span class="sxs-lookup"><span data-stu-id="091da-293">A garbage collection segment has been released.</span></span>|  
  
 <span data-ttu-id="091da-294">Aşağıdaki tabloda olay verilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="091da-294">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="091da-295">Alan adı</span><span class="sxs-lookup"><span data-stu-id="091da-295">Field name</span></span>|<span data-ttu-id="091da-296">Veri türü</span><span class="sxs-lookup"><span data-stu-id="091da-296">Data type</span></span>|<span data-ttu-id="091da-297">Açıklama</span><span class="sxs-lookup"><span data-stu-id="091da-297">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="091da-298">Adres</span><span class="sxs-lookup"><span data-stu-id="091da-298">Address</span></span>|<span data-ttu-id="091da-299">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="091da-299">win:UInt64</span></span>|<span data-ttu-id="091da-300">Kesim adresi.</span><span class="sxs-lookup"><span data-stu-id="091da-300">The address of the segment.</span></span>|  
|<span data-ttu-id="091da-301">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="091da-301">ClrInstanceID</span></span>|<span data-ttu-id="091da-302">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="091da-302">win:UInt16</span></span>|<span data-ttu-id="091da-303">CLR veya CoreCLR örneği için benzersiz kimlik.</span><span class="sxs-lookup"><span data-stu-id="091da-303">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="091da-304">Başa dön</span><span class="sxs-lookup"><span data-stu-id="091da-304">Back to top</span></span>](#top)  
  
<a name="gcrestarteebegin_v1_event"></a>   
## <a name="gcrestarteebeginv1-event"></a><span data-ttu-id="091da-305">GCRestartEEBegin_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="091da-305">GCRestartEEBegin_V1 Event</span></span>  
 <span data-ttu-id="091da-306">Aşağıdaki tablo düzeyi ve anahtar sözcüğü gösterir.</span><span class="sxs-lookup"><span data-stu-id="091da-306">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="091da-307">Olay oluşturma için anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="091da-307">Keyword for raising the event</span></span>|<span data-ttu-id="091da-308">Düzey</span><span class="sxs-lookup"><span data-stu-id="091da-308">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="091da-309">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="091da-309">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="091da-310">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="091da-310">Informational (4)</span></span>|  
  
 <span data-ttu-id="091da-311">Aşağıdaki tabloda olay bilgilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="091da-311">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="091da-312">Olay</span><span class="sxs-lookup"><span data-stu-id="091da-312">Event</span></span>|<span data-ttu-id="091da-313">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="091da-313">Event ID</span></span>|<span data-ttu-id="091da-314">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="091da-314">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCRestartEEBegin_V1`|<span data-ttu-id="091da-315">7</span><span class="sxs-lookup"><span data-stu-id="091da-315">7</span></span>|<span data-ttu-id="091da-316">Ortak dil çalışma zamanı askıya gelen sürdürme başladı.</span><span class="sxs-lookup"><span data-stu-id="091da-316">Resumption from common language runtime suspension has begun.</span></span>|  
  
 <span data-ttu-id="091da-317">Olay verisi yok.</span><span class="sxs-lookup"><span data-stu-id="091da-317">No event data.</span></span>  
  
 [<span data-ttu-id="091da-318">Başa dön</span><span class="sxs-lookup"><span data-stu-id="091da-318">Back to top</span></span>](#top)  
  
<a name="gcrestarteeend_v1_event"></a>   
## <a name="gcrestarteeendv1-event"></a><span data-ttu-id="091da-319">GCRestartEEEnd_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="091da-319">GCRestartEEEnd_V1 Event</span></span>  
 <span data-ttu-id="091da-320">Aşağıdaki tablo düzeyi ve anahtar sözcüğü gösterir.</span><span class="sxs-lookup"><span data-stu-id="091da-320">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="091da-321">Olay oluşturma için anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="091da-321">Keyword for raising the event</span></span>|<span data-ttu-id="091da-322">Düzey</span><span class="sxs-lookup"><span data-stu-id="091da-322">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="091da-323">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="091da-323">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="091da-324">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="091da-324">Informational (4)</span></span>|  
  
 <span data-ttu-id="091da-325">Aşağıdaki tabloda olay bilgilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="091da-325">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="091da-326">Olay</span><span class="sxs-lookup"><span data-stu-id="091da-326">Event</span></span>|<span data-ttu-id="091da-327">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="091da-327">Event Id</span></span>|<span data-ttu-id="091da-328">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="091da-328">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCRestartEEEnd_V1`|<span data-ttu-id="091da-329">3</span><span class="sxs-lookup"><span data-stu-id="091da-329">3</span></span>|<span data-ttu-id="091da-330">Ortak dil çalışma zamanı askıya gelen sürdürme sona erdi.</span><span class="sxs-lookup"><span data-stu-id="091da-330">Resumption from common language runtime suspension has ended.</span></span>|  
  
 <span data-ttu-id="091da-331">Olay verisi yok.</span><span class="sxs-lookup"><span data-stu-id="091da-331">No event data.</span></span>  
  
 [<span data-ttu-id="091da-332">Başa dön</span><span class="sxs-lookup"><span data-stu-id="091da-332">Back to top</span></span>](#top)  
  
<a name="gcsuspendee_v1_event"></a>   
## <a name="gcsuspendeev1-event"></a><span data-ttu-id="091da-333">GCSuspendEE_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="091da-333">GCSuspendEE_V1 Event</span></span>  
 <span data-ttu-id="091da-334">Aşağıdaki tablo düzeyi ve anahtar sözcüğü gösterir.</span><span class="sxs-lookup"><span data-stu-id="091da-334">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="091da-335">Olay oluşturma için anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="091da-335">Keyword for raising the event</span></span>|<span data-ttu-id="091da-336">Düzey</span><span class="sxs-lookup"><span data-stu-id="091da-336">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="091da-337">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="091da-337">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="091da-338">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="091da-338">Informational (4)</span></span>|  
  
 <span data-ttu-id="091da-339">Aşağıdaki tabloda olay bilgilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="091da-339">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="091da-340">Olay</span><span class="sxs-lookup"><span data-stu-id="091da-340">Event</span></span>|<span data-ttu-id="091da-341">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="091da-341">Event ID</span></span>|<span data-ttu-id="091da-342">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="091da-342">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCSuspendEE_V1`|<span data-ttu-id="091da-343">9</span><span class="sxs-lookup"><span data-stu-id="091da-343">9</span></span>|<span data-ttu-id="091da-344">Çöp toplama yürütme altyapısı ertelenmesi başlangıcı.</span><span class="sxs-lookup"><span data-stu-id="091da-344">Start of suspension of the execution engine for garbage collection.</span></span>|  
  
 <span data-ttu-id="091da-345">Aşağıdaki tabloda olay verilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="091da-345">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="091da-346">Alan adı</span><span class="sxs-lookup"><span data-stu-id="091da-346">Field name</span></span>|<span data-ttu-id="091da-347">Veri türü</span><span class="sxs-lookup"><span data-stu-id="091da-347">Data type</span></span>|<span data-ttu-id="091da-348">Açıklama</span><span class="sxs-lookup"><span data-stu-id="091da-348">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="091da-349">Neden</span><span class="sxs-lookup"><span data-stu-id="091da-349">Reason</span></span>|<span data-ttu-id="091da-350">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="091da-350">win:UInt16</span></span>|<span data-ttu-id="091da-351">0x0 - diğer.</span><span class="sxs-lookup"><span data-stu-id="091da-351">0x0 - Other.</span></span><br /><br /> <span data-ttu-id="091da-352">0x1 - atık toplama.</span><span class="sxs-lookup"><span data-stu-id="091da-352">0x1 - Garbage collection.</span></span><br /><br /> <span data-ttu-id="091da-353">0x2 - uygulama etki alanı kapatma.</span><span class="sxs-lookup"><span data-stu-id="091da-353">0x2 - Application domain shutdown.</span></span><br /><br /> <span data-ttu-id="091da-354">0x3 - kod pitching.</span><span class="sxs-lookup"><span data-stu-id="091da-354">0x3 - Code pitching.</span></span><br /><br /> <span data-ttu-id="091da-355">0x4 - kapatma.</span><span class="sxs-lookup"><span data-stu-id="091da-355">0x4 - Shutdown.</span></span><br /><br /> <span data-ttu-id="091da-356">0x5 - hata ayıklayıcı.</span><span class="sxs-lookup"><span data-stu-id="091da-356">0x5 - Debugger.</span></span><br /><br /> <span data-ttu-id="091da-357">0x6 - atık toplama için hazırlama.</span><span class="sxs-lookup"><span data-stu-id="091da-357">0x6 - Preparation for garbage collection.</span></span>|  
|<span data-ttu-id="091da-358">Sayısı</span><span class="sxs-lookup"><span data-stu-id="091da-358">Count</span></span>|<span data-ttu-id="091da-359">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="091da-359">win:UInt32</span></span>|<span data-ttu-id="091da-360">Zaman GC sayısı.</span><span class="sxs-lookup"><span data-stu-id="091da-360">The GC count at the time.</span></span> <span data-ttu-id="091da-361">Genellikle, bundan sonra bir sonraki GC başlangıç olayı görür ve biz çöp toplama sırasında GC dizin arttıkça sayımına bu sayı + 1 olacaktır.</span><span class="sxs-lookup"><span data-stu-id="091da-361">Usually, you would see a subsequent GC Start event after this, and its Count would be this Count + 1 as we increase the GC index during a garbage collection.</span></span>|  
|<span data-ttu-id="091da-362">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="091da-362">ClrInstanceID</span></span>|<span data-ttu-id="091da-363">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="091da-363">win:UInt16</span></span>|<span data-ttu-id="091da-364">CLR veya CoreCLR örneği için benzersiz kimlik.</span><span class="sxs-lookup"><span data-stu-id="091da-364">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="091da-365">Başa dön</span><span class="sxs-lookup"><span data-stu-id="091da-365">Back to top</span></span>](#top)  
  
<a name="gcsuspendeeend_v1_event"></a>   
## <a name="gcsuspendeeendv1-event"></a><span data-ttu-id="091da-366">GCSuspendEEEnd_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="091da-366">GCSuspendEEEnd_V1 Event</span></span>  
 <span data-ttu-id="091da-367">Aşağıdaki tablo düzeyi ve anahtar sözcüğü gösterir:</span><span class="sxs-lookup"><span data-stu-id="091da-367">The following table shows the keyword and level:</span></span>  
  
|<span data-ttu-id="091da-368">Olay oluşturma için anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="091da-368">Keyword for raising the event</span></span>|<span data-ttu-id="091da-369">Düzey</span><span class="sxs-lookup"><span data-stu-id="091da-369">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="091da-370">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="091da-370">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="091da-371">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="091da-371">Informational (4)</span></span>|  
  
 <span data-ttu-id="091da-372">Aşağıdaki tabloda olay bilgileri gösterir:</span><span class="sxs-lookup"><span data-stu-id="091da-372">The following table shows the event information:</span></span>  
  
|<span data-ttu-id="091da-373">Olay</span><span class="sxs-lookup"><span data-stu-id="091da-373">Event</span></span>|<span data-ttu-id="091da-374">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="091da-374">Event ID</span></span>|<span data-ttu-id="091da-375">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="091da-375">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCSuspendEEEnd_V1`|<span data-ttu-id="091da-376">8</span><span class="sxs-lookup"><span data-stu-id="091da-376">8</span></span>|<span data-ttu-id="091da-377">Çöp toplama yürütme altyapısı ertelenmesi sonu.</span><span class="sxs-lookup"><span data-stu-id="091da-377">End of suspension of the execution engine for garbage collection.</span></span>|  
  
 <span data-ttu-id="091da-378">Olay verisi yok.</span><span class="sxs-lookup"><span data-stu-id="091da-378">No event data.</span></span>  
  
 [<span data-ttu-id="091da-379">Başa dön</span><span class="sxs-lookup"><span data-stu-id="091da-379">Back to top</span></span>](#top)  
  
<a name="gcallocationtick_v2_event"></a>   
## <a name="gcallocationtickv2-event"></a><span data-ttu-id="091da-380">GCAllocationTick_V2 olayı</span><span class="sxs-lookup"><span data-stu-id="091da-380">GCAllocationTick_V2 Event</span></span>  
 <span data-ttu-id="091da-381">Aşağıdaki tablo düzeyi ve anahtar sözcüğü gösterir.</span><span class="sxs-lookup"><span data-stu-id="091da-381">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="091da-382">Olay oluşturma için anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="091da-382">Keyword for raising the event</span></span>|<span data-ttu-id="091da-383">Düzey</span><span class="sxs-lookup"><span data-stu-id="091da-383">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="091da-384">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="091da-384">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="091da-385">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="091da-385">Informational (4)</span></span>|  
  
 <span data-ttu-id="091da-386">Aşağıdaki tabloda olay bilgilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="091da-386">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="091da-387">Olay</span><span class="sxs-lookup"><span data-stu-id="091da-387">Event</span></span>|<span data-ttu-id="091da-388">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="091da-388">Event ID</span></span>|<span data-ttu-id="091da-389">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="091da-389">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCAllocationTick_V2`|<span data-ttu-id="091da-390">10</span><span class="sxs-lookup"><span data-stu-id="091da-390">10</span></span>|<span data-ttu-id="091da-391">Her seferinde yaklaşık 100 KB tahsis edilir.</span><span class="sxs-lookup"><span data-stu-id="091da-391">Each time approximately 100 KB is allocated.</span></span>|  
  
 <span data-ttu-id="091da-392">Aşağıdaki tabloda olay verilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="091da-392">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="091da-393">Alan adı</span><span class="sxs-lookup"><span data-stu-id="091da-393">Field name</span></span>|<span data-ttu-id="091da-394">Veri türü</span><span class="sxs-lookup"><span data-stu-id="091da-394">Data type</span></span>|<span data-ttu-id="091da-395">Açıklama</span><span class="sxs-lookup"><span data-stu-id="091da-395">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="091da-396">AllocationAmount</span><span class="sxs-lookup"><span data-stu-id="091da-396">AllocationAmount</span></span>|<span data-ttu-id="091da-397">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="091da-397">win:UInt32</span></span>|<span data-ttu-id="091da-398">Ayırma bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="091da-398">The allocation size, in bytes.</span></span> <span data-ttu-id="091da-399">Bu değer, ULONG (4,294,967,295 bayt) uzunluğundan daha küçük olan ayırma için doğrudur.</span><span class="sxs-lookup"><span data-stu-id="091da-399">This value is accurate for allocations that are less than the length of a ULONG (4,294,967,295 bytes).</span></span> <span data-ttu-id="091da-400">Ayırma büyükse, bu alan kesilmiş değer içerir.</span><span class="sxs-lookup"><span data-stu-id="091da-400">If the allocation is greater, this field contains a truncated value.</span></span> <span data-ttu-id="091da-401">Kullanım `AllocationAmount64` için çok büyük ayırma.</span><span class="sxs-lookup"><span data-stu-id="091da-401">Use `AllocationAmount64` for very large allocations.</span></span>|  
|<span data-ttu-id="091da-402">AllocationKind</span><span class="sxs-lookup"><span data-stu-id="091da-402">AllocationKind</span></span>|<span data-ttu-id="091da-403">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="091da-403">win:UInt32</span></span>|<span data-ttu-id="091da-404">0x0 - küçük nesne ayırma (küçük nesne yığın ayırma'dir).</span><span class="sxs-lookup"><span data-stu-id="091da-404">0x0 - Small object allocation (allocation is in small object heap).</span></span><br /><br /> <span data-ttu-id="091da-405">0x1 - büyük nesne ayırma (büyük nesne yığın ayırma'dir).</span><span class="sxs-lookup"><span data-stu-id="091da-405">0x1 - Large object allocation (allocation is in large object heap).</span></span>|  
|<span data-ttu-id="091da-406">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="091da-406">ClrInstanceID</span></span>|<span data-ttu-id="091da-407">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="091da-407">win:UInt16</span></span>|<span data-ttu-id="091da-408">CLR veya CoreCLR örneği için benzersiz kimlik.</span><span class="sxs-lookup"><span data-stu-id="091da-408">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
|<span data-ttu-id="091da-409">AllocationAmount64</span><span class="sxs-lookup"><span data-stu-id="091da-409">AllocationAmount64</span></span>|<span data-ttu-id="091da-410">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="091da-410">win:UInt64</span></span>|<span data-ttu-id="091da-411">Ayırma bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="091da-411">The allocation size, in bytes.</span></span> <span data-ttu-id="091da-412">Bu değer çok büyük ayırmalarını doğru olur.</span><span class="sxs-lookup"><span data-stu-id="091da-412">This value is accurate for very large allocations.</span></span>|  
|<span data-ttu-id="091da-413">TypeId</span><span class="sxs-lookup"><span data-stu-id="091da-413">TypeId</span></span>|<span data-ttu-id="091da-414">Win: işaretçi</span><span class="sxs-lookup"><span data-stu-id="091da-414">win:Pointer</span></span>|<span data-ttu-id="091da-415">MethodTable adresi.</span><span class="sxs-lookup"><span data-stu-id="091da-415">The address of the MethodTable.</span></span> <span data-ttu-id="091da-416">Bu olay sırasında ayrılan nesneleri çeşitli olduğunda, bu son (100 KB eşiği aşıldı nedeniyle nesne) ayrılmış nesne karşılık gelen MethodTable adresidir.</span><span class="sxs-lookup"><span data-stu-id="091da-416">When there are several types of objects that were allocated during this event, this is the address of the MethodTable that corresponds to the last object allocated (the object that caused the 100 KB threshold to be exceeded).</span></span>|  
|<span data-ttu-id="091da-417">TypeName</span><span class="sxs-lookup"><span data-stu-id="091da-417">TypeName</span></span>|<span data-ttu-id="091da-418">Win: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="091da-418">win:UnicodeString</span></span>|<span data-ttu-id="091da-419">Ayrıldı türünün adı.</span><span class="sxs-lookup"><span data-stu-id="091da-419">The name of the type that was allocated.</span></span> <span data-ttu-id="091da-420">Bu olay sırasında ayrılan nesneleri çeşitli olduğunda (100 KB eşiği aşıldı nedeniyle nesne) tahsis son nesnesinin türü budur.</span><span class="sxs-lookup"><span data-stu-id="091da-420">When there are several types of objects that were allocated during this event, this is the type of the last object allocated (the object that caused the 100 KB threshold to be exceeded).</span></span>|  
|<span data-ttu-id="091da-421">HeapIndex</span><span class="sxs-lookup"><span data-stu-id="091da-421">HeapIndex</span></span>|<span data-ttu-id="091da-422">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="091da-422">win:UInt32</span></span>|<span data-ttu-id="091da-423">Burada nesne ayrıldı yığın.</span><span class="sxs-lookup"><span data-stu-id="091da-423">The heap where the object was allocated.</span></span> <span data-ttu-id="091da-424">Bu değer, iş istasyonu çöp toplama ile çalışırken 0 (sıfır) olur.</span><span class="sxs-lookup"><span data-stu-id="091da-424">This value is 0 (zero) when running with workstation garbage collection.</span></span>|  
  
 [<span data-ttu-id="091da-425">Başa dön</span><span class="sxs-lookup"><span data-stu-id="091da-425">Back to top</span></span>](#top)  
  
<a name="gcfinalizersbegin_v1_event"></a>   
## <a name="gcfinalizersbeginv1-event"></a><span data-ttu-id="091da-426">GCFinalizersBegin_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="091da-426">GCFinalizersBegin_V1 Event</span></span>  
 <span data-ttu-id="091da-427">Aşağıdaki tablo düzeyi ve anahtar sözcüğü gösterir.</span><span class="sxs-lookup"><span data-stu-id="091da-427">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="091da-428">Olay oluşturma için anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="091da-428">Keyword for raising the event</span></span>|<span data-ttu-id="091da-429">Düzey</span><span class="sxs-lookup"><span data-stu-id="091da-429">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="091da-430">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="091da-430">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="091da-431">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="091da-431">Informational (4)</span></span>|  
  
 <span data-ttu-id="091da-432">Aşağıdaki tabloda olay bilgilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="091da-432">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="091da-433">Olay</span><span class="sxs-lookup"><span data-stu-id="091da-433">Event</span></span>|<span data-ttu-id="091da-434">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="091da-434">Event ID</span></span>|<span data-ttu-id="091da-435">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="091da-435">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCFinalizersBegin_V1`|<span data-ttu-id="091da-436">14</span><span class="sxs-lookup"><span data-stu-id="091da-436">14</span></span>|<span data-ttu-id="091da-437">Sonlandırıcılar çalıştıran başlangıcı.</span><span class="sxs-lookup"><span data-stu-id="091da-437">The start of running finalizers.</span></span>|  
  
 <span data-ttu-id="091da-438">Olay verisi yok.</span><span class="sxs-lookup"><span data-stu-id="091da-438">No event data.</span></span>  
  
 [<span data-ttu-id="091da-439">Başa dön</span><span class="sxs-lookup"><span data-stu-id="091da-439">Back to top</span></span>](#top)  
  
<a name="gcfinalizersend_v1_event"></a>   
## <a name="gcfinalizersendv1-event"></a><span data-ttu-id="091da-440">GCFinalizersEnd_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="091da-440">GCFinalizersEnd_V1 Event</span></span>  
 <span data-ttu-id="091da-441">Aşağıdaki tablo düzeyi ve anahtar sözcüğü gösterir.</span><span class="sxs-lookup"><span data-stu-id="091da-441">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="091da-442">Olay oluşturma için anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="091da-442">Keyword for raising the event</span></span>|<span data-ttu-id="091da-443">Düzey</span><span class="sxs-lookup"><span data-stu-id="091da-443">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="091da-444">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="091da-444">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="091da-445">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="091da-445">Informational (4)</span></span>|  
  
 <span data-ttu-id="091da-446">Aşağıdaki tabloda olay bilgilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="091da-446">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="091da-447">Olay</span><span class="sxs-lookup"><span data-stu-id="091da-447">Event</span></span>|<span data-ttu-id="091da-448">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="091da-448">Event ID</span></span>|<span data-ttu-id="091da-449">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="091da-449">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCFinalizersEnd_V1`|<span data-ttu-id="091da-450">13</span><span class="sxs-lookup"><span data-stu-id="091da-450">13</span></span>|<span data-ttu-id="091da-451">Sonlandırıcılar çalıştıran sonu.</span><span class="sxs-lookup"><span data-stu-id="091da-451">The end of running finalizers.</span></span>|  
  
 <span data-ttu-id="091da-452">Aşağıdaki tabloda olay verilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="091da-452">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="091da-453">Alan adı</span><span class="sxs-lookup"><span data-stu-id="091da-453">Field name</span></span>|<span data-ttu-id="091da-454">Veri türü</span><span class="sxs-lookup"><span data-stu-id="091da-454">Data type</span></span>|<span data-ttu-id="091da-455">Açıklama</span><span class="sxs-lookup"><span data-stu-id="091da-455">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="091da-456">Sayısı</span><span class="sxs-lookup"><span data-stu-id="091da-456">Count</span></span>|<span data-ttu-id="091da-457">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="091da-457">win:UInt32</span></span>|<span data-ttu-id="091da-458">Çalıştırılan sonlandırıcılar sayısı.</span><span class="sxs-lookup"><span data-stu-id="091da-458">The number of finalizers that were run.</span></span>|  
|<span data-ttu-id="091da-459">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="091da-459">ClrInstanceID</span></span>|<span data-ttu-id="091da-460">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="091da-460">win:UInt16</span></span>|<span data-ttu-id="091da-461">CLR veya CoreCLR örneği için benzersiz kimlik.</span><span class="sxs-lookup"><span data-stu-id="091da-461">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="091da-462">Başa dön</span><span class="sxs-lookup"><span data-stu-id="091da-462">Back to top</span></span>](#top)  
  
<a name="gccreateconcurrentthread_v1_event"></a>   
## <a name="gccreateconcurrentthreadv1-event"></a><span data-ttu-id="091da-463">GCCreateConcurrentThread_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="091da-463">GCCreateConcurrentThread_V1 Event</span></span>  
 <span data-ttu-id="091da-464">Aşağıdaki tablo düzeyi ve anahtar sözcüğü gösterir.</span><span class="sxs-lookup"><span data-stu-id="091da-464">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="091da-465">Olay oluşturma için anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="091da-465">Keyword for raising the event</span></span>|<span data-ttu-id="091da-466">Düzey</span><span class="sxs-lookup"><span data-stu-id="091da-466">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="091da-467">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="091da-467">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="091da-468">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="091da-468">Informational (4)</span></span>|  
|<span data-ttu-id="091da-469">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="091da-469">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="091da-470">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="091da-470">Informational (4)</span></span>|  
  
 <span data-ttu-id="091da-471">Aşağıdaki tabloda olay bilgilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="091da-471">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="091da-472">Olay</span><span class="sxs-lookup"><span data-stu-id="091da-472">Event</span></span>|<span data-ttu-id="091da-473">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="091da-473">Event ID</span></span>|<span data-ttu-id="091da-474">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="091da-474">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCCreateConcurrentThread_V1`|<span data-ttu-id="091da-475">11</span><span class="sxs-lookup"><span data-stu-id="091da-475">11</span></span>|<span data-ttu-id="091da-476">Eşzamanlı atık toplama iş parçacığı oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="091da-476">Concurrent garbage collection thread was created.</span></span>|  
  
 <span data-ttu-id="091da-477">Olay verisi yok.</span><span class="sxs-lookup"><span data-stu-id="091da-477">No event data.</span></span>  
  
 [<span data-ttu-id="091da-478">Başa dön</span><span class="sxs-lookup"><span data-stu-id="091da-478">Back to top</span></span>](#top)  
  
<a name="gcterminateconcurrentthread_v1_event"></a>   
## <a name="gcterminateconcurrentthreadv1-event"></a><span data-ttu-id="091da-479">GCTerminateConcurrentThread_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="091da-479">GCTerminateConcurrentThread_V1 Event</span></span>  
 <span data-ttu-id="091da-480">Aşağıdaki tablo düzeyi ve anahtar sözcüğü gösterir.</span><span class="sxs-lookup"><span data-stu-id="091da-480">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="091da-481">Olay oluşturma için anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="091da-481">Keyword for raising the event</span></span>|<span data-ttu-id="091da-482">Düzey</span><span class="sxs-lookup"><span data-stu-id="091da-482">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="091da-483">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="091da-483">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="091da-484">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="091da-484">Informational (4)</span></span>|  
|<span data-ttu-id="091da-485">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="091da-485">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="091da-486">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="091da-486">Informational (4)</span></span>|  
  
 <span data-ttu-id="091da-487">Aşağıdaki tabloda olay bilgilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="091da-487">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="091da-488">Olay</span><span class="sxs-lookup"><span data-stu-id="091da-488">Event</span></span>|<span data-ttu-id="091da-489">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="091da-489">Event ID</span></span>|<span data-ttu-id="091da-490">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="091da-490">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCTerminateConcurrentThread_V1`|<span data-ttu-id="091da-491">12</span><span class="sxs-lookup"><span data-stu-id="091da-491">12</span></span>|<span data-ttu-id="091da-492">Eşzamanlı atık toplama iş parçacığı sona erdirildi.</span><span class="sxs-lookup"><span data-stu-id="091da-492">Concurrent garbage collection thread was terminated.</span></span>|  
  
 <span data-ttu-id="091da-493">Olay verisi yok.</span><span class="sxs-lookup"><span data-stu-id="091da-493">No event data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="091da-494">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="091da-494">See Also</span></span>  
 [<span data-ttu-id="091da-495">CLR ETW Olayları</span><span class="sxs-lookup"><span data-stu-id="091da-495">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
