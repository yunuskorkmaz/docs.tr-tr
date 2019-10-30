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
ms.openlocfilehash: cd4a4699f115c5b134ea60e703607ff36c229a78
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040576"
---
# <a name="garbage-collection-etw-events"></a><span data-ttu-id="98a79-102">Çöp Toplama ETW Olayları</span><span class="sxs-lookup"><span data-stu-id="98a79-102">Garbage Collection ETW Events</span></span>

<span data-ttu-id="98a79-103">Bu olaylar çöp koleksiyonuyla ilgili bilgiler toplar.</span><span class="sxs-lookup"><span data-stu-id="98a79-103">These events collect information pertaining to garbage collection.</span></span> <span data-ttu-id="98a79-104">Çöp toplamanın kaç kez gerçekleştirildiğini, çöp toplama sırasında ne kadar bellek serbest olduğunu ve bu şekilde ne kadar bellek kaldığını belirleme dahil, tanılama ve hata ayıklamada yardımcı olurlar.</span><span class="sxs-lookup"><span data-stu-id="98a79-104">They help in diagnostics and debugging, including determining how many times garbage collection was performed, how much memory was freed during garbage collection, and so on.</span></span>

<span data-ttu-id="98a79-105">Bu kategori aşağıdaki olaylardan oluşur:</span><span class="sxs-lookup"><span data-stu-id="98a79-105">This category consists of the following events:</span></span>

