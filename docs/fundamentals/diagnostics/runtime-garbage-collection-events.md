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
# <a name="net-runtime-garbage-collection-events"></a><span data-ttu-id="92c29-103">.NET çalışma zamanı atık toplama olayları</span><span class="sxs-lookup"><span data-stu-id="92c29-103">.NET runtime garbage collection events</span></span>

<span data-ttu-id="92c29-104">Bu olaylar çöp koleksiyonuyla ilgili bilgiler toplar.</span><span class="sxs-lookup"><span data-stu-id="92c29-104">These events collect information pertaining to garbage collection.</span></span> <span data-ttu-id="92c29-105">Çöp toplamanın kaç kez gerçekleştirildiğini belirleme, çöp toplama sırasında ne kadar bellek serbest bırakılmış vb. gibi tanılama ve hata ayıklama konusunda yardımcı olurlar. Bu olayların tanılama amacıyla nasıl kullanılacağı hakkında daha fazla bilgi için bkz. [.NET uygulamalarını günlüğe kaydetme ve izleme](../../core/diagnostics/logging-tracing.md)</span><span class="sxs-lookup"><span data-stu-id="92c29-105">They help in diagnostics and debugging, including determining how many times garbage collection was performed, how much memory was freed during garbage collection, etc. For more information about how to use these events for diagnostic purposes, see [logging and tracing .NET applications](../../core/diagnostics/logging-tracing.md)</span></span>

## <a name="gcstart_v2-event"></a><span data-ttu-id="92c29-106">GCStart_V2 olayı</span><span class="sxs-lookup"><span data-stu-id="92c29-106">GCStart_V2 Event</span></span>

<span data-ttu-id="92c29-107">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="92c29-107">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="92c29-108">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="92c29-108">Keyword for raising the event</span></span>|<span data-ttu-id="92c29-109">Level</span><span class="sxs-lookup"><span data-stu-id="92c29-109">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="92c29-110">`GCKeyword` 0x1</span><span class="sxs-lookup"><span data-stu-id="92c29-110">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="92c29-111">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="92c29-111">Informational (4)</span></span>|

<span data-ttu-id="92c29-112">Aşağıdaki tabloda olay bilgileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="92c29-112">The following table shows the event information:</span></span>

|<span data-ttu-id="92c29-113">Olay</span><span class="sxs-lookup"><span data-stu-id="92c29-113">Event</span></span>|<span data-ttu-id="92c29-114">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="92c29-114">Event ID</span></span>|<span data-ttu-id="92c29-115">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="92c29-115">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCStart_V1`|<span data-ttu-id="92c29-116">1</span><span class="sxs-lookup"><span data-stu-id="92c29-116">1</span></span>|<span data-ttu-id="92c29-117">Çöp toplama işlemi başlatıldı.</span><span class="sxs-lookup"><span data-stu-id="92c29-117">A garbage collection has started.</span></span>|

<span data-ttu-id="92c29-118">Aşağıdaki tabloda olay verileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="92c29-118">The following table shows the event data:</span></span>

|<span data-ttu-id="92c29-119">Alan adı</span><span class="sxs-lookup"><span data-stu-id="92c29-119">Field name</span></span>|<span data-ttu-id="92c29-120">Veri türü</span><span class="sxs-lookup"><span data-stu-id="92c29-120">Data type</span></span>|<span data-ttu-id="92c29-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="92c29-121">Description</span></span>|
|----------------|---------------|-----------------|
|`Count`|`win:UInt32`|<span data-ttu-id="92c29-122">*N*. çöp toplama.</span><span class="sxs-lookup"><span data-stu-id="92c29-122">The *n* th garbage collection.</span></span>|
|`Depth`|`win:UInt32`|<span data-ttu-id="92c29-123">Toplanmakta olan oluşturma.</span><span class="sxs-lookup"><span data-stu-id="92c29-123">The generation that is being collected.</span></span>|
|`Reason`|`win:UInt32`|<span data-ttu-id="92c29-124">Çöp toplamanın neden tetiklendiği:</span><span class="sxs-lookup"><span data-stu-id="92c29-124">Why the garbage collection was triggered:</span></span><br /><br /> <span data-ttu-id="92c29-125">`0x0` -Küçük nesne yığını ayırması.</span><span class="sxs-lookup"><span data-stu-id="92c29-125">`0x0` - Small object heap allocation.</span></span><br /><br /> <span data-ttu-id="92c29-126">`0x1` Zorlanmadı.</span><span class="sxs-lookup"><span data-stu-id="92c29-126">`0x1` - Induced.</span></span><br /><br /> <span data-ttu-id="92c29-127">`0x2` -Düşük bellek.</span><span class="sxs-lookup"><span data-stu-id="92c29-127">`0x2` - Low memory.</span></span><br /><br /> <span data-ttu-id="92c29-128">`0x3` Olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="92c29-128">`0x3` - Empty.</span></span><br /><br /> <span data-ttu-id="92c29-129">`0x4` -Büyük nesne yığını ayırması.</span><span class="sxs-lookup"><span data-stu-id="92c29-129">`0x4` - Large object heap allocation.</span></span><br /><br /> <span data-ttu-id="92c29-130">`0x5` -Alan kalmadı (küçük nesne yığını için).</span><span class="sxs-lookup"><span data-stu-id="92c29-130">`0x5` - Out of space (for small object heap).</span></span><br /><br /> <span data-ttu-id="92c29-131">`0x6` -Alan kalmadı (büyük nesne yığını için).</span><span class="sxs-lookup"><span data-stu-id="92c29-131">`0x6` - Out of space (for large object heap).</span></span><br /><br /> <span data-ttu-id="92c29-132">`0x7` -Alınmış ancak engelleme olarak zorlanmadı.</span><span class="sxs-lookup"><span data-stu-id="92c29-132">`0x7` - Induced but not forced as blocking.</span></span>|
|`Type`|`win:UInt32`|<span data-ttu-id="92c29-133">`0x0` -Arka plan atık toplama dışında çöp toplama engelleme gerçekleşti.</span><span class="sxs-lookup"><span data-stu-id="92c29-133">`0x0` - Blocking garbage collection occurred outside background garbage collection.</span></span><br /><br /> <span data-ttu-id="92c29-134">`0x1` -Arka plan atık toplama.</span><span class="sxs-lookup"><span data-stu-id="92c29-134">`0x1` - Background garbage collection.</span></span><br /><br /> <span data-ttu-id="92c29-135">`0x2` -Arka plan atık toplama sırasında atık toplamayı engelleme oluştu.</span><span class="sxs-lookup"><span data-stu-id="92c29-135">`0x2` - Blocking garbage collection occurred during background garbage collection.</span></span>|
|`ClrInstanceID`|<span data-ttu-id="92c29-136">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="92c29-136">win:UInt16</span></span>|<span data-ttu-id="92c29-137">CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="92c29-137">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="gcend_v1-event"></a><span data-ttu-id="92c29-138">GCEnd_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="92c29-138">GCEnd_V1 Event</span></span>

<span data-ttu-id="92c29-139">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="92c29-139">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="92c29-140">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="92c29-140">Keyword for raising the event</span></span>|<span data-ttu-id="92c29-141">Level</span><span class="sxs-lookup"><span data-stu-id="92c29-141">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="92c29-142">`GCKeyword` 0x1</span><span class="sxs-lookup"><span data-stu-id="92c29-142">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="92c29-143">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="92c29-143">Informational (4)</span></span>|

<span data-ttu-id="92c29-144">Aşağıdaki tabloda olay bilgileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="92c29-144">The following table shows the event information:</span></span>

|<span data-ttu-id="92c29-145">Olay</span><span class="sxs-lookup"><span data-stu-id="92c29-145">Event</span></span>|<span data-ttu-id="92c29-146">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="92c29-146">Event ID</span></span>|<span data-ttu-id="92c29-147">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="92c29-147">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCEnd_V1`|<span data-ttu-id="92c29-148">2</span><span class="sxs-lookup"><span data-stu-id="92c29-148">2</span></span>|<span data-ttu-id="92c29-149">Çöp toplama sona erdi.</span><span class="sxs-lookup"><span data-stu-id="92c29-149">The garbage collection has ended.</span></span>|

<span data-ttu-id="92c29-150">Aşağıdaki tabloda olay verileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="92c29-150">The following table shows the event data:</span></span>

|<span data-ttu-id="92c29-151">Alan adı</span><span class="sxs-lookup"><span data-stu-id="92c29-151">Field name</span></span>|<span data-ttu-id="92c29-152">Veri türü</span><span class="sxs-lookup"><span data-stu-id="92c29-152">Data type</span></span>|<span data-ttu-id="92c29-153">Açıklama</span><span class="sxs-lookup"><span data-stu-id="92c29-153">Description</span></span>|
|----------------|---------------|-----------------|
|`Count`|`win:UInt32`|<span data-ttu-id="92c29-154">*N*. çöp toplama.</span><span class="sxs-lookup"><span data-stu-id="92c29-154">The *n* th garbage collection.</span></span>|
|`Depth`|`win:UInt32`|<span data-ttu-id="92c29-155">Toplanan nesil.</span><span class="sxs-lookup"><span data-stu-id="92c29-155">The generation that was collected.</span></span>|
|`ClrInstanceID`|<span data-ttu-id="92c29-156">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="92c29-156">win:UInt16</span></span>|<span data-ttu-id="92c29-157">CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="92c29-157">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="gcheapstats_v2-event"></a><span data-ttu-id="92c29-158">GCHeapStats_V2 olayı</span><span class="sxs-lookup"><span data-stu-id="92c29-158">GCHeapStats_V2 Event</span></span>

