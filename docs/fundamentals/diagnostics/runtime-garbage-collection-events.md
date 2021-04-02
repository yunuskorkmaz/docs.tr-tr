---
title: Çöp toplama çalışma zamanı olayları
description: .NET atık toplayıcısına özgü tanılama bilgilerini topladığımız .NET çalışma zamanı olaylarına bakın.
ms.date: 11/13/2020
ms.topic: reference
helpviewer_keywords:
- GC events
- garbage collection events (CoreCLR)
- ETW, EventPipe, LTTng garbage collection events (CoreCLR)
ms.openlocfilehash: 2799a93f351baf23ec7a359b0b4b2be5c216dc4d
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/30/2021
ms.locfileid: "96590001"
---
# <a name="net-runtime-garbage-collection-events"></a><span data-ttu-id="ce772-103">.NET çalışma zamanı atık toplama olayları</span><span class="sxs-lookup"><span data-stu-id="ce772-103">.NET runtime garbage collection events</span></span>

<span data-ttu-id="ce772-104">Bu olaylar çöp koleksiyonuyla ilgili bilgiler toplar.</span><span class="sxs-lookup"><span data-stu-id="ce772-104">These events collect information pertaining to garbage collection.</span></span> <span data-ttu-id="ce772-105">Çöp toplamanın kaç kez gerçekleştirildiğini belirleme, çöp toplama sırasında ne kadar bellek serbest bırakılmış vb. gibi tanılama ve hata ayıklama konusunda yardımcı olurlar. Bu olayların tanılama amacıyla nasıl kullanılacağı hakkında daha fazla bilgi için bkz. [.NET uygulamalarını günlüğe kaydetme ve izleme](../../core/diagnostics/logging-tracing.md)</span><span class="sxs-lookup"><span data-stu-id="ce772-105">They help in diagnostics and debugging, including determining how many times garbage collection was performed, how much memory was freed during garbage collection, etc. For more information about how to use these events for diagnostic purposes, see [logging and tracing .NET applications](../../core/diagnostics/logging-tracing.md)</span></span>

## <a name="gcstart_v2-event"></a><span data-ttu-id="ce772-106">GCStart_V2 olayı</span><span class="sxs-lookup"><span data-stu-id="ce772-106">GCStart_V2 Event</span></span>

<span data-ttu-id="ce772-107">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="ce772-107">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="ce772-108">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="ce772-108">Keyword for raising the event</span></span>|<span data-ttu-id="ce772-109">Level</span><span class="sxs-lookup"><span data-stu-id="ce772-109">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="ce772-110">`GCKeyword` 0x1</span><span class="sxs-lookup"><span data-stu-id="ce772-110">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="ce772-111">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="ce772-111">Informational (4)</span></span>|

<span data-ttu-id="ce772-112">Aşağıdaki tabloda olay bilgileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="ce772-112">The following table shows the event information:</span></span>

|<span data-ttu-id="ce772-113">Olay</span><span class="sxs-lookup"><span data-stu-id="ce772-113">Event</span></span>|<span data-ttu-id="ce772-114">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="ce772-114">Event ID</span></span>|<span data-ttu-id="ce772-115">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="ce772-115">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCStart_V1`|<span data-ttu-id="ce772-116">1</span><span class="sxs-lookup"><span data-stu-id="ce772-116">1</span></span>|<span data-ttu-id="ce772-117">Çöp toplama işlemi başlatıldı.</span><span class="sxs-lookup"><span data-stu-id="ce772-117">A garbage collection has started.</span></span>|

<span data-ttu-id="ce772-118">Aşağıdaki tabloda olay verileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="ce772-118">The following table shows the event data:</span></span>

|<span data-ttu-id="ce772-119">Alan adı</span><span class="sxs-lookup"><span data-stu-id="ce772-119">Field name</span></span>|<span data-ttu-id="ce772-120">Veri türü</span><span class="sxs-lookup"><span data-stu-id="ce772-120">Data type</span></span>|<span data-ttu-id="ce772-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ce772-121">Description</span></span>|
|----------------|---------------|-----------------|
|`Count`|`win:UInt32`|<span data-ttu-id="ce772-122">*N*. çöp toplama.</span><span class="sxs-lookup"><span data-stu-id="ce772-122">The *n* th garbage collection.</span></span>|
|`Depth`|`win:UInt32`|<span data-ttu-id="ce772-123">Toplanmakta olan oluşturma.</span><span class="sxs-lookup"><span data-stu-id="ce772-123">The generation that is being collected.</span></span>|
|`Reason`|`win:UInt32`|<span data-ttu-id="ce772-124">Çöp toplamanın neden tetiklendiği:</span><span class="sxs-lookup"><span data-stu-id="ce772-124">Why the garbage collection was triggered:</span></span><br /><br /> <span data-ttu-id="ce772-125">`0x0` -Küçük nesne yığını ayırması.</span><span class="sxs-lookup"><span data-stu-id="ce772-125">`0x0` - Small object heap allocation.</span></span><br /><br /> <span data-ttu-id="ce772-126">`0x1` Zorlanmadı.</span><span class="sxs-lookup"><span data-stu-id="ce772-126">`0x1` - Induced.</span></span><br /><br /> <span data-ttu-id="ce772-127">`0x2` -Düşük bellek.</span><span class="sxs-lookup"><span data-stu-id="ce772-127">`0x2` - Low memory.</span></span><br /><br /> <span data-ttu-id="ce772-128">`0x3` Olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="ce772-128">`0x3` - Empty.</span></span><br /><br /> <span data-ttu-id="ce772-129">`0x4` -Büyük nesne yığını ayırması.</span><span class="sxs-lookup"><span data-stu-id="ce772-129">`0x4` - Large object heap allocation.</span></span><br /><br /> <span data-ttu-id="ce772-130">`0x5` -Alan kalmadı (küçük nesne yığını için).</span><span class="sxs-lookup"><span data-stu-id="ce772-130">`0x5` - Out of space (for small object heap).</span></span><br /><br /> <span data-ttu-id="ce772-131">`0x6` -Alan kalmadı (büyük nesne yığını için).</span><span class="sxs-lookup"><span data-stu-id="ce772-131">`0x6` - Out of space (for large object heap).</span></span><br /><br /> <span data-ttu-id="ce772-132">`0x7` -Alınmış ancak engelleme olarak zorlanmadı.</span><span class="sxs-lookup"><span data-stu-id="ce772-132">`0x7` - Induced but not forced as blocking.</span></span>|
|`Type`|`win:UInt32`|<span data-ttu-id="ce772-133">`0x0` -Arka plan atık toplama dışında çöp toplama engelleme gerçekleşti.</span><span class="sxs-lookup"><span data-stu-id="ce772-133">`0x0` - Blocking garbage collection occurred outside background garbage collection.</span></span><br /><br /> <span data-ttu-id="ce772-134">`0x1` -Arka plan atık toplama.</span><span class="sxs-lookup"><span data-stu-id="ce772-134">`0x1` - Background garbage collection.</span></span><br /><br /> <span data-ttu-id="ce772-135">`0x2` -Arka plan atık toplama sırasında atık toplamayı engelleme oluştu.</span><span class="sxs-lookup"><span data-stu-id="ce772-135">`0x2` - Blocking garbage collection occurred during background garbage collection.</span></span>|
|`ClrInstanceID`|<span data-ttu-id="ce772-136">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="ce772-136">win:UInt16</span></span>|<span data-ttu-id="ce772-137">CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="ce772-137">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="gcend_v1-event"></a><span data-ttu-id="ce772-138">GCEnd_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="ce772-138">GCEnd_V1 Event</span></span>

<span data-ttu-id="ce772-139">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="ce772-139">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="ce772-140">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="ce772-140">Keyword for raising the event</span></span>|<span data-ttu-id="ce772-141">Level</span><span class="sxs-lookup"><span data-stu-id="ce772-141">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="ce772-142">`GCKeyword` 0x1</span><span class="sxs-lookup"><span data-stu-id="ce772-142">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="ce772-143">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="ce772-143">Informational (4)</span></span>|

<span data-ttu-id="ce772-144">Aşağıdaki tabloda olay bilgileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="ce772-144">The following table shows the event information:</span></span>

|<span data-ttu-id="ce772-145">Olay</span><span class="sxs-lookup"><span data-stu-id="ce772-145">Event</span></span>|<span data-ttu-id="ce772-146">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="ce772-146">Event ID</span></span>|<span data-ttu-id="ce772-147">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="ce772-147">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCEnd_V1`|<span data-ttu-id="ce772-148">2</span><span class="sxs-lookup"><span data-stu-id="ce772-148">2</span></span>|<span data-ttu-id="ce772-149">Çöp toplama sona erdi.</span><span class="sxs-lookup"><span data-stu-id="ce772-149">The garbage collection has ended.</span></span>|

<span data-ttu-id="ce772-150">Aşağıdaki tabloda olay verileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="ce772-150">The following table shows the event data:</span></span>

