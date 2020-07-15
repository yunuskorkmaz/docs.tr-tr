---
title: Çöp Toplama ETW Olayları
description: Çöp toplama ETW olayları hakkında ayrıntılı bilgi görüntüleyin. Kapsanan olaylar GCStart_V1, GCEnd_V1, GCHeapStats_V1, GCCreateSegment_V1 ve daha fazlasını içerir.
ms.date: 03/30/2017
helpviewer_keywords:
- GC events
- garbage collection events [.NET Framework]
- ETW, garbage collection events (CLR)
ms.assetid: f14b6fd7-0966-4d87-bc89-54ef3a44a94a
ms.openlocfilehash: 58ad874ef6a12c18c404640aa66577c391573534
ms.sourcegitcommit: 0fa2b7b658bf137e813a7f4d09589d64c148ebf5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/14/2020
ms.locfileid: "86309748"
---
# <a name="garbage-collection-etw-events"></a><span data-ttu-id="dca86-104">Çöp Toplama ETW Olayları</span><span class="sxs-lookup"><span data-stu-id="dca86-104">Garbage Collection ETW Events</span></span>

<span data-ttu-id="dca86-105">Bu olaylar çöp koleksiyonuyla ilgili bilgiler toplar.</span><span class="sxs-lookup"><span data-stu-id="dca86-105">These events collect information pertaining to garbage collection.</span></span> <span data-ttu-id="dca86-106">Çöp toplamanın kaç kez gerçekleştirildiğini, çöp toplama sırasında ne kadar bellek serbest olduğunu ve bu şekilde ne kadar bellek kaldığını belirleme dahil, tanılama ve hata ayıklamada yardımcı olurlar.</span><span class="sxs-lookup"><span data-stu-id="dca86-106">They help in diagnostics and debugging, including determining how many times garbage collection was performed, how much memory was freed during garbage collection, and so on.</span></span>

<span data-ttu-id="dca86-107">Bu kategori aşağıdaki olaylardan oluşur:</span><span class="sxs-lookup"><span data-stu-id="dca86-107">This category consists of the following events:</span></span>