- [<span data-ttu-id="98a79-106">GCStart_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="98a79-106">GCStart_V1 Event</span></span>](#gcstart_v1-event)
- [<span data-ttu-id="98a79-107">GCEnd_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="98a79-107">GCEnd_V1 Event</span></span>](#gcend_v1-event)
- [<span data-ttu-id="98a79-108">GCHeapStats_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="98a79-108">GCHeapStats_V1 Event</span></span>](#gcheapstats_v1-event)
- [<span data-ttu-id="98a79-109">GCCreateSegment_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="98a79-109">GCCreateSegment_V1 Event</span></span>](#gccreatesegment_v1-event)
- [<span data-ttu-id="98a79-110">GCFreeSegment_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="98a79-110">GCFreeSegment_V1 Event</span></span>](#gcfreesegment_v1-event)
- [<span data-ttu-id="98a79-111">GCRestartEEBegin_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="98a79-111">GCRestartEEBegin_V1 Event</span></span>](#gcrestarteebegin_v1-event)
- [<span data-ttu-id="98a79-112">GCRestartEEEnd_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="98a79-112">GCRestartEEEnd_V1 Event</span></span>](#gcrestarteeend_v1-event)
- [<span data-ttu-id="98a79-113">GCSuspendEE_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="98a79-113">GCSuspendEE_V1 Event</span></span>](#gcsuspendee_v1-event)
- [<span data-ttu-id="98a79-114">GCSuspendEEEnd_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="98a79-114">GCSuspendEEEnd_V1 Event</span></span>](#gcsuspendeeend_v1-event)
- [<span data-ttu-id="98a79-115">GCAllocationTick_V2 olayı</span><span class="sxs-lookup"><span data-stu-id="98a79-115">GCAllocationTick_V2 Event</span></span>](#gcallocationtick_v2-event)
- [<span data-ttu-id="98a79-116">GCFinalizersBegin_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="98a79-116">GCFinalizersBegin_V1 Event</span></span>](#gcfinalizersbegin_v1-event)
- [<span data-ttu-id="98a79-117">GCFinalizersEnd_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="98a79-117">GCFinalizersEnd_V1 Event</span></span>](#gcfinalizersend_v1-event)
- [<span data-ttu-id="98a79-118">GCCreateConcurrentThread_V1 Olayı</span><span class="sxs-lookup"><span data-stu-id="98a79-118">GCCreateConcurrentThread_V1 Event</span></span>](#gccreateconcurrentthread_v1-event)
- [<span data-ttu-id="98a79-119">GCTerminateConcurrentThread_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="98a79-119">GCTerminateConcurrentThread_V1 Event</span></span>](#gcterminateconcurrentthread_v1-event)

## <a name="gcstart_v1-event"></a><span data-ttu-id="98a79-120">GCStart_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="98a79-120">GCStart_V1 Event</span></span>  

<span data-ttu-id="98a79-121">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="98a79-121">The following table shows the keyword and level.</span></span> <span data-ttu-id="98a79-122">Daha fazla bilgi için bkz. [CLR ETW anahtar sözcükleri ve düzeyleri](clr-etw-keywords-and-levels.md).</span><span class="sxs-lookup"><span data-stu-id="98a79-122">For more information, see [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).</span></span>

|<span data-ttu-id="98a79-123">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="98a79-123">Keyword for raising the event</span></span>|<span data-ttu-id="98a79-124">Düzey</span><span class="sxs-lookup"><span data-stu-id="98a79-124">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="98a79-125">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="98a79-125">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="98a79-126">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="98a79-126">Informational (4)</span></span>|

<span data-ttu-id="98a79-127">Aşağıdaki tabloda olay bilgileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="98a79-127">The following table shows the event information:</span></span>

|<span data-ttu-id="98a79-128">Olay</span><span class="sxs-lookup"><span data-stu-id="98a79-128">Event</span></span>|<span data-ttu-id="98a79-129">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="98a79-129">Event ID</span></span>|<span data-ttu-id="98a79-130">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="98a79-130">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCStart_V1`|<span data-ttu-id="98a79-131">1\.</span><span class="sxs-lookup"><span data-stu-id="98a79-131">1</span></span>|<span data-ttu-id="98a79-132">Çöp toplama işlemi başlatıldı.</span><span class="sxs-lookup"><span data-stu-id="98a79-132">A garbage collection has started.</span></span>|

<span data-ttu-id="98a79-133">Aşağıdaki tabloda olay verileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="98a79-133">The following table shows the event data:</span></span>

|<span data-ttu-id="98a79-134">alan adı</span><span class="sxs-lookup"><span data-stu-id="98a79-134">Field name</span></span>|<span data-ttu-id="98a79-135">Veri türü</span><span class="sxs-lookup"><span data-stu-id="98a79-135">Data type</span></span>|<span data-ttu-id="98a79-136">Açıklama</span><span class="sxs-lookup"><span data-stu-id="98a79-136">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="98a79-137">Biriktirme</span><span class="sxs-lookup"><span data-stu-id="98a79-137">Count</span></span>|<span data-ttu-id="98a79-138">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="98a79-138">win:UInt32</span></span>|<span data-ttu-id="98a79-139">*N*. çöp toplama.</span><span class="sxs-lookup"><span data-stu-id="98a79-139">The *n*th garbage collection.</span></span>|
|<span data-ttu-id="98a79-140">Derinliğini</span><span class="sxs-lookup"><span data-stu-id="98a79-140">Depth</span></span>|<span data-ttu-id="98a79-141">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="98a79-141">win:UInt32</span></span>|<span data-ttu-id="98a79-142">Toplanmakta olan oluşturma.</span><span class="sxs-lookup"><span data-stu-id="98a79-142">The generation that is being collected.</span></span>|
|<span data-ttu-id="98a79-143">Neden</span><span class="sxs-lookup"><span data-stu-id="98a79-143">Reason</span></span>|<span data-ttu-id="98a79-144">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="98a79-144">win:UInt32</span></span>|<span data-ttu-id="98a79-145">Çöp toplamanın neden tetiklendiği:</span><span class="sxs-lookup"><span data-stu-id="98a79-145">Why the garbage collection was triggered:</span></span><br /><br /> <span data-ttu-id="98a79-146">0x0-küçük nesne yığını ayırması.</span><span class="sxs-lookup"><span data-stu-id="98a79-146">0x0 - Small object heap allocation.</span></span><br /><br /> <span data-ttu-id="98a79-147">0x1-alınmış.</span><span class="sxs-lookup"><span data-stu-id="98a79-147">0x1 - Induced.</span></span><br /><br /> <span data-ttu-id="98a79-148">0x2-düşük bellek.</span><span class="sxs-lookup"><span data-stu-id="98a79-148">0x2 - Low memory.</span></span><br /><br /> <span data-ttu-id="98a79-149">0x3-boş.</span><span class="sxs-lookup"><span data-stu-id="98a79-149">0x3 - Empty.</span></span><br /><br /> <span data-ttu-id="98a79-150">0x4-büyük nesne yığını ayırması.</span><span class="sxs-lookup"><span data-stu-id="98a79-150">0x4 - Large object heap allocation.</span></span><br /><br /> <span data-ttu-id="98a79-151">0x5-alan kalmadı (küçük nesne yığını için).</span><span class="sxs-lookup"><span data-stu-id="98a79-151">0x5 - Out of space (for small object heap).</span></span><br /><br /> <span data-ttu-id="98a79-152">0x6-alan kalmadı (büyük nesne yığını için).</span><span class="sxs-lookup"><span data-stu-id="98a79-152">0x6 - Out of space (for large object heap).</span></span><br /><br /> <span data-ttu-id="98a79-153">0x7-alınmış ancak engelleme olarak zorlanmadı.</span><span class="sxs-lookup"><span data-stu-id="98a79-153">0x7 - Induced but not forced as blocking.</span></span>|
|<span data-ttu-id="98a79-154">Tür</span><span class="sxs-lookup"><span data-stu-id="98a79-154">Type</span></span>|<span data-ttu-id="98a79-155">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="98a79-155">win:UInt32</span></span>|<span data-ttu-id="98a79-156">0x0-arka plan atık toplama dışında bir çöp toplama engelleme gerçekleşti.</span><span class="sxs-lookup"><span data-stu-id="98a79-156">0x0 - Blocking garbage collection occurred outside background garbage collection.</span></span><br /><br /> <span data-ttu-id="98a79-157">0x1-arka plan atık toplama.</span><span class="sxs-lookup"><span data-stu-id="98a79-157">0x1 - Background garbage collection.</span></span><br /><br /> <span data-ttu-id="98a79-158">0x2-arka plan atık toplama sırasında atık toplamayı engelleme oluştu.</span><span class="sxs-lookup"><span data-stu-id="98a79-158">0x2 - Blocking garbage collection occurred during background garbage collection.</span></span>|
|<span data-ttu-id="98a79-159">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="98a79-159">ClrInstanceID</span></span>|<span data-ttu-id="98a79-160">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="98a79-160">win:UInt16</span></span>|<span data-ttu-id="98a79-161">CLR veya CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="98a79-161">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="gcend_v1-event"></a><span data-ttu-id="98a79-162">GCEnd_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="98a79-162">GCEnd_V1 Event</span></span>

<span data-ttu-id="98a79-163">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="98a79-163">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="98a79-164">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="98a79-164">Keyword for raising the event</span></span>|<span data-ttu-id="98a79-165">Düzey</span><span class="sxs-lookup"><span data-stu-id="98a79-165">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="98a79-166">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="98a79-166">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="98a79-167">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="98a79-167">Informational (4)</span></span>|

<span data-ttu-id="98a79-168">Aşağıdaki tabloda olay bilgileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="98a79-168">The following table shows the event information:</span></span>

|<span data-ttu-id="98a79-169">Olay</span><span class="sxs-lookup"><span data-stu-id="98a79-169">Event</span></span>|<span data-ttu-id="98a79-170">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="98a79-170">Event ID</span></span>|<span data-ttu-id="98a79-171">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="98a79-171">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCEnd_V1`|<span data-ttu-id="98a79-172">2</span><span class="sxs-lookup"><span data-stu-id="98a79-172">2</span></span>|<span data-ttu-id="98a79-173">Çöp toplama sona erdi.</span><span class="sxs-lookup"><span data-stu-id="98a79-173">The garbage collection has ended.</span></span>|

<span data-ttu-id="98a79-174">Aşağıdaki tabloda olay verileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="98a79-174">The following table shows the event data:</span></span>

|<span data-ttu-id="98a79-175">alan adı</span><span class="sxs-lookup"><span data-stu-id="98a79-175">Field name</span></span>|<span data-ttu-id="98a79-176">Veri türü</span><span class="sxs-lookup"><span data-stu-id="98a79-176">Data type</span></span>|<span data-ttu-id="98a79-177">Açıklama</span><span class="sxs-lookup"><span data-stu-id="98a79-177">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="98a79-178">Biriktirme</span><span class="sxs-lookup"><span data-stu-id="98a79-178">Count</span></span>|<span data-ttu-id="98a79-179">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="98a79-179">win:UInt32</span></span>|<span data-ttu-id="98a79-180">*N*. çöp toplama.</span><span class="sxs-lookup"><span data-stu-id="98a79-180">The *n*th garbage collection.</span></span>|
|<span data-ttu-id="98a79-181">Derinliğini</span><span class="sxs-lookup"><span data-stu-id="98a79-181">Depth</span></span>|<span data-ttu-id="98a79-182">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="98a79-182">win:UInt32</span></span>|<span data-ttu-id="98a79-183">Toplanan nesil.</span><span class="sxs-lookup"><span data-stu-id="98a79-183">The generation that was collected.</span></span>|
|<span data-ttu-id="98a79-184">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="98a79-184">ClrInstanceID</span></span>|<span data-ttu-id="98a79-185">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="98a79-185">win:UInt16</span></span>|<span data-ttu-id="98a79-186">CLR veya CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="98a79-186">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="gcheapstats_v1-event"></a><span data-ttu-id="98a79-187">GCHeapStats_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="98a79-187">GCHeapStats_V1 Event</span></span>

<span data-ttu-id="98a79-188">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="98a79-188">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="98a79-189">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="98a79-189">Keyword for raising the event</span></span>|<span data-ttu-id="98a79-190">Düzey</span><span class="sxs-lookup"><span data-stu-id="98a79-190">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="98a79-191">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="98a79-191">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="98a79-192">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="98a79-192">Informational (4)</span></span>|

<span data-ttu-id="98a79-193">Aşağıdaki tabloda olay bilgileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="98a79-193">The following table shows the event information:</span></span>

|<span data-ttu-id="98a79-194">Olay</span><span class="sxs-lookup"><span data-stu-id="98a79-194">Event</span></span>|<span data-ttu-id="98a79-195">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="98a79-195">Event ID</span></span>|<span data-ttu-id="98a79-196">Açıklama</span><span class="sxs-lookup"><span data-stu-id="98a79-196">Description</span></span>|
|-----------|--------------|-----------------|
|`GCHeapStats_V1`|<span data-ttu-id="98a79-197">4</span><span class="sxs-lookup"><span data-stu-id="98a79-197">4</span></span>|<span data-ttu-id="98a79-198">Her çöp toplamanın sonundaki yığın istatistiklerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="98a79-198">Shows the heap statistics at the end of each garbage collection.</span></span>|

<span data-ttu-id="98a79-199">Aşağıdaki tabloda olay verileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="98a79-199">The following table shows the event data:</span></span>

|<span data-ttu-id="98a79-200">alan adı</span><span class="sxs-lookup"><span data-stu-id="98a79-200">Field name</span></span>|<span data-ttu-id="98a79-201">Veri türü</span><span class="sxs-lookup"><span data-stu-id="98a79-201">Data type</span></span>|<span data-ttu-id="98a79-202">Açıklama</span><span class="sxs-lookup"><span data-stu-id="98a79-202">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="98a79-203">GenerationSize0</span><span class="sxs-lookup"><span data-stu-id="98a79-203">GenerationSize0</span></span>|<span data-ttu-id="98a79-204">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="98a79-204">win:UInt64</span></span>|<span data-ttu-id="98a79-205">0\. nesil belleğin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="98a79-205">The size, in bytes, of generation 0 memory.</span></span>|
|<span data-ttu-id="98a79-206">TotalPromotedSize0</span><span class="sxs-lookup"><span data-stu-id="98a79-206">TotalPromotedSize0</span></span>|<span data-ttu-id="98a79-207">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="98a79-207">win:UInt64</span></span>|<span data-ttu-id="98a79-208">Nesil 0 ' dan 1 ' e yükseltilen bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="98a79-208">The number of bytes that are promoted from generation 0 to generation 1.</span></span>|
|<span data-ttu-id="98a79-209">GenerationSize1</span><span class="sxs-lookup"><span data-stu-id="98a79-209">GenerationSize1</span></span>|<span data-ttu-id="98a79-210">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="98a79-210">win:UInt64</span></span>|<span data-ttu-id="98a79-211">1\. nesil belleğin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="98a79-211">The size, in bytes, of generation 1 memory.</span></span>|
|<span data-ttu-id="98a79-212">TotalPromotedSize1</span><span class="sxs-lookup"><span data-stu-id="98a79-212">TotalPromotedSize1</span></span>|<span data-ttu-id="98a79-213">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="98a79-213">win:UInt64</span></span>|<span data-ttu-id="98a79-214">1\. nesil 2 ' ye kadar yükseltilen bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="98a79-214">The number of bytes that are promoted from generation 1 to generation 2.</span></span>|
|<span data-ttu-id="98a79-215">GenerationSize2</span><span class="sxs-lookup"><span data-stu-id="98a79-215">GenerationSize2</span></span>|<span data-ttu-id="98a79-216">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="98a79-216">win:UInt64</span></span>|<span data-ttu-id="98a79-217">2\. nesil belleğin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="98a79-217">The size, in bytes, of generation 2 memory.</span></span>|
|<span data-ttu-id="98a79-218">TotalPromotedSize2</span><span class="sxs-lookup"><span data-stu-id="98a79-218">TotalPromotedSize2</span></span>|<span data-ttu-id="98a79-219">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="98a79-219">win:UInt64</span></span>|<span data-ttu-id="98a79-220">Son koleksiyondan sonra 2. nesil üzerinde kalan bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="98a79-220">The number of bytes that survived in generation 2 after the last collection.</span></span>|
|<span data-ttu-id="98a79-221">GenerationSize3</span><span class="sxs-lookup"><span data-stu-id="98a79-221">GenerationSize3</span></span>|<span data-ttu-id="98a79-222">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="98a79-222">win:UInt64</span></span>|<span data-ttu-id="98a79-223">Büyük nesne yığınının bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="98a79-223">The size, in bytes, of the large object heap.</span></span>|
|<span data-ttu-id="98a79-224">TotalPromotedSize3</span><span class="sxs-lookup"><span data-stu-id="98a79-224">TotalPromotedSize3</span></span>|<span data-ttu-id="98a79-225">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="98a79-225">win:UInt64</span></span>|<span data-ttu-id="98a79-226">Son koleksiyondan sonra büyük nesne yığınında kalan bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="98a79-226">The number of bytes that survived in the large object heap after the last collection.</span></span>|
|<span data-ttu-id="98a79-227">Sonlandırizationpromotedsize</span><span class="sxs-lookup"><span data-stu-id="98a79-227">FinalizationPromotedSize</span></span>|<span data-ttu-id="98a79-228">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="98a79-228">win:UInt64</span></span>|<span data-ttu-id="98a79-229">Sonlandırma için hazırlanma nesnelerinin bayt cinsinden toplam boyutu.</span><span class="sxs-lookup"><span data-stu-id="98a79-229">The total size, in bytes, of the objects that are ready for finalization.</span></span>|
|<span data-ttu-id="98a79-230">Sonlandırizationpromotedcount</span><span class="sxs-lookup"><span data-stu-id="98a79-230">FinalizationPromotedCount</span></span>|<span data-ttu-id="98a79-231">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="98a79-231">win:UInt64</span></span>|<span data-ttu-id="98a79-232">Sonlandırmaya hazırlanma nesne sayısı.</span><span class="sxs-lookup"><span data-stu-id="98a79-232">The number of objects that are ready for finalization.</span></span>|
|<span data-ttu-id="98a79-233">PinnedObjectCount</span><span class="sxs-lookup"><span data-stu-id="98a79-233">PinnedObjectCount</span></span>|<span data-ttu-id="98a79-234">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="98a79-234">win:UInt32</span></span>|<span data-ttu-id="98a79-235">Sabitlenmiş (taşınamaz) nesne sayısı.</span><span class="sxs-lookup"><span data-stu-id="98a79-235">The number of pinned (unmovable) objects.</span></span>|
|<span data-ttu-id="98a79-236">SinkBlockCount</span><span class="sxs-lookup"><span data-stu-id="98a79-236">SinkBlockCount</span></span>|<span data-ttu-id="98a79-237">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="98a79-237">win:UInt32</span></span>|<span data-ttu-id="98a79-238">Kullanımdaki eşitleme bloklarının sayısı.</span><span class="sxs-lookup"><span data-stu-id="98a79-238">The number of synchronization blocks in use.</span></span>|
|<span data-ttu-id="98a79-239">Gchandlet sayısı</span><span class="sxs-lookup"><span data-stu-id="98a79-239">GCHandleCount</span></span>|<span data-ttu-id="98a79-240">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="98a79-240">win:UInt32</span></span>|<span data-ttu-id="98a79-241">Kullanımdaki çöp toplama tanıtıcılarının sayısı.</span><span class="sxs-lookup"><span data-stu-id="98a79-241">The number of garbage collection handles in use.</span></span>|
|<span data-ttu-id="98a79-242">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="98a79-242">ClrInstanceID</span></span>|<span data-ttu-id="98a79-243">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="98a79-243">win:UInt16</span></span>|<span data-ttu-id="98a79-244">CLR veya CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="98a79-244">Unique ID for the instance of CLR or CoreCLR.</span></span>|
  
## <a name="gccreatesegment_v1-event"></a><span data-ttu-id="98a79-245">GCCreateSegment_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="98a79-245">GCCreateSegment_V1 Event</span></span>

<span data-ttu-id="98a79-246">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="98a79-246">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="98a79-247">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="98a79-247">Keyword for raising the event</span></span>|<span data-ttu-id="98a79-248">Düzey</span><span class="sxs-lookup"><span data-stu-id="98a79-248">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="98a79-249">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="98a79-249">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="98a79-250">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="98a79-250">Informational (4)</span></span>|

<span data-ttu-id="98a79-251">Aşağıdaki tabloda olay bilgileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="98a79-251">The following table shows the event information:</span></span>

|<span data-ttu-id="98a79-252">Olay</span><span class="sxs-lookup"><span data-stu-id="98a79-252">Event</span></span>|<span data-ttu-id="98a79-253">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="98a79-253">Event ID</span></span>|<span data-ttu-id="98a79-254">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="98a79-254">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCCreateSegment_V1`|<span data-ttu-id="98a79-255">5</span><span class="sxs-lookup"><span data-stu-id="98a79-255">5</span></span>|<span data-ttu-id="98a79-256">Yeni bir atık toplama segmenti oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="98a79-256">A new garbage collection segment has been created.</span></span> <span data-ttu-id="98a79-257">Ayrıca, izleme zaten çalışmakta olan bir işlemde etkinleştirildiğinde, bu olay varolan her segment için oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="98a79-257">In addition, when tracing is enabled on a process that is already running, this event is raised for each existing segment.</span></span>|

<span data-ttu-id="98a79-258">Aşağıdaki tabloda olay verileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="98a79-258">The following table shows the event data:</span></span>

|<span data-ttu-id="98a79-259">alan adı</span><span class="sxs-lookup"><span data-stu-id="98a79-259">Field name</span></span>|<span data-ttu-id="98a79-260">Veri türü</span><span class="sxs-lookup"><span data-stu-id="98a79-260">Data type</span></span>|<span data-ttu-id="98a79-261">Açıklama</span><span class="sxs-lookup"><span data-stu-id="98a79-261">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="98a79-262">Adrestir</span><span class="sxs-lookup"><span data-stu-id="98a79-262">Address</span></span>|<span data-ttu-id="98a79-263">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="98a79-263">win:UInt64</span></span>|<span data-ttu-id="98a79-264">Segmentin adresi.</span><span class="sxs-lookup"><span data-stu-id="98a79-264">The address of the segment.</span></span>|
|<span data-ttu-id="98a79-265">Boyut</span><span class="sxs-lookup"><span data-stu-id="98a79-265">Size</span></span>|<span data-ttu-id="98a79-266">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="98a79-266">win:UInt64</span></span>|<span data-ttu-id="98a79-267">Segmentin boyutu.</span><span class="sxs-lookup"><span data-stu-id="98a79-267">The size of the segment.</span></span>|
|<span data-ttu-id="98a79-268">Tür</span><span class="sxs-lookup"><span data-stu-id="98a79-268">Type</span></span>|<span data-ttu-id="98a79-269">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="98a79-269">win:UInt32</span></span>|<span data-ttu-id="98a79-270">0x0-küçük nesne yığını.</span><span class="sxs-lookup"><span data-stu-id="98a79-270">0x0 - Small object heap.</span></span><br /><br /> <span data-ttu-id="98a79-271">0x1-büyük nesne yığını.</span><span class="sxs-lookup"><span data-stu-id="98a79-271">0x1 - Large object heap.</span></span><br /><br /> <span data-ttu-id="98a79-272">0x2-salt okunurdur yığın.</span><span class="sxs-lookup"><span data-stu-id="98a79-272">0x2 - Read-only heap.</span></span>|
|<span data-ttu-id="98a79-273">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="98a79-273">ClrInstanceID</span></span>|<span data-ttu-id="98a79-274">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="98a79-274">win:UInt16</span></span>|<span data-ttu-id="98a79-275">CLR veya CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="98a79-275">Unique ID for the instance of CLR or CoreCLR.</span></span>|

<span data-ttu-id="98a79-276">Çöp toplayıcı tarafından ayrılan parçaların boyutunun uygulamaya özgü olduğunu ve düzenli güncelleştirmeler de dahil olmak üzere herhangi bir zamanda değişikliğe tabi olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="98a79-276">Note that the size of segments allocated by the garbage collector is implementation-specific and is subject to change at any time, including in periodic updates.</span></span> <span data-ttu-id="98a79-277">Uygulamanız, belirli bir kesim boyutuna ilişkin varsayımları asla belirtmemelidir veya buna bağlı olarak, kesim ayırmaları için kullanılabilir bellek miktarını yapılandırmayı denemelidir.</span><span class="sxs-lookup"><span data-stu-id="98a79-277">Your app should never make assumptions about or depend on a particular segment size, nor should it attempt to configure the amount of memory available for segment allocations.</span></span>

## <a name="gcfreesegment_v1-event"></a><span data-ttu-id="98a79-278">GCFreeSegment_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="98a79-278">GCFreeSegment_V1 Event</span></span>

<span data-ttu-id="98a79-279">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="98a79-279">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="98a79-280">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="98a79-280">Keyword for raising the event</span></span>|<span data-ttu-id="98a79-281">Düzey</span><span class="sxs-lookup"><span data-stu-id="98a79-281">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="98a79-282">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="98a79-282">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="98a79-283">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="98a79-283">Informational (4)</span></span>|

<span data-ttu-id="98a79-284">Aşağıdaki tabloda olay bilgileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="98a79-284">The following table shows the event information:</span></span>

|<span data-ttu-id="98a79-285">Olay</span><span class="sxs-lookup"><span data-stu-id="98a79-285">Event</span></span>|<span data-ttu-id="98a79-286">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="98a79-286">Event ID</span></span>|<span data-ttu-id="98a79-287">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="98a79-287">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCFreeSegment_V1`|<span data-ttu-id="98a79-288">6</span><span class="sxs-lookup"><span data-stu-id="98a79-288">6</span></span>|<span data-ttu-id="98a79-289">Çöp toplama segmenti yayınlandı.</span><span class="sxs-lookup"><span data-stu-id="98a79-289">A garbage collection segment has been released.</span></span>|

<span data-ttu-id="98a79-290">Aşağıdaki tabloda olay verileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="98a79-290">The following table shows the event data:</span></span>

|<span data-ttu-id="98a79-291">alan adı</span><span class="sxs-lookup"><span data-stu-id="98a79-291">Field name</span></span>|<span data-ttu-id="98a79-292">Veri türü</span><span class="sxs-lookup"><span data-stu-id="98a79-292">Data type</span></span>|<span data-ttu-id="98a79-293">Açıklama</span><span class="sxs-lookup"><span data-stu-id="98a79-293">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="98a79-294">Adrestir</span><span class="sxs-lookup"><span data-stu-id="98a79-294">Address</span></span>|<span data-ttu-id="98a79-295">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="98a79-295">win:UInt64</span></span>|<span data-ttu-id="98a79-296">Segmentin adresi.</span><span class="sxs-lookup"><span data-stu-id="98a79-296">The address of the segment.</span></span>|
|<span data-ttu-id="98a79-297">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="98a79-297">ClrInstanceID</span></span>|<span data-ttu-id="98a79-298">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="98a79-298">win:UInt16</span></span>|<span data-ttu-id="98a79-299">CLR veya CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="98a79-299">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="gcrestarteebegin_v1-event"></a><span data-ttu-id="98a79-300">GCRestartEEBegin_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="98a79-300">GCRestartEEBegin_V1 Event</span></span>

<span data-ttu-id="98a79-301">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="98a79-301">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="98a79-302">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="98a79-302">Keyword for raising the event</span></span>|<span data-ttu-id="98a79-303">Düzey</span><span class="sxs-lookup"><span data-stu-id="98a79-303">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="98a79-304">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="98a79-304">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="98a79-305">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="98a79-305">Informational (4)</span></span>|

<span data-ttu-id="98a79-306">Aşağıdaki tabloda olay bilgileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="98a79-306">The following table shows the event information:</span></span>

|<span data-ttu-id="98a79-307">Olay</span><span class="sxs-lookup"><span data-stu-id="98a79-307">Event</span></span>|<span data-ttu-id="98a79-308">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="98a79-308">Event ID</span></span>|<span data-ttu-id="98a79-309">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="98a79-309">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCRestartEEBegin_V1`|<span data-ttu-id="98a79-310">7</span><span class="sxs-lookup"><span data-stu-id="98a79-310">7</span></span>|<span data-ttu-id="98a79-311">Ortak dil çalışma zamanı askıya alma işleminden sürdürme başladı.</span><span class="sxs-lookup"><span data-stu-id="98a79-311">Resumption from common language runtime suspension has begun.</span></span>|

<span data-ttu-id="98a79-312">Olay verisi yok.</span><span class="sxs-lookup"><span data-stu-id="98a79-312">No event data.</span></span>

## <a name="gcrestarteeend_v1-event"></a><span data-ttu-id="98a79-313">GCRestartEEEnd_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="98a79-313">GCRestartEEEnd_V1 Event</span></span>

<span data-ttu-id="98a79-314">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="98a79-314">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="98a79-315">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="98a79-315">Keyword for raising the event</span></span>|<span data-ttu-id="98a79-316">Düzey</span><span class="sxs-lookup"><span data-stu-id="98a79-316">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="98a79-317">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="98a79-317">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="98a79-318">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="98a79-318">Informational (4)</span></span>|

<span data-ttu-id="98a79-319">Aşağıdaki tabloda olay bilgileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="98a79-319">The following table shows the event information:</span></span>

|<span data-ttu-id="98a79-320">Olay</span><span class="sxs-lookup"><span data-stu-id="98a79-320">Event</span></span>|<span data-ttu-id="98a79-321">Olay kimliği</span><span class="sxs-lookup"><span data-stu-id="98a79-321">Event Id</span></span>|<span data-ttu-id="98a79-322">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="98a79-322">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCRestartEEEnd_V1`|<span data-ttu-id="98a79-323">3</span><span class="sxs-lookup"><span data-stu-id="98a79-323">3</span></span>|<span data-ttu-id="98a79-324">Ortak dil çalışma zamanı askıya alma işleminden sürdürme sonlandı.</span><span class="sxs-lookup"><span data-stu-id="98a79-324">Resumption from common language runtime suspension has ended.</span></span>|

<span data-ttu-id="98a79-325">Olay verisi yok.</span><span class="sxs-lookup"><span data-stu-id="98a79-325">No event data.</span></span>

## <a name="gcsuspendee_v1-event"></a><span data-ttu-id="98a79-326">GCSuspendEE_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="98a79-326">GCSuspendEE_V1 Event</span></span>

<span data-ttu-id="98a79-327">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="98a79-327">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="98a79-328">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="98a79-328">Keyword for raising the event</span></span>|<span data-ttu-id="98a79-329">Düzey</span><span class="sxs-lookup"><span data-stu-id="98a79-329">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="98a79-330">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="98a79-330">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="98a79-331">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="98a79-331">Informational (4)</span></span>|

<span data-ttu-id="98a79-332">Aşağıdaki tabloda olay bilgileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="98a79-332">The following table shows the event information:</span></span>

|<span data-ttu-id="98a79-333">Olay</span><span class="sxs-lookup"><span data-stu-id="98a79-333">Event</span></span>|<span data-ttu-id="98a79-334">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="98a79-334">Event ID</span></span>|<span data-ttu-id="98a79-335">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="98a79-335">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCSuspendEE_V1`|<span data-ttu-id="98a79-336">9</span><span class="sxs-lookup"><span data-stu-id="98a79-336">9</span></span>|<span data-ttu-id="98a79-337">Çöp toplama için yürütme altyapısının askıya alınma başlangıcı.</span><span class="sxs-lookup"><span data-stu-id="98a79-337">Start of suspension of the execution engine for garbage collection.</span></span>|

<span data-ttu-id="98a79-338">Aşağıdaki tabloda olay verileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="98a79-338">The following table shows the event data:</span></span>

|<span data-ttu-id="98a79-339">alan adı</span><span class="sxs-lookup"><span data-stu-id="98a79-339">Field name</span></span>|<span data-ttu-id="98a79-340">Veri türü</span><span class="sxs-lookup"><span data-stu-id="98a79-340">Data type</span></span>|<span data-ttu-id="98a79-341">Açıklama</span><span class="sxs-lookup"><span data-stu-id="98a79-341">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="98a79-342">Neden</span><span class="sxs-lookup"><span data-stu-id="98a79-342">Reason</span></span>|<span data-ttu-id="98a79-343">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="98a79-343">win:UInt16</span></span>|<span data-ttu-id="98a79-344">0x0-diğer.</span><span class="sxs-lookup"><span data-stu-id="98a79-344">0x0 - Other.</span></span><br /><br /> <span data-ttu-id="98a79-345">0x1-çöp toplama.</span><span class="sxs-lookup"><span data-stu-id="98a79-345">0x1 - Garbage collection.</span></span><br /><br /> <span data-ttu-id="98a79-346">0x2-Uygulama etki alanı kapanıyor.</span><span class="sxs-lookup"><span data-stu-id="98a79-346">0x2 - Application domain shutdown.</span></span><br /><br /> <span data-ttu-id="98a79-347">0x3-kod yeniden getiriliyor.</span><span class="sxs-lookup"><span data-stu-id="98a79-347">0x3 - Code pitching.</span></span><br /><br /> <span data-ttu-id="98a79-348">0x4-kapanıyor.</span><span class="sxs-lookup"><span data-stu-id="98a79-348">0x4 - Shutdown.</span></span><br /><br /> <span data-ttu-id="98a79-349">0x5-Debugger.</span><span class="sxs-lookup"><span data-stu-id="98a79-349">0x5 - Debugger.</span></span><br /><br /> <span data-ttu-id="98a79-350">çöp toplama için 0x6 hazırlığı.</span><span class="sxs-lookup"><span data-stu-id="98a79-350">0x6 - Preparation for garbage collection.</span></span>|
|<span data-ttu-id="98a79-351">Biriktirme</span><span class="sxs-lookup"><span data-stu-id="98a79-351">Count</span></span>|<span data-ttu-id="98a79-352">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="98a79-352">win:UInt32</span></span>|<span data-ttu-id="98a79-353">GC sayısı (saat).</span><span class="sxs-lookup"><span data-stu-id="98a79-353">The GC count at the time.</span></span> <span data-ttu-id="98a79-354">Genellikle, bundan sonra sonraki bir GC başlangıç olayını görürsünüz ve çöp toplama sırasında GC dizinini artırdıkça bu sayı + 1 olur.</span><span class="sxs-lookup"><span data-stu-id="98a79-354">Usually, you would see a subsequent GC Start event after this, and its Count would be this Count + 1 as we increase the GC index during a garbage collection.</span></span>|
|<span data-ttu-id="98a79-355">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="98a79-355">ClrInstanceID</span></span>|<span data-ttu-id="98a79-356">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="98a79-356">win:UInt16</span></span>|<span data-ttu-id="98a79-357">CLR veya CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="98a79-357">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="gcsuspendeeend_v1-event"></a><span data-ttu-id="98a79-358">GCSuspendEEEnd_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="98a79-358">GCSuspendEEEnd_V1 Event</span></span>

<span data-ttu-id="98a79-359">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="98a79-359">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="98a79-360">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="98a79-360">Keyword for raising the event</span></span>|<span data-ttu-id="98a79-361">Düzey</span><span class="sxs-lookup"><span data-stu-id="98a79-361">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="98a79-362">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="98a79-362">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="98a79-363">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="98a79-363">Informational (4)</span></span>|

<span data-ttu-id="98a79-364">Aşağıdaki tabloda olay bilgileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="98a79-364">The following table shows the event information:</span></span>

|<span data-ttu-id="98a79-365">Olay</span><span class="sxs-lookup"><span data-stu-id="98a79-365">Event</span></span>|<span data-ttu-id="98a79-366">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="98a79-366">Event ID</span></span>|<span data-ttu-id="98a79-367">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="98a79-367">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCSuspendEEEnd_V1`|<span data-ttu-id="98a79-368">8</span><span class="sxs-lookup"><span data-stu-id="98a79-368">8</span></span>|<span data-ttu-id="98a79-369">Çöp toplama için yürütme altyapısının askıya alınma sonu.</span><span class="sxs-lookup"><span data-stu-id="98a79-369">End of suspension of the execution engine for garbage collection.</span></span>|

<span data-ttu-id="98a79-370">Olay verisi yok.</span><span class="sxs-lookup"><span data-stu-id="98a79-370">No event data.</span></span>

## <a name="gcallocationtick_v2-event"></a><span data-ttu-id="98a79-371">GCAllocationTick_V2 olayı</span><span class="sxs-lookup"><span data-stu-id="98a79-371">GCAllocationTick_V2 Event</span></span>

<span data-ttu-id="98a79-372">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="98a79-372">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="98a79-373">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="98a79-373">Keyword for raising the event</span></span>|<span data-ttu-id="98a79-374">Düzey</span><span class="sxs-lookup"><span data-stu-id="98a79-374">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="98a79-375">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="98a79-375">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="98a79-376">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="98a79-376">Informational (4)</span></span>|

<span data-ttu-id="98a79-377">Aşağıdaki tabloda olay bilgileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="98a79-377">The following table shows the event information:</span></span>

|<span data-ttu-id="98a79-378">Olay</span><span class="sxs-lookup"><span data-stu-id="98a79-378">Event</span></span>|<span data-ttu-id="98a79-379">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="98a79-379">Event ID</span></span>|<span data-ttu-id="98a79-380">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="98a79-380">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCAllocationTick_V2`|<span data-ttu-id="98a79-381">10</span><span class="sxs-lookup"><span data-stu-id="98a79-381">10</span></span>|<span data-ttu-id="98a79-382">Yaklaşık 100 KB ayrıldığı her seferinde.</span><span class="sxs-lookup"><span data-stu-id="98a79-382">Each time approximately 100 KB is allocated.</span></span>|

<span data-ttu-id="98a79-383">Aşağıdaki tabloda olay verileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="98a79-383">The following table shows the event data:</span></span>

|<span data-ttu-id="98a79-384">alan adı</span><span class="sxs-lookup"><span data-stu-id="98a79-384">Field name</span></span>|<span data-ttu-id="98a79-385">Veri türü</span><span class="sxs-lookup"><span data-stu-id="98a79-385">Data type</span></span>|<span data-ttu-id="98a79-386">Açıklama</span><span class="sxs-lookup"><span data-stu-id="98a79-386">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="98a79-387">AllocationAmount</span><span class="sxs-lookup"><span data-stu-id="98a79-387">AllocationAmount</span></span>|<span data-ttu-id="98a79-388">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="98a79-388">win:UInt32</span></span>|<span data-ttu-id="98a79-389">Bayt cinsinden ayırma boyutu.</span><span class="sxs-lookup"><span data-stu-id="98a79-389">The allocation size, in bytes.</span></span> <span data-ttu-id="98a79-390">Bu değer, ULONG 'un uzunluğundan (4.294.967.295 bayt) daha az olan ayırmalar için doğrudur.</span><span class="sxs-lookup"><span data-stu-id="98a79-390">This value is accurate for allocations that are less than the length of a ULONG (4,294,967,295 bytes).</span></span> <span data-ttu-id="98a79-391">Ayırma daha büyükse, bu alan kesilmiş bir değer içerir.</span><span class="sxs-lookup"><span data-stu-id="98a79-391">If the allocation is greater, this field contains a truncated value.</span></span> <span data-ttu-id="98a79-392">Çok büyük ayırmalar için `AllocationAmount64` kullanın.</span><span class="sxs-lookup"><span data-stu-id="98a79-392">Use `AllocationAmount64` for very large allocations.</span></span>|
|<span data-ttu-id="98a79-393">AllocationKind</span><span class="sxs-lookup"><span data-stu-id="98a79-393">AllocationKind</span></span>|<span data-ttu-id="98a79-394">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="98a79-394">win:UInt32</span></span>|<span data-ttu-id="98a79-395">0x0-küçük nesne ayırma (ayırma küçük nesne yığınında).</span><span class="sxs-lookup"><span data-stu-id="98a79-395">0x0 - Small object allocation (allocation is in small object heap).</span></span><br /><br /> <span data-ttu-id="98a79-396">0x1-büyük nesne ayırma (ayırma büyük nesne yığınında).</span><span class="sxs-lookup"><span data-stu-id="98a79-396">0x1 - Large object allocation (allocation is in large object heap).</span></span>|
|<span data-ttu-id="98a79-397">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="98a79-397">ClrInstanceID</span></span>|<span data-ttu-id="98a79-398">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="98a79-398">win:UInt16</span></span>|<span data-ttu-id="98a79-399">CLR veya CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="98a79-399">Unique ID for the instance of CLR or CoreCLR.</span></span>|
|<span data-ttu-id="98a79-400">AllocationAmount64</span><span class="sxs-lookup"><span data-stu-id="98a79-400">AllocationAmount64</span></span>|<span data-ttu-id="98a79-401">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="98a79-401">win:UInt64</span></span>|<span data-ttu-id="98a79-402">Bayt cinsinden ayırma boyutu.</span><span class="sxs-lookup"><span data-stu-id="98a79-402">The allocation size, in bytes.</span></span> <span data-ttu-id="98a79-403">Bu değer, çok büyük ayırmalar için doğrudur.</span><span class="sxs-lookup"><span data-stu-id="98a79-403">This value is accurate for very large allocations.</span></span>|
|<span data-ttu-id="98a79-404">Türü</span><span class="sxs-lookup"><span data-stu-id="98a79-404">TypeId</span></span>|<span data-ttu-id="98a79-405">Win: Işaretçi</span><span class="sxs-lookup"><span data-stu-id="98a79-405">win:Pointer</span></span>|<span data-ttu-id="98a79-406">MethodTable 'ın adresi.</span><span class="sxs-lookup"><span data-stu-id="98a79-406">The address of the MethodTable.</span></span> <span data-ttu-id="98a79-407">Bu olay sırasında ayrılan çeşitli nesne türleri olduğunda, bu, ayrılan son nesneye (100 KB eşiğinin aşılmasına neden olan nesne) karşılık gelen MethodTable 'ın adresidir.</span><span class="sxs-lookup"><span data-stu-id="98a79-407">When there are several types of objects that were allocated during this event, this is the address of the MethodTable that corresponds to the last object allocated (the object that caused the 100 KB threshold to be exceeded).</span></span>|
|<span data-ttu-id="98a79-408">TypeName</span><span class="sxs-lookup"><span data-stu-id="98a79-408">TypeName</span></span>|<span data-ttu-id="98a79-409">Win: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="98a79-409">win:UnicodeString</span></span>|<span data-ttu-id="98a79-410">Ayrılan türün adı.</span><span class="sxs-lookup"><span data-stu-id="98a79-410">The name of the type that was allocated.</span></span> <span data-ttu-id="98a79-411">Bu olay sırasında ayrılan çeşitli nesne türleri varsa, bu, ayrılan son nesnenin türüdür (100 KB eşiğinin aşılmasına neden olan nesne).</span><span class="sxs-lookup"><span data-stu-id="98a79-411">When there are several types of objects that were allocated during this event, this is the type of the last object allocated (the object that caused the 100 KB threshold to be exceeded).</span></span>|
|<span data-ttu-id="98a79-412">Heapındex</span><span class="sxs-lookup"><span data-stu-id="98a79-412">HeapIndex</span></span>|<span data-ttu-id="98a79-413">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="98a79-413">win:UInt32</span></span>|<span data-ttu-id="98a79-414">Nesnenin ayrıldığı yığın.</span><span class="sxs-lookup"><span data-stu-id="98a79-414">The heap where the object was allocated.</span></span> <span data-ttu-id="98a79-415">Bu değer, iş istasyonu atık toplama ile çalıştırılırken 0 (sıfır) değeridir.</span><span class="sxs-lookup"><span data-stu-id="98a79-415">This value is 0 (zero) when running with workstation garbage collection.</span></span>|

## <a name="gcfinalizersbegin_v1-event"></a><span data-ttu-id="98a79-416">GCFinalizersBegin_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="98a79-416">GCFinalizersBegin_V1 Event</span></span>

<span data-ttu-id="98a79-417">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="98a79-417">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="98a79-418">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="98a79-418">Keyword for raising the event</span></span>|<span data-ttu-id="98a79-419">Düzey</span><span class="sxs-lookup"><span data-stu-id="98a79-419">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="98a79-420">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="98a79-420">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="98a79-421">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="98a79-421">Informational (4)</span></span>|

<span data-ttu-id="98a79-422">Aşağıdaki tabloda olay bilgileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="98a79-422">The following table shows the event information:</span></span>

|<span data-ttu-id="98a79-423">Olay</span><span class="sxs-lookup"><span data-stu-id="98a79-423">Event</span></span>|<span data-ttu-id="98a79-424">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="98a79-424">Event ID</span></span>|<span data-ttu-id="98a79-425">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="98a79-425">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCFinalizersBegin_V1`|<span data-ttu-id="98a79-426">14</span><span class="sxs-lookup"><span data-stu-id="98a79-426">14</span></span>|<span data-ttu-id="98a79-427">Sonlandırıcıları çalıştırmanın başlangıcı.</span><span class="sxs-lookup"><span data-stu-id="98a79-427">The start of running finalizers.</span></span>|

<span data-ttu-id="98a79-428">Olay verisi yok.</span><span class="sxs-lookup"><span data-stu-id="98a79-428">No event data.</span></span>

## <a name="gcfinalizersend_v1-event"></a><span data-ttu-id="98a79-429">GCFinalizersEnd_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="98a79-429">GCFinalizersEnd_V1 Event</span></span>

<span data-ttu-id="98a79-430">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="98a79-430">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="98a79-431">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="98a79-431">Keyword for raising the event</span></span>|<span data-ttu-id="98a79-432">Düzey</span><span class="sxs-lookup"><span data-stu-id="98a79-432">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="98a79-433">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="98a79-433">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="98a79-434">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="98a79-434">Informational (4)</span></span>|

<span data-ttu-id="98a79-435">Aşağıdaki tabloda olay bilgileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="98a79-435">The following table shows the event information:</span></span>

|<span data-ttu-id="98a79-436">Olay</span><span class="sxs-lookup"><span data-stu-id="98a79-436">Event</span></span>|<span data-ttu-id="98a79-437">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="98a79-437">Event ID</span></span>|<span data-ttu-id="98a79-438">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="98a79-438">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCFinalizersEnd_V1`|<span data-ttu-id="98a79-439">13</span><span class="sxs-lookup"><span data-stu-id="98a79-439">13</span></span>|<span data-ttu-id="98a79-440">Sonlandırıcılardan çalıştırmanın sonu.</span><span class="sxs-lookup"><span data-stu-id="98a79-440">The end of running finalizers.</span></span>|

<span data-ttu-id="98a79-441">Aşağıdaki tabloda olay verileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="98a79-441">The following table shows the event data:</span></span>

|<span data-ttu-id="98a79-442">alan adı</span><span class="sxs-lookup"><span data-stu-id="98a79-442">Field name</span></span>|<span data-ttu-id="98a79-443">Veri türü</span><span class="sxs-lookup"><span data-stu-id="98a79-443">Data type</span></span>|<span data-ttu-id="98a79-444">Açıklama</span><span class="sxs-lookup"><span data-stu-id="98a79-444">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="98a79-445">Biriktirme</span><span class="sxs-lookup"><span data-stu-id="98a79-445">Count</span></span>|<span data-ttu-id="98a79-446">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="98a79-446">win:UInt32</span></span>|<span data-ttu-id="98a79-447">Çalıştırılan sonlandırıcılar sayısı.</span><span class="sxs-lookup"><span data-stu-id="98a79-447">The number of finalizers that were run.</span></span>|
|<span data-ttu-id="98a79-448">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="98a79-448">ClrInstanceID</span></span>|<span data-ttu-id="98a79-449">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="98a79-449">win:UInt16</span></span>|<span data-ttu-id="98a79-450">CLR veya CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="98a79-450">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="gccreateconcurrentthread_v1-event"></a><span data-ttu-id="98a79-451">GCCreateConcurrentThread_V1 Olayı</span><span class="sxs-lookup"><span data-stu-id="98a79-451">GCCreateConcurrentThread_V1 Event</span></span>

<span data-ttu-id="98a79-452">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="98a79-452">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="98a79-453">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="98a79-453">Keyword for raising the event</span></span>|<span data-ttu-id="98a79-454">Düzey</span><span class="sxs-lookup"><span data-stu-id="98a79-454">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="98a79-455">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="98a79-455">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="98a79-456">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="98a79-456">Informational (4)</span></span>|
|<span data-ttu-id="98a79-457">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="98a79-457">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="98a79-458">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="98a79-458">Informational (4)</span></span>|

<span data-ttu-id="98a79-459">Aşağıdaki tabloda olay bilgileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="98a79-459">The following table shows the event information:</span></span>

|<span data-ttu-id="98a79-460">Olay</span><span class="sxs-lookup"><span data-stu-id="98a79-460">Event</span></span>|<span data-ttu-id="98a79-461">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="98a79-461">Event ID</span></span>|<span data-ttu-id="98a79-462">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="98a79-462">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCCreateConcurrentThread_V1`|<span data-ttu-id="98a79-463">11</span><span class="sxs-lookup"><span data-stu-id="98a79-463">11</span></span>|<span data-ttu-id="98a79-464">Eşzamanlı atık toplama iş parçacığı oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="98a79-464">Concurrent garbage collection thread was created.</span></span>|

<span data-ttu-id="98a79-465">Olay verisi yok.</span><span class="sxs-lookup"><span data-stu-id="98a79-465">No event data.</span></span>

## <a name="gcterminateconcurrentthread_v1-event"></a><span data-ttu-id="98a79-466">GCTerminateConcurrentThread_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="98a79-466">GCTerminateConcurrentThread_V1 Event</span></span>

<span data-ttu-id="98a79-467">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="98a79-467">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="98a79-468">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="98a79-468">Keyword for raising the event</span></span>|<span data-ttu-id="98a79-469">Düzey</span><span class="sxs-lookup"><span data-stu-id="98a79-469">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="98a79-470">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="98a79-470">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="98a79-471">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="98a79-471">Informational (4)</span></span>|
|<span data-ttu-id="98a79-472">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="98a79-472">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="98a79-473">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="98a79-473">Informational (4)</span></span>|

<span data-ttu-id="98a79-474">Aşağıdaki tabloda olay bilgileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="98a79-474">The following table shows the event information:</span></span>

|<span data-ttu-id="98a79-475">Olay</span><span class="sxs-lookup"><span data-stu-id="98a79-475">Event</span></span>|<span data-ttu-id="98a79-476">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="98a79-476">Event ID</span></span>|<span data-ttu-id="98a79-477">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="98a79-477">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCTerminateConcurrentThread_V1`|<span data-ttu-id="98a79-478">12</span><span class="sxs-lookup"><span data-stu-id="98a79-478">12</span></span>|<span data-ttu-id="98a79-479">Eşzamanlı atık toplama iş parçacığı sonlandırıldı.</span><span class="sxs-lookup"><span data-stu-id="98a79-479">Concurrent garbage collection thread was terminated.</span></span>|

<span data-ttu-id="98a79-480">Olay verisi yok.</span><span class="sxs-lookup"><span data-stu-id="98a79-480">No event data.</span></span>

## <a name="see-also"></a><span data-ttu-id="98a79-481">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="98a79-481">See also</span></span>

- [<span data-ttu-id="98a79-482">CLR ETW Olayları</span><span class="sxs-lookup"><span data-stu-id="98a79-482">CLR ETW Events</span></span>](clr-etw-events.md)