|<span data-ttu-id="ce772-151">Alan adı</span><span class="sxs-lookup"><span data-stu-id="ce772-151">Field name</span></span>|<span data-ttu-id="ce772-152">Veri türü</span><span class="sxs-lookup"><span data-stu-id="ce772-152">Data type</span></span>|<span data-ttu-id="ce772-153">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ce772-153">Description</span></span>|
|----------------|---------------|-----------------|
|`Count`|`win:UInt32`|<span data-ttu-id="ce772-154">*N*. çöp toplama.</span><span class="sxs-lookup"><span data-stu-id="ce772-154">The *n* th garbage collection.</span></span>|
|`Depth`|`win:UInt32`|<span data-ttu-id="ce772-155">Toplanan nesil.</span><span class="sxs-lookup"><span data-stu-id="ce772-155">The generation that was collected.</span></span>|
|`ClrInstanceID`|<span data-ttu-id="ce772-156">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="ce772-156">win:UInt16</span></span>|<span data-ttu-id="ce772-157">CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="ce772-157">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="gcheapstats_v2-event"></a><span data-ttu-id="ce772-158">GCHeapStats_V2 olayı</span><span class="sxs-lookup"><span data-stu-id="ce772-158">GCHeapStats_V2 Event</span></span>

<span data-ttu-id="ce772-159">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="ce772-159">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="ce772-160">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="ce772-160">Keyword for raising the event</span></span>|<span data-ttu-id="ce772-161">Level</span><span class="sxs-lookup"><span data-stu-id="ce772-161">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="ce772-162">`GCKeyword` 0x1</span><span class="sxs-lookup"><span data-stu-id="ce772-162">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="ce772-163">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="ce772-163">Informational (4)</span></span>|

<span data-ttu-id="ce772-164">Aşağıdaki tabloda olay bilgileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="ce772-164">The following table shows the event information:</span></span>

|<span data-ttu-id="ce772-165">Olay</span><span class="sxs-lookup"><span data-stu-id="ce772-165">Event</span></span>|<span data-ttu-id="ce772-166">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="ce772-166">Event ID</span></span>|<span data-ttu-id="ce772-167">Description</span><span class="sxs-lookup"><span data-stu-id="ce772-167">Description</span></span>|
|-----------|--------------|-----------------|
|`GCHeapStats_V2`|<span data-ttu-id="ce772-168">4</span><span class="sxs-lookup"><span data-stu-id="ce772-168">4</span></span>|<span data-ttu-id="ce772-169">Her çöp toplamanın sonundaki yığın istatistiklerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="ce772-169">Shows the heap statistics at the end of each garbage collection.</span></span>|

<span data-ttu-id="ce772-170">Aşağıdaki tabloda olay verileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="ce772-170">The following table shows the event data:</span></span>

|<span data-ttu-id="ce772-171">Alan adı</span><span class="sxs-lookup"><span data-stu-id="ce772-171">Field name</span></span>|<span data-ttu-id="ce772-172">Veri türü</span><span class="sxs-lookup"><span data-stu-id="ce772-172">Data type</span></span>|<span data-ttu-id="ce772-173">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ce772-173">Description</span></span>|
|----------------|---------------|-----------------|
|`GenerationSize0`|`win:UInt64`|<span data-ttu-id="ce772-174">0. nesil belleğin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="ce772-174">The size, in bytes, of generation 0 memory.</span></span>|
|`TotalPromotedSize0`|`win:UInt64`|<span data-ttu-id="ce772-175">Nesil 0 ' dan 1 ' e yükseltilen bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="ce772-175">The number of bytes that are promoted from generation 0 to generation 1.</span></span>|
|`GenerationSize1`|`win:UInt64`|<span data-ttu-id="ce772-176">1. nesil belleğin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="ce772-176">The size, in bytes, of generation 1 memory.</span></span>|
|`TotalPromotedSize1`|`win:UInt64`|<span data-ttu-id="ce772-177">1. nesil 2 ' ye kadar yükseltilen bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="ce772-177">The number of bytes that are promoted from generation 1 to generation 2.</span></span>|
|`GenerationSize2`|`win:UInt64`|<span data-ttu-id="ce772-178">2. nesil belleğin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="ce772-178">The size, in bytes, of generation 2 memory.</span></span>|
|`TotalPromotedSize2`|`win:UInt64`|<span data-ttu-id="ce772-179">Son koleksiyondan sonra 2. nesil üzerinde kalan bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="ce772-179">The number of bytes that survived in generation 2 after the last collection.</span></span>|
|`GenerationSize3`|`win:UInt64`|<span data-ttu-id="ce772-180">Büyük nesne yığınının bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="ce772-180">The size, in bytes, of the large object heap.</span></span>|
|`TotalPromotedSize3`|`win:UInt64`|<span data-ttu-id="ce772-181">Son koleksiyondan sonra büyük nesne yığınında kalan bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="ce772-181">The number of bytes that survived in the large object heap after the last collection.</span></span>|
|`FinalizationPromotedSize`|`win:UInt64`|<span data-ttu-id="ce772-182">Sonlandırma için hazırlanma nesnelerinin bayt cinsinden toplam boyutu.</span><span class="sxs-lookup"><span data-stu-id="ce772-182">The total size, in bytes, of the objects that are ready for finalization.</span></span>|
|`FinalizationPromotedCount`|`win:UInt64`|<span data-ttu-id="ce772-183">Sonlandırmaya hazırlanma nesne sayısı.</span><span class="sxs-lookup"><span data-stu-id="ce772-183">The number of objects that are ready for finalization.</span></span>|
|`PinnedObjectCount`|`win:UInt32`|<span data-ttu-id="ce772-184">Sabitlenmiş (taşınamaz) nesne sayısı.</span><span class="sxs-lookup"><span data-stu-id="ce772-184">The number of pinned (unmovable) objects.</span></span>|
|`SinkBlockCount`|`win:UInt32`|<span data-ttu-id="ce772-185">Kullanımdaki eşitleme bloklarının sayısı.</span><span class="sxs-lookup"><span data-stu-id="ce772-185">The number of synchronization blocks in use.</span></span>|
|`GCHandleCount`|`win:UInt32`|<span data-ttu-id="ce772-186">Kullanımdaki çöp toplama tanıtıcılarının sayısı.</span><span class="sxs-lookup"><span data-stu-id="ce772-186">The number of garbage collection handles in use.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="ce772-187">CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="ce772-187">Unique ID for the instance of CoreCLR.</span></span>|
|`GenerationSize4`|`win:UInt64`|<span data-ttu-id="ce772-188">Sabitlenmiş nesne yığınının bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="ce772-188">The size, in bytes, of the pinned object heap.</span></span>|
|`TotalPromotedSize4`|`win:UInt64`|<span data-ttu-id="ce772-189">Son koleksiyondan sonra sabitlenmiş nesne yığınında kalan bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="ce772-189">The number of bytes that survived in the pinned object heap after the last collection.</span></span>|

## <a name="gccreatesegment_v1-event"></a><span data-ttu-id="ce772-190">GCCreateSegment_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="ce772-190">GCCreateSegment_V1 event</span></span>

<span data-ttu-id="ce772-191">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="ce772-191">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="ce772-192">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="ce772-192">Keyword for raising the event</span></span>|<span data-ttu-id="ce772-193">Level</span><span class="sxs-lookup"><span data-stu-id="ce772-193">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="ce772-194">`GCKeyword` 0x1</span><span class="sxs-lookup"><span data-stu-id="ce772-194">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="ce772-195">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="ce772-195">Informational (4)</span></span>|

<span data-ttu-id="ce772-196">Aşağıdaki tabloda olay bilgileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="ce772-196">The following table shows the event information:</span></span>