<span data-ttu-id="92c29-159">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="92c29-159">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="92c29-160">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="92c29-160">Keyword for raising the event</span></span>|<span data-ttu-id="92c29-161">Level</span><span class="sxs-lookup"><span data-stu-id="92c29-161">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="92c29-162">`GCKeyword` 0x1</span><span class="sxs-lookup"><span data-stu-id="92c29-162">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="92c29-163">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="92c29-163">Informational (4)</span></span>|

<span data-ttu-id="92c29-164">Aşağıdaki tabloda olay bilgileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="92c29-164">The following table shows the event information:</span></span>

|<span data-ttu-id="92c29-165">Olay</span><span class="sxs-lookup"><span data-stu-id="92c29-165">Event</span></span>|<span data-ttu-id="92c29-166">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="92c29-166">Event ID</span></span>|<span data-ttu-id="92c29-167">Description</span><span class="sxs-lookup"><span data-stu-id="92c29-167">Description</span></span>|
|-----------|--------------|-----------------|
|`GCHeapStats_V2`|<span data-ttu-id="92c29-168">4</span><span class="sxs-lookup"><span data-stu-id="92c29-168">4</span></span>|<span data-ttu-id="92c29-169">Her çöp toplamanın sonundaki yığın istatistiklerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="92c29-169">Shows the heap statistics at the end of each garbage collection.</span></span>|

<span data-ttu-id="92c29-170">Aşağıdaki tabloda olay verileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="92c29-170">The following table shows the event data:</span></span>

|<span data-ttu-id="92c29-171">Alan adı</span><span class="sxs-lookup"><span data-stu-id="92c29-171">Field name</span></span>|<span data-ttu-id="92c29-172">Veri türü</span><span class="sxs-lookup"><span data-stu-id="92c29-172">Data type</span></span>|<span data-ttu-id="92c29-173">Açıklama</span><span class="sxs-lookup"><span data-stu-id="92c29-173">Description</span></span>|
|----------------|---------------|-----------------|
|`GenerationSize0`|`win:UInt64`|<span data-ttu-id="92c29-174">0. nesil belleğin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="92c29-174">The size, in bytes, of generation 0 memory.</span></span>|
|`TotalPromotedSize0`|`win:UInt64`|<span data-ttu-id="92c29-175">Nesil 0 ' dan 1 ' e yükseltilen bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="92c29-175">The number of bytes that are promoted from generation 0 to generation 1.</span></span>|
|`GenerationSize1`|`win:UInt64`|<span data-ttu-id="92c29-176">1. nesil belleğin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="92c29-176">The size, in bytes, of generation 1 memory.</span></span>|
|`TotalPromotedSize1`|`win:UInt64`|<span data-ttu-id="92c29-177">1. nesil 2 ' ye kadar yükseltilen bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="92c29-177">The number of bytes that are promoted from generation 1 to generation 2.</span></span>|
|`GenerationSize2`|`win:UInt64`|<span data-ttu-id="92c29-178">2. nesil belleğin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="92c29-178">The size, in bytes, of generation 2 memory.</span></span>|
|`TotalPromotedSize2`|`win:UInt64`|<span data-ttu-id="92c29-179">Son koleksiyondan sonra 2. nesil üzerinde kalan bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="92c29-179">The number of bytes that survived in generation 2 after the last collection.</span></span>|
|`GenerationSize3`|`win:UInt64`|<span data-ttu-id="92c29-180">Büyük nesne yığınının bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="92c29-180">The size, in bytes, of the large object heap.</span></span>|
|`TotalPromotedSize3`|`win:UInt64`|<span data-ttu-id="92c29-181">Son koleksiyondan sonra büyük nesne yığınında kalan bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="92c29-181">The number of bytes that survived in the large object heap after the last collection.</span></span>|
|`FinalizationPromotedSize`|`win:UInt64`|<span data-ttu-id="92c29-182">Sonlandırma için hazırlanma nesnelerinin bayt cinsinden toplam boyutu.</span><span class="sxs-lookup"><span data-stu-id="92c29-182">The total size, in bytes, of the objects that are ready for finalization.</span></span>|
|`FinalizationPromotedCount`|`win:UInt64`|<span data-ttu-id="92c29-183">Sonlandırmaya hazırlanma nesne sayısı.</span><span class="sxs-lookup"><span data-stu-id="92c29-183">The number of objects that are ready for finalization.</span></span>|
|`PinnedObjectCount`|`win:UInt32`|<span data-ttu-id="92c29-184">Sabitlenmiş (taşınamaz) nesne sayısı.</span><span class="sxs-lookup"><span data-stu-id="92c29-184">The number of pinned (unmovable) objects.</span></span>|
|`SinkBlockCount`|`win:UInt32`|<span data-ttu-id="92c29-185">Kullanımdaki eşitleme bloklarının sayısı.</span><span class="sxs-lookup"><span data-stu-id="92c29-185">The number of synchronization blocks in use.</span></span>|
|`GCHandleCount`|`win:UInt32`|<span data-ttu-id="92c29-186">Kullanımdaki çöp toplama tanıtıcılarının sayısı.</span><span class="sxs-lookup"><span data-stu-id="92c29-186">The number of garbage collection handles in use.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="92c29-187">CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="92c29-187">Unique ID for the instance of CoreCLR.</span></span>|
|`GenerationSize4`|`win:UInt64`|<span data-ttu-id="92c29-188">Sabitlenmiş nesne yığınının bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="92c29-188">The size, in bytes, of the pinned object heap.</span></span>|
|`TotalPromotedSize4`|`win:UInt64`|<span data-ttu-id="92c29-189">Son koleksiyondan sonra sabitlenmiş nesne yığınında kalan bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="92c29-189">The number of bytes that survived in the pinned object heap after the last collection.</span></span>|

## <a name="gccreatesegment_v1-event"></a><span data-ttu-id="92c29-190">GCCreateSegment_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="92c29-190">GCCreateSegment_V1 event</span></span>

<span data-ttu-id="92c29-191">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="92c29-191">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="92c29-192">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="92c29-192">Keyword for raising the event</span></span>|<span data-ttu-id="92c29-193">Level</span><span class="sxs-lookup"><span data-stu-id="92c29-193">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="92c29-194">`GCKeyword` 0x1</span><span class="sxs-lookup"><span data-stu-id="92c29-194">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="92c29-195">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="92c29-195">Informational (4)</span></span>|

<span data-ttu-id="92c29-196">Aşağıdaki tabloda olay bilgileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="92c29-196">The following table shows the event information:</span></span>