- [<span data-ttu-id="dca86-108">GCStart_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="dca86-108">GCStart_V1 Event</span></span>](#gcstart_v1-event)
- [<span data-ttu-id="dca86-109">GCEnd_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="dca86-109">GCEnd_V1 Event</span></span>](#gcend_v1-event)
- [<span data-ttu-id="dca86-110">GCHeapStats_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="dca86-110">GCHeapStats_V1 Event</span></span>](#gcheapstats_v1-event)
- [<span data-ttu-id="dca86-111">GCCreateSegment_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="dca86-111">GCCreateSegment_V1 Event</span></span>](#gccreatesegment_v1-event)
- [<span data-ttu-id="dca86-112">GCFreeSegment_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="dca86-112">GCFreeSegment_V1 Event</span></span>](#gcfreesegment_v1-event)
- [<span data-ttu-id="dca86-113">GCRestartEEBegin_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="dca86-113">GCRestartEEBegin_V1 Event</span></span>](#gcrestarteebegin_v1-event)
- [<span data-ttu-id="dca86-114">GCRestartEEEnd_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="dca86-114">GCRestartEEEnd_V1 Event</span></span>](#gcrestarteeend_v1-event)
- [<span data-ttu-id="dca86-115">GCSuspendEE_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="dca86-115">GCSuspendEE_V1 Event</span></span>](#gcsuspendee_v1-event)
- [<span data-ttu-id="dca86-116">GCSuspendEEEnd_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="dca86-116">GCSuspendEEEnd_V1 Event</span></span>](#gcsuspendeeend_v1-event)
- [<span data-ttu-id="dca86-117">GCAllocationTick_V2 olayı</span><span class="sxs-lookup"><span data-stu-id="dca86-117">GCAllocationTick_V2 Event</span></span>](#gcallocationtick_v2-event)
- [<span data-ttu-id="dca86-118">GCFinalizersBegin_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="dca86-118">GCFinalizersBegin_V1 Event</span></span>](#gcfinalizersbegin_v1-event)
- [<span data-ttu-id="dca86-119">GCFinalizersEnd_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="dca86-119">GCFinalizersEnd_V1 Event</span></span>](#gcfinalizersend_v1-event)
- [<span data-ttu-id="dca86-120">GCCreateConcurrentThread_V1 Olayı</span><span class="sxs-lookup"><span data-stu-id="dca86-120">GCCreateConcurrentThread_V1 Event</span></span>](#gccreateconcurrentthread_v1-event)
- [<span data-ttu-id="dca86-121">GCTerminateConcurrentThread_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="dca86-121">GCTerminateConcurrentThread_V1 Event</span></span>](#gcterminateconcurrentthread_v1-event)

## <a name="gcstart_v1-event"></a><span data-ttu-id="dca86-122">GCStart_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="dca86-122">GCStart_V1 Event</span></span>  

<span data-ttu-id="dca86-123">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="dca86-123">The following table shows the keyword and level.</span></span> <span data-ttu-id="dca86-124">Daha fazla bilgi için bkz. [CLR ETW anahtar sözcükleri ve düzeyleri](clr-etw-keywords-and-levels.md).</span><span class="sxs-lookup"><span data-stu-id="dca86-124">For more information, see [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).</span></span>

|<span data-ttu-id="dca86-125">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="dca86-125">Keyword for raising the event</span></span>|<span data-ttu-id="dca86-126">Düzey</span><span class="sxs-lookup"><span data-stu-id="dca86-126">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="dca86-127">`GCKeyword`0x1</span><span class="sxs-lookup"><span data-stu-id="dca86-127">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="dca86-128">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="dca86-128">Informational (4)</span></span>|

<span data-ttu-id="dca86-129">Aşağıdaki tabloda olay bilgileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="dca86-129">The following table shows the event information:</span></span>

|<span data-ttu-id="dca86-130">Olay</span><span class="sxs-lookup"><span data-stu-id="dca86-130">Event</span></span>|<span data-ttu-id="dca86-131">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="dca86-131">Event ID</span></span>|<span data-ttu-id="dca86-132">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="dca86-132">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCStart_V1`|<span data-ttu-id="dca86-133">1</span><span class="sxs-lookup"><span data-stu-id="dca86-133">1</span></span>|<span data-ttu-id="dca86-134">Çöp toplama işlemi başlatıldı.</span><span class="sxs-lookup"><span data-stu-id="dca86-134">A garbage collection has started.</span></span>|

<span data-ttu-id="dca86-135">Aşağıdaki tabloda olay verileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="dca86-135">The following table shows the event data:</span></span>

|<span data-ttu-id="dca86-136">Alan adı</span><span class="sxs-lookup"><span data-stu-id="dca86-136">Field name</span></span>|<span data-ttu-id="dca86-137">Veri türü</span><span class="sxs-lookup"><span data-stu-id="dca86-137">Data type</span></span>|<span data-ttu-id="dca86-138">Description</span><span class="sxs-lookup"><span data-stu-id="dca86-138">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="dca86-139">Count</span><span class="sxs-lookup"><span data-stu-id="dca86-139">Count</span></span>|<span data-ttu-id="dca86-140">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="dca86-140">win:UInt32</span></span>|<span data-ttu-id="dca86-141">*N*. çöp toplama.</span><span class="sxs-lookup"><span data-stu-id="dca86-141">The *n*th garbage collection.</span></span>|
|<span data-ttu-id="dca86-142">Derinliğini</span><span class="sxs-lookup"><span data-stu-id="dca86-142">Depth</span></span>|<span data-ttu-id="dca86-143">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="dca86-143">win:UInt32</span></span>|<span data-ttu-id="dca86-144">Toplanmakta olan oluşturma.</span><span class="sxs-lookup"><span data-stu-id="dca86-144">The generation that is being collected.</span></span>|
|<span data-ttu-id="dca86-145">Neden</span><span class="sxs-lookup"><span data-stu-id="dca86-145">Reason</span></span>|<span data-ttu-id="dca86-146">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="dca86-146">win:UInt32</span></span>|<span data-ttu-id="dca86-147">Çöp toplamanın neden tetiklendiği:</span><span class="sxs-lookup"><span data-stu-id="dca86-147">Why the garbage collection was triggered:</span></span><br /><br /> <span data-ttu-id="dca86-148">0x0-küçük nesne yığını ayırması.</span><span class="sxs-lookup"><span data-stu-id="dca86-148">0x0 - Small object heap allocation.</span></span><br /><br /> <span data-ttu-id="dca86-149">0x1-alınmış.</span><span class="sxs-lookup"><span data-stu-id="dca86-149">0x1 - Induced.</span></span><br /><br /> <span data-ttu-id="dca86-150">0x2-düşük bellek.</span><span class="sxs-lookup"><span data-stu-id="dca86-150">0x2 - Low memory.</span></span><br /><br /> <span data-ttu-id="dca86-151">0x3-boş.</span><span class="sxs-lookup"><span data-stu-id="dca86-151">0x3 - Empty.</span></span><br /><br /> <span data-ttu-id="dca86-152">0x4-büyük nesne yığını ayırması.</span><span class="sxs-lookup"><span data-stu-id="dca86-152">0x4 - Large object heap allocation.</span></span><br /><br /> <span data-ttu-id="dca86-153">0x5-alan kalmadı (küçük nesne yığını için).</span><span class="sxs-lookup"><span data-stu-id="dca86-153">0x5 - Out of space (for small object heap).</span></span><br /><br /> <span data-ttu-id="dca86-154">0x6-alan kalmadı (büyük nesne yığını için).</span><span class="sxs-lookup"><span data-stu-id="dca86-154">0x6 - Out of space (for large object heap).</span></span><br /><br /> <span data-ttu-id="dca86-155">0x7-alınmış ancak engelleme olarak zorlanmadı.</span><span class="sxs-lookup"><span data-stu-id="dca86-155">0x7 - Induced but not forced as blocking.</span></span>|
|<span data-ttu-id="dca86-156">Tür</span><span class="sxs-lookup"><span data-stu-id="dca86-156">Type</span></span>|<span data-ttu-id="dca86-157">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="dca86-157">win:UInt32</span></span>|<span data-ttu-id="dca86-158">0x0-arka plan atık toplama dışında bir çöp toplama engelleme gerçekleşti.</span><span class="sxs-lookup"><span data-stu-id="dca86-158">0x0 - Blocking garbage collection occurred outside background garbage collection.</span></span><br /><br /> <span data-ttu-id="dca86-159">0x1-arka plan atık toplama.</span><span class="sxs-lookup"><span data-stu-id="dca86-159">0x1 - Background garbage collection.</span></span><br /><br /> <span data-ttu-id="dca86-160">0x2-arka plan atık toplama sırasında atık toplamayı engelleme oluştu.</span><span class="sxs-lookup"><span data-stu-id="dca86-160">0x2 - Blocking garbage collection occurred during background garbage collection.</span></span>|
|<span data-ttu-id="dca86-161">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="dca86-161">ClrInstanceID</span></span>|<span data-ttu-id="dca86-162">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="dca86-162">win:UInt16</span></span>|<span data-ttu-id="dca86-163">CLR veya CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="dca86-163">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="gcend_v1-event"></a><span data-ttu-id="dca86-164">GCEnd_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="dca86-164">GCEnd_V1 Event</span></span>

<span data-ttu-id="dca86-165">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="dca86-165">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="dca86-166">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="dca86-166">Keyword for raising the event</span></span>|<span data-ttu-id="dca86-167">Düzey</span><span class="sxs-lookup"><span data-stu-id="dca86-167">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="dca86-168">`GCKeyword`0x1</span><span class="sxs-lookup"><span data-stu-id="dca86-168">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="dca86-169">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="dca86-169">Informational (4)</span></span>|

<span data-ttu-id="dca86-170">Aşağıdaki tabloda olay bilgileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="dca86-170">The following table shows the event information:</span></span>

|<span data-ttu-id="dca86-171">Olay</span><span class="sxs-lookup"><span data-stu-id="dca86-171">Event</span></span>|<span data-ttu-id="dca86-172">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="dca86-172">Event ID</span></span>|<span data-ttu-id="dca86-173">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="dca86-173">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCEnd_V1`|<span data-ttu-id="dca86-174">2</span><span class="sxs-lookup"><span data-stu-id="dca86-174">2</span></span>|<span data-ttu-id="dca86-175">Çöp toplama sona erdi.</span><span class="sxs-lookup"><span data-stu-id="dca86-175">The garbage collection has ended.</span></span>|

<span data-ttu-id="dca86-176">Aşağıdaki tabloda olay verileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="dca86-176">The following table shows the event data:</span></span>

|<span data-ttu-id="dca86-177">Alan adı</span><span class="sxs-lookup"><span data-stu-id="dca86-177">Field name</span></span>|<span data-ttu-id="dca86-178">Veri türü</span><span class="sxs-lookup"><span data-stu-id="dca86-178">Data type</span></span>|<span data-ttu-id="dca86-179">Description</span><span class="sxs-lookup"><span data-stu-id="dca86-179">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="dca86-180">Count</span><span class="sxs-lookup"><span data-stu-id="dca86-180">Count</span></span>|<span data-ttu-id="dca86-181">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="dca86-181">win:UInt32</span></span>|<span data-ttu-id="dca86-182">*N*. çöp toplama.</span><span class="sxs-lookup"><span data-stu-id="dca86-182">The *n*th garbage collection.</span></span>|
|<span data-ttu-id="dca86-183">Derinliğini</span><span class="sxs-lookup"><span data-stu-id="dca86-183">Depth</span></span>|<span data-ttu-id="dca86-184">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="dca86-184">win:UInt32</span></span>|<span data-ttu-id="dca86-185">Toplanan nesil.</span><span class="sxs-lookup"><span data-stu-id="dca86-185">The generation that was collected.</span></span>|
|<span data-ttu-id="dca86-186">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="dca86-186">ClrInstanceID</span></span>|<span data-ttu-id="dca86-187">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="dca86-187">win:UInt16</span></span>|<span data-ttu-id="dca86-188">CLR veya CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="dca86-188">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="gcheapstats_v1-event"></a><span data-ttu-id="dca86-189">GCHeapStats_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="dca86-189">GCHeapStats_V1 Event</span></span>

<span data-ttu-id="dca86-190">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="dca86-190">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="dca86-191">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="dca86-191">Keyword for raising the event</span></span>|<span data-ttu-id="dca86-192">Düzey</span><span class="sxs-lookup"><span data-stu-id="dca86-192">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="dca86-193">`GCKeyword`0x1</span><span class="sxs-lookup"><span data-stu-id="dca86-193">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="dca86-194">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="dca86-194">Informational (4)</span></span>|

<span data-ttu-id="dca86-195">Aşağıdaki tabloda olay bilgileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="dca86-195">The following table shows the event information:</span></span>

|<span data-ttu-id="dca86-196">Olay</span><span class="sxs-lookup"><span data-stu-id="dca86-196">Event</span></span>|<span data-ttu-id="dca86-197">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="dca86-197">Event ID</span></span>|<span data-ttu-id="dca86-198">Description</span><span class="sxs-lookup"><span data-stu-id="dca86-198">Description</span></span>|
|-----------|--------------|-----------------|
|`GCHeapStats_V1`|<span data-ttu-id="dca86-199">4</span><span class="sxs-lookup"><span data-stu-id="dca86-199">4</span></span>|<span data-ttu-id="dca86-200">Her çöp toplamanın sonundaki yığın istatistiklerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="dca86-200">Shows the heap statistics at the end of each garbage collection.</span></span>|

<span data-ttu-id="dca86-201">Aşağıdaki tabloda olay verileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="dca86-201">The following table shows the event data:</span></span>

|<span data-ttu-id="dca86-202">Alan adı</span><span class="sxs-lookup"><span data-stu-id="dca86-202">Field name</span></span>|<span data-ttu-id="dca86-203">Veri türü</span><span class="sxs-lookup"><span data-stu-id="dca86-203">Data type</span></span>|<span data-ttu-id="dca86-204">Description</span><span class="sxs-lookup"><span data-stu-id="dca86-204">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="dca86-205">GenerationSize0</span><span class="sxs-lookup"><span data-stu-id="dca86-205">GenerationSize0</span></span>|<span data-ttu-id="dca86-206">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="dca86-206">win:UInt64</span></span>|<span data-ttu-id="dca86-207">0. nesil belleğin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="dca86-207">The size, in bytes, of generation 0 memory.</span></span>|
|<span data-ttu-id="dca86-208">TotalPromotedSize0</span><span class="sxs-lookup"><span data-stu-id="dca86-208">TotalPromotedSize0</span></span>|<span data-ttu-id="dca86-209">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="dca86-209">win:UInt64</span></span>|<span data-ttu-id="dca86-210">Nesil 0 ' dan 1 ' e yükseltilen bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="dca86-210">The number of bytes that are promoted from generation 0 to generation 1.</span></span>|
|<span data-ttu-id="dca86-211">GenerationSize1</span><span class="sxs-lookup"><span data-stu-id="dca86-211">GenerationSize1</span></span>|<span data-ttu-id="dca86-212">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="dca86-212">win:UInt64</span></span>|<span data-ttu-id="dca86-213">1. nesil belleğin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="dca86-213">The size, in bytes, of generation 1 memory.</span></span>|
|<span data-ttu-id="dca86-214">TotalPromotedSize1</span><span class="sxs-lookup"><span data-stu-id="dca86-214">TotalPromotedSize1</span></span>|<span data-ttu-id="dca86-215">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="dca86-215">win:UInt64</span></span>|<span data-ttu-id="dca86-216">1. nesil 2 ' ye kadar yükseltilen bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="dca86-216">The number of bytes that are promoted from generation 1 to generation 2.</span></span>|
|<span data-ttu-id="dca86-217">GenerationSize2</span><span class="sxs-lookup"><span data-stu-id="dca86-217">GenerationSize2</span></span>|<span data-ttu-id="dca86-218">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="dca86-218">win:UInt64</span></span>|<span data-ttu-id="dca86-219">2. nesil belleğin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="dca86-219">The size, in bytes, of generation 2 memory.</span></span>|
|<span data-ttu-id="dca86-220">TotalPromotedSize2</span><span class="sxs-lookup"><span data-stu-id="dca86-220">TotalPromotedSize2</span></span>|<span data-ttu-id="dca86-221">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="dca86-221">win:UInt64</span></span>|<span data-ttu-id="dca86-222">Son koleksiyondan sonra 2. nesil üzerinde kalan bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="dca86-222">The number of bytes that survived in generation 2 after the last collection.</span></span>|
|<span data-ttu-id="dca86-223">GenerationSize3</span><span class="sxs-lookup"><span data-stu-id="dca86-223">GenerationSize3</span></span>|<span data-ttu-id="dca86-224">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="dca86-224">win:UInt64</span></span>|<span data-ttu-id="dca86-225">Büyük nesne yığınının bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="dca86-225">The size, in bytes, of the large object heap.</span></span>|
|<span data-ttu-id="dca86-226">TotalPromotedSize3</span><span class="sxs-lookup"><span data-stu-id="dca86-226">TotalPromotedSize3</span></span>|<span data-ttu-id="dca86-227">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="dca86-227">win:UInt64</span></span>|<span data-ttu-id="dca86-228">Son koleksiyondan sonra büyük nesne yığınında kalan bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="dca86-228">The number of bytes that survived in the large object heap after the last collection.</span></span>|
|<span data-ttu-id="dca86-229">Sonlandırizationpromotedsize</span><span class="sxs-lookup"><span data-stu-id="dca86-229">FinalizationPromotedSize</span></span>|<span data-ttu-id="dca86-230">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="dca86-230">win:UInt64</span></span>|<span data-ttu-id="dca86-231">Sonlandırma için hazırlanma nesnelerinin bayt cinsinden toplam boyutu.</span><span class="sxs-lookup"><span data-stu-id="dca86-231">The total size, in bytes, of the objects that are ready for finalization.</span></span>|
|<span data-ttu-id="dca86-232">Sonlandırizationpromotedcount</span><span class="sxs-lookup"><span data-stu-id="dca86-232">FinalizationPromotedCount</span></span>|<span data-ttu-id="dca86-233">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="dca86-233">win:UInt64</span></span>|<span data-ttu-id="dca86-234">Sonlandırmaya hazırlanma nesne sayısı.</span><span class="sxs-lookup"><span data-stu-id="dca86-234">The number of objects that are ready for finalization.</span></span>|
|<span data-ttu-id="dca86-235">PinnedObjectCount</span><span class="sxs-lookup"><span data-stu-id="dca86-235">PinnedObjectCount</span></span>|<span data-ttu-id="dca86-236">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="dca86-236">win:UInt32</span></span>|<span data-ttu-id="dca86-237">Sabitlenmiş (taşınamaz) nesne sayısı.</span><span class="sxs-lookup"><span data-stu-id="dca86-237">The number of pinned (unmovable) objects.</span></span>|
|<span data-ttu-id="dca86-238">SinkBlockCount</span><span class="sxs-lookup"><span data-stu-id="dca86-238">SinkBlockCount</span></span>|<span data-ttu-id="dca86-239">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="dca86-239">win:UInt32</span></span>|<span data-ttu-id="dca86-240">Kullanımdaki eşitleme bloklarının sayısı.</span><span class="sxs-lookup"><span data-stu-id="dca86-240">The number of synchronization blocks in use.</span></span>|
|<span data-ttu-id="dca86-241">Gchandlet sayısı</span><span class="sxs-lookup"><span data-stu-id="dca86-241">GCHandleCount</span></span>|<span data-ttu-id="dca86-242">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="dca86-242">win:UInt32</span></span>|<span data-ttu-id="dca86-243">Kullanımdaki çöp toplama tanıtıcılarının sayısı.</span><span class="sxs-lookup"><span data-stu-id="dca86-243">The number of garbage collection handles in use.</span></span>|
|<span data-ttu-id="dca86-244">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="dca86-244">ClrInstanceID</span></span>|<span data-ttu-id="dca86-245">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="dca86-245">win:UInt16</span></span>|<span data-ttu-id="dca86-246">CLR veya CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="dca86-246">Unique ID for the instance of CLR or CoreCLR.</span></span>|
  
## <a name="gccreatesegment_v1-event"></a><span data-ttu-id="dca86-247">GCCreateSegment_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="dca86-247">GCCreateSegment_V1 Event</span></span>

<span data-ttu-id="dca86-248">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="dca86-248">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="dca86-249">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="dca86-249">Keyword for raising the event</span></span>|<span data-ttu-id="dca86-250">Düzey</span><span class="sxs-lookup"><span data-stu-id="dca86-250">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="dca86-251">`GCKeyword`0x1</span><span class="sxs-lookup"><span data-stu-id="dca86-251">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="dca86-252">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="dca86-252">Informational (4)</span></span>|

<span data-ttu-id="dca86-253">Aşağıdaki tabloda olay bilgileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="dca86-253">The following table shows the event information:</span></span>

|<span data-ttu-id="dca86-254">Olay</span><span class="sxs-lookup"><span data-stu-id="dca86-254">Event</span></span>|<span data-ttu-id="dca86-255">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="dca86-255">Event ID</span></span>|<span data-ttu-id="dca86-256">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="dca86-256">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCCreateSegment_V1`|<span data-ttu-id="dca86-257">5</span><span class="sxs-lookup"><span data-stu-id="dca86-257">5</span></span>|<span data-ttu-id="dca86-258">Yeni bir atık toplama segmenti oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="dca86-258">A new garbage collection segment has been created.</span></span> <span data-ttu-id="dca86-259">Ayrıca, izleme zaten çalışmakta olan bir işlemde etkinleştirildiğinde, bu olay varolan her segment için oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="dca86-259">In addition, when tracing is enabled on a process that is already running, this event is raised for each existing segment.</span></span>|

<span data-ttu-id="dca86-260">Aşağıdaki tabloda olay verileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="dca86-260">The following table shows the event data:</span></span>

|<span data-ttu-id="dca86-261">Alan adı</span><span class="sxs-lookup"><span data-stu-id="dca86-261">Field name</span></span>|<span data-ttu-id="dca86-262">Veri türü</span><span class="sxs-lookup"><span data-stu-id="dca86-262">Data type</span></span>|<span data-ttu-id="dca86-263">Description</span><span class="sxs-lookup"><span data-stu-id="dca86-263">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="dca86-264">Adres</span><span class="sxs-lookup"><span data-stu-id="dca86-264">Address</span></span>|<span data-ttu-id="dca86-265">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="dca86-265">win:UInt64</span></span>|<span data-ttu-id="dca86-266">Segmentin adresi.</span><span class="sxs-lookup"><span data-stu-id="dca86-266">The address of the segment.</span></span>|
|<span data-ttu-id="dca86-267">Boyut</span><span class="sxs-lookup"><span data-stu-id="dca86-267">Size</span></span>|<span data-ttu-id="dca86-268">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="dca86-268">win:UInt64</span></span>|<span data-ttu-id="dca86-269">Segmentin boyutu.</span><span class="sxs-lookup"><span data-stu-id="dca86-269">The size of the segment.</span></span>|
|<span data-ttu-id="dca86-270">Tür</span><span class="sxs-lookup"><span data-stu-id="dca86-270">Type</span></span>|<span data-ttu-id="dca86-271">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="dca86-271">win:UInt32</span></span>|<span data-ttu-id="dca86-272">0x0-küçük nesne yığını.</span><span class="sxs-lookup"><span data-stu-id="dca86-272">0x0 - Small object heap.</span></span><br /><br /> <span data-ttu-id="dca86-273">0x1-büyük nesne yığını.</span><span class="sxs-lookup"><span data-stu-id="dca86-273">0x1 - Large object heap.</span></span><br /><br /> <span data-ttu-id="dca86-274">0x2-salt okunurdur yığın.</span><span class="sxs-lookup"><span data-stu-id="dca86-274">0x2 - Read-only heap.</span></span>|
|<span data-ttu-id="dca86-275">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="dca86-275">ClrInstanceID</span></span>|<span data-ttu-id="dca86-276">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="dca86-276">win:UInt16</span></span>|<span data-ttu-id="dca86-277">CLR veya CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="dca86-277">Unique ID for the instance of CLR or CoreCLR.</span></span>|

<span data-ttu-id="dca86-278">Çöp toplayıcı tarafından ayrılan parçaların boyutunun uygulamaya özgü olduğunu ve düzenli güncelleştirmeler de dahil olmak üzere herhangi bir zamanda değişikliğe tabi olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="dca86-278">Note that the size of segments allocated by the garbage collector is implementation-specific and is subject to change at any time, including in periodic updates.</span></span> <span data-ttu-id="dca86-279">Uygulamanız, belirli bir kesim boyutuna ilişkin varsayımları asla belirtmemelidir veya buna bağlı olarak, kesim ayırmaları için kullanılabilir bellek miktarını yapılandırmayı denemelidir.</span><span class="sxs-lookup"><span data-stu-id="dca86-279">Your app should never make assumptions about or depend on a particular segment size, nor should it attempt to configure the amount of memory available for segment allocations.</span></span>

## <a name="gcfreesegment_v1-event"></a><span data-ttu-id="dca86-280">GCFreeSegment_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="dca86-280">GCFreeSegment_V1 Event</span></span>

<span data-ttu-id="dca86-281">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="dca86-281">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="dca86-282">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="dca86-282">Keyword for raising the event</span></span>|<span data-ttu-id="dca86-283">Düzey</span><span class="sxs-lookup"><span data-stu-id="dca86-283">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="dca86-284">`GCKeyword`0x1</span><span class="sxs-lookup"><span data-stu-id="dca86-284">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="dca86-285">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="dca86-285">Informational (4)</span></span>|

<span data-ttu-id="dca86-286">Aşağıdaki tabloda olay bilgileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="dca86-286">The following table shows the event information:</span></span>

|<span data-ttu-id="dca86-287">Olay</span><span class="sxs-lookup"><span data-stu-id="dca86-287">Event</span></span>|<span data-ttu-id="dca86-288">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="dca86-288">Event ID</span></span>|<span data-ttu-id="dca86-289">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="dca86-289">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCFreeSegment_V1`|<span data-ttu-id="dca86-290">6</span><span class="sxs-lookup"><span data-stu-id="dca86-290">6</span></span>|<span data-ttu-id="dca86-291">Çöp toplama segmenti yayınlandı.</span><span class="sxs-lookup"><span data-stu-id="dca86-291">A garbage collection segment has been released.</span></span>|

<span data-ttu-id="dca86-292">Aşağıdaki tabloda olay verileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="dca86-292">The following table shows the event data:</span></span>

|<span data-ttu-id="dca86-293">Alan adı</span><span class="sxs-lookup"><span data-stu-id="dca86-293">Field name</span></span>|<span data-ttu-id="dca86-294">Veri türü</span><span class="sxs-lookup"><span data-stu-id="dca86-294">Data type</span></span>|<span data-ttu-id="dca86-295">Description</span><span class="sxs-lookup"><span data-stu-id="dca86-295">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="dca86-296">Adres</span><span class="sxs-lookup"><span data-stu-id="dca86-296">Address</span></span>|<span data-ttu-id="dca86-297">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="dca86-297">win:UInt64</span></span>|<span data-ttu-id="dca86-298">Segmentin adresi.</span><span class="sxs-lookup"><span data-stu-id="dca86-298">The address of the segment.</span></span>|
|<span data-ttu-id="dca86-299">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="dca86-299">ClrInstanceID</span></span>|<span data-ttu-id="dca86-300">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="dca86-300">win:UInt16</span></span>|<span data-ttu-id="dca86-301">CLR veya CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="dca86-301">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="gcrestarteebegin_v1-event"></a><span data-ttu-id="dca86-302">GCRestartEEBegin_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="dca86-302">GCRestartEEBegin_V1 Event</span></span>

<span data-ttu-id="dca86-303">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="dca86-303">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="dca86-304">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="dca86-304">Keyword for raising the event</span></span>|<span data-ttu-id="dca86-305">Düzey</span><span class="sxs-lookup"><span data-stu-id="dca86-305">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="dca86-306">`GCKeyword`0x1</span><span class="sxs-lookup"><span data-stu-id="dca86-306">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="dca86-307">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="dca86-307">Informational (4)</span></span>|

<span data-ttu-id="dca86-308">Aşağıdaki tabloda olay bilgileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="dca86-308">The following table shows the event information:</span></span>

|<span data-ttu-id="dca86-309">Olay</span><span class="sxs-lookup"><span data-stu-id="dca86-309">Event</span></span>|<span data-ttu-id="dca86-310">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="dca86-310">Event ID</span></span>|<span data-ttu-id="dca86-311">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="dca86-311">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCRestartEEBegin_V1`|<span data-ttu-id="dca86-312">7</span><span class="sxs-lookup"><span data-stu-id="dca86-312">7</span></span>|<span data-ttu-id="dca86-313">Ortak dil çalışma zamanı askıya alma işleminden sürdürme başladı.</span><span class="sxs-lookup"><span data-stu-id="dca86-313">Resumption from common language runtime suspension has begun.</span></span>|

<span data-ttu-id="dca86-314">Olay verisi yok.</span><span class="sxs-lookup"><span data-stu-id="dca86-314">No event data.</span></span>

## <a name="gcrestarteeend_v1-event"></a><span data-ttu-id="dca86-315">GCRestartEEEnd_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="dca86-315">GCRestartEEEnd_V1 Event</span></span>

<span data-ttu-id="dca86-316">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="dca86-316">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="dca86-317">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="dca86-317">Keyword for raising the event</span></span>|<span data-ttu-id="dca86-318">Düzey</span><span class="sxs-lookup"><span data-stu-id="dca86-318">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="dca86-319">`GCKeyword`0x1</span><span class="sxs-lookup"><span data-stu-id="dca86-319">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="dca86-320">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="dca86-320">Informational (4)</span></span>|

<span data-ttu-id="dca86-321">Aşağıdaki tabloda olay bilgileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="dca86-321">The following table shows the event information:</span></span>

|<span data-ttu-id="dca86-322">Olay</span><span class="sxs-lookup"><span data-stu-id="dca86-322">Event</span></span>|<span data-ttu-id="dca86-323">Olay kimliği</span><span class="sxs-lookup"><span data-stu-id="dca86-323">Event Id</span></span>|<span data-ttu-id="dca86-324">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="dca86-324">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCRestartEEEnd_V1`|<span data-ttu-id="dca86-325">3</span><span class="sxs-lookup"><span data-stu-id="dca86-325">3</span></span>|<span data-ttu-id="dca86-326">Ortak dil çalışma zamanı askıya alma işleminden sürdürme sonlandı.</span><span class="sxs-lookup"><span data-stu-id="dca86-326">Resumption from common language runtime suspension has ended.</span></span>|

<span data-ttu-id="dca86-327">Olay verisi yok.</span><span class="sxs-lookup"><span data-stu-id="dca86-327">No event data.</span></span>

## <a name="gcsuspendee_v1-event"></a><span data-ttu-id="dca86-328">GCSuspendEE_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="dca86-328">GCSuspendEE_V1 Event</span></span>

<span data-ttu-id="dca86-329">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="dca86-329">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="dca86-330">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="dca86-330">Keyword for raising the event</span></span>|<span data-ttu-id="dca86-331">Düzey</span><span class="sxs-lookup"><span data-stu-id="dca86-331">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="dca86-332">`GCKeyword`0x1</span><span class="sxs-lookup"><span data-stu-id="dca86-332">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="dca86-333">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="dca86-333">Informational (4)</span></span>|

<span data-ttu-id="dca86-334">Aşağıdaki tabloda olay bilgileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="dca86-334">The following table shows the event information:</span></span>

|<span data-ttu-id="dca86-335">Olay</span><span class="sxs-lookup"><span data-stu-id="dca86-335">Event</span></span>|<span data-ttu-id="dca86-336">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="dca86-336">Event ID</span></span>|<span data-ttu-id="dca86-337">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="dca86-337">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCSuspendEE_V1`|<span data-ttu-id="dca86-338">9</span><span class="sxs-lookup"><span data-stu-id="dca86-338">9</span></span>|<span data-ttu-id="dca86-339">Çöp toplama için yürütme altyapısının askıya alınma başlangıcı.</span><span class="sxs-lookup"><span data-stu-id="dca86-339">Start of suspension of the execution engine for garbage collection.</span></span>|

<span data-ttu-id="dca86-340">Aşağıdaki tabloda olay verileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="dca86-340">The following table shows the event data:</span></span>

|<span data-ttu-id="dca86-341">Alan adı</span><span class="sxs-lookup"><span data-stu-id="dca86-341">Field name</span></span>|<span data-ttu-id="dca86-342">Veri türü</span><span class="sxs-lookup"><span data-stu-id="dca86-342">Data type</span></span>|<span data-ttu-id="dca86-343">Description</span><span class="sxs-lookup"><span data-stu-id="dca86-343">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="dca86-344">Neden</span><span class="sxs-lookup"><span data-stu-id="dca86-344">Reason</span></span>|<span data-ttu-id="dca86-345">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="dca86-345">win:UInt16</span></span>|<span data-ttu-id="dca86-346">0x0-diğer.</span><span class="sxs-lookup"><span data-stu-id="dca86-346">0x0 - Other.</span></span><br /><br /> <span data-ttu-id="dca86-347">0x1-çöp toplama.</span><span class="sxs-lookup"><span data-stu-id="dca86-347">0x1 - Garbage collection.</span></span><br /><br /> <span data-ttu-id="dca86-348">0x2-Uygulama etki alanı kapanıyor.</span><span class="sxs-lookup"><span data-stu-id="dca86-348">0x2 - Application domain shutdown.</span></span><br /><br /> <span data-ttu-id="dca86-349">0x3-kod yeniden getiriliyor.</span><span class="sxs-lookup"><span data-stu-id="dca86-349">0x3 - Code pitching.</span></span><br /><br /> <span data-ttu-id="dca86-350">0x4-kapanıyor.</span><span class="sxs-lookup"><span data-stu-id="dca86-350">0x4 - Shutdown.</span></span><br /><br /> <span data-ttu-id="dca86-351">0x5-Debugger.</span><span class="sxs-lookup"><span data-stu-id="dca86-351">0x5 - Debugger.</span></span><br /><br /> <span data-ttu-id="dca86-352">çöp toplama için 0x6 hazırlığı.</span><span class="sxs-lookup"><span data-stu-id="dca86-352">0x6 - Preparation for garbage collection.</span></span>|
|<span data-ttu-id="dca86-353">Count</span><span class="sxs-lookup"><span data-stu-id="dca86-353">Count</span></span>|<span data-ttu-id="dca86-354">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="dca86-354">win:UInt32</span></span>|<span data-ttu-id="dca86-355">GC sayısı (saat).</span><span class="sxs-lookup"><span data-stu-id="dca86-355">The GC count at the time.</span></span> <span data-ttu-id="dca86-356">Genellikle, bundan sonra sonraki bir GC başlangıç olayını görürsünüz ve çöp toplama sırasında GC dizinini artırdıkça bu sayı + 1 olur.</span><span class="sxs-lookup"><span data-stu-id="dca86-356">Usually, you would see a subsequent GC Start event after this, and its Count would be this Count + 1 as we increase the GC index during a garbage collection.</span></span>|
|<span data-ttu-id="dca86-357">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="dca86-357">ClrInstanceID</span></span>|<span data-ttu-id="dca86-358">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="dca86-358">win:UInt16</span></span>|<span data-ttu-id="dca86-359">CLR veya CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="dca86-359">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="gcsuspendeeend_v1-event"></a><span data-ttu-id="dca86-360">GCSuspendEEEnd_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="dca86-360">GCSuspendEEEnd_V1 Event</span></span>

<span data-ttu-id="dca86-361">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="dca86-361">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="dca86-362">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="dca86-362">Keyword for raising the event</span></span>|<span data-ttu-id="dca86-363">Düzey</span><span class="sxs-lookup"><span data-stu-id="dca86-363">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="dca86-364">`GCKeyword`0x1</span><span class="sxs-lookup"><span data-stu-id="dca86-364">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="dca86-365">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="dca86-365">Informational (4)</span></span>|

<span data-ttu-id="dca86-366">Aşağıdaki tabloda olay bilgileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="dca86-366">The following table shows the event information:</span></span>

|<span data-ttu-id="dca86-367">Olay</span><span class="sxs-lookup"><span data-stu-id="dca86-367">Event</span></span>|<span data-ttu-id="dca86-368">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="dca86-368">Event ID</span></span>|<span data-ttu-id="dca86-369">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="dca86-369">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCSuspendEEEnd_V1`|<span data-ttu-id="dca86-370">8</span><span class="sxs-lookup"><span data-stu-id="dca86-370">8</span></span>|<span data-ttu-id="dca86-371">Çöp toplama için yürütme altyapısının askıya alınma sonu.</span><span class="sxs-lookup"><span data-stu-id="dca86-371">End of suspension of the execution engine for garbage collection.</span></span>|

<span data-ttu-id="dca86-372">Olay verisi yok.</span><span class="sxs-lookup"><span data-stu-id="dca86-372">No event data.</span></span>

## <a name="gcallocationtick_v2-event"></a><span data-ttu-id="dca86-373">GCAllocationTick_V2 olayı</span><span class="sxs-lookup"><span data-stu-id="dca86-373">GCAllocationTick_V2 Event</span></span>

<span data-ttu-id="dca86-374">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="dca86-374">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="dca86-375">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="dca86-375">Keyword for raising the event</span></span>|<span data-ttu-id="dca86-376">Düzey</span><span class="sxs-lookup"><span data-stu-id="dca86-376">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="dca86-377">`GCKeyword`0x1</span><span class="sxs-lookup"><span data-stu-id="dca86-377">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="dca86-378">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="dca86-378">Informational (4)</span></span>|

<span data-ttu-id="dca86-379">Aşağıdaki tabloda olay bilgileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="dca86-379">The following table shows the event information:</span></span>

|<span data-ttu-id="dca86-380">Olay</span><span class="sxs-lookup"><span data-stu-id="dca86-380">Event</span></span>|<span data-ttu-id="dca86-381">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="dca86-381">Event ID</span></span>|<span data-ttu-id="dca86-382">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="dca86-382">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCAllocationTick_V2`|<span data-ttu-id="dca86-383">10</span><span class="sxs-lookup"><span data-stu-id="dca86-383">10</span></span>|<span data-ttu-id="dca86-384">Yaklaşık 100 KB ayrıldığı her seferinde.</span><span class="sxs-lookup"><span data-stu-id="dca86-384">Each time approximately 100 KB is allocated.</span></span>|

<span data-ttu-id="dca86-385">Aşağıdaki tabloda olay verileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="dca86-385">The following table shows the event data:</span></span>

|<span data-ttu-id="dca86-386">Alan adı</span><span class="sxs-lookup"><span data-stu-id="dca86-386">Field name</span></span>|<span data-ttu-id="dca86-387">Veri türü</span><span class="sxs-lookup"><span data-stu-id="dca86-387">Data type</span></span>|<span data-ttu-id="dca86-388">Description</span><span class="sxs-lookup"><span data-stu-id="dca86-388">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="dca86-389">AllocationAmount</span><span class="sxs-lookup"><span data-stu-id="dca86-389">AllocationAmount</span></span>|<span data-ttu-id="dca86-390">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="dca86-390">win:UInt32</span></span>|<span data-ttu-id="dca86-391">Bayt cinsinden ayırma boyutu.</span><span class="sxs-lookup"><span data-stu-id="dca86-391">The allocation size, in bytes.</span></span> <span data-ttu-id="dca86-392">Bu değer, ULONG 'un uzunluğundan (4.294.967.295 bayt) daha az olan ayırmalar için doğrudur.</span><span class="sxs-lookup"><span data-stu-id="dca86-392">This value is accurate for allocations that are less than the length of a ULONG (4,294,967,295 bytes).</span></span> <span data-ttu-id="dca86-393">Ayırma daha büyükse, bu alan kesilmiş bir değer içerir.</span><span class="sxs-lookup"><span data-stu-id="dca86-393">If the allocation is greater, this field contains a truncated value.</span></span> <span data-ttu-id="dca86-394">`AllocationAmount64`Çok büyük ayırmalar için kullanın.</span><span class="sxs-lookup"><span data-stu-id="dca86-394">Use `AllocationAmount64` for very large allocations.</span></span>|
|<span data-ttu-id="dca86-395">AllocationKind</span><span class="sxs-lookup"><span data-stu-id="dca86-395">AllocationKind</span></span>|<span data-ttu-id="dca86-396">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="dca86-396">win:UInt32</span></span>|<span data-ttu-id="dca86-397">0x0-küçük nesne ayırma (ayırma küçük nesne yığınında).</span><span class="sxs-lookup"><span data-stu-id="dca86-397">0x0 - Small object allocation (allocation is in small object heap).</span></span><br /><br /> <span data-ttu-id="dca86-398">0x1-büyük nesne ayırma (ayırma büyük nesne yığınında).</span><span class="sxs-lookup"><span data-stu-id="dca86-398">0x1 - Large object allocation (allocation is in large object heap).</span></span>|
|<span data-ttu-id="dca86-399">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="dca86-399">ClrInstanceID</span></span>|<span data-ttu-id="dca86-400">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="dca86-400">win:UInt16</span></span>|<span data-ttu-id="dca86-401">CLR veya CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="dca86-401">Unique ID for the instance of CLR or CoreCLR.</span></span>|
|<span data-ttu-id="dca86-402">AllocationAmount64</span><span class="sxs-lookup"><span data-stu-id="dca86-402">AllocationAmount64</span></span>|<span data-ttu-id="dca86-403">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="dca86-403">win:UInt64</span></span>|<span data-ttu-id="dca86-404">Bayt cinsinden ayırma boyutu.</span><span class="sxs-lookup"><span data-stu-id="dca86-404">The allocation size, in bytes.</span></span> <span data-ttu-id="dca86-405">Bu değer, çok büyük ayırmalar için doğrudur.</span><span class="sxs-lookup"><span data-stu-id="dca86-405">This value is accurate for very large allocations.</span></span>|
|<span data-ttu-id="dca86-406">Türü</span><span class="sxs-lookup"><span data-stu-id="dca86-406">TypeId</span></span>|<span data-ttu-id="dca86-407">Win: Işaretçi</span><span class="sxs-lookup"><span data-stu-id="dca86-407">win:Pointer</span></span>|<span data-ttu-id="dca86-408">MethodTable 'ın adresi.</span><span class="sxs-lookup"><span data-stu-id="dca86-408">The address of the MethodTable.</span></span> <span data-ttu-id="dca86-409">Bu olay sırasında ayrılan çeşitli nesne türleri olduğunda, bu, ayrılan son nesneye (100 KB eşiğinin aşılmasına neden olan nesne) karşılık gelen MethodTable 'ın adresidir.</span><span class="sxs-lookup"><span data-stu-id="dca86-409">When there are several types of objects that were allocated during this event, this is the address of the MethodTable that corresponds to the last object allocated (the object that caused the 100 KB threshold to be exceeded).</span></span>|
|<span data-ttu-id="dca86-410">TypeName</span><span class="sxs-lookup"><span data-stu-id="dca86-410">TypeName</span></span>|<span data-ttu-id="dca86-411">Win: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="dca86-411">win:UnicodeString</span></span>|<span data-ttu-id="dca86-412">Ayrılan türün adı.</span><span class="sxs-lookup"><span data-stu-id="dca86-412">The name of the type that was allocated.</span></span> <span data-ttu-id="dca86-413">Bu olay sırasında ayrılan çeşitli nesne türleri varsa, bu, ayrılan son nesnenin türüdür (100 KB eşiğinin aşılmasına neden olan nesne).</span><span class="sxs-lookup"><span data-stu-id="dca86-413">When there are several types of objects that were allocated during this event, this is the type of the last object allocated (the object that caused the 100 KB threshold to be exceeded).</span></span>|
|<span data-ttu-id="dca86-414">Heapındex</span><span class="sxs-lookup"><span data-stu-id="dca86-414">HeapIndex</span></span>|<span data-ttu-id="dca86-415">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="dca86-415">win:UInt32</span></span>|<span data-ttu-id="dca86-416">Nesnenin ayrıldığı yığın.</span><span class="sxs-lookup"><span data-stu-id="dca86-416">The heap where the object was allocated.</span></span> <span data-ttu-id="dca86-417">Bu değer, iş istasyonu atık toplama ile çalıştırılırken 0 (sıfır) değeridir.</span><span class="sxs-lookup"><span data-stu-id="dca86-417">This value is 0 (zero) when running with workstation garbage collection.</span></span>|

## <a name="gcfinalizersbegin_v1-event"></a><span data-ttu-id="dca86-418">GCFinalizersBegin_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="dca86-418">GCFinalizersBegin_V1 Event</span></span>

<span data-ttu-id="dca86-419">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="dca86-419">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="dca86-420">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="dca86-420">Keyword for raising the event</span></span>|<span data-ttu-id="dca86-421">Düzey</span><span class="sxs-lookup"><span data-stu-id="dca86-421">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="dca86-422">`GCKeyword`0x1</span><span class="sxs-lookup"><span data-stu-id="dca86-422">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="dca86-423">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="dca86-423">Informational (4)</span></span>|

<span data-ttu-id="dca86-424">Aşağıdaki tabloda olay bilgileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="dca86-424">The following table shows the event information:</span></span>

|<span data-ttu-id="dca86-425">Olay</span><span class="sxs-lookup"><span data-stu-id="dca86-425">Event</span></span>|<span data-ttu-id="dca86-426">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="dca86-426">Event ID</span></span>|<span data-ttu-id="dca86-427">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="dca86-427">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCFinalizersBegin_V1`|<span data-ttu-id="dca86-428">14</span><span class="sxs-lookup"><span data-stu-id="dca86-428">14</span></span>|<span data-ttu-id="dca86-429">Sonlandırıcıları çalıştırmanın başlangıcı.</span><span class="sxs-lookup"><span data-stu-id="dca86-429">The start of running finalizers.</span></span>|

<span data-ttu-id="dca86-430">Olay verisi yok.</span><span class="sxs-lookup"><span data-stu-id="dca86-430">No event data.</span></span>

## <a name="gcfinalizersend_v1-event"></a><span data-ttu-id="dca86-431">GCFinalizersEnd_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="dca86-431">GCFinalizersEnd_V1 Event</span></span>

<span data-ttu-id="dca86-432">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="dca86-432">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="dca86-433">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="dca86-433">Keyword for raising the event</span></span>|<span data-ttu-id="dca86-434">Düzey</span><span class="sxs-lookup"><span data-stu-id="dca86-434">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="dca86-435">`GCKeyword`0x1</span><span class="sxs-lookup"><span data-stu-id="dca86-435">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="dca86-436">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="dca86-436">Informational (4)</span></span>|

<span data-ttu-id="dca86-437">Aşağıdaki tabloda olay bilgileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="dca86-437">The following table shows the event information:</span></span>

|<span data-ttu-id="dca86-438">Olay</span><span class="sxs-lookup"><span data-stu-id="dca86-438">Event</span></span>|<span data-ttu-id="dca86-439">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="dca86-439">Event ID</span></span>|<span data-ttu-id="dca86-440">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="dca86-440">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCFinalizersEnd_V1`|<span data-ttu-id="dca86-441">13</span><span class="sxs-lookup"><span data-stu-id="dca86-441">13</span></span>|<span data-ttu-id="dca86-442">Sonlandırıcılardan çalıştırmanın sonu.</span><span class="sxs-lookup"><span data-stu-id="dca86-442">The end of running finalizers.</span></span>|

<span data-ttu-id="dca86-443">Aşağıdaki tabloda olay verileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="dca86-443">The following table shows the event data:</span></span>

|<span data-ttu-id="dca86-444">Alan adı</span><span class="sxs-lookup"><span data-stu-id="dca86-444">Field name</span></span>|<span data-ttu-id="dca86-445">Veri türü</span><span class="sxs-lookup"><span data-stu-id="dca86-445">Data type</span></span>|<span data-ttu-id="dca86-446">Description</span><span class="sxs-lookup"><span data-stu-id="dca86-446">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="dca86-447">Count</span><span class="sxs-lookup"><span data-stu-id="dca86-447">Count</span></span>|<span data-ttu-id="dca86-448">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="dca86-448">win:UInt32</span></span>|<span data-ttu-id="dca86-449">Çalıştırılan sonlandırıcılar sayısı.</span><span class="sxs-lookup"><span data-stu-id="dca86-449">The number of finalizers that were run.</span></span>|
|<span data-ttu-id="dca86-450">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="dca86-450">ClrInstanceID</span></span>|<span data-ttu-id="dca86-451">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="dca86-451">win:UInt16</span></span>|<span data-ttu-id="dca86-452">CLR veya CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="dca86-452">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="gccreateconcurrentthread_v1-event"></a><span data-ttu-id="dca86-453">GCCreateConcurrentThread_V1 Olayı</span><span class="sxs-lookup"><span data-stu-id="dca86-453">GCCreateConcurrentThread_V1 Event</span></span>

<span data-ttu-id="dca86-454">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="dca86-454">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="dca86-455">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="dca86-455">Keyword for raising the event</span></span>|<span data-ttu-id="dca86-456">Düzey</span><span class="sxs-lookup"><span data-stu-id="dca86-456">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="dca86-457">`GCKeyword`0x1</span><span class="sxs-lookup"><span data-stu-id="dca86-457">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="dca86-458">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="dca86-458">Informational (4)</span></span>|
|<span data-ttu-id="dca86-459">`ThreadingKeyword`(0x10000)</span><span class="sxs-lookup"><span data-stu-id="dca86-459">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="dca86-460">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="dca86-460">Informational (4)</span></span>|

<span data-ttu-id="dca86-461">Aşağıdaki tabloda olay bilgileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="dca86-461">The following table shows the event information:</span></span>

|<span data-ttu-id="dca86-462">Olay</span><span class="sxs-lookup"><span data-stu-id="dca86-462">Event</span></span>|<span data-ttu-id="dca86-463">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="dca86-463">Event ID</span></span>|<span data-ttu-id="dca86-464">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="dca86-464">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCCreateConcurrentThread_V1`|<span data-ttu-id="dca86-465">11</span><span class="sxs-lookup"><span data-stu-id="dca86-465">11</span></span>|<span data-ttu-id="dca86-466">Eşzamanlı atık toplama iş parçacığı oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="dca86-466">Concurrent garbage collection thread was created.</span></span>|

<span data-ttu-id="dca86-467">Olay verisi yok.</span><span class="sxs-lookup"><span data-stu-id="dca86-467">No event data.</span></span>

## <a name="gcterminateconcurrentthread_v1-event"></a><span data-ttu-id="dca86-468">GCTerminateConcurrentThread_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="dca86-468">GCTerminateConcurrentThread_V1 Event</span></span>

<span data-ttu-id="dca86-469">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="dca86-469">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="dca86-470">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="dca86-470">Keyword for raising the event</span></span>|<span data-ttu-id="dca86-471">Düzey</span><span class="sxs-lookup"><span data-stu-id="dca86-471">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="dca86-472">`GCKeyword`0x1</span><span class="sxs-lookup"><span data-stu-id="dca86-472">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="dca86-473">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="dca86-473">Informational (4)</span></span>|
|<span data-ttu-id="dca86-474">`ThreadingKeyword`(0x10000)</span><span class="sxs-lookup"><span data-stu-id="dca86-474">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="dca86-475">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="dca86-475">Informational (4)</span></span>|

<span data-ttu-id="dca86-476">Aşağıdaki tabloda olay bilgileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="dca86-476">The following table shows the event information:</span></span>

|<span data-ttu-id="dca86-477">Olay</span><span class="sxs-lookup"><span data-stu-id="dca86-477">Event</span></span>|<span data-ttu-id="dca86-478">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="dca86-478">Event ID</span></span>|<span data-ttu-id="dca86-479">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="dca86-479">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCTerminateConcurrentThread_V1`|<span data-ttu-id="dca86-480">12</span><span class="sxs-lookup"><span data-stu-id="dca86-480">12</span></span>|<span data-ttu-id="dca86-481">Eşzamanlı atık toplama iş parçacığı sonlandırıldı.</span><span class="sxs-lookup"><span data-stu-id="dca86-481">Concurrent garbage collection thread was terminated.</span></span>|

<span data-ttu-id="dca86-482">Olay verisi yok.</span><span class="sxs-lookup"><span data-stu-id="dca86-482">No event data.</span></span>

## <a name="see-also"></a><span data-ttu-id="dca86-483">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dca86-483">See also</span></span>

- [<span data-ttu-id="dca86-484">CLR ETW Olayları</span><span class="sxs-lookup"><span data-stu-id="dca86-484">CLR ETW Events</span></span>](clr-etw-events.md)