|<span data-ttu-id="ce772-197">Olay</span><span class="sxs-lookup"><span data-stu-id="ce772-197">Event</span></span>|<span data-ttu-id="ce772-198">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="ce772-198">Event ID</span></span>|<span data-ttu-id="ce772-199">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="ce772-199">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCCreateSegment_V1`|<span data-ttu-id="ce772-200">5</span><span class="sxs-lookup"><span data-stu-id="ce772-200">5</span></span>|<span data-ttu-id="ce772-201">Yeni bir atık toplama segmenti oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="ce772-201">A new garbage collection segment has been created.</span></span> <span data-ttu-id="ce772-202">Ayrıca, izleme zaten çalışmakta olan bir işlemde etkinleştirildiğinde, bu olay varolan her segment için oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="ce772-202">In addition, when tracing is enabled on a process that is already running, this event is raised for each existing segment.</span></span>|

<span data-ttu-id="ce772-203">Aşağıdaki tabloda olay verileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="ce772-203">The following table shows the event data:</span></span>

|<span data-ttu-id="ce772-204">Alan adı</span><span class="sxs-lookup"><span data-stu-id="ce772-204">Field name</span></span>|<span data-ttu-id="ce772-205">Veri türü</span><span class="sxs-lookup"><span data-stu-id="ce772-205">Data type</span></span>|<span data-ttu-id="ce772-206">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ce772-206">Description</span></span>|
|----------------|---------------|-----------------|
|`Address`|`win:UInt64`|<span data-ttu-id="ce772-207">Segmentin adresi.</span><span class="sxs-lookup"><span data-stu-id="ce772-207">The address of the segment.</span></span>|
|`Size`|`win:UInt64`|<span data-ttu-id="ce772-208">Segmentin boyutu.</span><span class="sxs-lookup"><span data-stu-id="ce772-208">The size of the segment.</span></span>|
|`Type`|`win:UInt32`|<span data-ttu-id="ce772-209">0x0-küçük nesne yığını.</span><span class="sxs-lookup"><span data-stu-id="ce772-209">0x0 - Small object heap.</span></span><br /><br /> <span data-ttu-id="ce772-210">0x1-büyük nesne yığını.</span><span class="sxs-lookup"><span data-stu-id="ce772-210">0x1 - Large object heap.</span></span><br /><br /> <span data-ttu-id="ce772-211">0x2-salt okunurdur yığın.</span><span class="sxs-lookup"><span data-stu-id="ce772-211">0x2 - Read-only heap.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="ce772-212">CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="ce772-212">Unique ID for the instance of CoreCLR.</span></span>|

<span data-ttu-id="ce772-213">Çöp toplayıcı tarafından ayrılan parçaların boyutunun uygulamaya özgü olduğunu ve düzenli güncelleştirmeler de dahil olmak üzere herhangi bir zamanda değişikliğe tabi olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="ce772-213">Note that the size of segments allocated by the garbage collector is implementation-specific and is subject to change at any time, including in periodic updates.</span></span> <span data-ttu-id="ce772-214">Uygulamanız, belirli bir kesim boyutuna ilişkin varsayımları asla belirtmemelidir veya buna bağlı olarak, kesim ayırmaları için kullanılabilir bellek miktarını yapılandırmayı denemelidir.</span><span class="sxs-lookup"><span data-stu-id="ce772-214">Your app should never make assumptions about or depend on a particular segment size, nor should it attempt to configure the amount of memory available for segment allocations.</span></span>

## <a name="gcfreesegment_v1-event"></a><span data-ttu-id="ce772-215">GCFreeSegment_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="ce772-215">GCFreeSegment_V1 event</span></span>

<span data-ttu-id="ce772-216">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="ce772-216">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="ce772-217">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="ce772-217">Keyword for raising the event</span></span>|<span data-ttu-id="ce772-218">Level</span><span class="sxs-lookup"><span data-stu-id="ce772-218">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="ce772-219">`GCKeyword` 0x1</span><span class="sxs-lookup"><span data-stu-id="ce772-219">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="ce772-220">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="ce772-220">Informational (4)</span></span>|

<span data-ttu-id="ce772-221">Aşağıdaki tabloda olay bilgileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="ce772-221">The following table shows the event information:</span></span>

|<span data-ttu-id="ce772-222">Olay</span><span class="sxs-lookup"><span data-stu-id="ce772-222">Event</span></span>|<span data-ttu-id="ce772-223">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="ce772-223">Event ID</span></span>|<span data-ttu-id="ce772-224">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="ce772-224">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCFreeSegment_V1`|<span data-ttu-id="ce772-225">6</span><span class="sxs-lookup"><span data-stu-id="ce772-225">6</span></span>|<span data-ttu-id="ce772-226">Çöp toplama segmenti yayınlandı.</span><span class="sxs-lookup"><span data-stu-id="ce772-226">A garbage collection segment has been released.</span></span>|

<span data-ttu-id="ce772-227">Aşağıdaki tabloda olay verileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="ce772-227">The following table shows the event data:</span></span>

|<span data-ttu-id="ce772-228">Alan adı</span><span class="sxs-lookup"><span data-stu-id="ce772-228">Field name</span></span>|<span data-ttu-id="ce772-229">Veri türü</span><span class="sxs-lookup"><span data-stu-id="ce772-229">Data type</span></span>|<span data-ttu-id="ce772-230">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ce772-230">Description</span></span>|
|----------------|---------------|-----------------|
|`Address`|`win:UInt64`|<span data-ttu-id="ce772-231">Segmentin adresi.</span><span class="sxs-lookup"><span data-stu-id="ce772-231">The address of the segment.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="ce772-232">CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="ce772-232">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="gcrestarteebegin_v1-event"></a><span data-ttu-id="ce772-233">GCRestartEEBegin_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="ce772-233">GCRestartEEBegin_V1 event</span></span>

<span data-ttu-id="ce772-234">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="ce772-234">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="ce772-235">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="ce772-235">Keyword for raising the event</span></span>|<span data-ttu-id="ce772-236">Level</span><span class="sxs-lookup"><span data-stu-id="ce772-236">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="ce772-237">`GCKeyword` 0x1</span><span class="sxs-lookup"><span data-stu-id="ce772-237">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="ce772-238">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="ce772-238">Informational (4)</span></span>|

<span data-ttu-id="ce772-239">Aşağıdaki tabloda olay bilgileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="ce772-239">The following table shows the event information:</span></span>

|<span data-ttu-id="ce772-240">Olay</span><span class="sxs-lookup"><span data-stu-id="ce772-240">Event</span></span>|<span data-ttu-id="ce772-241">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="ce772-241">Event ID</span></span>|<span data-ttu-id="ce772-242">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="ce772-242">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCRestartEEBegin_V1`|<span data-ttu-id="ce772-243">7</span><span class="sxs-lookup"><span data-stu-id="ce772-243">7</span></span>|<span data-ttu-id="ce772-244">Ortak dil çalışma zamanı askıya alma işleminden sürdürme başladı.</span><span class="sxs-lookup"><span data-stu-id="ce772-244">Resumption from common language runtime suspension has begun.</span></span>|

<span data-ttu-id="ce772-245">Bu olay hiçbir olay verisine sahip değil.</span><span class="sxs-lookup"><span data-stu-id="ce772-245">This event does not have any event data.</span></span>

## <a name="gcrestarteeend_v1-event"></a><span data-ttu-id="ce772-246">GCRestartEEEnd_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="ce772-246">GCRestartEEEnd_V1 event</span></span>

<span data-ttu-id="ce772-247">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="ce772-247">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="ce772-248">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="ce772-248">Keyword for raising the event</span></span>|<span data-ttu-id="ce772-249">Level</span><span class="sxs-lookup"><span data-stu-id="ce772-249">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="ce772-250">`GCKeyword` 0x1</span><span class="sxs-lookup"><span data-stu-id="ce772-250">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="ce772-251">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="ce772-251">Informational (4)</span></span>|

<span data-ttu-id="ce772-252">Aşağıdaki tabloda olay bilgileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="ce772-252">The following table shows the event information:</span></span>

|<span data-ttu-id="ce772-253">Olay</span><span class="sxs-lookup"><span data-stu-id="ce772-253">Event</span></span>|<span data-ttu-id="ce772-254">Olay kimliği</span><span class="sxs-lookup"><span data-stu-id="ce772-254">Event Id</span></span>|<span data-ttu-id="ce772-255">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="ce772-255">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCRestartEEEnd_V1`|<span data-ttu-id="ce772-256">3</span><span class="sxs-lookup"><span data-stu-id="ce772-256">3</span></span>|<span data-ttu-id="ce772-257">Ortak dil çalışma zamanı askıya alma işleminden sürdürme sonlandı.</span><span class="sxs-lookup"><span data-stu-id="ce772-257">Resumption from common language runtime suspension has ended.</span></span>|

<span data-ttu-id="ce772-258">Bu olay hiçbir olay verisine sahip değil.</span><span class="sxs-lookup"><span data-stu-id="ce772-258">This event does not have any event data.</span></span>

## <a name="gcsuspendeeend_v1-event"></a><span data-ttu-id="ce772-259">GCSuspendEEEnd_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="ce772-259">GCSuspendEEEnd_V1 event</span></span>

<span data-ttu-id="ce772-260">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="ce772-260">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="ce772-261">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="ce772-261">Keyword for raising the event</span></span>|<span data-ttu-id="ce772-262">Level</span><span class="sxs-lookup"><span data-stu-id="ce772-262">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="ce772-263">`GCKeyword` 0x1</span><span class="sxs-lookup"><span data-stu-id="ce772-263">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="ce772-264">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="ce772-264">Informational (4)</span></span>|

<span data-ttu-id="ce772-265">Aşağıdaki tabloda olay bilgileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="ce772-265">The following table shows the event information:</span></span>