|<span data-ttu-id="92c29-197">Olay</span><span class="sxs-lookup"><span data-stu-id="92c29-197">Event</span></span>|<span data-ttu-id="92c29-198">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="92c29-198">Event ID</span></span>|<span data-ttu-id="92c29-199">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="92c29-199">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCCreateSegment_V1`|<span data-ttu-id="92c29-200">5</span><span class="sxs-lookup"><span data-stu-id="92c29-200">5</span></span>|<span data-ttu-id="92c29-201">Yeni bir atık toplama segmenti oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="92c29-201">A new garbage collection segment has been created.</span></span> <span data-ttu-id="92c29-202">Ayrıca, izleme zaten çalışmakta olan bir işlemde etkinleştirildiğinde, bu olay varolan her segment için oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="92c29-202">In addition, when tracing is enabled on a process that is already running, this event is raised for each existing segment.</span></span>|

<span data-ttu-id="92c29-203">Aşağıdaki tabloda olay verileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="92c29-203">The following table shows the event data:</span></span>

|<span data-ttu-id="92c29-204">Alan adı</span><span class="sxs-lookup"><span data-stu-id="92c29-204">Field name</span></span>|<span data-ttu-id="92c29-205">Veri türü</span><span class="sxs-lookup"><span data-stu-id="92c29-205">Data type</span></span>|<span data-ttu-id="92c29-206">Açıklama</span><span class="sxs-lookup"><span data-stu-id="92c29-206">Description</span></span>|
|----------------|---------------|-----------------|
|`Address`|`win:UInt64`|<span data-ttu-id="92c29-207">Segmentin adresi.</span><span class="sxs-lookup"><span data-stu-id="92c29-207">The address of the segment.</span></span>|
|`Size`|`win:UInt64`|<span data-ttu-id="92c29-208">Segmentin boyutu.</span><span class="sxs-lookup"><span data-stu-id="92c29-208">The size of the segment.</span></span>|
|`Type`|`win:UInt32`|<span data-ttu-id="92c29-209">0x0-küçük nesne yığını.</span><span class="sxs-lookup"><span data-stu-id="92c29-209">0x0 - Small object heap.</span></span><br /><br /> <span data-ttu-id="92c29-210">0x1-büyük nesne yığını.</span><span class="sxs-lookup"><span data-stu-id="92c29-210">0x1 - Large object heap.</span></span><br /><br /> <span data-ttu-id="92c29-211">0x2-salt okunurdur yığın.</span><span class="sxs-lookup"><span data-stu-id="92c29-211">0x2 - Read-only heap.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="92c29-212">CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="92c29-212">Unique ID for the instance of CoreCLR.</span></span>|

<span data-ttu-id="92c29-213">Çöp toplayıcı tarafından ayrılan parçaların boyutunun uygulamaya özgü olduğunu ve düzenli güncelleştirmeler de dahil olmak üzere herhangi bir zamanda değişikliğe tabi olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="92c29-213">Note that the size of segments allocated by the garbage collector is implementation-specific and is subject to change at any time, including in periodic updates.</span></span> <span data-ttu-id="92c29-214">Uygulamanız, belirli bir kesim boyutuna ilişkin varsayımları asla belirtmemelidir veya buna bağlı olarak, kesim ayırmaları için kullanılabilir bellek miktarını yapılandırmayı denemelidir.</span><span class="sxs-lookup"><span data-stu-id="92c29-214">Your app should never make assumptions about or depend on a particular segment size, nor should it attempt to configure the amount of memory available for segment allocations.</span></span>

## <a name="gcfreesegment_v1-event"></a><span data-ttu-id="92c29-215">GCFreeSegment_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="92c29-215">GCFreeSegment_V1 event</span></span>

<span data-ttu-id="92c29-216">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="92c29-216">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="92c29-217">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="92c29-217">Keyword for raising the event</span></span>|<span data-ttu-id="92c29-218">Level</span><span class="sxs-lookup"><span data-stu-id="92c29-218">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="92c29-219">`GCKeyword` 0x1</span><span class="sxs-lookup"><span data-stu-id="92c29-219">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="92c29-220">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="92c29-220">Informational (4)</span></span>|

<span data-ttu-id="92c29-221">Aşağıdaki tabloda olay bilgileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="92c29-221">The following table shows the event information:</span></span>

|<span data-ttu-id="92c29-222">Olay</span><span class="sxs-lookup"><span data-stu-id="92c29-222">Event</span></span>|<span data-ttu-id="92c29-223">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="92c29-223">Event ID</span></span>|<span data-ttu-id="92c29-224">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="92c29-224">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCFreeSegment_V1`|<span data-ttu-id="92c29-225">6</span><span class="sxs-lookup"><span data-stu-id="92c29-225">6</span></span>|<span data-ttu-id="92c29-226">Çöp toplama segmenti yayınlandı.</span><span class="sxs-lookup"><span data-stu-id="92c29-226">A garbage collection segment has been released.</span></span>|

<span data-ttu-id="92c29-227">Aşağıdaki tabloda olay verileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="92c29-227">The following table shows the event data:</span></span>

|<span data-ttu-id="92c29-228">Alan adı</span><span class="sxs-lookup"><span data-stu-id="92c29-228">Field name</span></span>|<span data-ttu-id="92c29-229">Veri türü</span><span class="sxs-lookup"><span data-stu-id="92c29-229">Data type</span></span>|<span data-ttu-id="92c29-230">Açıklama</span><span class="sxs-lookup"><span data-stu-id="92c29-230">Description</span></span>|
|----------------|---------------|-----------------|
|`Address`|`win:UInt64`|<span data-ttu-id="92c29-231">Segmentin adresi.</span><span class="sxs-lookup"><span data-stu-id="92c29-231">The address of the segment.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="92c29-232">CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="92c29-232">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="gcrestarteebegin_v1-event"></a><span data-ttu-id="92c29-233">GCRestartEEBegin_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="92c29-233">GCRestartEEBegin_V1 event</span></span>

<span data-ttu-id="92c29-234">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="92c29-234">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="92c29-235">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="92c29-235">Keyword for raising the event</span></span>|<span data-ttu-id="92c29-236">Level</span><span class="sxs-lookup"><span data-stu-id="92c29-236">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="92c29-237">`GCKeyword` 0x1</span><span class="sxs-lookup"><span data-stu-id="92c29-237">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="92c29-238">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="92c29-238">Informational (4)</span></span>|

<span data-ttu-id="92c29-239">Aşağıdaki tabloda olay bilgileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="92c29-239">The following table shows the event information:</span></span>

|<span data-ttu-id="92c29-240">Olay</span><span class="sxs-lookup"><span data-stu-id="92c29-240">Event</span></span>|<span data-ttu-id="92c29-241">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="92c29-241">Event ID</span></span>|<span data-ttu-id="92c29-242">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="92c29-242">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCRestartEEBegin_V1`|<span data-ttu-id="92c29-243">7</span><span class="sxs-lookup"><span data-stu-id="92c29-243">7</span></span>|<span data-ttu-id="92c29-244">Ortak dil çalışma zamanı askıya alma işleminden sürdürme başladı.</span><span class="sxs-lookup"><span data-stu-id="92c29-244">Resumption from common language runtime suspension has begun.</span></span>|

<span data-ttu-id="92c29-245">Bu olay hiçbir olay verisine sahip değil.</span><span class="sxs-lookup"><span data-stu-id="92c29-245">This event does not have any event data.</span></span>

## <a name="gcrestarteeend_v1-event"></a><span data-ttu-id="92c29-246">GCRestartEEEnd_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="92c29-246">GCRestartEEEnd_V1 event</span></span>

<span data-ttu-id="92c29-247">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="92c29-247">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="92c29-248">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="92c29-248">Keyword for raising the event</span></span>|<span data-ttu-id="92c29-249">Level</span><span class="sxs-lookup"><span data-stu-id="92c29-249">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="92c29-250">`GCKeyword` 0x1</span><span class="sxs-lookup"><span data-stu-id="92c29-250">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="92c29-251">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="92c29-251">Informational (4)</span></span>|

<span data-ttu-id="92c29-252">Aşağıdaki tabloda olay bilgileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="92c29-252">The following table shows the event information:</span></span>

|<span data-ttu-id="92c29-253">Olay</span><span class="sxs-lookup"><span data-stu-id="92c29-253">Event</span></span>|<span data-ttu-id="92c29-254">Olay kimliği</span><span class="sxs-lookup"><span data-stu-id="92c29-254">Event Id</span></span>|<span data-ttu-id="92c29-255">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="92c29-255">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCRestartEEEnd_V1`|<span data-ttu-id="92c29-256">3</span><span class="sxs-lookup"><span data-stu-id="92c29-256">3</span></span>|<span data-ttu-id="92c29-257">Ortak dil çalışma zamanı askıya alma işleminden sürdürme sonlandı.</span><span class="sxs-lookup"><span data-stu-id="92c29-257">Resumption from common language runtime suspension has ended.</span></span>|

<span data-ttu-id="92c29-258">Bu olay hiçbir olay verisine sahip değil.</span><span class="sxs-lookup"><span data-stu-id="92c29-258">This event does not have any event data.</span></span>

## <a name="gcsuspendeeend_v1-event"></a><span data-ttu-id="92c29-259">GCSuspendEEEnd_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="92c29-259">GCSuspendEEEnd_V1 event</span></span>

<span data-ttu-id="92c29-260">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="92c29-260">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="92c29-261">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="92c29-261">Keyword for raising the event</span></span>|<span data-ttu-id="92c29-262">Level</span><span class="sxs-lookup"><span data-stu-id="92c29-262">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="92c29-263">`GCKeyword` 0x1</span><span class="sxs-lookup"><span data-stu-id="92c29-263">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="92c29-264">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="92c29-264">Informational (4)</span></span>|

<span data-ttu-id="92c29-265">Aşağıdaki tabloda olay bilgileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="92c29-265">The following table shows the event information:</span></span>

|<span data-ttu-id="92c29-266">Olay</span><span class="sxs-lookup"><span data-stu-id="92c29-266">Event</span></span>|<span data-ttu-id="92c29-267">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="92c29-267">Event ID</span></span>|<span data-ttu-id="92c29-268">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="92c29-268">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCSuspendEEEnd_V1`|<span data-ttu-id="92c29-269">8</span><span class="sxs-lookup"><span data-stu-id="92c29-269">8</span></span>|<span data-ttu-id="92c29-270">Çöp toplama için yürütme altyapısının askıya alınma sonu.</span><span class="sxs-lookup"><span data-stu-id="92c29-270">End of suspension of the execution engine for garbage collection.</span></span>|

<span data-ttu-id="92c29-271">Bu olay hiçbir olay verisine sahip değil.</span><span class="sxs-lookup"><span data-stu-id="92c29-271">This event does not have any event data.</span></span>

## <a name="gcsuspendeebegin_v1-event"></a><span data-ttu-id="92c29-272">GCSuspendEEBegin_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="92c29-272">GCSuspendEEBegin_V1 event</span></span>

<span data-ttu-id="92c29-273">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="92c29-273">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="92c29-274">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="92c29-274">Keyword for raising the event</span></span>|<span data-ttu-id="92c29-275">Level</span><span class="sxs-lookup"><span data-stu-id="92c29-275">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="92c29-276">`GCKeyword` 0x1</span><span class="sxs-lookup"><span data-stu-id="92c29-276">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="92c29-277">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="92c29-277">Informational (4)</span></span>|

<span data-ttu-id="92c29-278">Aşağıdaki tabloda olay bilgileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="92c29-278">The following table shows the event information:</span></span>

|<span data-ttu-id="92c29-279">Olay</span><span class="sxs-lookup"><span data-stu-id="92c29-279">Event</span></span>|<span data-ttu-id="92c29-280">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="92c29-280">Event ID</span></span>|<span data-ttu-id="92c29-281">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="92c29-281">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCSuspendEEBegin_V1`|<span data-ttu-id="92c29-282">8</span><span class="sxs-lookup"><span data-stu-id="92c29-282">8</span></span>|<span data-ttu-id="92c29-283">Çöp toplama için yürütme altyapısının askıya alınma başlangıcı.</span><span class="sxs-lookup"><span data-stu-id="92c29-283">Start of suspension of the execution engine for garbage collection.</span></span>|