|<span data-ttu-id="ce772-266">Olay</span><span class="sxs-lookup"><span data-stu-id="ce772-266">Event</span></span>|<span data-ttu-id="ce772-267">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="ce772-267">Event ID</span></span>|<span data-ttu-id="ce772-268">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="ce772-268">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCSuspendEEEnd_V1`|<span data-ttu-id="ce772-269">8</span><span class="sxs-lookup"><span data-stu-id="ce772-269">8</span></span>|<span data-ttu-id="ce772-270">Çöp toplama için yürütme altyapısının askıya alınma sonu.</span><span class="sxs-lookup"><span data-stu-id="ce772-270">End of suspension of the execution engine for garbage collection.</span></span>|

<span data-ttu-id="ce772-271">Bu olay hiçbir olay verisine sahip değil.</span><span class="sxs-lookup"><span data-stu-id="ce772-271">This event does not have any event data.</span></span>

## <a name="gcsuspendeebegin_v1-event"></a><span data-ttu-id="ce772-272">GCSuspendEEBegin_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="ce772-272">GCSuspendEEBegin_V1 event</span></span>

<span data-ttu-id="ce772-273">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="ce772-273">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="ce772-274">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="ce772-274">Keyword for raising the event</span></span>|<span data-ttu-id="ce772-275">Level</span><span class="sxs-lookup"><span data-stu-id="ce772-275">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="ce772-276">`GCKeyword` 0x1</span><span class="sxs-lookup"><span data-stu-id="ce772-276">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="ce772-277">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="ce772-277">Informational (4)</span></span>|

<span data-ttu-id="ce772-278">Aşağıdaki tabloda olay bilgileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="ce772-278">The following table shows the event information:</span></span>

|<span data-ttu-id="ce772-279">Olay</span><span class="sxs-lookup"><span data-stu-id="ce772-279">Event</span></span>|<span data-ttu-id="ce772-280">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="ce772-280">Event ID</span></span>|<span data-ttu-id="ce772-281">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="ce772-281">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCSuspendEEBegin_V1`|<span data-ttu-id="ce772-282">8</span><span class="sxs-lookup"><span data-stu-id="ce772-282">8</span></span>|<span data-ttu-id="ce772-283">Çöp toplama için yürütme altyapısının askıya alınma başlangıcı.</span><span class="sxs-lookup"><span data-stu-id="ce772-283">Start of suspension of the execution engine for garbage collection.</span></span>|

|<span data-ttu-id="ce772-284">Alan adı</span><span class="sxs-lookup"><span data-stu-id="ce772-284">Field name</span></span>|<span data-ttu-id="ce772-285">Veri türü</span><span class="sxs-lookup"><span data-stu-id="ce772-285">Data type</span></span>|<span data-ttu-id="ce772-286">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ce772-286">Description</span></span>|
|----------------|---------------|-----------------|
|`Count`|`win:UInt32`|<span data-ttu-id="ce772-287">*N*. çöp toplama.</span><span class="sxs-lookup"><span data-stu-id="ce772-287">The *n* th garbage collection.</span></span>|
|`Reason`|`win:UInt32`|<span data-ttu-id="ce772-288">EE askıya alma nedeni.</span><span class="sxs-lookup"><span data-stu-id="ce772-288">Reason for EE suspension.</span></span><br/><br/><span data-ttu-id="ce772-289">`0x0`: Diğerleri için askıya al</span><span class="sxs-lookup"><span data-stu-id="ce772-289">`0x0`: Suspend for Other</span></span><br/><br/><span data-ttu-id="ce772-290">`0x1`: GC için askıya alın.</span><span class="sxs-lookup"><span data-stu-id="ce772-290">`0x1`: Suspend for GC.</span></span><br/><br/><span data-ttu-id="ce772-291">`0x2`: AppDomain kapatması için askıya al.</span><span class="sxs-lookup"><span data-stu-id="ce772-291">`0x2`: Suspend for AppDomain shutdown.</span></span><br/><br/><span data-ttu-id="ce772-292">`0x3`: Kod alma için askıya al.</span><span class="sxs-lookup"><span data-stu-id="ce772-292">`0x3`: Suspend for code pitching.</span></span><br/><br/><span data-ttu-id="ce772-293">`0x4`: Kapat için askıya al.</span><span class="sxs-lookup"><span data-stu-id="ce772-293">`0x4`: Suspend for shutdown.</span></span><br/><br/><span data-ttu-id="ce772-294">`0x5`: Hata ayıklayıcı için askıya al.</span><span class="sxs-lookup"><span data-stu-id="ce772-294">`0x5`: Suspend for debugger.</span></span><br/><br/><span data-ttu-id="ce772-295">`0x6`: GC hazırlığı için askıya alın.</span><span class="sxs-lookup"><span data-stu-id="ce772-295">`0x6`: Suspend for GC Prep.</span></span><br/><br/><span data-ttu-id="ce772-296">`0x7`: Hata ayıklayıcı tarama için askıya al</span><span class="sxs-lookup"><span data-stu-id="ce772-296">`0x7`: Suspend for debugger sweep</span></span>|

## <a name="gcallocationtick_v3-event"></a><span data-ttu-id="ce772-297">GCAllocationTick_V3 olayı</span><span class="sxs-lookup"><span data-stu-id="ce772-297">GCAllocationTick_V3 event</span></span>

<span data-ttu-id="ce772-298">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="ce772-298">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="ce772-299">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="ce772-299">Keyword for raising the event</span></span>|<span data-ttu-id="ce772-300">Level</span><span class="sxs-lookup"><span data-stu-id="ce772-300">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="ce772-301">`GCKeyword` 0x1</span><span class="sxs-lookup"><span data-stu-id="ce772-301">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="ce772-302">Verbose (4)</span><span class="sxs-lookup"><span data-stu-id="ce772-302">Verbose (4)</span></span>|

<span data-ttu-id="ce772-303">Aşağıdaki tabloda olay bilgileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="ce772-303">The following table shows the event information:</span></span>

|<span data-ttu-id="ce772-304">Olay</span><span class="sxs-lookup"><span data-stu-id="ce772-304">Event</span></span>|<span data-ttu-id="ce772-305">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="ce772-305">Event ID</span></span>|<span data-ttu-id="ce772-306">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="ce772-306">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCAllocationTick_V3`|<span data-ttu-id="ce772-307">10</span><span class="sxs-lookup"><span data-stu-id="ce772-307">10</span></span>|<span data-ttu-id="ce772-308">Yaklaşık 100 KB ayrıldığı her seferinde.</span><span class="sxs-lookup"><span data-stu-id="ce772-308">Each time approximately 100 KB is allocated.</span></span>|

<span data-ttu-id="ce772-309">Aşağıdaki tabloda olay verileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="ce772-309">The following table shows the event data:</span></span>

|<span data-ttu-id="ce772-310">Alan adı</span><span class="sxs-lookup"><span data-stu-id="ce772-310">Field name</span></span>|<span data-ttu-id="ce772-311">Veri türü</span><span class="sxs-lookup"><span data-stu-id="ce772-311">Data type</span></span>|<span data-ttu-id="ce772-312">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ce772-312">Description</span></span>|
|----------------|---------------|-----------------|
|`AllocationAmount`|`win:UInt32`|<span data-ttu-id="ce772-313">Bayt cinsinden ayırma boyutu.</span><span class="sxs-lookup"><span data-stu-id="ce772-313">The allocation size, in bytes.</span></span> <span data-ttu-id="ce772-314">Bu değer, ULONG 'un uzunluğundan (4.294.967.295 bayt) daha az olan ayırmalar için doğrudur.</span><span class="sxs-lookup"><span data-stu-id="ce772-314">This value is accurate for allocations that are less than the length of a ULONG (4,294,967,295 bytes).</span></span> <span data-ttu-id="ce772-315">Ayırma daha büyükse, bu alan kesilmiş bir değer içerir.</span><span class="sxs-lookup"><span data-stu-id="ce772-315">If the allocation is greater, this field contains a truncated value.</span></span> <span data-ttu-id="ce772-316">`AllocationAmount64`Çok büyük ayırmalar için kullanın.</span><span class="sxs-lookup"><span data-stu-id="ce772-316">Use `AllocationAmount64` for very large allocations.</span></span>|
|`AllocationKind`|`win:UInt32`|<span data-ttu-id="ce772-317">`0x0` -Küçük nesne ayırma (ayırma küçük nesne yığınında).</span><span class="sxs-lookup"><span data-stu-id="ce772-317">`0x0` - Small object allocation (allocation is in small object heap).</span></span><br /><br /> <span data-ttu-id="ce772-318">`0x1` -Büyük nesne ayırma (ayırma büyük nesne yığınında).</span><span class="sxs-lookup"><span data-stu-id="ce772-318">`0x1` - Large object allocation (allocation is in large object heap).</span></span>|
|`AllocationAmount64`|`win:UInt64`|<span data-ttu-id="ce772-319">Bayt cinsinden ayırma boyutu.</span><span class="sxs-lookup"><span data-stu-id="ce772-319">The allocation size, in bytes.</span></span> <span data-ttu-id="ce772-320">Bu değer, çok büyük ayırmalar için doğrudur.</span><span class="sxs-lookup"><span data-stu-id="ce772-320">This value is accurate for very large allocations.</span></span>|
|`TypeId`|`win:Pointer`|<span data-ttu-id="ce772-321">MethodTable 'ın adresi.</span><span class="sxs-lookup"><span data-stu-id="ce772-321">The address of the MethodTable.</span></span> <span data-ttu-id="ce772-322">Bu olay sırasında ayrılan çeşitli nesne türleri olduğunda, bu, ayrılan son nesneye (100 KB eşiğinin aşılmasına neden olan nesne) karşılık gelen MethodTable 'ın adresidir.</span><span class="sxs-lookup"><span data-stu-id="ce772-322">When there are several types of objects that were allocated during this event, this is the address of the MethodTable that corresponds to the last object allocated (the object that caused the 100 KB threshold to be exceeded).</span></span>|
|`TypeName`|`win:UnicodeString`|<span data-ttu-id="ce772-323">Ayrılan türün adı.</span><span class="sxs-lookup"><span data-stu-id="ce772-323">The name of the type that was allocated.</span></span> <span data-ttu-id="ce772-324">Bu olay sırasında ayrılan çeşitli nesne türleri varsa, bu, ayrılan son nesnenin türüdür (100 KB eşiğinin aşılmasına neden olan nesne).</span><span class="sxs-lookup"><span data-stu-id="ce772-324">When there are several types of objects that were allocated during this event, this is the type of the last object allocated (the object that caused the 100 KB threshold to be exceeded).</span></span>|
|`HeapIndex`|`win:UInt32`|<span data-ttu-id="ce772-325">Nesnenin ayrıldığı yığın.</span><span class="sxs-lookup"><span data-stu-id="ce772-325">The heap where the object was allocated.</span></span> <span data-ttu-id="ce772-326">Bu değer, iş istasyonu atık toplama ile çalıştırılırken 0 (sıfır) değeridir.</span><span class="sxs-lookup"><span data-stu-id="ce772-326">This value is 0 (zero) when running with workstation garbage collection.</span></span>|
|`Address`|`win:Pointer`|<span data-ttu-id="ce772-327">Son ayrılan nesnenin adresi.</span><span class="sxs-lookup"><span data-stu-id="ce772-327">The address of the last allocated object.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="ce772-328">CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="ce772-328">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="gccreateconcurrentthread_v1-event"></a><span data-ttu-id="ce772-329">GCCreateConcurrentThread_V1 Olayı</span><span class="sxs-lookup"><span data-stu-id="ce772-329">GCCreateConcurrentThread_V1 event</span></span>

<span data-ttu-id="ce772-330">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="ce772-330">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="ce772-331">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="ce772-331">Keyword for raising the event</span></span>|<span data-ttu-id="ce772-332">Level</span><span class="sxs-lookup"><span data-stu-id="ce772-332">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="ce772-333">`GCKeyword` 0x1</span><span class="sxs-lookup"><span data-stu-id="ce772-333">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="ce772-334">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="ce772-334">Informational (4)</span></span>|
|<span data-ttu-id="ce772-335">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="ce772-335">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="ce772-336">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="ce772-336">Informational (4)</span></span>|

<span data-ttu-id="ce772-337">Aşağıdaki tabloda olay bilgileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="ce772-337">The following table shows the event information:</span></span>

|<span data-ttu-id="ce772-338">Olay</span><span class="sxs-lookup"><span data-stu-id="ce772-338">Event</span></span>|<span data-ttu-id="ce772-339">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="ce772-339">Event ID</span></span>|<span data-ttu-id="ce772-340">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="ce772-340">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCCreateConcurrentThread_V1`|<span data-ttu-id="ce772-341">11</span><span class="sxs-lookup"><span data-stu-id="ce772-341">11</span></span>|<span data-ttu-id="ce772-342">Eşzamanlı atık toplama iş parçacığı oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="ce772-342">Concurrent garbage collection thread was created.</span></span>|

<span data-ttu-id="ce772-343">Bu olay hiçbir olay verisine sahip değil.</span><span class="sxs-lookup"><span data-stu-id="ce772-343">This event does not have any event data.</span></span>

## <a name="gcterminateconcurrentthread_v1-event"></a><span data-ttu-id="ce772-344">GCTerminateConcurrentThread_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="ce772-344">GCTerminateConcurrentThread_V1 event</span></span>

<span data-ttu-id="ce772-345">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="ce772-345">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="ce772-346">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="ce772-346">Keyword for raising the event</span></span>|<span data-ttu-id="ce772-347">Level</span><span class="sxs-lookup"><span data-stu-id="ce772-347">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="ce772-348">`GCKeyword` 0x1</span><span class="sxs-lookup"><span data-stu-id="ce772-348">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="ce772-349">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="ce772-349">Informational (4)</span></span>|
|<span data-ttu-id="ce772-350">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="ce772-350">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="ce772-351">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="ce772-351">Informational (4)</span></span>|

<span data-ttu-id="ce772-352">Aşağıdaki tabloda olay bilgileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="ce772-352">The following table shows the event information:</span></span>

|<span data-ttu-id="ce772-353">Olay</span><span class="sxs-lookup"><span data-stu-id="ce772-353">Event</span></span>|<span data-ttu-id="ce772-354">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="ce772-354">Event ID</span></span>|<span data-ttu-id="ce772-355">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="ce772-355">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCTerminateConcurrentThread_V1`|<span data-ttu-id="ce772-356">12</span><span class="sxs-lookup"><span data-stu-id="ce772-356">12</span></span>|<span data-ttu-id="ce772-357">Eşzamanlı atık toplama iş parçacığı sonlandırıldı.</span><span class="sxs-lookup"><span data-stu-id="ce772-357">Concurrent garbage collection thread was terminated.</span></span>|

<span data-ttu-id="ce772-358">Bu olay hiçbir olay verisine sahip değil.</span><span class="sxs-lookup"><span data-stu-id="ce772-358">This event does not have any event data.</span></span>

## <a name="gcfinalizersbegin_v1-event"></a><span data-ttu-id="ce772-359">GCFinalizersBegin_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="ce772-359">GCFinalizersBegin_V1 event</span></span>

<span data-ttu-id="ce772-360">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="ce772-360">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="ce772-361">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="ce772-361">Keyword for raising the event</span></span>|<span data-ttu-id="ce772-362">Level</span><span class="sxs-lookup"><span data-stu-id="ce772-362">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="ce772-363">`GCKeyword` 0x1</span><span class="sxs-lookup"><span data-stu-id="ce772-363">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="ce772-364">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="ce772-364">Informational (4)</span></span>|

<span data-ttu-id="ce772-365">Aşağıdaki tabloda olay bilgileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="ce772-365">The following table shows the event information:</span></span>

|<span data-ttu-id="ce772-366">Olay</span><span class="sxs-lookup"><span data-stu-id="ce772-366">Event</span></span>|<span data-ttu-id="ce772-367">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="ce772-367">Event ID</span></span>|<span data-ttu-id="ce772-368">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="ce772-368">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCFinalizersBegin_V1`|<span data-ttu-id="ce772-369">14</span><span class="sxs-lookup"><span data-stu-id="ce772-369">14</span></span>|<span data-ttu-id="ce772-370">Sonlandırıcıları çalıştırmanın başlangıcı.</span><span class="sxs-lookup"><span data-stu-id="ce772-370">The start of running finalizers.</span></span>|

<span data-ttu-id="ce772-371">Bu olay hiçbir olay verisine sahip değil.</span><span class="sxs-lookup"><span data-stu-id="ce772-371">This event does not have any event data.</span></span>

## <a name="gcfinalizersend_v1-event"></a><span data-ttu-id="ce772-372">GCFinalizersEnd_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="ce772-372">GCFinalizersEnd_V1 event</span></span>

<span data-ttu-id="ce772-373">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="ce772-373">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="ce772-374">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="ce772-374">Keyword for raising the event</span></span>|<span data-ttu-id="ce772-375">Level</span><span class="sxs-lookup"><span data-stu-id="ce772-375">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="ce772-376">`GCKeyword` 0x1</span><span class="sxs-lookup"><span data-stu-id="ce772-376">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="ce772-377">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="ce772-377">Informational (4)</span></span>|

<span data-ttu-id="ce772-378">Aşağıdaki tabloda olay bilgileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="ce772-378">The following table shows the event information:</span></span>