|<span data-ttu-id="92c29-284">Alan adı</span><span class="sxs-lookup"><span data-stu-id="92c29-284">Field name</span></span>|<span data-ttu-id="92c29-285">Veri türü</span><span class="sxs-lookup"><span data-stu-id="92c29-285">Data type</span></span>|<span data-ttu-id="92c29-286">Açıklama</span><span class="sxs-lookup"><span data-stu-id="92c29-286">Description</span></span>|
|----------------|---------------|-----------------|
|`Count`|`win:UInt32`|<span data-ttu-id="92c29-287">*N*. çöp toplama.</span><span class="sxs-lookup"><span data-stu-id="92c29-287">The *n* th garbage collection.</span></span>|
|`Reason`|`win:UInt32`|<span data-ttu-id="92c29-288">EE askıya alma nedeni.</span><span class="sxs-lookup"><span data-stu-id="92c29-288">Reason for EE suspension.</span></span><br/><br/><span data-ttu-id="92c29-289">`0x0`: Diğerleri için askıya al</span><span class="sxs-lookup"><span data-stu-id="92c29-289">`0x0`: Suspend for Other</span></span><br/><br/><span data-ttu-id="92c29-290">`0x1`: GC için askıya alın.</span><span class="sxs-lookup"><span data-stu-id="92c29-290">`0x1`: Suspend for GC.</span></span><br/><br/><span data-ttu-id="92c29-291">`0x2`: AppDomain kapatması için askıya al.</span><span class="sxs-lookup"><span data-stu-id="92c29-291">`0x2`: Suspend for AppDomain shutdown.</span></span><br/><br/><span data-ttu-id="92c29-292">`0x3`: Kod alma için askıya al.</span><span class="sxs-lookup"><span data-stu-id="92c29-292">`0x3`: Suspend for code pitching.</span></span><br/><br/><span data-ttu-id="92c29-293">`0x4`: Kapat için askıya al.</span><span class="sxs-lookup"><span data-stu-id="92c29-293">`0x4`: Suspend for shutdown.</span></span><br/><br/><span data-ttu-id="92c29-294">`0x5`: Hata ayıklayıcı için askıya al.</span><span class="sxs-lookup"><span data-stu-id="92c29-294">`0x5`: Suspend for debugger.</span></span><br/><br/><span data-ttu-id="92c29-295">`0x6`: GC hazırlığı için askıya alın.</span><span class="sxs-lookup"><span data-stu-id="92c29-295">`0x6`: Suspend for GC Prep.</span></span><br/><br/><span data-ttu-id="92c29-296">`0x7`: Hata ayıklayıcı tarama için askıya al</span><span class="sxs-lookup"><span data-stu-id="92c29-296">`0x7`: Suspend for debugger sweep</span></span>|

## <a name="gcallocationtick_v3-event"></a><span data-ttu-id="92c29-297">GCAllocationTick_V3 olayı</span><span class="sxs-lookup"><span data-stu-id="92c29-297">GCAllocationTick_V3 event</span></span>

<span data-ttu-id="92c29-298">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="92c29-298">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="92c29-299">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="92c29-299">Keyword for raising the event</span></span>|<span data-ttu-id="92c29-300">Level</span><span class="sxs-lookup"><span data-stu-id="92c29-300">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="92c29-301">`GCKeyword` 0x1</span><span class="sxs-lookup"><span data-stu-id="92c29-301">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="92c29-302">Verbose (4)</span><span class="sxs-lookup"><span data-stu-id="92c29-302">Verbose (4)</span></span>|

<span data-ttu-id="92c29-303">Aşağıdaki tabloda olay bilgileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="92c29-303">The following table shows the event information:</span></span>

|<span data-ttu-id="92c29-304">Olay</span><span class="sxs-lookup"><span data-stu-id="92c29-304">Event</span></span>|<span data-ttu-id="92c29-305">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="92c29-305">Event ID</span></span>|<span data-ttu-id="92c29-306">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="92c29-306">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCAllocationTick_V3`|<span data-ttu-id="92c29-307">10</span><span class="sxs-lookup"><span data-stu-id="92c29-307">10</span></span>|<span data-ttu-id="92c29-308">Yaklaşık 100 KB ayrıldığı her seferinde.</span><span class="sxs-lookup"><span data-stu-id="92c29-308">Each time approximately 100 KB is allocated.</span></span>|

<span data-ttu-id="92c29-309">Aşağıdaki tabloda olay verileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="92c29-309">The following table shows the event data:</span></span>

|<span data-ttu-id="92c29-310">Alan adı</span><span class="sxs-lookup"><span data-stu-id="92c29-310">Field name</span></span>|<span data-ttu-id="92c29-311">Veri türü</span><span class="sxs-lookup"><span data-stu-id="92c29-311">Data type</span></span>|<span data-ttu-id="92c29-312">Açıklama</span><span class="sxs-lookup"><span data-stu-id="92c29-312">Description</span></span>|
|----------------|---------------|-----------------|
|`AllocationAmount`|`win:UInt32`|<span data-ttu-id="92c29-313">Bayt cinsinden ayırma boyutu.</span><span class="sxs-lookup"><span data-stu-id="92c29-313">The allocation size, in bytes.</span></span> <span data-ttu-id="92c29-314">Bu değer, ULONG 'un uzunluğundan (4.294.967.295 bayt) daha az olan ayırmalar için doğrudur.</span><span class="sxs-lookup"><span data-stu-id="92c29-314">This value is accurate for allocations that are less than the length of a ULONG (4,294,967,295 bytes).</span></span> <span data-ttu-id="92c29-315">Ayırma daha büyükse, bu alan kesilmiş bir değer içerir.</span><span class="sxs-lookup"><span data-stu-id="92c29-315">If the allocation is greater, this field contains a truncated value.</span></span> <span data-ttu-id="92c29-316">`AllocationAmount64`Çok büyük ayırmalar için kullanın.</span><span class="sxs-lookup"><span data-stu-id="92c29-316">Use `AllocationAmount64` for very large allocations.</span></span>|
|`AllocationKind`|`win:UInt32`|<span data-ttu-id="92c29-317">`0x0` -Küçük nesne ayırma (ayırma küçük nesne yığınında).</span><span class="sxs-lookup"><span data-stu-id="92c29-317">`0x0` - Small object allocation (allocation is in small object heap).</span></span><br /><br /> <span data-ttu-id="92c29-318">`0x1` -Büyük nesne ayırma (ayırma büyük nesne yığınında).</span><span class="sxs-lookup"><span data-stu-id="92c29-318">`0x1` - Large object allocation (allocation is in large object heap).</span></span>|
|`AllocationAmount64`|`win:UInt64`|<span data-ttu-id="92c29-319">Bayt cinsinden ayırma boyutu.</span><span class="sxs-lookup"><span data-stu-id="92c29-319">The allocation size, in bytes.</span></span> <span data-ttu-id="92c29-320">Bu değer, çok büyük ayırmalar için doğrudur.</span><span class="sxs-lookup"><span data-stu-id="92c29-320">This value is accurate for very large allocations.</span></span>|
|`TypeId`|`win:Pointer`|<span data-ttu-id="92c29-321">MethodTable 'ın adresi.</span><span class="sxs-lookup"><span data-stu-id="92c29-321">The address of the MethodTable.</span></span> <span data-ttu-id="92c29-322">Bu olay sırasında ayrılan çeşitli nesne türleri olduğunda, bu, ayrılan son nesneye (100 KB eşiğinin aşılmasına neden olan nesne) karşılık gelen MethodTable 'ın adresidir.</span><span class="sxs-lookup"><span data-stu-id="92c29-322">When there are several types of objects that were allocated during this event, this is the address of the MethodTable that corresponds to the last object allocated (the object that caused the 100 KB threshold to be exceeded).</span></span>|
|`TypeName`|`win:UnicodeString`|<span data-ttu-id="92c29-323">Ayrılan türün adı.</span><span class="sxs-lookup"><span data-stu-id="92c29-323">The name of the type that was allocated.</span></span> <span data-ttu-id="92c29-324">Bu olay sırasında ayrılan çeşitli nesne türleri varsa, bu, ayrılan son nesnenin türüdür (100 KB eşiğinin aşılmasına neden olan nesne).</span><span class="sxs-lookup"><span data-stu-id="92c29-324">When there are several types of objects that were allocated during this event, this is the type of the last object allocated (the object that caused the 100 KB threshold to be exceeded).</span></span>|
|`HeapIndex`|`win:UInt32`|<span data-ttu-id="92c29-325">Nesnenin ayrıldığı yığın.</span><span class="sxs-lookup"><span data-stu-id="92c29-325">The heap where the object was allocated.</span></span> <span data-ttu-id="92c29-326">Bu değer, iş istasyonu atık toplama ile çalıştırılırken 0 (sıfır) değeridir.</span><span class="sxs-lookup"><span data-stu-id="92c29-326">This value is 0 (zero) when running with workstation garbage collection.</span></span>|
|`Address`|`win:Pointer`|<span data-ttu-id="92c29-327">Son ayrılan nesnenin adresi.</span><span class="sxs-lookup"><span data-stu-id="92c29-327">The address of the last allocated object.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="92c29-328">CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="92c29-328">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="gccreateconcurrentthread_v1-event"></a><span data-ttu-id="92c29-329">GCCreateConcurrentThread_V1 Olayı</span><span class="sxs-lookup"><span data-stu-id="92c29-329">GCCreateConcurrentThread_V1 event</span></span>

<span data-ttu-id="92c29-330">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="92c29-330">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="92c29-331">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="92c29-331">Keyword for raising the event</span></span>|<span data-ttu-id="92c29-332">Level</span><span class="sxs-lookup"><span data-stu-id="92c29-332">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="92c29-333">`GCKeyword` 0x1</span><span class="sxs-lookup"><span data-stu-id="92c29-333">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="92c29-334">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="92c29-334">Informational (4)</span></span>|
|<span data-ttu-id="92c29-335">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="92c29-335">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="92c29-336">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="92c29-336">Informational (4)</span></span>|

<span data-ttu-id="92c29-337">Aşağıdaki tabloda olay bilgileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="92c29-337">The following table shows the event information:</span></span>

|<span data-ttu-id="92c29-338">Olay</span><span class="sxs-lookup"><span data-stu-id="92c29-338">Event</span></span>|<span data-ttu-id="92c29-339">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="92c29-339">Event ID</span></span>|<span data-ttu-id="92c29-340">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="92c29-340">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCCreateConcurrentThread_V1`|<span data-ttu-id="92c29-341">11</span><span class="sxs-lookup"><span data-stu-id="92c29-341">11</span></span>|<span data-ttu-id="92c29-342">Eşzamanlı atık toplama iş parçacığı oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="92c29-342">Concurrent garbage collection thread was created.</span></span>|