|<span data-ttu-id="ce772-379">Olay</span><span class="sxs-lookup"><span data-stu-id="ce772-379">Event</span></span>|<span data-ttu-id="ce772-380">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="ce772-380">Event ID</span></span>|<span data-ttu-id="ce772-381">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="ce772-381">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCFinalizersEnd_V1`|<span data-ttu-id="ce772-382">13</span><span class="sxs-lookup"><span data-stu-id="ce772-382">13</span></span>|<span data-ttu-id="ce772-383">Sonlandırıcılardan çalıştırmanın sonu.</span><span class="sxs-lookup"><span data-stu-id="ce772-383">The end of running finalizers.</span></span>|

<span data-ttu-id="ce772-384">Aşağıdaki tabloda olay verileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="ce772-384">The following table shows the event data:</span></span>

|<span data-ttu-id="ce772-385">Alan adı</span><span class="sxs-lookup"><span data-stu-id="ce772-385">Field name</span></span>|<span data-ttu-id="ce772-386">Veri türü</span><span class="sxs-lookup"><span data-stu-id="ce772-386">Data type</span></span>|<span data-ttu-id="ce772-387">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ce772-387">Description</span></span>|
|----------------|---------------|-----------------|
|`Count`|`win:UInt32`|<span data-ttu-id="ce772-388">Çalıştırılan sonlandırıcılar sayısı.</span><span class="sxs-lookup"><span data-stu-id="ce772-388">The number of finalizers that were run.</span></span>|
|`ClrInstanceID`|<span data-ttu-id="ce772-389">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="ce772-389">win:UInt16</span></span>|<span data-ttu-id="ce772-390">CLR veya CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="ce772-390">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="setgchandle-event"></a><span data-ttu-id="ce772-391">SetGCHandle olayı</span><span class="sxs-lookup"><span data-stu-id="ce772-391">SetGCHandle event</span></span>

<span data-ttu-id="ce772-392">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="ce772-392">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="ce772-393">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="ce772-393">Keyword for raising the event</span></span>|<span data-ttu-id="ce772-394">Level</span><span class="sxs-lookup"><span data-stu-id="ce772-394">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="ce772-395">`GCHandleKeyword` 0x2</span><span class="sxs-lookup"><span data-stu-id="ce772-395">`GCHandleKeyword` (0x2)</span></span>|<span data-ttu-id="ce772-396">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="ce772-396">Informational (4)</span></span>|

<span data-ttu-id="ce772-397">Aşağıdaki tabloda olay bilgileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="ce772-397">The following table shows the event information:</span></span>

|<span data-ttu-id="ce772-398">Olay</span><span class="sxs-lookup"><span data-stu-id="ce772-398">Event</span></span>|<span data-ttu-id="ce772-399">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="ce772-399">Event ID</span></span>|<span data-ttu-id="ce772-400">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="ce772-400">Raised when</span></span>|
|-----------|--------------|-----------------|
|`SetGCHandle`|<span data-ttu-id="ce772-401">30</span><span class="sxs-lookup"><span data-stu-id="ce772-401">30</span></span>|<span data-ttu-id="ce772-402">GC tanıtıcısı ayarlandı.</span><span class="sxs-lookup"><span data-stu-id="ce772-402">A GC Handle has been set.</span></span>|

<span data-ttu-id="ce772-403">Aşağıdaki tabloda olay verileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="ce772-403">The following table shows the event data:</span></span>

|<span data-ttu-id="ce772-404">Alan adı</span><span class="sxs-lookup"><span data-stu-id="ce772-404">Field name</span></span>|<span data-ttu-id="ce772-405">Veri türü</span><span class="sxs-lookup"><span data-stu-id="ce772-405">Data type</span></span>|<span data-ttu-id="ce772-406">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ce772-406">Description</span></span>|
|----------------|---------------|-----------------|
|`HandleID`|`win:Pointer`|<span data-ttu-id="ce772-407">Ayrılmış tanıtıcının adresi.</span><span class="sxs-lookup"><span data-stu-id="ce772-407">The address of the allocated handle.</span></span>|
|`ObjectID`|`win:Pointer`|<span data-ttu-id="ce772-408">Tutamacı oluşturulan nesnenin adresi.</span><span class="sxs-lookup"><span data-stu-id="ce772-408">The address of the object whose handle was created.</span></span>|
|`Kind`|`win:UInt32`|<span data-ttu-id="ce772-409">Ayarlanan GC tanıtıcısının türü.</span><span class="sxs-lookup"><span data-stu-id="ce772-409">The type of GC handle that was set.</span></span> <br /><br /><span data-ttu-id="ce772-410">`0x0`: WeakShort</span><span class="sxs-lookup"><span data-stu-id="ce772-410">`0x0`: WeakShort</span></span> <br/><br/><span data-ttu-id="ce772-411">`0x1`: WeakLong</span><span class="sxs-lookup"><span data-stu-id="ce772-411">`0x1`: WeakLong</span></span> <br /><br /><span data-ttu-id="ce772-412">`0x2`: Strong</span><span class="sxs-lookup"><span data-stu-id="ce772-412">`0x2`: Strong</span></span> <br /><br /><span data-ttu-id="ce772-413">`0x3`: Sabitlenmiş</span><span class="sxs-lookup"><span data-stu-id="ce772-413">`0x3`: Pinned</span></span> <br /><br /><span data-ttu-id="ce772-414">`0x4`: Değişken</span><span class="sxs-lookup"><span data-stu-id="ce772-414">`0x4`: Variable</span></span><br /><br /><span data-ttu-id="ce772-415">`0x5`: Refsayılan</span><span class="sxs-lookup"><span data-stu-id="ce772-415">`0x5`: RefCounted</span></span> <br /><br /><span data-ttu-id="ce772-416">`0x6`: Bağımlı</span><span class="sxs-lookup"><span data-stu-id="ce772-416">`0x6`: Dependent</span></span><br /><br /><span data-ttu-id="ce772-417">`0x7`: Asyncpınlan</span><span class="sxs-lookup"><span data-stu-id="ce772-417">`0x7`: AsyncPinned</span></span><br /><br /><span data-ttu-id="ce772-418">`0x8`: SizedRef</span><span class="sxs-lookup"><span data-stu-id="ce772-418">`0x8`: SizedRef</span></span>|
|`Generation`|`win:UInt32`|<span data-ttu-id="ce772-419">Tutamacı oluşturulduğu nesnenin oluşturulması.</span><span class="sxs-lookup"><span data-stu-id="ce772-419">The generation of the object whose handle was created.</span></span>|
|`AppDomainID`|`win:UInt64`|<span data-ttu-id="ce772-420">AppDomain KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="ce772-420">The AppDomain ID.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="ce772-421">CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="ce772-421">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="destroygchandle-event"></a><span data-ttu-id="ce772-422">DestroyGCHandle olayı</span><span class="sxs-lookup"><span data-stu-id="ce772-422">DestroyGCHandle event</span></span>

<span data-ttu-id="ce772-423">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="ce772-423">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="ce772-424">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="ce772-424">Keyword for raising the event</span></span>|<span data-ttu-id="ce772-425">Level</span><span class="sxs-lookup"><span data-stu-id="ce772-425">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="ce772-426">`GCHandleKeyword` 0x2</span><span class="sxs-lookup"><span data-stu-id="ce772-426">`GCHandleKeyword` (0x2)</span></span>|<span data-ttu-id="ce772-427">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="ce772-427">Informational (4)</span></span>|

<span data-ttu-id="ce772-428">Aşağıdaki tabloda olay bilgileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="ce772-428">The following table shows the event information:</span></span>

|<span data-ttu-id="ce772-429">Olay</span><span class="sxs-lookup"><span data-stu-id="ce772-429">Event</span></span>|<span data-ttu-id="ce772-430">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="ce772-430">Event ID</span></span>|<span data-ttu-id="ce772-431">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="ce772-431">Raised when</span></span>|
|-----------|--------------|-----------------|
|`DestroyGCHandle`|<span data-ttu-id="ce772-432">31</span><span class="sxs-lookup"><span data-stu-id="ce772-432">31</span></span>|<span data-ttu-id="ce772-433">GC tanıtıcısı yok edilir.</span><span class="sxs-lookup"><span data-stu-id="ce772-433">A GC Handle is destroyed.</span></span>|

<span data-ttu-id="ce772-434">Aşağıdaki tabloda olay verileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="ce772-434">The following table shows the event data:</span></span>

|<span data-ttu-id="ce772-435">Alan adı</span><span class="sxs-lookup"><span data-stu-id="ce772-435">Field name</span></span>|<span data-ttu-id="ce772-436">Veri türü</span><span class="sxs-lookup"><span data-stu-id="ce772-436">Data type</span></span>|<span data-ttu-id="ce772-437">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ce772-437">Description</span></span>|
|----------------|---------------|-----------------|
|`HandleID`|`win:Pointer`|<span data-ttu-id="ce772-438">Yok etme tanıtıcısının adresi.</span><span class="sxs-lookup"><span data-stu-id="ce772-438">The address of the destroyed handle.</span></span>|
|`ClrInstanceID`|<span data-ttu-id="ce772-439">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="ce772-439">win:UInt16</span></span>|<span data-ttu-id="ce772-440">CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="ce772-440">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="pinobjectatgctime-event"></a><span data-ttu-id="ce772-441">PinObjectAtGCTime olayı</span><span class="sxs-lookup"><span data-stu-id="ce772-441">PinObjectAtGCTime event</span></span>

<span data-ttu-id="ce772-442">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="ce772-442">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="ce772-443">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="ce772-443">Keyword for raising the event</span></span>|<span data-ttu-id="ce772-444">Level</span><span class="sxs-lookup"><span data-stu-id="ce772-444">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="ce772-445">`GCKeyword` 0x1</span><span class="sxs-lookup"><span data-stu-id="ce772-445">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="ce772-446">Verbose (5)</span><span class="sxs-lookup"><span data-stu-id="ce772-446">Verbose (5)</span></span>|

<span data-ttu-id="ce772-447">Aşağıdaki tabloda olay bilgileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="ce772-447">The following table shows the event information:</span></span>

|<span data-ttu-id="ce772-448">Olay</span><span class="sxs-lookup"><span data-stu-id="ce772-448">Event</span></span>|<span data-ttu-id="ce772-449">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="ce772-449">Event ID</span></span>|<span data-ttu-id="ce772-450">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="ce772-450">Raised when</span></span>|
|-----------|--------------|-----------------|
|`PinObjectAtGCTime`|<span data-ttu-id="ce772-451">33</span><span class="sxs-lookup"><span data-stu-id="ce772-451">33</span></span>|<span data-ttu-id="ce772-452">GC sırasında bir nesne sabitlendi.</span><span class="sxs-lookup"><span data-stu-id="ce772-452">An object was pinned during a GC.</span></span>|

<span data-ttu-id="ce772-453">Aşağıdaki tabloda olay verileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="ce772-453">The following table shows the event data:</span></span>

|<span data-ttu-id="ce772-454">Alan adı</span><span class="sxs-lookup"><span data-stu-id="ce772-454">Field name</span></span>|<span data-ttu-id="ce772-455">Veri türü</span><span class="sxs-lookup"><span data-stu-id="ce772-455">Data type</span></span>|<span data-ttu-id="ce772-456">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ce772-456">Description</span></span>|
|----------------|---------------|-----------------|
|`HandleID`|`win:Pointer`|<span data-ttu-id="ce772-457">Tanıtıcının adresi.</span><span class="sxs-lookup"><span data-stu-id="ce772-457">The address of the handle.</span></span>|
|`ObjectID`|`win:Pointer`|<span data-ttu-id="ce772-458">Sabitlenmiş nesnenin adresi.</span><span class="sxs-lookup"><span data-stu-id="ce772-458">The address of the pinned object.</span></span>|
|`ObjectSize`|`win:UInt64`|<span data-ttu-id="ce772-459">Sabitlenmiş nesnenin boyutu.</span><span class="sxs-lookup"><span data-stu-id="ce772-459">The size of the pinned object.</span></span>|
|`TypeName`|`win:UnicodeString`|<span data-ttu-id="ce772-460">Sabitlenmiş nesnenin türünün adı.</span><span class="sxs-lookup"><span data-stu-id="ce772-460">The name of the type of the pinned object.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="ce772-461">CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="ce772-461">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="gctriggered-event"></a><span data-ttu-id="ce772-462">GCTriggered olayı</span><span class="sxs-lookup"><span data-stu-id="ce772-462">GCTriggered event</span></span>

<span data-ttu-id="ce772-463">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="ce772-463">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="ce772-464">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="ce772-464">Keyword for raising the event</span></span>|<span data-ttu-id="ce772-465">Level</span><span class="sxs-lookup"><span data-stu-id="ce772-465">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="ce772-466">`GCKeyword` 0x1</span><span class="sxs-lookup"><span data-stu-id="ce772-466">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="ce772-467">Verbose (5)</span><span class="sxs-lookup"><span data-stu-id="ce772-467">Verbose (5)</span></span>|

<span data-ttu-id="ce772-468">Aşağıdaki tabloda olay bilgileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="ce772-468">The following table shows the event information:</span></span>

|<span data-ttu-id="ce772-469">Olay</span><span class="sxs-lookup"><span data-stu-id="ce772-469">Event</span></span>|<span data-ttu-id="ce772-470">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="ce772-470">Event ID</span></span>|<span data-ttu-id="ce772-471">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="ce772-471">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCTriggered`|<span data-ttu-id="ce772-472">33</span><span class="sxs-lookup"><span data-stu-id="ce772-472">33</span></span>|<span data-ttu-id="ce772-473">GC tetiklendi.</span><span class="sxs-lookup"><span data-stu-id="ce772-473">A GC has been triggered.</span></span>|