<span data-ttu-id="92c29-343">Bu olay hiçbir olay verisine sahip değil.</span><span class="sxs-lookup"><span data-stu-id="92c29-343">This event does not have any event data.</span></span>

## <a name="gcterminateconcurrentthread_v1-event"></a><span data-ttu-id="92c29-344">GCTerminateConcurrentThread_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="92c29-344">GCTerminateConcurrentThread_V1 event</span></span>

<span data-ttu-id="92c29-345">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="92c29-345">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="92c29-346">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="92c29-346">Keyword for raising the event</span></span>|<span data-ttu-id="92c29-347">Level</span><span class="sxs-lookup"><span data-stu-id="92c29-347">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="92c29-348">`GCKeyword` 0x1</span><span class="sxs-lookup"><span data-stu-id="92c29-348">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="92c29-349">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="92c29-349">Informational (4)</span></span>|
|<span data-ttu-id="92c29-350">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="92c29-350">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="92c29-351">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="92c29-351">Informational (4)</span></span>|

<span data-ttu-id="92c29-352">Aşağıdaki tabloda olay bilgileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="92c29-352">The following table shows the event information:</span></span>

|<span data-ttu-id="92c29-353">Olay</span><span class="sxs-lookup"><span data-stu-id="92c29-353">Event</span></span>|<span data-ttu-id="92c29-354">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="92c29-354">Event ID</span></span>|<span data-ttu-id="92c29-355">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="92c29-355">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCTerminateConcurrentThread_V1`|<span data-ttu-id="92c29-356">12</span><span class="sxs-lookup"><span data-stu-id="92c29-356">12</span></span>|<span data-ttu-id="92c29-357">Eşzamanlı atık toplama iş parçacığı sonlandırıldı.</span><span class="sxs-lookup"><span data-stu-id="92c29-357">Concurrent garbage collection thread was terminated.</span></span>|

<span data-ttu-id="92c29-358">Bu olay hiçbir olay verisine sahip değil.</span><span class="sxs-lookup"><span data-stu-id="92c29-358">This event does not have any event data.</span></span>

## <a name="gcfinalizersbegin_v1-event"></a><span data-ttu-id="92c29-359">GCFinalizersBegin_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="92c29-359">GCFinalizersBegin_V1 event</span></span>

<span data-ttu-id="92c29-360">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="92c29-360">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="92c29-361">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="92c29-361">Keyword for raising the event</span></span>|<span data-ttu-id="92c29-362">Level</span><span class="sxs-lookup"><span data-stu-id="92c29-362">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="92c29-363">`GCKeyword` 0x1</span><span class="sxs-lookup"><span data-stu-id="92c29-363">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="92c29-364">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="92c29-364">Informational (4)</span></span>|

<span data-ttu-id="92c29-365">Aşağıdaki tabloda olay bilgileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="92c29-365">The following table shows the event information:</span></span>

|<span data-ttu-id="92c29-366">Olay</span><span class="sxs-lookup"><span data-stu-id="92c29-366">Event</span></span>|<span data-ttu-id="92c29-367">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="92c29-367">Event ID</span></span>|<span data-ttu-id="92c29-368">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="92c29-368">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCFinalizersBegin_V1`|<span data-ttu-id="92c29-369">14</span><span class="sxs-lookup"><span data-stu-id="92c29-369">14</span></span>|<span data-ttu-id="92c29-370">Sonlandırıcıları çalıştırmanın başlangıcı.</span><span class="sxs-lookup"><span data-stu-id="92c29-370">The start of running finalizers.</span></span>|

<span data-ttu-id="92c29-371">Bu olay hiçbir olay verisine sahip değil.</span><span class="sxs-lookup"><span data-stu-id="92c29-371">This event does not have any event data.</span></span>

## <a name="gcfinalizersend_v1-event"></a><span data-ttu-id="92c29-372">GCFinalizersEnd_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="92c29-372">GCFinalizersEnd_V1 event</span></span>

<span data-ttu-id="92c29-373">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="92c29-373">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="92c29-374">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="92c29-374">Keyword for raising the event</span></span>|<span data-ttu-id="92c29-375">Level</span><span class="sxs-lookup"><span data-stu-id="92c29-375">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="92c29-376">`GCKeyword` 0x1</span><span class="sxs-lookup"><span data-stu-id="92c29-376">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="92c29-377">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="92c29-377">Informational (4)</span></span>|

<span data-ttu-id="92c29-378">Aşağıdaki tabloda olay bilgileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="92c29-378">The following table shows the event information:</span></span>