<span data-ttu-id="ce772-474">Aşağıdaki tabloda olay verileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="ce772-474">The following table shows the event data:</span></span>

|<span data-ttu-id="ce772-475">Alan adı</span><span class="sxs-lookup"><span data-stu-id="ce772-475">Field name</span></span>|<span data-ttu-id="ce772-476">Veri türü</span><span class="sxs-lookup"><span data-stu-id="ce772-476">Data type</span></span>|<span data-ttu-id="ce772-477">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ce772-477">Description</span></span>|
|----------------|---------------|-----------------|
|`Reason`|`win:UInt32`|<span data-ttu-id="ce772-478">GC 'nin tetiklenme nedeni.</span><span class="sxs-lookup"><span data-stu-id="ce772-478">The reason a GC was triggered.</span></span><br/><br/><span data-ttu-id="ce772-479">`0x0`: AllocSmall</span><span class="sxs-lookup"><span data-stu-id="ce772-479">`0x0`: AllocSmall</span></span><br/><br/><span data-ttu-id="ce772-480">`0x1`: Alınmış</span><span class="sxs-lookup"><span data-stu-id="ce772-480">`0x1`: Induced</span></span> <br/><br/><span data-ttu-id="ce772-481">`0x2`: LowMemory</span><span class="sxs-lookup"><span data-stu-id="ce772-481">`0x2`: LowMemory</span></span> <br/><br/><span data-ttu-id="ce772-482">`0x3`: Boş</span><span class="sxs-lookup"><span data-stu-id="ce772-482">`0x3`: Empty</span></span> <br/><br/><span data-ttu-id="ce772-483">`0x4`: AllocLarge</span><span class="sxs-lookup"><span data-stu-id="ce772-483">`0x4`: AllocLarge</span></span> <br/><br/><span data-ttu-id="ce772-484">`0x5`: OutOfSpaceSmallObjectHeap</span><span class="sxs-lookup"><span data-stu-id="ce772-484">`0x5`: OutOfSpaceSmallObjectHeap</span></span> <br/><br/><span data-ttu-id="ce772-485">`0x6`: OutOfSpaceLargeObjectHeap</span><span class="sxs-lookup"><span data-stu-id="ce772-485">`0x6`: OutOfSpaceLargeObjectHeap</span></span> <br/><br/><span data-ttu-id="ce772-486">`0x7`:InducedNoForce</span><span class="sxs-lookup"><span data-stu-id="ce772-486">`0x7`:InducedNoForce</span></span> <br/><br/><span data-ttu-id="ce772-487">`0x8`: Stres</span><span class="sxs-lookup"><span data-stu-id="ce772-487">`0x8`: Stress</span></span> <br/><br/><span data-ttu-id="ce772-488">`0x9`: Endücedlowmemory</span><span class="sxs-lookup"><span data-stu-id="ce772-488">`0x9`: InducedLowMemory</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="ce772-489">CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="ce772-489">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="increasememorypressure-event"></a><span data-ttu-id="ce772-490">Increasememorypresbir olay</span><span class="sxs-lookup"><span data-stu-id="ce772-490">IncreaseMemoryPressure event</span></span>

<span data-ttu-id="ce772-491">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="ce772-491">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="ce772-492">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="ce772-492">Keyword for raising the event</span></span>|<span data-ttu-id="ce772-493">Level</span><span class="sxs-lookup"><span data-stu-id="ce772-493">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="ce772-494">`GCKeyword` 0x1</span><span class="sxs-lookup"><span data-stu-id="ce772-494">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="ce772-495">Bilgi (4)</span><span class="sxs-lookup"><span data-stu-id="ce772-495">Information (4)</span></span>|

<span data-ttu-id="ce772-496">Aşağıdaki tabloda olay bilgileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="ce772-496">The following table shows the event information:</span></span>

|<span data-ttu-id="ce772-497">Olay</span><span class="sxs-lookup"><span data-stu-id="ce772-497">Event</span></span>|<span data-ttu-id="ce772-498">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="ce772-498">Event ID</span></span>|<span data-ttu-id="ce772-499">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="ce772-499">Raised when</span></span>|
|----------------|---------------|-----------------|
|`IncreaseMemoryPressure`|<span data-ttu-id="ce772-500">200</span><span class="sxs-lookup"><span data-stu-id="ce772-500">200</span></span>|<span data-ttu-id="ce772-501">Bellek baskısı arttı.</span><span class="sxs-lookup"><span data-stu-id="ce772-501">Memory pressure was increased.</span></span>|

<span data-ttu-id="ce772-502">Aşağıdaki tabloda olay verileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="ce772-502">The following table shows the event data:</span></span>

|<span data-ttu-id="ce772-503">Alan Adı</span><span class="sxs-lookup"><span data-stu-id="ce772-503">Field Name</span></span>|<span data-ttu-id="ce772-504">Veri türü</span><span class="sxs-lookup"><span data-stu-id="ce772-504">Data type</span></span>|<span data-ttu-id="ce772-505">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ce772-505">Description</span></span>|
|----------------|---------------|-----------------|
|`ClrInstanceID`|<span data-ttu-id="ce772-506">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="ce772-506">win:UInt16</span></span>|<span data-ttu-id="ce772-507">CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="ce772-507">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="decreasememorypressure-event"></a><span data-ttu-id="ce772-508">DecreaseMemoryPressure olayı</span><span class="sxs-lookup"><span data-stu-id="ce772-508">DecreaseMemoryPressure event</span></span>

<span data-ttu-id="ce772-509">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="ce772-509">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="ce772-510">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="ce772-510">Keyword for raising the event</span></span>|<span data-ttu-id="ce772-511">Level</span><span class="sxs-lookup"><span data-stu-id="ce772-511">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="ce772-512">`GCKeyword` 0x1</span><span class="sxs-lookup"><span data-stu-id="ce772-512">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="ce772-513">Bilgi (4)</span><span class="sxs-lookup"><span data-stu-id="ce772-513">Information (4)</span></span>|

<span data-ttu-id="ce772-514">Aşağıdaki tabloda olay bilgileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="ce772-514">The following table shows the event information:</span></span>

|<span data-ttu-id="ce772-515">Olay</span><span class="sxs-lookup"><span data-stu-id="ce772-515">Event</span></span>|<span data-ttu-id="ce772-516">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="ce772-516">Event ID</span></span>|<span data-ttu-id="ce772-517">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="ce772-517">Raised when</span></span>|
|----------------|---------------|-----------------|
|`DecreaseMemoryPressure`|<span data-ttu-id="ce772-518">201</span><span class="sxs-lookup"><span data-stu-id="ce772-518">201</span></span>|<span data-ttu-id="ce772-519">Bellek baskısı azaltılmıştı.</span><span class="sxs-lookup"><span data-stu-id="ce772-519">Memory pressure was decreased.</span></span>|