|<span data-ttu-id="92c29-379">Olay</span><span class="sxs-lookup"><span data-stu-id="92c29-379">Event</span></span>|<span data-ttu-id="92c29-380">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="92c29-380">Event ID</span></span>|<span data-ttu-id="92c29-381">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="92c29-381">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCFinalizersEnd_V1`|<span data-ttu-id="92c29-382">13</span><span class="sxs-lookup"><span data-stu-id="92c29-382">13</span></span>|<span data-ttu-id="92c29-383">Sonlandırıcılardan çalıştırmanın sonu.</span><span class="sxs-lookup"><span data-stu-id="92c29-383">The end of running finalizers.</span></span>|

<span data-ttu-id="92c29-384">Aşağıdaki tabloda olay verileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="92c29-384">The following table shows the event data:</span></span>

|<span data-ttu-id="92c29-385">Alan adı</span><span class="sxs-lookup"><span data-stu-id="92c29-385">Field name</span></span>|<span data-ttu-id="92c29-386">Veri türü</span><span class="sxs-lookup"><span data-stu-id="92c29-386">Data type</span></span>|<span data-ttu-id="92c29-387">Açıklama</span><span class="sxs-lookup"><span data-stu-id="92c29-387">Description</span></span>|
|----------------|---------------|-----------------|
|`Count`|`win:UInt32`|<span data-ttu-id="92c29-388">Çalıştırılan sonlandırıcılar sayısı.</span><span class="sxs-lookup"><span data-stu-id="92c29-388">The number of finalizers that were run.</span></span>|
|`ClrInstanceID`|<span data-ttu-id="92c29-389">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="92c29-389">win:UInt16</span></span>|<span data-ttu-id="92c29-390">CLR veya CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="92c29-390">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="setgchandle-event"></a><span data-ttu-id="92c29-391">SetGCHandle olayı</span><span class="sxs-lookup"><span data-stu-id="92c29-391">SetGCHandle event</span></span>

<span data-ttu-id="92c29-392">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="92c29-392">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="92c29-393">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="92c29-393">Keyword for raising the event</span></span>|<span data-ttu-id="92c29-394">Level</span><span class="sxs-lookup"><span data-stu-id="92c29-394">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="92c29-395">`GCHandleKeyword` 0x2</span><span class="sxs-lookup"><span data-stu-id="92c29-395">`GCHandleKeyword` (0x2)</span></span>|<span data-ttu-id="92c29-396">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="92c29-396">Informational (4)</span></span>|

<span data-ttu-id="92c29-397">Aşağıdaki tabloda olay bilgileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="92c29-397">The following table shows the event information:</span></span>

|<span data-ttu-id="92c29-398">Olay</span><span class="sxs-lookup"><span data-stu-id="92c29-398">Event</span></span>|<span data-ttu-id="92c29-399">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="92c29-399">Event ID</span></span>|<span data-ttu-id="92c29-400">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="92c29-400">Raised when</span></span>|
|-----------|--------------|-----------------|
|`SetGCHandle`|<span data-ttu-id="92c29-401">30</span><span class="sxs-lookup"><span data-stu-id="92c29-401">30</span></span>|<span data-ttu-id="92c29-402">GC tanıtıcısı ayarlandı.</span><span class="sxs-lookup"><span data-stu-id="92c29-402">A GC Handle has been set.</span></span>|

<span data-ttu-id="92c29-403">Aşağıdaki tabloda olay verileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="92c29-403">The following table shows the event data:</span></span>

|<span data-ttu-id="92c29-404">Alan adı</span><span class="sxs-lookup"><span data-stu-id="92c29-404">Field name</span></span>|<span data-ttu-id="92c29-405">Veri türü</span><span class="sxs-lookup"><span data-stu-id="92c29-405">Data type</span></span>|<span data-ttu-id="92c29-406">Açıklama</span><span class="sxs-lookup"><span data-stu-id="92c29-406">Description</span></span>|
|----------------|---------------|-----------------|
|`HandleID`|`win:Pointer`|<span data-ttu-id="92c29-407">Ayrılmış tanıtıcının adresi.</span><span class="sxs-lookup"><span data-stu-id="92c29-407">The address of the allocated handle.</span></span>|
|`ObjectID`|`win:Pointer`|<span data-ttu-id="92c29-408">Tutamacı oluşturulan nesnenin adresi.</span><span class="sxs-lookup"><span data-stu-id="92c29-408">The address of the object whose handle was created.</span></span>|
|`Kind`|`win:UInt32`|<span data-ttu-id="92c29-409">Ayarlanan GC tanıtıcısının türü.</span><span class="sxs-lookup"><span data-stu-id="92c29-409">The type of GC handle that was set.</span></span> <br /><br /><span data-ttu-id="92c29-410">`0x0`: WeakShort</span><span class="sxs-lookup"><span data-stu-id="92c29-410">`0x0`: WeakShort</span></span> <br/><br/><span data-ttu-id="92c29-411">`0x1`: WeakLong</span><span class="sxs-lookup"><span data-stu-id="92c29-411">`0x1`: WeakLong</span></span> <br /><br /><span data-ttu-id="92c29-412">`0x2`: Strong</span><span class="sxs-lookup"><span data-stu-id="92c29-412">`0x2`: Strong</span></span> <br /><br /><span data-ttu-id="92c29-413">`0x3`: Sabitlenmiş</span><span class="sxs-lookup"><span data-stu-id="92c29-413">`0x3`: Pinned</span></span> <br /><br /><span data-ttu-id="92c29-414">`0x4`: Değişken</span><span class="sxs-lookup"><span data-stu-id="92c29-414">`0x4`: Variable</span></span><br /><br /><span data-ttu-id="92c29-415">`0x5`: Refsayılan</span><span class="sxs-lookup"><span data-stu-id="92c29-415">`0x5`: RefCounted</span></span> <br /><br /><span data-ttu-id="92c29-416">`0x6`: Bağımlı</span><span class="sxs-lookup"><span data-stu-id="92c29-416">`0x6`: Dependent</span></span><br /><br /><span data-ttu-id="92c29-417">`0x7`: Asyncpınlan</span><span class="sxs-lookup"><span data-stu-id="92c29-417">`0x7`: AsyncPinned</span></span><br /><br /><span data-ttu-id="92c29-418">`0x8`: SizedRef</span><span class="sxs-lookup"><span data-stu-id="92c29-418">`0x8`: SizedRef</span></span>|
|`Generation`|`win:UInt32`|<span data-ttu-id="92c29-419">Tutamacı oluşturulduğu nesnenin oluşturulması.</span><span class="sxs-lookup"><span data-stu-id="92c29-419">The generation of the object whose handle was created.</span></span>|
|`AppDomainID`|`win:UInt64`|<span data-ttu-id="92c29-420">AppDomain KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="92c29-420">The AppDomain ID.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="92c29-421">CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="92c29-421">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="destroygchandle-event"></a><span data-ttu-id="92c29-422">DestroyGCHandle olayı</span><span class="sxs-lookup"><span data-stu-id="92c29-422">DestroyGCHandle event</span></span>

<span data-ttu-id="92c29-423">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="92c29-423">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="92c29-424">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="92c29-424">Keyword for raising the event</span></span>|<span data-ttu-id="92c29-425">Level</span><span class="sxs-lookup"><span data-stu-id="92c29-425">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="92c29-426">`GCHandleKeyword` 0x2</span><span class="sxs-lookup"><span data-stu-id="92c29-426">`GCHandleKeyword` (0x2)</span></span>|<span data-ttu-id="92c29-427">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="92c29-427">Informational (4)</span></span>|

<span data-ttu-id="92c29-428">Aşağıdaki tabloda olay bilgileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="92c29-428">The following table shows the event information:</span></span>

|<span data-ttu-id="92c29-429">Olay</span><span class="sxs-lookup"><span data-stu-id="92c29-429">Event</span></span>|<span data-ttu-id="92c29-430">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="92c29-430">Event ID</span></span>|<span data-ttu-id="92c29-431">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="92c29-431">Raised when</span></span>|
|-----------|--------------|-----------------|
|`DestroyGCHandle`|<span data-ttu-id="92c29-432">31</span><span class="sxs-lookup"><span data-stu-id="92c29-432">31</span></span>|<span data-ttu-id="92c29-433">GC tanıtıcısı yok edilir.</span><span class="sxs-lookup"><span data-stu-id="92c29-433">A GC Handle is destroyed.</span></span>|

<span data-ttu-id="92c29-434">Aşağıdaki tabloda olay verileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="92c29-434">The following table shows the event data:</span></span>

|<span data-ttu-id="92c29-435">Alan adı</span><span class="sxs-lookup"><span data-stu-id="92c29-435">Field name</span></span>|<span data-ttu-id="92c29-436">Veri türü</span><span class="sxs-lookup"><span data-stu-id="92c29-436">Data type</span></span>|<span data-ttu-id="92c29-437">Açıklama</span><span class="sxs-lookup"><span data-stu-id="92c29-437">Description</span></span>|
|----------------|---------------|-----------------|
|`HandleID`|`win:Pointer`|<span data-ttu-id="92c29-438">Yok etme tanıtıcısının adresi.</span><span class="sxs-lookup"><span data-stu-id="92c29-438">The address of the destroyed handle.</span></span>|
|`ClrInstanceID`|<span data-ttu-id="92c29-439">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="92c29-439">win:UInt16</span></span>|<span data-ttu-id="92c29-440">CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="92c29-440">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="pinobjectatgctime-event"></a><span data-ttu-id="92c29-441">PinObjectAtGCTime olayı</span><span class="sxs-lookup"><span data-stu-id="92c29-441">PinObjectAtGCTime event</span></span>

<span data-ttu-id="92c29-442">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="92c29-442">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="92c29-443">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="92c29-443">Keyword for raising the event</span></span>|<span data-ttu-id="92c29-444">Level</span><span class="sxs-lookup"><span data-stu-id="92c29-444">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="92c29-445">`GCKeyword` 0x1</span><span class="sxs-lookup"><span data-stu-id="92c29-445">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="92c29-446">Verbose (5)</span><span class="sxs-lookup"><span data-stu-id="92c29-446">Verbose (5)</span></span>|

<span data-ttu-id="92c29-447">Aşağıdaki tabloda olay bilgileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="92c29-447">The following table shows the event information:</span></span>

|<span data-ttu-id="92c29-448">Olay</span><span class="sxs-lookup"><span data-stu-id="92c29-448">Event</span></span>|<span data-ttu-id="92c29-449">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="92c29-449">Event ID</span></span>|<span data-ttu-id="92c29-450">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="92c29-450">Raised when</span></span>|
|-----------|--------------|-----------------|
|`PinObjectAtGCTime`|<span data-ttu-id="92c29-451">33</span><span class="sxs-lookup"><span data-stu-id="92c29-451">33</span></span>|<span data-ttu-id="92c29-452">GC sırasında bir nesne sabitlendi.</span><span class="sxs-lookup"><span data-stu-id="92c29-452">An object was pinned during a GC.</span></span>|

<span data-ttu-id="92c29-453">Aşağıdaki tabloda olay verileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="92c29-453">The following table shows the event data:</span></span>

|<span data-ttu-id="92c29-454">Alan adı</span><span class="sxs-lookup"><span data-stu-id="92c29-454">Field name</span></span>|<span data-ttu-id="92c29-455">Veri türü</span><span class="sxs-lookup"><span data-stu-id="92c29-455">Data type</span></span>|<span data-ttu-id="92c29-456">Açıklama</span><span class="sxs-lookup"><span data-stu-id="92c29-456">Description</span></span>|
|----------------|---------------|-----------------|
|`HandleID`|`win:Pointer`|<span data-ttu-id="92c29-457">Tanıtıcının adresi.</span><span class="sxs-lookup"><span data-stu-id="92c29-457">The address of the handle.</span></span>|
|`ObjectID`|`win:Pointer`|<span data-ttu-id="92c29-458">Sabitlenmiş nesnenin adresi.</span><span class="sxs-lookup"><span data-stu-id="92c29-458">The address of the pinned object.</span></span>|
|`ObjectSize`|`win:UInt64`|<span data-ttu-id="92c29-459">Sabitlenmiş nesnenin boyutu.</span><span class="sxs-lookup"><span data-stu-id="92c29-459">The size of the pinned object.</span></span>|
|`TypeName`|`win:UnicodeString`|<span data-ttu-id="92c29-460">Sabitlenmiş nesnenin türünün adı.</span><span class="sxs-lookup"><span data-stu-id="92c29-460">The name of the type of the pinned object.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="92c29-461">CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="92c29-461">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="gctriggered-event"></a><span data-ttu-id="92c29-462">GCTriggered olayı</span><span class="sxs-lookup"><span data-stu-id="92c29-462">GCTriggered event</span></span>

<span data-ttu-id="92c29-463">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="92c29-463">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="92c29-464">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="92c29-464">Keyword for raising the event</span></span>|<span data-ttu-id="92c29-465">Level</span><span class="sxs-lookup"><span data-stu-id="92c29-465">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="92c29-466">`GCKeyword` 0x1</span><span class="sxs-lookup"><span data-stu-id="92c29-466">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="92c29-467">Verbose (5)</span><span class="sxs-lookup"><span data-stu-id="92c29-467">Verbose (5)</span></span>|

<span data-ttu-id="92c29-468">Aşağıdaki tabloda olay bilgileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="92c29-468">The following table shows the event information:</span></span>

|<span data-ttu-id="92c29-469">Olay</span><span class="sxs-lookup"><span data-stu-id="92c29-469">Event</span></span>|<span data-ttu-id="92c29-470">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="92c29-470">Event ID</span></span>|<span data-ttu-id="92c29-471">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="92c29-471">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCTriggered`|<span data-ttu-id="92c29-472">33</span><span class="sxs-lookup"><span data-stu-id="92c29-472">33</span></span>|<span data-ttu-id="92c29-473">GC tetiklendi.</span><span class="sxs-lookup"><span data-stu-id="92c29-473">A GC has been triggered.</span></span>|

<span data-ttu-id="92c29-474">Aşağıdaki tabloda olay verileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="92c29-474">The following table shows the event data:</span></span>

|<span data-ttu-id="92c29-475">Alan adı</span><span class="sxs-lookup"><span data-stu-id="92c29-475">Field name</span></span>|<span data-ttu-id="92c29-476">Veri türü</span><span class="sxs-lookup"><span data-stu-id="92c29-476">Data type</span></span>|<span data-ttu-id="92c29-477">Açıklama</span><span class="sxs-lookup"><span data-stu-id="92c29-477">Description</span></span>|
|----------------|---------------|-----------------|
|`Reason`|`win:UInt32`|<span data-ttu-id="92c29-478">GC 'nin tetiklenme nedeni.</span><span class="sxs-lookup"><span data-stu-id="92c29-478">The reason a GC was triggered.</span></span><br/><br/><span data-ttu-id="92c29-479">`0x0`: AllocSmall</span><span class="sxs-lookup"><span data-stu-id="92c29-479">`0x0`: AllocSmall</span></span><br/><br/><span data-ttu-id="92c29-480">`0x1`: Alınmış</span><span class="sxs-lookup"><span data-stu-id="92c29-480">`0x1`: Induced</span></span> <br/><br/><span data-ttu-id="92c29-481">`0x2`: LowMemory</span><span class="sxs-lookup"><span data-stu-id="92c29-481">`0x2`: LowMemory</span></span> <br/><br/><span data-ttu-id="92c29-482">`0x3`: Boş</span><span class="sxs-lookup"><span data-stu-id="92c29-482">`0x3`: Empty</span></span> <br/><br/><span data-ttu-id="92c29-483">`0x4`: AllocLarge</span><span class="sxs-lookup"><span data-stu-id="92c29-483">`0x4`: AllocLarge</span></span> <br/><br/><span data-ttu-id="92c29-484">`0x5`: OutOfSpaceSmallObjectHeap</span><span class="sxs-lookup"><span data-stu-id="92c29-484">`0x5`: OutOfSpaceSmallObjectHeap</span></span> <br/><br/><span data-ttu-id="92c29-485">`0x6`: OutOfSpaceLargeObjectHeap</span><span class="sxs-lookup"><span data-stu-id="92c29-485">`0x6`: OutOfSpaceLargeObjectHeap</span></span> <br/><br/><span data-ttu-id="92c29-486">`0x7`:InducedNoForce</span><span class="sxs-lookup"><span data-stu-id="92c29-486">`0x7`:InducedNoForce</span></span> <br/><br/><span data-ttu-id="92c29-487">`0x8`: Stres</span><span class="sxs-lookup"><span data-stu-id="92c29-487">`0x8`: Stress</span></span> <br/><br/><span data-ttu-id="92c29-488">`0x9`: Endücedlowmemory</span><span class="sxs-lookup"><span data-stu-id="92c29-488">`0x9`: InducedLowMemory</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="92c29-489">CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="92c29-489">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="increasememorypressure-event"></a><span data-ttu-id="92c29-490">Increasememorypresbir olay</span><span class="sxs-lookup"><span data-stu-id="92c29-490">IncreaseMemoryPressure event</span></span>

<span data-ttu-id="92c29-491">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="92c29-491">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="92c29-492">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="92c29-492">Keyword for raising the event</span></span>|<span data-ttu-id="92c29-493">Level</span><span class="sxs-lookup"><span data-stu-id="92c29-493">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="92c29-494">`GCKeyword` 0x1</span><span class="sxs-lookup"><span data-stu-id="92c29-494">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="92c29-495">Bilgi (4)</span><span class="sxs-lookup"><span data-stu-id="92c29-495">Information (4)</span></span>|

<span data-ttu-id="92c29-496">Aşağıdaki tabloda olay bilgileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="92c29-496">The following table shows the event information:</span></span>

|<span data-ttu-id="92c29-497">Olay</span><span class="sxs-lookup"><span data-stu-id="92c29-497">Event</span></span>|<span data-ttu-id="92c29-498">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="92c29-498">Event ID</span></span>|<span data-ttu-id="92c29-499">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="92c29-499">Raised when</span></span>|
|----------------|---------------|-----------------|
|`IncreaseMemoryPressure`|<span data-ttu-id="92c29-500">200</span><span class="sxs-lookup"><span data-stu-id="92c29-500">200</span></span>|<span data-ttu-id="92c29-501">Bellek baskısı arttı.</span><span class="sxs-lookup"><span data-stu-id="92c29-501">Memory pressure was increased.</span></span>|

<span data-ttu-id="92c29-502">Aşağıdaki tabloda olay verileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="92c29-502">The following table shows the event data:</span></span>

|<span data-ttu-id="92c29-503">Alan Adı</span><span class="sxs-lookup"><span data-stu-id="92c29-503">Field Name</span></span>|<span data-ttu-id="92c29-504">Veri türü</span><span class="sxs-lookup"><span data-stu-id="92c29-504">Data type</span></span>|<span data-ttu-id="92c29-505">Açıklama</span><span class="sxs-lookup"><span data-stu-id="92c29-505">Description</span></span>|
|----------------|---------------|-----------------|
|`ClrInstanceID`|<span data-ttu-id="92c29-506">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="92c29-506">win:UInt16</span></span>|<span data-ttu-id="92c29-507">CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="92c29-507">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="decreasememorypressure-event"></a><span data-ttu-id="92c29-508">DecreaseMemoryPressure olayı</span><span class="sxs-lookup"><span data-stu-id="92c29-508">DecreaseMemoryPressure event</span></span>

<span data-ttu-id="92c29-509">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="92c29-509">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="92c29-510">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="92c29-510">Keyword for raising the event</span></span>|<span data-ttu-id="92c29-511">Level</span><span class="sxs-lookup"><span data-stu-id="92c29-511">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="92c29-512">`GCKeyword` 0x1</span><span class="sxs-lookup"><span data-stu-id="92c29-512">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="92c29-513">Bilgi (4)</span><span class="sxs-lookup"><span data-stu-id="92c29-513">Information (4)</span></span>|

<span data-ttu-id="92c29-514">Aşağıdaki tabloda olay bilgileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="92c29-514">The following table shows the event information:</span></span>

|<span data-ttu-id="92c29-515">Olay</span><span class="sxs-lookup"><span data-stu-id="92c29-515">Event</span></span>|<span data-ttu-id="92c29-516">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="92c29-516">Event ID</span></span>|<span data-ttu-id="92c29-517">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="92c29-517">Raised when</span></span>|
|----------------|---------------|-----------------|
|`DecreaseMemoryPressure`|<span data-ttu-id="92c29-518">201</span><span class="sxs-lookup"><span data-stu-id="92c29-518">201</span></span>|<span data-ttu-id="92c29-519">Bellek baskısı azaltılmıştı.</span><span class="sxs-lookup"><span data-stu-id="92c29-519">Memory pressure was decreased.</span></span>|