<span data-ttu-id="ce772-520">Aşağıdaki tabloda olay verileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="ce772-520">The following table shows the event data:</span></span>

|<span data-ttu-id="ce772-521">Alan Adı</span><span class="sxs-lookup"><span data-stu-id="ce772-521">Field Name</span></span>|<span data-ttu-id="ce772-522">Veri türü</span><span class="sxs-lookup"><span data-stu-id="ce772-522">Data type</span></span>|<span data-ttu-id="ce772-523">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ce772-523">Description</span></span>|
|----------------|---------------|-----------------|
|`BytesFreed`|`win:UInt32`|<span data-ttu-id="ce772-524">Serbest bırakılan bayt.</span><span class="sxs-lookup"><span data-stu-id="ce772-524">Bytes freed.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="ce772-525">CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="ce772-525">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="gcmarkwithtype-event"></a><span data-ttu-id="ce772-526">GCMarkWithType olayı</span><span class="sxs-lookup"><span data-stu-id="ce772-526">GCMarkWithType event</span></span>

<span data-ttu-id="ce772-527">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="ce772-527">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="ce772-528">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="ce772-528">Keyword for raising the event</span></span>|<span data-ttu-id="ce772-529">Level</span><span class="sxs-lookup"><span data-stu-id="ce772-529">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="ce772-530">`GCKeyword` 0x1</span><span class="sxs-lookup"><span data-stu-id="ce772-530">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="ce772-531">Bilgi (4)</span><span class="sxs-lookup"><span data-stu-id="ce772-531">Information (4)</span></span>|

<span data-ttu-id="ce772-532">Aşağıdaki tabloda olay bilgileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="ce772-532">The following table shows the event information:</span></span>

|<span data-ttu-id="ce772-533">Olay</span><span class="sxs-lookup"><span data-stu-id="ce772-533">Event</span></span>|<span data-ttu-id="ce772-534">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="ce772-534">Event ID</span></span>|<span data-ttu-id="ce772-535">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="ce772-535">Raised when</span></span>|
|----------------|---------------|-----------------|
|`GCMarkWithType`|<span data-ttu-id="ce772-536">202</span><span class="sxs-lookup"><span data-stu-id="ce772-536">202</span></span>|<span data-ttu-id="ce772-537">GC işareti aşamasında bir GC kökü işaretlendi.</span><span class="sxs-lookup"><span data-stu-id="ce772-537">A GC root has been marked during GC mark phase.</span></span>|

<span data-ttu-id="ce772-538">Aşağıdaki tabloda olay verileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="ce772-538">The following table shows the event data:</span></span>

|<span data-ttu-id="ce772-539">Alan Adı</span><span class="sxs-lookup"><span data-stu-id="ce772-539">Field Name</span></span>|<span data-ttu-id="ce772-540">Veri türü</span><span class="sxs-lookup"><span data-stu-id="ce772-540">Data type</span></span>|<span data-ttu-id="ce772-541">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ce772-541">Description</span></span>|
|----------------|---------------|-----------------|
|`HeapNum`|`win:UInt32`|<span data-ttu-id="ce772-542">Yığın numarası.</span><span class="sxs-lookup"><span data-stu-id="ce772-542">The heap number.</span></span>|
|`ClrInstanceID`|<span data-ttu-id="ce772-543">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="ce772-543">win:UInt16</span></span>|<span data-ttu-id="ce772-544">CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="ce772-544">Unique ID for the instance of CoreCLR.</span></span>|
|`Type`|`win:UInt32`|<span data-ttu-id="ce772-545">GC kök türü.</span><span class="sxs-lookup"><span data-stu-id="ce772-545">The GC root type.</span></span><br/><br/><span data-ttu-id="ce772-546">`0x0`: Yığın</span><span class="sxs-lookup"><span data-stu-id="ce772-546">`0x0`: Stack</span></span><br/><br/><span data-ttu-id="ce772-547">`0x1`: Sonlandırıcı</span><span class="sxs-lookup"><span data-stu-id="ce772-547">`0x1`: Finalizer</span></span><br/><br/><span data-ttu-id="ce772-548">`0x2`: Tanıtıcı</span><span class="sxs-lookup"><span data-stu-id="ce772-548">`0x2`: Handle</span></span><br/><br/><span data-ttu-id="ce772-549">`0x3`: Daha eski</span><span class="sxs-lookup"><span data-stu-id="ce772-549">`0x3`: Older</span></span><br/><br/><span data-ttu-id="ce772-550">`0x4`: SizedRef</span><span class="sxs-lookup"><span data-stu-id="ce772-550">`0x4`: SizedRef</span></span><br/><br/><span data-ttu-id="ce772-551">`0x5`: Taşma</span><span class="sxs-lookup"><span data-stu-id="ce772-551">`0x5`: Overflow</span></span><br/><br/>|
|`Bytes`|`win:UInt64`|<span data-ttu-id="ce772-552">İşaretlenmiş baytların sayısı.</span><span class="sxs-lookup"><span data-stu-id="ce772-552">The number of bytes marked.</span></span>|

## <a name="gcjoin_v2-event"></a><span data-ttu-id="ce772-553">GCJoin_V2 olayı</span><span class="sxs-lookup"><span data-stu-id="ce772-553">GCJoin_V2 event</span></span>

<span data-ttu-id="ce772-554">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="ce772-554">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="ce772-555">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="ce772-555">Keyword for raising the event</span></span>|<span data-ttu-id="ce772-556">Level</span><span class="sxs-lookup"><span data-stu-id="ce772-556">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="ce772-557">`GCKeyword` 0x1</span><span class="sxs-lookup"><span data-stu-id="ce772-557">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="ce772-558">Verbose (5)</span><span class="sxs-lookup"><span data-stu-id="ce772-558">Verbose (5)</span></span>|

<span data-ttu-id="ce772-559">Aşağıdaki tabloda olay bilgileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="ce772-559">The following table shows the event information:</span></span>

|<span data-ttu-id="ce772-560">Olay</span><span class="sxs-lookup"><span data-stu-id="ce772-560">Event</span></span>|<span data-ttu-id="ce772-561">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="ce772-561">Event ID</span></span>|<span data-ttu-id="ce772-562">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="ce772-562">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCJoin_V2`|<span data-ttu-id="ce772-563">203</span><span class="sxs-lookup"><span data-stu-id="ce772-563">203</span></span>|<span data-ttu-id="ce772-564">Birleştirilmiş bir GC iş parçacığı.</span><span class="sxs-lookup"><span data-stu-id="ce772-564">A GC thread joined.</span></span>|

<span data-ttu-id="ce772-565">Aşağıdaki tabloda olay verileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="ce772-565">The following table shows the event data:</span></span>

|<span data-ttu-id="ce772-566">Alan adı</span><span class="sxs-lookup"><span data-stu-id="ce772-566">Field name</span></span>|<span data-ttu-id="ce772-567">Veri türü</span><span class="sxs-lookup"><span data-stu-id="ce772-567">Data type</span></span>|<span data-ttu-id="ce772-568">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ce772-568">Description</span></span>|
|----------------|---------------|-----------------|
|`Heap`|`win:UInt32`|<span data-ttu-id="ce772-569">Yığın numarası</span><span class="sxs-lookup"><span data-stu-id="ce772-569">The heap number</span></span>|
|`JoinTime`|`win:UInt32`|<span data-ttu-id="ce772-570">Bu olayın birleştirmenin başlangıcında mi, yoksa bir birleşimin sonunda mi tetiklendiğini belirtir (JOIN `0x0` için, `0x1` JOIN End for JOIN için)</span><span class="sxs-lookup"><span data-stu-id="ce772-570">Indicates whether this event is fired at the start of a join or end of a join (`0x0` for join start, `0x1` for join end)</span></span>|
|`JoinType`|`win:UInt32`|<span data-ttu-id="ce772-571">JOIN türü.</span><span class="sxs-lookup"><span data-stu-id="ce772-571">The join type.</span></span> <br/><br/><span data-ttu-id="ce772-572">`0x0`: Son ekleme</span><span class="sxs-lookup"><span data-stu-id="ce772-572">`0x0`: Last Join</span></span><br/><br/><span data-ttu-id="ce772-573">`0x1`: Birleştir</span><span class="sxs-lookup"><span data-stu-id="ce772-573">`0x1`: Join</span></span> <br/><br/><span data-ttu-id="ce772-574">`0x2`: Yeniden Başlat</span><span class="sxs-lookup"><span data-stu-id="ce772-574">`0x2`: Restart</span></span> <br/><br/><span data-ttu-id="ce772-575">`0x3`: İlk olarak katılmayı geri çevir</span><span class="sxs-lookup"><span data-stu-id="ce772-575">`0x3`: First Reverse Join</span></span><br/><br/><span data-ttu-id="ce772-576">`0x4`: Ters Birleştir</span><span class="sxs-lookup"><span data-stu-id="ce772-576">`0x4`: Reverse Join</span></span><br/><br/>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="ce772-577">CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="ce772-577">Unique ID for the instance of CoreCLR.</span></span>|