<span data-ttu-id="92c29-520">Aşağıdaki tabloda olay verileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="92c29-520">The following table shows the event data:</span></span>

|<span data-ttu-id="92c29-521">Alan Adı</span><span class="sxs-lookup"><span data-stu-id="92c29-521">Field Name</span></span>|<span data-ttu-id="92c29-522">Veri türü</span><span class="sxs-lookup"><span data-stu-id="92c29-522">Data type</span></span>|<span data-ttu-id="92c29-523">Açıklama</span><span class="sxs-lookup"><span data-stu-id="92c29-523">Description</span></span>|
|----------------|---------------|-----------------|
|`BytesFreed`|`win:UInt32`|<span data-ttu-id="92c29-524">Serbest bırakılan bayt.</span><span class="sxs-lookup"><span data-stu-id="92c29-524">Bytes freed.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="92c29-525">CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="92c29-525">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="gcmarkwithtype-event"></a><span data-ttu-id="92c29-526">GCMarkWithType olayı</span><span class="sxs-lookup"><span data-stu-id="92c29-526">GCMarkWithType event</span></span>

<span data-ttu-id="92c29-527">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="92c29-527">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="92c29-528">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="92c29-528">Keyword for raising the event</span></span>|<span data-ttu-id="92c29-529">Level</span><span class="sxs-lookup"><span data-stu-id="92c29-529">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="92c29-530">`GCKeyword` 0x1</span><span class="sxs-lookup"><span data-stu-id="92c29-530">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="92c29-531">Bilgi (4)</span><span class="sxs-lookup"><span data-stu-id="92c29-531">Information (4)</span></span>|

<span data-ttu-id="92c29-532">Aşağıdaki tabloda olay bilgileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="92c29-532">The following table shows the event information:</span></span>

|<span data-ttu-id="92c29-533">Olay</span><span class="sxs-lookup"><span data-stu-id="92c29-533">Event</span></span>|<span data-ttu-id="92c29-534">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="92c29-534">Event ID</span></span>|<span data-ttu-id="92c29-535">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="92c29-535">Raised when</span></span>|
|----------------|---------------|-----------------|
|`GCMarkWithType`|<span data-ttu-id="92c29-536">202</span><span class="sxs-lookup"><span data-stu-id="92c29-536">202</span></span>|<span data-ttu-id="92c29-537">GC işareti aşamasında bir GC kökü işaretlendi.</span><span class="sxs-lookup"><span data-stu-id="92c29-537">A GC root has been marked during GC mark phase.</span></span>|

<span data-ttu-id="92c29-538">Aşağıdaki tabloda olay verileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="92c29-538">The following table shows the event data:</span></span>

|<span data-ttu-id="92c29-539">Alan Adı</span><span class="sxs-lookup"><span data-stu-id="92c29-539">Field Name</span></span>|<span data-ttu-id="92c29-540">Veri türü</span><span class="sxs-lookup"><span data-stu-id="92c29-540">Data type</span></span>|<span data-ttu-id="92c29-541">Açıklama</span><span class="sxs-lookup"><span data-stu-id="92c29-541">Description</span></span>|
|----------------|---------------|-----------------|
|`HeapNum`|`win:UInt32`|<span data-ttu-id="92c29-542">Yığın numarası.</span><span class="sxs-lookup"><span data-stu-id="92c29-542">The heap number.</span></span>|
|`ClrInstanceID`|<span data-ttu-id="92c29-543">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="92c29-543">win:UInt16</span></span>|<span data-ttu-id="92c29-544">CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="92c29-544">Unique ID for the instance of CoreCLR.</span></span>|
|`Type`|`win:UInt32`|<span data-ttu-id="92c29-545">GC kök türü.</span><span class="sxs-lookup"><span data-stu-id="92c29-545">The GC root type.</span></span><br/><br/><span data-ttu-id="92c29-546">`0x0`: Yığın</span><span class="sxs-lookup"><span data-stu-id="92c29-546">`0x0`: Stack</span></span><br/><br/><span data-ttu-id="92c29-547">`0x1`: Sonlandırıcı</span><span class="sxs-lookup"><span data-stu-id="92c29-547">`0x1`: Finalizer</span></span><br/><br/><span data-ttu-id="92c29-548">`0x2`: Tanıtıcı</span><span class="sxs-lookup"><span data-stu-id="92c29-548">`0x2`: Handle</span></span><br/><br/><span data-ttu-id="92c29-549">`0x3`: Daha eski</span><span class="sxs-lookup"><span data-stu-id="92c29-549">`0x3`: Older</span></span><br/><br/><span data-ttu-id="92c29-550">`0x4`: SizedRef</span><span class="sxs-lookup"><span data-stu-id="92c29-550">`0x4`: SizedRef</span></span><br/><br/><span data-ttu-id="92c29-551">`0x5`: Taşma</span><span class="sxs-lookup"><span data-stu-id="92c29-551">`0x5`: Overflow</span></span><br/><br/>|
|`Bytes`|`win:UInt64`|<span data-ttu-id="92c29-552">İşaretlenmiş baytların sayısı.</span><span class="sxs-lookup"><span data-stu-id="92c29-552">The number of bytes marked.</span></span>|

## <a name="gcjoin_v2-event"></a><span data-ttu-id="92c29-553">GCJoin_V2 olayı</span><span class="sxs-lookup"><span data-stu-id="92c29-553">GCJoin_V2 event</span></span>

<span data-ttu-id="92c29-554">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="92c29-554">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="92c29-555">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="92c29-555">Keyword for raising the event</span></span>|<span data-ttu-id="92c29-556">Level</span><span class="sxs-lookup"><span data-stu-id="92c29-556">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="92c29-557">`GCKeyword` 0x1</span><span class="sxs-lookup"><span data-stu-id="92c29-557">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="92c29-558">Verbose (5)</span><span class="sxs-lookup"><span data-stu-id="92c29-558">Verbose (5)</span></span>|

<span data-ttu-id="92c29-559">Aşağıdaki tabloda olay bilgileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="92c29-559">The following table shows the event information:</span></span>

|<span data-ttu-id="92c29-560">Olay</span><span class="sxs-lookup"><span data-stu-id="92c29-560">Event</span></span>|<span data-ttu-id="92c29-561">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="92c29-561">Event ID</span></span>|<span data-ttu-id="92c29-562">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="92c29-562">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCJoin_V2`|<span data-ttu-id="92c29-563">203</span><span class="sxs-lookup"><span data-stu-id="92c29-563">203</span></span>|<span data-ttu-id="92c29-564">Birleştirilmiş bir GC iş parçacığı.</span><span class="sxs-lookup"><span data-stu-id="92c29-564">A GC thread joined.</span></span>|

<span data-ttu-id="92c29-565">Aşağıdaki tabloda olay verileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="92c29-565">The following table shows the event data:</span></span>

|<span data-ttu-id="92c29-566">Alan adı</span><span class="sxs-lookup"><span data-stu-id="92c29-566">Field name</span></span>|<span data-ttu-id="92c29-567">Veri türü</span><span class="sxs-lookup"><span data-stu-id="92c29-567">Data type</span></span>|<span data-ttu-id="92c29-568">Açıklama</span><span class="sxs-lookup"><span data-stu-id="92c29-568">Description</span></span>|
|----------------|---------------|-----------------|
|`Heap`|`win:UInt32`|<span data-ttu-id="92c29-569">Yığın numarası</span><span class="sxs-lookup"><span data-stu-id="92c29-569">The heap number</span></span>|
|`JoinTime`|`win:UInt32`|<span data-ttu-id="92c29-570">Bu olayın birleştirmenin başlangıcında mi, yoksa bir birleşimin sonunda mi tetiklendiğini belirtir (JOIN `0x0` için, `0x1` JOIN End for JOIN için)</span><span class="sxs-lookup"><span data-stu-id="92c29-570">Indicates whether this event is fired at the start of a join or end of a join (`0x0` for join start, `0x1` for join end)</span></span>|
|`JoinType`|`win:UInt32`|<span data-ttu-id="92c29-571">JOIN türü.</span><span class="sxs-lookup"><span data-stu-id="92c29-571">The join type.</span></span> <br/><br/><span data-ttu-id="92c29-572">`0x0`: Son ekleme</span><span class="sxs-lookup"><span data-stu-id="92c29-572">`0x0`: Last Join</span></span><br/><br/><span data-ttu-id="92c29-573">`0x1`: Birleştir</span><span class="sxs-lookup"><span data-stu-id="92c29-573">`0x1`: Join</span></span> <br/><br/><span data-ttu-id="92c29-574">`0x2`: Yeniden Başlat</span><span class="sxs-lookup"><span data-stu-id="92c29-574">`0x2`: Restart</span></span> <br/><br/><span data-ttu-id="92c29-575">`0x3`: İlk olarak katılmayı geri çevir</span><span class="sxs-lookup"><span data-stu-id="92c29-575">`0x3`: First Reverse Join</span></span><br/><br/><span data-ttu-id="92c29-576">`0x4`: Ters Birleştir</span><span class="sxs-lookup"><span data-stu-id="92c29-576">`0x4`: Reverse Join</span></span><br/><br/>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="92c29-577">CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="92c29-577">Unique ID for the instance of CoreCLR.</span></span>|
