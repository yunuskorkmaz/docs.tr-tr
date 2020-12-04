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
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2020
ms.locfileid: "96590001"
---
# <a name="net-runtime-garbage-collection-events"></a><span data-ttu-id="7bb7e-103">.NET çalışma zamanı atık toplama olayları</span><span class="sxs-lookup"><span data-stu-id="7bb7e-103">.NET runtime garbage collection events</span></span>

<span data-ttu-id="7bb7e-104">Bu olaylar çöp koleksiyonuyla ilgili bilgiler toplar.</span><span class="sxs-lookup"><span data-stu-id="7bb7e-104">These events collect information pertaining to garbage collection.</span></span> <span data-ttu-id="7bb7e-105">Çöp toplamanın kaç kez gerçekleştirildiğini belirleme, çöp toplama sırasında ne kadar bellek serbest bırakılmış vb. gibi tanılama ve hata ayıklama konusunda yardımcı olurlar. Bu olayların tanılama amacıyla nasıl kullanılacağı hakkında daha fazla bilgi için bkz. [.NET uygulamalarını günlüğe kaydetme ve izleme](../../core/diagnostics/logging-tracing.md)</span><span class="sxs-lookup"><span data-stu-id="7bb7e-105">They help in diagnostics and debugging, including determining how many times garbage collection was performed, how much memory was freed during garbage collection, etc. For more information about how to use these events for diagnostic purposes, see [logging and tracing .NET applications](../../core/diagnostics/logging-tracing.md)</span></span>

## <a name="gcstart_v2-event"></a><span data-ttu-id="7bb7e-106">GCStart_V2 olayı</span><span class="sxs-lookup"><span data-stu-id="7bb7e-106">GCStart_V2 Event</span></span>

<span data-ttu-id="7bb7e-107">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="7bb7e-107">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="7bb7e-108">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="7bb7e-108">Keyword for raising the event</span></span>|<span data-ttu-id="7bb7e-109">Level</span><span class="sxs-lookup"><span data-stu-id="7bb7e-109">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="7bb7e-110">`GCKeyword` 0x1</span><span class="sxs-lookup"><span data-stu-id="7bb7e-110">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="7bb7e-111">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="7bb7e-111">Informational (4)</span></span>|

<span data-ttu-id="7bb7e-112">Aşağıdaki tabloda olay bilgileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="7bb7e-112">The following table shows the event information:</span></span>

|<span data-ttu-id="7bb7e-113">Olay</span><span class="sxs-lookup"><span data-stu-id="7bb7e-113">Event</span></span>|<span data-ttu-id="7bb7e-114">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="7bb7e-114">Event ID</span></span>|<span data-ttu-id="7bb7e-115">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="7bb7e-115">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCStart_V1`|<span data-ttu-id="7bb7e-116">1</span><span class="sxs-lookup"><span data-stu-id="7bb7e-116">1</span></span>|<span data-ttu-id="7bb7e-117">Çöp toplama işlemi başlatıldı.</span><span class="sxs-lookup"><span data-stu-id="7bb7e-117">A garbage collection has started.</span></span>|

<span data-ttu-id="7bb7e-118">Aşağıdaki tabloda olay verileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="7bb7e-118">The following table shows the event data:</span></span>

|<span data-ttu-id="7bb7e-119">Alan adı</span><span class="sxs-lookup"><span data-stu-id="7bb7e-119">Field name</span></span>|<span data-ttu-id="7bb7e-120">Veri türü</span><span class="sxs-lookup"><span data-stu-id="7bb7e-120">Data type</span></span>|<span data-ttu-id="7bb7e-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7bb7e-121">Description</span></span>|
|----------------|---------------|-----------------|
|`Count`|`win:UInt32`|<span data-ttu-id="7bb7e-122">*N*. çöp toplama.</span><span class="sxs-lookup"><span data-stu-id="7bb7e-122">The *n* th garbage collection.</span></span>|
|`Depth`|`win:UInt32`|<span data-ttu-id="7bb7e-123">Toplanmakta olan oluşturma.</span><span class="sxs-lookup"><span data-stu-id="7bb7e-123">The generation that is being collected.</span></span>|
|`Reason`|`win:UInt32`|<span data-ttu-id="7bb7e-124">Çöp toplamanın neden tetiklendiği:</span><span class="sxs-lookup"><span data-stu-id="7bb7e-124">Why the garbage collection was triggered:</span></span><br /><br /> <span data-ttu-id="7bb7e-125">`0x0` -Küçük nesne yığını ayırması.</span><span class="sxs-lookup"><span data-stu-id="7bb7e-125">`0x0` - Small object heap allocation.</span></span><br /><br /> <span data-ttu-id="7bb7e-126">`0x1` Zorlanmadı.</span><span class="sxs-lookup"><span data-stu-id="7bb7e-126">`0x1` - Induced.</span></span><br /><br /> <span data-ttu-id="7bb7e-127">`0x2` -Düşük bellek.</span><span class="sxs-lookup"><span data-stu-id="7bb7e-127">`0x2` - Low memory.</span></span><br /><br /> <span data-ttu-id="7bb7e-128">`0x3` Olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="7bb7e-128">`0x3` - Empty.</span></span><br /><br /> <span data-ttu-id="7bb7e-129">`0x4` -Büyük nesne yığını ayırması.</span><span class="sxs-lookup"><span data-stu-id="7bb7e-129">`0x4` - Large object heap allocation.</span></span><br /><br /> <span data-ttu-id="7bb7e-130">`0x5` -Alan kalmadı (küçük nesne yığını için).</span><span class="sxs-lookup"><span data-stu-id="7bb7e-130">`0x5` - Out of space (for small object heap).</span></span><br /><br /> <span data-ttu-id="7bb7e-131">`0x6` -Alan kalmadı (büyük nesne yığını için).</span><span class="sxs-lookup"><span data-stu-id="7bb7e-131">`0x6` - Out of space (for large object heap).</span></span><br /><br /> <span data-ttu-id="7bb7e-132">`0x7` -Alınmış ancak engelleme olarak zorlanmadı.</span><span class="sxs-lookup"><span data-stu-id="7bb7e-132">`0x7` - Induced but not forced as blocking.</span></span>|
|`Type`|`win:UInt32`|<span data-ttu-id="7bb7e-133">`0x0` -Arka plan atık toplama dışında çöp toplama engelleme gerçekleşti.</span><span class="sxs-lookup"><span data-stu-id="7bb7e-133">`0x0` - Blocking garbage collection occurred outside background garbage collection.</span></span><br /><br /> <span data-ttu-id="7bb7e-134">`0x1` -Arka plan atık toplama.</span><span class="sxs-lookup"><span data-stu-id="7bb7e-134">`0x1` - Background garbage collection.</span></span><br /><br /> <span data-ttu-id="7bb7e-135">`0x2` -Arka plan atık toplama sırasında atık toplamayı engelleme oluştu.</span><span class="sxs-lookup"><span data-stu-id="7bb7e-135">`0x2` - Blocking garbage collection occurred during background garbage collection.</span></span>|
|`ClrInstanceID`|<span data-ttu-id="7bb7e-136">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="7bb7e-136">win:UInt16</span></span>|<span data-ttu-id="7bb7e-137">CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="7bb7e-137">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="gcend_v1-event"></a><span data-ttu-id="7bb7e-138">GCEnd_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="7bb7e-138">GCEnd_V1 Event</span></span>

<span data-ttu-id="7bb7e-139">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="7bb7e-139">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="7bb7e-140">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="7bb7e-140">Keyword for raising the event</span></span>|<span data-ttu-id="7bb7e-141">Level</span><span class="sxs-lookup"><span data-stu-id="7bb7e-141">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="7bb7e-142">`GCKeyword` 0x1</span><span class="sxs-lookup"><span data-stu-id="7bb7e-142">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="7bb7e-143">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="7bb7e-143">Informational (4)</span></span>|

<span data-ttu-id="7bb7e-144">Aşağıdaki tabloda olay bilgileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="7bb7e-144">The following table shows the event information:</span></span>

|<span data-ttu-id="7bb7e-145">Olay</span><span class="sxs-lookup"><span data-stu-id="7bb7e-145">Event</span></span>|<span data-ttu-id="7bb7e-146">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="7bb7e-146">Event ID</span></span>|<span data-ttu-id="7bb7e-147">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="7bb7e-147">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCEnd_V1`|<span data-ttu-id="7bb7e-148">2</span><span class="sxs-lookup"><span data-stu-id="7bb7e-148">2</span></span>|<span data-ttu-id="7bb7e-149">Çöp toplama sona erdi.</span><span class="sxs-lookup"><span data-stu-id="7bb7e-149">The garbage collection has ended.</span></span>|

<span data-ttu-id="7bb7e-150">Aşağıdaki tabloda olay verileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="7bb7e-150">The following table shows the event data:</span></span>

|<span data-ttu-id="7bb7e-151">Alan adı</span><span class="sxs-lookup"><span data-stu-id="7bb7e-151">Field name</span></span>|<span data-ttu-id="7bb7e-152">Veri türü</span><span class="sxs-lookup"><span data-stu-id="7bb7e-152">Data type</span></span>|<span data-ttu-id="7bb7e-153">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7bb7e-153">Description</span></span>|
|----------------|---------------|-----------------|
|`Count`|`win:UInt32`|<span data-ttu-id="7bb7e-154">*N*. çöp toplama.</span><span class="sxs-lookup"><span data-stu-id="7bb7e-154">The *n* th garbage collection.</span></span>|
|`Depth`|`win:UInt32`|<span data-ttu-id="7bb7e-155">Toplanan nesil.</span><span class="sxs-lookup"><span data-stu-id="7bb7e-155">The generation that was collected.</span></span>|
|`ClrInstanceID`|<span data-ttu-id="7bb7e-156">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="7bb7e-156">win:UInt16</span></span>|<span data-ttu-id="7bb7e-157">CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="7bb7e-157">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="gcheapstats_v2-event"></a><span data-ttu-id="7bb7e-158">GCHeapStats_V2 olayı</span><span class="sxs-lookup"><span data-stu-id="7bb7e-158">GCHeapStats_V2 Event</span></span>

<span data-ttu-id="7bb7e-159">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="7bb7e-159">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="7bb7e-160">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="7bb7e-160">Keyword for raising the event</span></span>|<span data-ttu-id="7bb7e-161">Level</span><span class="sxs-lookup"><span data-stu-id="7bb7e-161">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="7bb7e-162">`GCKeyword` 0x1</span><span class="sxs-lookup"><span data-stu-id="7bb7e-162">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="7bb7e-163">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="7bb7e-163">Informational (4)</span></span>|

<span data-ttu-id="7bb7e-164">Aşağıdaki tabloda olay bilgileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="7bb7e-164">The following table shows the event information:</span></span>

|<span data-ttu-id="7bb7e-165">Olay</span><span class="sxs-lookup"><span data-stu-id="7bb7e-165">Event</span></span>|<span data-ttu-id="7bb7e-166">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="7bb7e-166">Event ID</span></span>|<span data-ttu-id="7bb7e-167">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7bb7e-167">Description</span></span>|
|-----------|--------------|-----------------|
|`GCHeapStats_V2`|<span data-ttu-id="7bb7e-168">4</span><span class="sxs-lookup"><span data-stu-id="7bb7e-168">4</span></span>|<span data-ttu-id="7bb7e-169">Her çöp toplamanın sonundaki yığın istatistiklerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="7bb7e-169">Shows the heap statistics at the end of each garbage collection.</span></span>|

<span data-ttu-id="7bb7e-170">Aşağıdaki tabloda olay verileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="7bb7e-170">The following table shows the event data:</span></span>

|<span data-ttu-id="7bb7e-171">Alan adı</span><span class="sxs-lookup"><span data-stu-id="7bb7e-171">Field name</span></span>|<span data-ttu-id="7bb7e-172">Veri türü</span><span class="sxs-lookup"><span data-stu-id="7bb7e-172">Data type</span></span>|<span data-ttu-id="7bb7e-173">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7bb7e-173">Description</span></span>|
|----------------|---------------|-----------------|
|`GenerationSize0`|`win:UInt64`|<span data-ttu-id="7bb7e-174">0. nesil belleğin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="7bb7e-174">The size, in bytes, of generation 0 memory.</span></span>|
|`TotalPromotedSize0`|`win:UInt64`|<span data-ttu-id="7bb7e-175">Nesil 0 ' dan 1 ' e yükseltilen bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="7bb7e-175">The number of bytes that are promoted from generation 0 to generation 1.</span></span>|
|`GenerationSize1`|`win:UInt64`|<span data-ttu-id="7bb7e-176">1. nesil belleğin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="7bb7e-176">The size, in bytes, of generation 1 memory.</span></span>|
|`TotalPromotedSize1`|`win:UInt64`|<span data-ttu-id="7bb7e-177">1. nesil 2 ' ye kadar yükseltilen bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="7bb7e-177">The number of bytes that are promoted from generation 1 to generation 2.</span></span>|
|`GenerationSize2`|`win:UInt64`|<span data-ttu-id="7bb7e-178">2. nesil belleğin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="7bb7e-178">The size, in bytes, of generation 2 memory.</span></span>|
|`TotalPromotedSize2`|`win:UInt64`|<span data-ttu-id="7bb7e-179">Son koleksiyondan sonra 2. nesil üzerinde kalan bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="7bb7e-179">The number of bytes that survived in generation 2 after the last collection.</span></span>|
|`GenerationSize3`|`win:UInt64`|<span data-ttu-id="7bb7e-180">Büyük nesne yığınının bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="7bb7e-180">The size, in bytes, of the large object heap.</span></span>|
|`TotalPromotedSize3`|`win:UInt64`|<span data-ttu-id="7bb7e-181">Son koleksiyondan sonra büyük nesne yığınında kalan bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="7bb7e-181">The number of bytes that survived in the large object heap after the last collection.</span></span>|
|`FinalizationPromotedSize`|`win:UInt64`|<span data-ttu-id="7bb7e-182">Sonlandırma için hazırlanma nesnelerinin bayt cinsinden toplam boyutu.</span><span class="sxs-lookup"><span data-stu-id="7bb7e-182">The total size, in bytes, of the objects that are ready for finalization.</span></span>|
|`FinalizationPromotedCount`|`win:UInt64`|<span data-ttu-id="7bb7e-183">Sonlandırmaya hazırlanma nesne sayısı.</span><span class="sxs-lookup"><span data-stu-id="7bb7e-183">The number of objects that are ready for finalization.</span></span>|
|`PinnedObjectCount`|`win:UInt32`|<span data-ttu-id="7bb7e-184">Sabitlenmiş (taşınamaz) nesne sayısı.</span><span class="sxs-lookup"><span data-stu-id="7bb7e-184">The number of pinned (unmovable) objects.</span></span>|
|`SinkBlockCount`|`win:UInt32`|<span data-ttu-id="7bb7e-185">Kullanımdaki eşitleme bloklarının sayısı.</span><span class="sxs-lookup"><span data-stu-id="7bb7e-185">The number of synchronization blocks in use.</span></span>|
|`GCHandleCount`|`win:UInt32`|<span data-ttu-id="7bb7e-186">Kullanımdaki çöp toplama tanıtıcılarının sayısı.</span><span class="sxs-lookup"><span data-stu-id="7bb7e-186">The number of garbage collection handles in use.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="7bb7e-187">CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="7bb7e-187">Unique ID for the instance of CoreCLR.</span></span>|
|`GenerationSize4`|`win:UInt64`|<span data-ttu-id="7bb7e-188">Sabitlenmiş nesne yığınının bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="7bb7e-188">The size, in bytes, of the pinned object heap.</span></span>|
|`TotalPromotedSize4`|`win:UInt64`|<span data-ttu-id="7bb7e-189">Son koleksiyondan sonra sabitlenmiş nesne yığınında kalan bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="7bb7e-189">The number of bytes that survived in the pinned object heap after the last collection.</span></span>|

## <a name="gccreatesegment_v1-event"></a><span data-ttu-id="7bb7e-190">GCCreateSegment_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="7bb7e-190">GCCreateSegment_V1 event</span></span>

<span data-ttu-id="7bb7e-191">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="7bb7e-191">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="7bb7e-192">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="7bb7e-192">Keyword for raising the event</span></span>|<span data-ttu-id="7bb7e-193">Level</span><span class="sxs-lookup"><span data-stu-id="7bb7e-193">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="7bb7e-194">`GCKeyword` 0x1</span><span class="sxs-lookup"><span data-stu-id="7bb7e-194">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="7bb7e-195">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="7bb7e-195">Informational (4)</span></span>|

<span data-ttu-id="7bb7e-196">Aşağıdaki tabloda olay bilgileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="7bb7e-196">The following table shows the event information:</span></span>

|<span data-ttu-id="7bb7e-197">Olay</span><span class="sxs-lookup"><span data-stu-id="7bb7e-197">Event</span></span>|<span data-ttu-id="7bb7e-198">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="7bb7e-198">Event ID</span></span>|<span data-ttu-id="7bb7e-199">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="7bb7e-199">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCCreateSegment_V1`|<span data-ttu-id="7bb7e-200">5</span><span class="sxs-lookup"><span data-stu-id="7bb7e-200">5</span></span>|<span data-ttu-id="7bb7e-201">Yeni bir atık toplama segmenti oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="7bb7e-201">A new garbage collection segment has been created.</span></span> <span data-ttu-id="7bb7e-202">Ayrıca, izleme zaten çalışmakta olan bir işlemde etkinleştirildiğinde, bu olay varolan her segment için oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="7bb7e-202">In addition, when tracing is enabled on a process that is already running, this event is raised for each existing segment.</span></span>|

<span data-ttu-id="7bb7e-203">Aşağıdaki tabloda olay verileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="7bb7e-203">The following table shows the event data:</span></span>

|<span data-ttu-id="7bb7e-204">Alan adı</span><span class="sxs-lookup"><span data-stu-id="7bb7e-204">Field name</span></span>|<span data-ttu-id="7bb7e-205">Veri türü</span><span class="sxs-lookup"><span data-stu-id="7bb7e-205">Data type</span></span>|<span data-ttu-id="7bb7e-206">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7bb7e-206">Description</span></span>|
|----------------|---------------|-----------------|
|`Address`|`win:UInt64`|<span data-ttu-id="7bb7e-207">Segmentin adresi.</span><span class="sxs-lookup"><span data-stu-id="7bb7e-207">The address of the segment.</span></span>|
|`Size`|`win:UInt64`|<span data-ttu-id="7bb7e-208">Segmentin boyutu.</span><span class="sxs-lookup"><span data-stu-id="7bb7e-208">The size of the segment.</span></span>|
|`Type`|`win:UInt32`|<span data-ttu-id="7bb7e-209">0x0-küçük nesne yığını.</span><span class="sxs-lookup"><span data-stu-id="7bb7e-209">0x0 - Small object heap.</span></span><br /><br /> <span data-ttu-id="7bb7e-210">0x1-büyük nesne yığını.</span><span class="sxs-lookup"><span data-stu-id="7bb7e-210">0x1 - Large object heap.</span></span><br /><br /> <span data-ttu-id="7bb7e-211">0x2-salt okunurdur yığın.</span><span class="sxs-lookup"><span data-stu-id="7bb7e-211">0x2 - Read-only heap.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="7bb7e-212">CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="7bb7e-212">Unique ID for the instance of CoreCLR.</span></span>|

<span data-ttu-id="7bb7e-213">Çöp toplayıcı tarafından ayrılan parçaların boyutunun uygulamaya özgü olduğunu ve düzenli güncelleştirmeler de dahil olmak üzere herhangi bir zamanda değişikliğe tabi olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="7bb7e-213">Note that the size of segments allocated by the garbage collector is implementation-specific and is subject to change at any time, including in periodic updates.</span></span> <span data-ttu-id="7bb7e-214">Uygulamanız, belirli bir kesim boyutuna ilişkin varsayımları asla belirtmemelidir veya buna bağlı olarak, kesim ayırmaları için kullanılabilir bellek miktarını yapılandırmayı denemelidir.</span><span class="sxs-lookup"><span data-stu-id="7bb7e-214">Your app should never make assumptions about or depend on a particular segment size, nor should it attempt to configure the amount of memory available for segment allocations.</span></span>

## <a name="gcfreesegment_v1-event"></a><span data-ttu-id="7bb7e-215">GCFreeSegment_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="7bb7e-215">GCFreeSegment_V1 event</span></span>

<span data-ttu-id="7bb7e-216">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="7bb7e-216">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="7bb7e-217">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="7bb7e-217">Keyword for raising the event</span></span>|<span data-ttu-id="7bb7e-218">Level</span><span class="sxs-lookup"><span data-stu-id="7bb7e-218">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="7bb7e-219">`GCKeyword` 0x1</span><span class="sxs-lookup"><span data-stu-id="7bb7e-219">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="7bb7e-220">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="7bb7e-220">Informational (4)</span></span>|

<span data-ttu-id="7bb7e-221">Aşağıdaki tabloda olay bilgileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="7bb7e-221">The following table shows the event information:</span></span>

|<span data-ttu-id="7bb7e-222">Olay</span><span class="sxs-lookup"><span data-stu-id="7bb7e-222">Event</span></span>|<span data-ttu-id="7bb7e-223">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="7bb7e-223">Event ID</span></span>|<span data-ttu-id="7bb7e-224">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="7bb7e-224">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCFreeSegment_V1`|<span data-ttu-id="7bb7e-225">6</span><span class="sxs-lookup"><span data-stu-id="7bb7e-225">6</span></span>|<span data-ttu-id="7bb7e-226">Çöp toplama segmenti yayınlandı.</span><span class="sxs-lookup"><span data-stu-id="7bb7e-226">A garbage collection segment has been released.</span></span>|

<span data-ttu-id="7bb7e-227">Aşağıdaki tabloda olay verileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="7bb7e-227">The following table shows the event data:</span></span>

|<span data-ttu-id="7bb7e-228">Alan adı</span><span class="sxs-lookup"><span data-stu-id="7bb7e-228">Field name</span></span>|<span data-ttu-id="7bb7e-229">Veri türü</span><span class="sxs-lookup"><span data-stu-id="7bb7e-229">Data type</span></span>|<span data-ttu-id="7bb7e-230">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7bb7e-230">Description</span></span>|
|----------------|---------------|-----------------|
|`Address`|`win:UInt64`|<span data-ttu-id="7bb7e-231">Segmentin adresi.</span><span class="sxs-lookup"><span data-stu-id="7bb7e-231">The address of the segment.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="7bb7e-232">CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="7bb7e-232">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="gcrestarteebegin_v1-event"></a><span data-ttu-id="7bb7e-233">GCRestartEEBegin_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="7bb7e-233">GCRestartEEBegin_V1 event</span></span>

<span data-ttu-id="7bb7e-234">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="7bb7e-234">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="7bb7e-235">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="7bb7e-235">Keyword for raising the event</span></span>|<span data-ttu-id="7bb7e-236">Level</span><span class="sxs-lookup"><span data-stu-id="7bb7e-236">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="7bb7e-237">`GCKeyword` 0x1</span><span class="sxs-lookup"><span data-stu-id="7bb7e-237">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="7bb7e-238">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="7bb7e-238">Informational (4)</span></span>|

<span data-ttu-id="7bb7e-239">Aşağıdaki tabloda olay bilgileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="7bb7e-239">The following table shows the event information:</span></span>

|<span data-ttu-id="7bb7e-240">Olay</span><span class="sxs-lookup"><span data-stu-id="7bb7e-240">Event</span></span>|<span data-ttu-id="7bb7e-241">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="7bb7e-241">Event ID</span></span>|<span data-ttu-id="7bb7e-242">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="7bb7e-242">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCRestartEEBegin_V1`|<span data-ttu-id="7bb7e-243">7</span><span class="sxs-lookup"><span data-stu-id="7bb7e-243">7</span></span>|<span data-ttu-id="7bb7e-244">Ortak dil çalışma zamanı askıya alma işleminden sürdürme başladı.</span><span class="sxs-lookup"><span data-stu-id="7bb7e-244">Resumption from common language runtime suspension has begun.</span></span>|

<span data-ttu-id="7bb7e-245">Bu olay hiçbir olay verisine sahip değil.</span><span class="sxs-lookup"><span data-stu-id="7bb7e-245">This event does not have any event data.</span></span>

## <a name="gcrestarteeend_v1-event"></a><span data-ttu-id="7bb7e-246">GCRestartEEEnd_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="7bb7e-246">GCRestartEEEnd_V1 event</span></span>

<span data-ttu-id="7bb7e-247">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="7bb7e-247">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="7bb7e-248">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="7bb7e-248">Keyword for raising the event</span></span>|<span data-ttu-id="7bb7e-249">Level</span><span class="sxs-lookup"><span data-stu-id="7bb7e-249">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="7bb7e-250">`GCKeyword` 0x1</span><span class="sxs-lookup"><span data-stu-id="7bb7e-250">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="7bb7e-251">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="7bb7e-251">Informational (4)</span></span>|

<span data-ttu-id="7bb7e-252">Aşağıdaki tabloda olay bilgileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="7bb7e-252">The following table shows the event information:</span></span>

|<span data-ttu-id="7bb7e-253">Olay</span><span class="sxs-lookup"><span data-stu-id="7bb7e-253">Event</span></span>|<span data-ttu-id="7bb7e-254">Olay kimliği</span><span class="sxs-lookup"><span data-stu-id="7bb7e-254">Event Id</span></span>|<span data-ttu-id="7bb7e-255">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="7bb7e-255">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCRestartEEEnd_V1`|<span data-ttu-id="7bb7e-256">3</span><span class="sxs-lookup"><span data-stu-id="7bb7e-256">3</span></span>|<span data-ttu-id="7bb7e-257">Ortak dil çalışma zamanı askıya alma işleminden sürdürme sonlandı.</span><span class="sxs-lookup"><span data-stu-id="7bb7e-257">Resumption from common language runtime suspension has ended.</span></span>|

<span data-ttu-id="7bb7e-258">Bu olay hiçbir olay verisine sahip değil.</span><span class="sxs-lookup"><span data-stu-id="7bb7e-258">This event does not have any event data.</span></span>

## <a name="gcsuspendeeend_v1-event"></a><span data-ttu-id="7bb7e-259">GCSuspendEEEnd_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="7bb7e-259">GCSuspendEEEnd_V1 event</span></span>

<span data-ttu-id="7bb7e-260">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="7bb7e-260">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="7bb7e-261">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="7bb7e-261">Keyword for raising the event</span></span>|<span data-ttu-id="7bb7e-262">Level</span><span class="sxs-lookup"><span data-stu-id="7bb7e-262">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="7bb7e-263">`GCKeyword` 0x1</span><span class="sxs-lookup"><span data-stu-id="7bb7e-263">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="7bb7e-264">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="7bb7e-264">Informational (4)</span></span>|

<span data-ttu-id="7bb7e-265">Aşağıdaki tabloda olay bilgileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="7bb7e-265">The following table shows the event information:</span></span>

|<span data-ttu-id="7bb7e-266">Olay</span><span class="sxs-lookup"><span data-stu-id="7bb7e-266">Event</span></span>|<span data-ttu-id="7bb7e-267">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="7bb7e-267">Event ID</span></span>|<span data-ttu-id="7bb7e-268">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="7bb7e-268">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCSuspendEEEnd_V1`|<span data-ttu-id="7bb7e-269">8</span><span class="sxs-lookup"><span data-stu-id="7bb7e-269">8</span></span>|<span data-ttu-id="7bb7e-270">Çöp toplama için yürütme altyapısının askıya alınma sonu.</span><span class="sxs-lookup"><span data-stu-id="7bb7e-270">End of suspension of the execution engine for garbage collection.</span></span>|

<span data-ttu-id="7bb7e-271">Bu olay hiçbir olay verisine sahip değil.</span><span class="sxs-lookup"><span data-stu-id="7bb7e-271">This event does not have any event data.</span></span>

## <a name="gcsuspendeebegin_v1-event"></a><span data-ttu-id="7bb7e-272">GCSuspendEEBegin_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="7bb7e-272">GCSuspendEEBegin_V1 event</span></span>

<span data-ttu-id="7bb7e-273">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="7bb7e-273">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="7bb7e-274">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="7bb7e-274">Keyword for raising the event</span></span>|<span data-ttu-id="7bb7e-275">Level</span><span class="sxs-lookup"><span data-stu-id="7bb7e-275">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="7bb7e-276">`GCKeyword` 0x1</span><span class="sxs-lookup"><span data-stu-id="7bb7e-276">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="7bb7e-277">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="7bb7e-277">Informational (4)</span></span>|

<span data-ttu-id="7bb7e-278">Aşağıdaki tabloda olay bilgileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="7bb7e-278">The following table shows the event information:</span></span>

|<span data-ttu-id="7bb7e-279">Olay</span><span class="sxs-lookup"><span data-stu-id="7bb7e-279">Event</span></span>|<span data-ttu-id="7bb7e-280">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="7bb7e-280">Event ID</span></span>|<span data-ttu-id="7bb7e-281">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="7bb7e-281">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCSuspendEEBegin_V1`|<span data-ttu-id="7bb7e-282">8</span><span class="sxs-lookup"><span data-stu-id="7bb7e-282">8</span></span>|<span data-ttu-id="7bb7e-283">Çöp toplama için yürütme altyapısının askıya alınma başlangıcı.</span><span class="sxs-lookup"><span data-stu-id="7bb7e-283">Start of suspension of the execution engine for garbage collection.</span></span>|

|<span data-ttu-id="7bb7e-284">Alan adı</span><span class="sxs-lookup"><span data-stu-id="7bb7e-284">Field name</span></span>|<span data-ttu-id="7bb7e-285">Veri türü</span><span class="sxs-lookup"><span data-stu-id="7bb7e-285">Data type</span></span>|<span data-ttu-id="7bb7e-286">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7bb7e-286">Description</span></span>|
|----------------|---------------|-----------------|
|`Count`|`win:UInt32`|<span data-ttu-id="7bb7e-287">*N*. çöp toplama.</span><span class="sxs-lookup"><span data-stu-id="7bb7e-287">The *n* th garbage collection.</span></span>|
|`Reason`|`win:UInt32`|<span data-ttu-id="7bb7e-288">EE askıya alma nedeni.</span><span class="sxs-lookup"><span data-stu-id="7bb7e-288">Reason for EE suspension.</span></span><br/><br/><span data-ttu-id="7bb7e-289">`0x0`: Diğerleri için askıya al</span><span class="sxs-lookup"><span data-stu-id="7bb7e-289">`0x0`: Suspend for Other</span></span><br/><br/><span data-ttu-id="7bb7e-290">`0x1`: GC için askıya alın.</span><span class="sxs-lookup"><span data-stu-id="7bb7e-290">`0x1`: Suspend for GC.</span></span><br/><br/><span data-ttu-id="7bb7e-291">`0x2`: AppDomain kapatması için askıya al.</span><span class="sxs-lookup"><span data-stu-id="7bb7e-291">`0x2`: Suspend for AppDomain shutdown.</span></span><br/><br/><span data-ttu-id="7bb7e-292">`0x3`: Kod alma için askıya al.</span><span class="sxs-lookup"><span data-stu-id="7bb7e-292">`0x3`: Suspend for code pitching.</span></span><br/><br/><span data-ttu-id="7bb7e-293">`0x4`: Kapat için askıya al.</span><span class="sxs-lookup"><span data-stu-id="7bb7e-293">`0x4`: Suspend for shutdown.</span></span><br/><br/><span data-ttu-id="7bb7e-294">`0x5`: Hata ayıklayıcı için askıya al.</span><span class="sxs-lookup"><span data-stu-id="7bb7e-294">`0x5`: Suspend for debugger.</span></span><br/><br/><span data-ttu-id="7bb7e-295">`0x6`: GC hazırlığı için askıya alın.</span><span class="sxs-lookup"><span data-stu-id="7bb7e-295">`0x6`: Suspend for GC Prep.</span></span><br/><br/><span data-ttu-id="7bb7e-296">`0x7`: Hata ayıklayıcı tarama için askıya al</span><span class="sxs-lookup"><span data-stu-id="7bb7e-296">`0x7`: Suspend for debugger sweep</span></span>|

## <a name="gcallocationtick_v3-event"></a><span data-ttu-id="7bb7e-297">GCAllocationTick_V3 olayı</span><span class="sxs-lookup"><span data-stu-id="7bb7e-297">GCAllocationTick_V3 event</span></span>

<span data-ttu-id="7bb7e-298">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="7bb7e-298">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="7bb7e-299">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="7bb7e-299">Keyword for raising the event</span></span>|<span data-ttu-id="7bb7e-300">Level</span><span class="sxs-lookup"><span data-stu-id="7bb7e-300">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="7bb7e-301">`GCKeyword` 0x1</span><span class="sxs-lookup"><span data-stu-id="7bb7e-301">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="7bb7e-302">Verbose (4)</span><span class="sxs-lookup"><span data-stu-id="7bb7e-302">Verbose (4)</span></span>|

<span data-ttu-id="7bb7e-303">Aşağıdaki tabloda olay bilgileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="7bb7e-303">The following table shows the event information:</span></span>

|<span data-ttu-id="7bb7e-304">Olay</span><span class="sxs-lookup"><span data-stu-id="7bb7e-304">Event</span></span>|<span data-ttu-id="7bb7e-305">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="7bb7e-305">Event ID</span></span>|<span data-ttu-id="7bb7e-306">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="7bb7e-306">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCAllocationTick_V3`|<span data-ttu-id="7bb7e-307">10</span><span class="sxs-lookup"><span data-stu-id="7bb7e-307">10</span></span>|<span data-ttu-id="7bb7e-308">Yaklaşık 100 KB ayrıldığı her seferinde.</span><span class="sxs-lookup"><span data-stu-id="7bb7e-308">Each time approximately 100 KB is allocated.</span></span>|

<span data-ttu-id="7bb7e-309">Aşağıdaki tabloda olay verileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="7bb7e-309">The following table shows the event data:</span></span>

|<span data-ttu-id="7bb7e-310">Alan adı</span><span class="sxs-lookup"><span data-stu-id="7bb7e-310">Field name</span></span>|<span data-ttu-id="7bb7e-311">Veri türü</span><span class="sxs-lookup"><span data-stu-id="7bb7e-311">Data type</span></span>|<span data-ttu-id="7bb7e-312">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7bb7e-312">Description</span></span>|
|----------------|---------------|-----------------|
|`AllocationAmount`|`win:UInt32`|<span data-ttu-id="7bb7e-313">Bayt cinsinden ayırma boyutu.</span><span class="sxs-lookup"><span data-stu-id="7bb7e-313">The allocation size, in bytes.</span></span> <span data-ttu-id="7bb7e-314">Bu değer, ULONG 'un uzunluğundan (4.294.967.295 bayt) daha az olan ayırmalar için doğrudur.</span><span class="sxs-lookup"><span data-stu-id="7bb7e-314">This value is accurate for allocations that are less than the length of a ULONG (4,294,967,295 bytes).</span></span> <span data-ttu-id="7bb7e-315">Ayırma daha büyükse, bu alan kesilmiş bir değer içerir.</span><span class="sxs-lookup"><span data-stu-id="7bb7e-315">If the allocation is greater, this field contains a truncated value.</span></span> <span data-ttu-id="7bb7e-316">`AllocationAmount64`Çok büyük ayırmalar için kullanın.</span><span class="sxs-lookup"><span data-stu-id="7bb7e-316">Use `AllocationAmount64` for very large allocations.</span></span>|
|`AllocationKind`|`win:UInt32`|<span data-ttu-id="7bb7e-317">`0x0` -Küçük nesne ayırma (ayırma küçük nesne yığınında).</span><span class="sxs-lookup"><span data-stu-id="7bb7e-317">`0x0` - Small object allocation (allocation is in small object heap).</span></span><br /><br /> <span data-ttu-id="7bb7e-318">`0x1` -Büyük nesne ayırma (ayırma büyük nesne yığınında).</span><span class="sxs-lookup"><span data-stu-id="7bb7e-318">`0x1` - Large object allocation (allocation is in large object heap).</span></span>|
|`AllocationAmount64`|`win:UInt64`|<span data-ttu-id="7bb7e-319">Bayt cinsinden ayırma boyutu.</span><span class="sxs-lookup"><span data-stu-id="7bb7e-319">The allocation size, in bytes.</span></span> <span data-ttu-id="7bb7e-320">Bu değer, çok büyük ayırmalar için doğrudur.</span><span class="sxs-lookup"><span data-stu-id="7bb7e-320">This value is accurate for very large allocations.</span></span>|
|`TypeId`|`win:Pointer`|<span data-ttu-id="7bb7e-321">MethodTable 'ın adresi.</span><span class="sxs-lookup"><span data-stu-id="7bb7e-321">The address of the MethodTable.</span></span> <span data-ttu-id="7bb7e-322">Bu olay sırasında ayrılan çeşitli nesne türleri olduğunda, bu, ayrılan son nesneye (100 KB eşiğinin aşılmasına neden olan nesne) karşılık gelen MethodTable 'ın adresidir.</span><span class="sxs-lookup"><span data-stu-id="7bb7e-322">When there are several types of objects that were allocated during this event, this is the address of the MethodTable that corresponds to the last object allocated (the object that caused the 100 KB threshold to be exceeded).</span></span>|
|`TypeName`|`win:UnicodeString`|<span data-ttu-id="7bb7e-323">Ayrılan türün adı.</span><span class="sxs-lookup"><span data-stu-id="7bb7e-323">The name of the type that was allocated.</span></span> <span data-ttu-id="7bb7e-324">Bu olay sırasında ayrılan çeşitli nesne türleri varsa, bu, ayrılan son nesnenin türüdür (100 KB eşiğinin aşılmasına neden olan nesne).</span><span class="sxs-lookup"><span data-stu-id="7bb7e-324">When there are several types of objects that were allocated during this event, this is the type of the last object allocated (the object that caused the 100 KB threshold to be exceeded).</span></span>|
|`HeapIndex`|`win:UInt32`|<span data-ttu-id="7bb7e-325">Nesnenin ayrıldığı yığın.</span><span class="sxs-lookup"><span data-stu-id="7bb7e-325">The heap where the object was allocated.</span></span> <span data-ttu-id="7bb7e-326">Bu değer, iş istasyonu atık toplama ile çalıştırılırken 0 (sıfır) değeridir.</span><span class="sxs-lookup"><span data-stu-id="7bb7e-326">This value is 0 (zero) when running with workstation garbage collection.</span></span>|
|`Address`|`win:Pointer`|<span data-ttu-id="7bb7e-327">Son ayrılan nesnenin adresi.</span><span class="sxs-lookup"><span data-stu-id="7bb7e-327">The address of the last allocated object.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="7bb7e-328">CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="7bb7e-328">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="gccreateconcurrentthread_v1-event"></a><span data-ttu-id="7bb7e-329">GCCreateConcurrentThread_V1 Olayı</span><span class="sxs-lookup"><span data-stu-id="7bb7e-329">GCCreateConcurrentThread_V1 event</span></span>

<span data-ttu-id="7bb7e-330">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="7bb7e-330">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="7bb7e-331">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="7bb7e-331">Keyword for raising the event</span></span>|<span data-ttu-id="7bb7e-332">Level</span><span class="sxs-lookup"><span data-stu-id="7bb7e-332">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="7bb7e-333">`GCKeyword` 0x1</span><span class="sxs-lookup"><span data-stu-id="7bb7e-333">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="7bb7e-334">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="7bb7e-334">Informational (4)</span></span>|
|<span data-ttu-id="7bb7e-335">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="7bb7e-335">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="7bb7e-336">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="7bb7e-336">Informational (4)</span></span>|

<span data-ttu-id="7bb7e-337">Aşağıdaki tabloda olay bilgileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="7bb7e-337">The following table shows the event information:</span></span>

|<span data-ttu-id="7bb7e-338">Olay</span><span class="sxs-lookup"><span data-stu-id="7bb7e-338">Event</span></span>|<span data-ttu-id="7bb7e-339">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="7bb7e-339">Event ID</span></span>|<span data-ttu-id="7bb7e-340">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="7bb7e-340">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCCreateConcurrentThread_V1`|<span data-ttu-id="7bb7e-341">11</span><span class="sxs-lookup"><span data-stu-id="7bb7e-341">11</span></span>|<span data-ttu-id="7bb7e-342">Eşzamanlı atık toplama iş parçacığı oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="7bb7e-342">Concurrent garbage collection thread was created.</span></span>|

<span data-ttu-id="7bb7e-343">Bu olay hiçbir olay verisine sahip değil.</span><span class="sxs-lookup"><span data-stu-id="7bb7e-343">This event does not have any event data.</span></span>

## <a name="gcterminateconcurrentthread_v1-event"></a><span data-ttu-id="7bb7e-344">GCTerminateConcurrentThread_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="7bb7e-344">GCTerminateConcurrentThread_V1 event</span></span>

<span data-ttu-id="7bb7e-345">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="7bb7e-345">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="7bb7e-346">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="7bb7e-346">Keyword for raising the event</span></span>|<span data-ttu-id="7bb7e-347">Level</span><span class="sxs-lookup"><span data-stu-id="7bb7e-347">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="7bb7e-348">`GCKeyword` 0x1</span><span class="sxs-lookup"><span data-stu-id="7bb7e-348">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="7bb7e-349">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="7bb7e-349">Informational (4)</span></span>|
|<span data-ttu-id="7bb7e-350">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="7bb7e-350">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="7bb7e-351">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="7bb7e-351">Informational (4)</span></span>|

<span data-ttu-id="7bb7e-352">Aşağıdaki tabloda olay bilgileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="7bb7e-352">The following table shows the event information:</span></span>

|<span data-ttu-id="7bb7e-353">Olay</span><span class="sxs-lookup"><span data-stu-id="7bb7e-353">Event</span></span>|<span data-ttu-id="7bb7e-354">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="7bb7e-354">Event ID</span></span>|<span data-ttu-id="7bb7e-355">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="7bb7e-355">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCTerminateConcurrentThread_V1`|<span data-ttu-id="7bb7e-356">12</span><span class="sxs-lookup"><span data-stu-id="7bb7e-356">12</span></span>|<span data-ttu-id="7bb7e-357">Eşzamanlı atık toplama iş parçacığı sonlandırıldı.</span><span class="sxs-lookup"><span data-stu-id="7bb7e-357">Concurrent garbage collection thread was terminated.</span></span>|

<span data-ttu-id="7bb7e-358">Bu olay hiçbir olay verisine sahip değil.</span><span class="sxs-lookup"><span data-stu-id="7bb7e-358">This event does not have any event data.</span></span>

## <a name="gcfinalizersbegin_v1-event"></a><span data-ttu-id="7bb7e-359">GCFinalizersBegin_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="7bb7e-359">GCFinalizersBegin_V1 event</span></span>

<span data-ttu-id="7bb7e-360">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="7bb7e-360">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="7bb7e-361">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="7bb7e-361">Keyword for raising the event</span></span>|<span data-ttu-id="7bb7e-362">Level</span><span class="sxs-lookup"><span data-stu-id="7bb7e-362">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="7bb7e-363">`GCKeyword` 0x1</span><span class="sxs-lookup"><span data-stu-id="7bb7e-363">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="7bb7e-364">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="7bb7e-364">Informational (4)</span></span>|

<span data-ttu-id="7bb7e-365">Aşağıdaki tabloda olay bilgileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="7bb7e-365">The following table shows the event information:</span></span>

|<span data-ttu-id="7bb7e-366">Olay</span><span class="sxs-lookup"><span data-stu-id="7bb7e-366">Event</span></span>|<span data-ttu-id="7bb7e-367">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="7bb7e-367">Event ID</span></span>|<span data-ttu-id="7bb7e-368">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="7bb7e-368">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCFinalizersBegin_V1`|<span data-ttu-id="7bb7e-369">14</span><span class="sxs-lookup"><span data-stu-id="7bb7e-369">14</span></span>|<span data-ttu-id="7bb7e-370">Sonlandırıcıları çalıştırmanın başlangıcı.</span><span class="sxs-lookup"><span data-stu-id="7bb7e-370">The start of running finalizers.</span></span>|

<span data-ttu-id="7bb7e-371">Bu olay hiçbir olay verisine sahip değil.</span><span class="sxs-lookup"><span data-stu-id="7bb7e-371">This event does not have any event data.</span></span>

## <a name="gcfinalizersend_v1-event"></a><span data-ttu-id="7bb7e-372">GCFinalizersEnd_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="7bb7e-372">GCFinalizersEnd_V1 event</span></span>

<span data-ttu-id="7bb7e-373">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="7bb7e-373">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="7bb7e-374">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="7bb7e-374">Keyword for raising the event</span></span>|<span data-ttu-id="7bb7e-375">Level</span><span class="sxs-lookup"><span data-stu-id="7bb7e-375">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="7bb7e-376">`GCKeyword` 0x1</span><span class="sxs-lookup"><span data-stu-id="7bb7e-376">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="7bb7e-377">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="7bb7e-377">Informational (4)</span></span>|

<span data-ttu-id="7bb7e-378">Aşağıdaki tabloda olay bilgileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="7bb7e-378">The following table shows the event information:</span></span>

|<span data-ttu-id="7bb7e-379">Olay</span><span class="sxs-lookup"><span data-stu-id="7bb7e-379">Event</span></span>|<span data-ttu-id="7bb7e-380">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="7bb7e-380">Event ID</span></span>|<span data-ttu-id="7bb7e-381">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="7bb7e-381">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCFinalizersEnd_V1`|<span data-ttu-id="7bb7e-382">13</span><span class="sxs-lookup"><span data-stu-id="7bb7e-382">13</span></span>|<span data-ttu-id="7bb7e-383">Sonlandırıcılardan çalıştırmanın sonu.</span><span class="sxs-lookup"><span data-stu-id="7bb7e-383">The end of running finalizers.</span></span>|

<span data-ttu-id="7bb7e-384">Aşağıdaki tabloda olay verileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="7bb7e-384">The following table shows the event data:</span></span>

|<span data-ttu-id="7bb7e-385">Alan adı</span><span class="sxs-lookup"><span data-stu-id="7bb7e-385">Field name</span></span>|<span data-ttu-id="7bb7e-386">Veri türü</span><span class="sxs-lookup"><span data-stu-id="7bb7e-386">Data type</span></span>|<span data-ttu-id="7bb7e-387">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7bb7e-387">Description</span></span>|
|----------------|---------------|-----------------|
|`Count`|`win:UInt32`|<span data-ttu-id="7bb7e-388">Çalıştırılan sonlandırıcılar sayısı.</span><span class="sxs-lookup"><span data-stu-id="7bb7e-388">The number of finalizers that were run.</span></span>|
|`ClrInstanceID`|<span data-ttu-id="7bb7e-389">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="7bb7e-389">win:UInt16</span></span>|<span data-ttu-id="7bb7e-390">CLR veya CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="7bb7e-390">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="setgchandle-event"></a><span data-ttu-id="7bb7e-391">SetGCHandle olayı</span><span class="sxs-lookup"><span data-stu-id="7bb7e-391">SetGCHandle event</span></span>

<span data-ttu-id="7bb7e-392">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="7bb7e-392">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="7bb7e-393">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="7bb7e-393">Keyword for raising the event</span></span>|<span data-ttu-id="7bb7e-394">Level</span><span class="sxs-lookup"><span data-stu-id="7bb7e-394">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="7bb7e-395">`GCHandleKeyword` 0x2</span><span class="sxs-lookup"><span data-stu-id="7bb7e-395">`GCHandleKeyword` (0x2)</span></span>|<span data-ttu-id="7bb7e-396">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="7bb7e-396">Informational (4)</span></span>|

<span data-ttu-id="7bb7e-397">Aşağıdaki tabloda olay bilgileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="7bb7e-397">The following table shows the event information:</span></span>

|<span data-ttu-id="7bb7e-398">Olay</span><span class="sxs-lookup"><span data-stu-id="7bb7e-398">Event</span></span>|<span data-ttu-id="7bb7e-399">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="7bb7e-399">Event ID</span></span>|<span data-ttu-id="7bb7e-400">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="7bb7e-400">Raised when</span></span>|
|-----------|--------------|-----------------|
|`SetGCHandle`|<span data-ttu-id="7bb7e-401">30</span><span class="sxs-lookup"><span data-stu-id="7bb7e-401">30</span></span>|<span data-ttu-id="7bb7e-402">GC tanıtıcısı ayarlandı.</span><span class="sxs-lookup"><span data-stu-id="7bb7e-402">A GC Handle has been set.</span></span>|

<span data-ttu-id="7bb7e-403">Aşağıdaki tabloda olay verileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="7bb7e-403">The following table shows the event data:</span></span>

|<span data-ttu-id="7bb7e-404">Alan adı</span><span class="sxs-lookup"><span data-stu-id="7bb7e-404">Field name</span></span>|<span data-ttu-id="7bb7e-405">Veri türü</span><span class="sxs-lookup"><span data-stu-id="7bb7e-405">Data type</span></span>|<span data-ttu-id="7bb7e-406">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7bb7e-406">Description</span></span>|
|----------------|---------------|-----------------|
|`HandleID`|`win:Pointer`|<span data-ttu-id="7bb7e-407">Ayrılmış tanıtıcının adresi.</span><span class="sxs-lookup"><span data-stu-id="7bb7e-407">The address of the allocated handle.</span></span>|
|`ObjectID`|`win:Pointer`|<span data-ttu-id="7bb7e-408">Tutamacı oluşturulan nesnenin adresi.</span><span class="sxs-lookup"><span data-stu-id="7bb7e-408">The address of the object whose handle was created.</span></span>|
|`Kind`|`win:UInt32`|<span data-ttu-id="7bb7e-409">Ayarlanan GC tanıtıcısının türü.</span><span class="sxs-lookup"><span data-stu-id="7bb7e-409">The type of GC handle that was set.</span></span> <br /><br /><span data-ttu-id="7bb7e-410">`0x0`: WeakShort</span><span class="sxs-lookup"><span data-stu-id="7bb7e-410">`0x0`: WeakShort</span></span> <br/><br/><span data-ttu-id="7bb7e-411">`0x1`: WeakLong</span><span class="sxs-lookup"><span data-stu-id="7bb7e-411">`0x1`: WeakLong</span></span> <br /><br /><span data-ttu-id="7bb7e-412">`0x2`: Strong</span><span class="sxs-lookup"><span data-stu-id="7bb7e-412">`0x2`: Strong</span></span> <br /><br /><span data-ttu-id="7bb7e-413">`0x3`: Sabitlenmiş</span><span class="sxs-lookup"><span data-stu-id="7bb7e-413">`0x3`: Pinned</span></span> <br /><br /><span data-ttu-id="7bb7e-414">`0x4`: Değişken</span><span class="sxs-lookup"><span data-stu-id="7bb7e-414">`0x4`: Variable</span></span><br /><br /><span data-ttu-id="7bb7e-415">`0x5`: Refsayılan</span><span class="sxs-lookup"><span data-stu-id="7bb7e-415">`0x5`: RefCounted</span></span> <br /><br /><span data-ttu-id="7bb7e-416">`0x6`: Bağımlı</span><span class="sxs-lookup"><span data-stu-id="7bb7e-416">`0x6`: Dependent</span></span><br /><br /><span data-ttu-id="7bb7e-417">`0x7`: Asyncpınlan</span><span class="sxs-lookup"><span data-stu-id="7bb7e-417">`0x7`: AsyncPinned</span></span><br /><br /><span data-ttu-id="7bb7e-418">`0x8`: SizedRef</span><span class="sxs-lookup"><span data-stu-id="7bb7e-418">`0x8`: SizedRef</span></span>|
|`Generation`|`win:UInt32`|<span data-ttu-id="7bb7e-419">Tutamacı oluşturulduğu nesnenin oluşturulması.</span><span class="sxs-lookup"><span data-stu-id="7bb7e-419">The generation of the object whose handle was created.</span></span>|
|`AppDomainID`|`win:UInt64`|<span data-ttu-id="7bb7e-420">AppDomain KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="7bb7e-420">The AppDomain ID.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="7bb7e-421">CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="7bb7e-421">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="destroygchandle-event"></a><span data-ttu-id="7bb7e-422">DestroyGCHandle olayı</span><span class="sxs-lookup"><span data-stu-id="7bb7e-422">DestroyGCHandle event</span></span>

<span data-ttu-id="7bb7e-423">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="7bb7e-423">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="7bb7e-424">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="7bb7e-424">Keyword for raising the event</span></span>|<span data-ttu-id="7bb7e-425">Level</span><span class="sxs-lookup"><span data-stu-id="7bb7e-425">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="7bb7e-426">`GCHandleKeyword` 0x2</span><span class="sxs-lookup"><span data-stu-id="7bb7e-426">`GCHandleKeyword` (0x2)</span></span>|<span data-ttu-id="7bb7e-427">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="7bb7e-427">Informational (4)</span></span>|

<span data-ttu-id="7bb7e-428">Aşağıdaki tabloda olay bilgileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="7bb7e-428">The following table shows the event information:</span></span>

|<span data-ttu-id="7bb7e-429">Olay</span><span class="sxs-lookup"><span data-stu-id="7bb7e-429">Event</span></span>|<span data-ttu-id="7bb7e-430">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="7bb7e-430">Event ID</span></span>|<span data-ttu-id="7bb7e-431">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="7bb7e-431">Raised when</span></span>|
|-----------|--------------|-----------------|
|`DestroyGCHandle`|<span data-ttu-id="7bb7e-432">31</span><span class="sxs-lookup"><span data-stu-id="7bb7e-432">31</span></span>|<span data-ttu-id="7bb7e-433">GC tanıtıcısı yok edilir.</span><span class="sxs-lookup"><span data-stu-id="7bb7e-433">A GC Handle is destroyed.</span></span>|

<span data-ttu-id="7bb7e-434">Aşağıdaki tabloda olay verileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="7bb7e-434">The following table shows the event data:</span></span>

|<span data-ttu-id="7bb7e-435">Alan adı</span><span class="sxs-lookup"><span data-stu-id="7bb7e-435">Field name</span></span>|<span data-ttu-id="7bb7e-436">Veri türü</span><span class="sxs-lookup"><span data-stu-id="7bb7e-436">Data type</span></span>|<span data-ttu-id="7bb7e-437">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7bb7e-437">Description</span></span>|
|----------------|---------------|-----------------|
|`HandleID`|`win:Pointer`|<span data-ttu-id="7bb7e-438">Yok etme tanıtıcısının adresi.</span><span class="sxs-lookup"><span data-stu-id="7bb7e-438">The address of the destroyed handle.</span></span>|
|`ClrInstanceID`|<span data-ttu-id="7bb7e-439">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="7bb7e-439">win:UInt16</span></span>|<span data-ttu-id="7bb7e-440">CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="7bb7e-440">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="pinobjectatgctime-event"></a><span data-ttu-id="7bb7e-441">PinObjectAtGCTime olayı</span><span class="sxs-lookup"><span data-stu-id="7bb7e-441">PinObjectAtGCTime event</span></span>

<span data-ttu-id="7bb7e-442">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="7bb7e-442">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="7bb7e-443">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="7bb7e-443">Keyword for raising the event</span></span>|<span data-ttu-id="7bb7e-444">Level</span><span class="sxs-lookup"><span data-stu-id="7bb7e-444">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="7bb7e-445">`GCKeyword` 0x1</span><span class="sxs-lookup"><span data-stu-id="7bb7e-445">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="7bb7e-446">Verbose (5)</span><span class="sxs-lookup"><span data-stu-id="7bb7e-446">Verbose (5)</span></span>|

<span data-ttu-id="7bb7e-447">Aşağıdaki tabloda olay bilgileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="7bb7e-447">The following table shows the event information:</span></span>

|<span data-ttu-id="7bb7e-448">Olay</span><span class="sxs-lookup"><span data-stu-id="7bb7e-448">Event</span></span>|<span data-ttu-id="7bb7e-449">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="7bb7e-449">Event ID</span></span>|<span data-ttu-id="7bb7e-450">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="7bb7e-450">Raised when</span></span>|
|-----------|--------------|-----------------|
|`PinObjectAtGCTime`|<span data-ttu-id="7bb7e-451">33</span><span class="sxs-lookup"><span data-stu-id="7bb7e-451">33</span></span>|<span data-ttu-id="7bb7e-452">GC sırasında bir nesne sabitlendi.</span><span class="sxs-lookup"><span data-stu-id="7bb7e-452">An object was pinned during a GC.</span></span>|

<span data-ttu-id="7bb7e-453">Aşağıdaki tabloda olay verileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="7bb7e-453">The following table shows the event data:</span></span>

|<span data-ttu-id="7bb7e-454">Alan adı</span><span class="sxs-lookup"><span data-stu-id="7bb7e-454">Field name</span></span>|<span data-ttu-id="7bb7e-455">Veri türü</span><span class="sxs-lookup"><span data-stu-id="7bb7e-455">Data type</span></span>|<span data-ttu-id="7bb7e-456">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7bb7e-456">Description</span></span>|
|----------------|---------------|-----------------|
|`HandleID`|`win:Pointer`|<span data-ttu-id="7bb7e-457">Tanıtıcının adresi.</span><span class="sxs-lookup"><span data-stu-id="7bb7e-457">The address of the handle.</span></span>|
|`ObjectID`|`win:Pointer`|<span data-ttu-id="7bb7e-458">Sabitlenmiş nesnenin adresi.</span><span class="sxs-lookup"><span data-stu-id="7bb7e-458">The address of the pinned object.</span></span>|
|`ObjectSize`|`win:UInt64`|<span data-ttu-id="7bb7e-459">Sabitlenmiş nesnenin boyutu.</span><span class="sxs-lookup"><span data-stu-id="7bb7e-459">The size of the pinned object.</span></span>|
|`TypeName`|`win:UnicodeString`|<span data-ttu-id="7bb7e-460">Sabitlenmiş nesnenin türünün adı.</span><span class="sxs-lookup"><span data-stu-id="7bb7e-460">The name of the type of the pinned object.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="7bb7e-461">CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="7bb7e-461">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="gctriggered-event"></a><span data-ttu-id="7bb7e-462">GCTriggered olayı</span><span class="sxs-lookup"><span data-stu-id="7bb7e-462">GCTriggered event</span></span>

<span data-ttu-id="7bb7e-463">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="7bb7e-463">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="7bb7e-464">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="7bb7e-464">Keyword for raising the event</span></span>|<span data-ttu-id="7bb7e-465">Level</span><span class="sxs-lookup"><span data-stu-id="7bb7e-465">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="7bb7e-466">`GCKeyword` 0x1</span><span class="sxs-lookup"><span data-stu-id="7bb7e-466">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="7bb7e-467">Verbose (5)</span><span class="sxs-lookup"><span data-stu-id="7bb7e-467">Verbose (5)</span></span>|

<span data-ttu-id="7bb7e-468">Aşağıdaki tabloda olay bilgileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="7bb7e-468">The following table shows the event information:</span></span>

|<span data-ttu-id="7bb7e-469">Olay</span><span class="sxs-lookup"><span data-stu-id="7bb7e-469">Event</span></span>|<span data-ttu-id="7bb7e-470">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="7bb7e-470">Event ID</span></span>|<span data-ttu-id="7bb7e-471">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="7bb7e-471">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCTriggered`|<span data-ttu-id="7bb7e-472">33</span><span class="sxs-lookup"><span data-stu-id="7bb7e-472">33</span></span>|<span data-ttu-id="7bb7e-473">GC tetiklendi.</span><span class="sxs-lookup"><span data-stu-id="7bb7e-473">A GC has been triggered.</span></span>|

<span data-ttu-id="7bb7e-474">Aşağıdaki tabloda olay verileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="7bb7e-474">The following table shows the event data:</span></span>

|<span data-ttu-id="7bb7e-475">Alan adı</span><span class="sxs-lookup"><span data-stu-id="7bb7e-475">Field name</span></span>|<span data-ttu-id="7bb7e-476">Veri türü</span><span class="sxs-lookup"><span data-stu-id="7bb7e-476">Data type</span></span>|<span data-ttu-id="7bb7e-477">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7bb7e-477">Description</span></span>|
|----------------|---------------|-----------------|
|`Reason`|`win:UInt32`|<span data-ttu-id="7bb7e-478">GC 'nin tetiklenme nedeni.</span><span class="sxs-lookup"><span data-stu-id="7bb7e-478">The reason a GC was triggered.</span></span><br/><br/><span data-ttu-id="7bb7e-479">`0x0`: AllocSmall</span><span class="sxs-lookup"><span data-stu-id="7bb7e-479">`0x0`: AllocSmall</span></span><br/><br/><span data-ttu-id="7bb7e-480">`0x1`: Alınmış</span><span class="sxs-lookup"><span data-stu-id="7bb7e-480">`0x1`: Induced</span></span> <br/><br/><span data-ttu-id="7bb7e-481">`0x2`: LowMemory</span><span class="sxs-lookup"><span data-stu-id="7bb7e-481">`0x2`: LowMemory</span></span> <br/><br/><span data-ttu-id="7bb7e-482">`0x3`: Boş</span><span class="sxs-lookup"><span data-stu-id="7bb7e-482">`0x3`: Empty</span></span> <br/><br/><span data-ttu-id="7bb7e-483">`0x4`: AllocLarge</span><span class="sxs-lookup"><span data-stu-id="7bb7e-483">`0x4`: AllocLarge</span></span> <br/><br/><span data-ttu-id="7bb7e-484">`0x5`: OutOfSpaceSmallObjectHeap</span><span class="sxs-lookup"><span data-stu-id="7bb7e-484">`0x5`: OutOfSpaceSmallObjectHeap</span></span> <br/><br/><span data-ttu-id="7bb7e-485">`0x6`: OutOfSpaceLargeObjectHeap</span><span class="sxs-lookup"><span data-stu-id="7bb7e-485">`0x6`: OutOfSpaceLargeObjectHeap</span></span> <br/><br/><span data-ttu-id="7bb7e-486">`0x7`:InducedNoForce</span><span class="sxs-lookup"><span data-stu-id="7bb7e-486">`0x7`:InducedNoForce</span></span> <br/><br/><span data-ttu-id="7bb7e-487">`0x8`: Stres</span><span class="sxs-lookup"><span data-stu-id="7bb7e-487">`0x8`: Stress</span></span> <br/><br/><span data-ttu-id="7bb7e-488">`0x9`: Endücedlowmemory</span><span class="sxs-lookup"><span data-stu-id="7bb7e-488">`0x9`: InducedLowMemory</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="7bb7e-489">CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="7bb7e-489">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="increasememorypressure-event"></a><span data-ttu-id="7bb7e-490">Increasememorypresbir olay</span><span class="sxs-lookup"><span data-stu-id="7bb7e-490">IncreaseMemoryPressure event</span></span>

<span data-ttu-id="7bb7e-491">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="7bb7e-491">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="7bb7e-492">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="7bb7e-492">Keyword for raising the event</span></span>|<span data-ttu-id="7bb7e-493">Level</span><span class="sxs-lookup"><span data-stu-id="7bb7e-493">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="7bb7e-494">`GCKeyword` 0x1</span><span class="sxs-lookup"><span data-stu-id="7bb7e-494">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="7bb7e-495">Bilgi (4)</span><span class="sxs-lookup"><span data-stu-id="7bb7e-495">Information (4)</span></span>|

<span data-ttu-id="7bb7e-496">Aşağıdaki tabloda olay bilgileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="7bb7e-496">The following table shows the event information:</span></span>

|<span data-ttu-id="7bb7e-497">Olay</span><span class="sxs-lookup"><span data-stu-id="7bb7e-497">Event</span></span>|<span data-ttu-id="7bb7e-498">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="7bb7e-498">Event ID</span></span>|<span data-ttu-id="7bb7e-499">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="7bb7e-499">Raised when</span></span>|
|----------------|---------------|-----------------|
|`IncreaseMemoryPressure`|<span data-ttu-id="7bb7e-500">200</span><span class="sxs-lookup"><span data-stu-id="7bb7e-500">200</span></span>|<span data-ttu-id="7bb7e-501">Bellek baskısı arttı.</span><span class="sxs-lookup"><span data-stu-id="7bb7e-501">Memory pressure was increased.</span></span>|

<span data-ttu-id="7bb7e-502">Aşağıdaki tabloda olay verileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="7bb7e-502">The following table shows the event data:</span></span>

|<span data-ttu-id="7bb7e-503">Alan Adı</span><span class="sxs-lookup"><span data-stu-id="7bb7e-503">Field Name</span></span>|<span data-ttu-id="7bb7e-504">Veri türü</span><span class="sxs-lookup"><span data-stu-id="7bb7e-504">Data type</span></span>|<span data-ttu-id="7bb7e-505">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7bb7e-505">Description</span></span>|
|----------------|---------------|-----------------|
|`ClrInstanceID`|<span data-ttu-id="7bb7e-506">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="7bb7e-506">win:UInt16</span></span>|<span data-ttu-id="7bb7e-507">CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="7bb7e-507">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="decreasememorypressure-event"></a><span data-ttu-id="7bb7e-508">DecreaseMemoryPressure olayı</span><span class="sxs-lookup"><span data-stu-id="7bb7e-508">DecreaseMemoryPressure event</span></span>

<span data-ttu-id="7bb7e-509">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="7bb7e-509">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="7bb7e-510">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="7bb7e-510">Keyword for raising the event</span></span>|<span data-ttu-id="7bb7e-511">Level</span><span class="sxs-lookup"><span data-stu-id="7bb7e-511">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="7bb7e-512">`GCKeyword` 0x1</span><span class="sxs-lookup"><span data-stu-id="7bb7e-512">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="7bb7e-513">Bilgi (4)</span><span class="sxs-lookup"><span data-stu-id="7bb7e-513">Information (4)</span></span>|

<span data-ttu-id="7bb7e-514">Aşağıdaki tabloda olay bilgileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="7bb7e-514">The following table shows the event information:</span></span>

|<span data-ttu-id="7bb7e-515">Olay</span><span class="sxs-lookup"><span data-stu-id="7bb7e-515">Event</span></span>|<span data-ttu-id="7bb7e-516">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="7bb7e-516">Event ID</span></span>|<span data-ttu-id="7bb7e-517">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="7bb7e-517">Raised when</span></span>|
|----------------|---------------|-----------------|
|`DecreaseMemoryPressure`|<span data-ttu-id="7bb7e-518">201</span><span class="sxs-lookup"><span data-stu-id="7bb7e-518">201</span></span>|<span data-ttu-id="7bb7e-519">Bellek baskısı azaltılmıştı.</span><span class="sxs-lookup"><span data-stu-id="7bb7e-519">Memory pressure was decreased.</span></span>|

<span data-ttu-id="7bb7e-520">Aşağıdaki tabloda olay verileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="7bb7e-520">The following table shows the event data:</span></span>

|<span data-ttu-id="7bb7e-521">Alan Adı</span><span class="sxs-lookup"><span data-stu-id="7bb7e-521">Field Name</span></span>|<span data-ttu-id="7bb7e-522">Veri türü</span><span class="sxs-lookup"><span data-stu-id="7bb7e-522">Data type</span></span>|<span data-ttu-id="7bb7e-523">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7bb7e-523">Description</span></span>|
|----------------|---------------|-----------------|
|`BytesFreed`|`win:UInt32`|<span data-ttu-id="7bb7e-524">Serbest bırakılan bayt.</span><span class="sxs-lookup"><span data-stu-id="7bb7e-524">Bytes freed.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="7bb7e-525">CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="7bb7e-525">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="gcmarkwithtype-event"></a><span data-ttu-id="7bb7e-526">GCMarkWithType olayı</span><span class="sxs-lookup"><span data-stu-id="7bb7e-526">GCMarkWithType event</span></span>

<span data-ttu-id="7bb7e-527">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="7bb7e-527">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="7bb7e-528">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="7bb7e-528">Keyword for raising the event</span></span>|<span data-ttu-id="7bb7e-529">Level</span><span class="sxs-lookup"><span data-stu-id="7bb7e-529">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="7bb7e-530">`GCKeyword` 0x1</span><span class="sxs-lookup"><span data-stu-id="7bb7e-530">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="7bb7e-531">Bilgi (4)</span><span class="sxs-lookup"><span data-stu-id="7bb7e-531">Information (4)</span></span>|

<span data-ttu-id="7bb7e-532">Aşağıdaki tabloda olay bilgileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="7bb7e-532">The following table shows the event information:</span></span>

|<span data-ttu-id="7bb7e-533">Olay</span><span class="sxs-lookup"><span data-stu-id="7bb7e-533">Event</span></span>|<span data-ttu-id="7bb7e-534">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="7bb7e-534">Event ID</span></span>|<span data-ttu-id="7bb7e-535">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="7bb7e-535">Raised when</span></span>|
|----------------|---------------|-----------------|
|`GCMarkWithType`|<span data-ttu-id="7bb7e-536">202</span><span class="sxs-lookup"><span data-stu-id="7bb7e-536">202</span></span>|<span data-ttu-id="7bb7e-537">GC işareti aşamasında bir GC kökü işaretlendi.</span><span class="sxs-lookup"><span data-stu-id="7bb7e-537">A GC root has been marked during GC mark phase.</span></span>|

<span data-ttu-id="7bb7e-538">Aşağıdaki tabloda olay verileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="7bb7e-538">The following table shows the event data:</span></span>

|<span data-ttu-id="7bb7e-539">Alan Adı</span><span class="sxs-lookup"><span data-stu-id="7bb7e-539">Field Name</span></span>|<span data-ttu-id="7bb7e-540">Veri türü</span><span class="sxs-lookup"><span data-stu-id="7bb7e-540">Data type</span></span>|<span data-ttu-id="7bb7e-541">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7bb7e-541">Description</span></span>|
|----------------|---------------|-----------------|
|`HeapNum`|`win:UInt32`|<span data-ttu-id="7bb7e-542">Yığın numarası.</span><span class="sxs-lookup"><span data-stu-id="7bb7e-542">The heap number.</span></span>|
|`ClrInstanceID`|<span data-ttu-id="7bb7e-543">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="7bb7e-543">win:UInt16</span></span>|<span data-ttu-id="7bb7e-544">CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="7bb7e-544">Unique ID for the instance of CoreCLR.</span></span>|
|`Type`|`win:UInt32`|<span data-ttu-id="7bb7e-545">GC kök türü.</span><span class="sxs-lookup"><span data-stu-id="7bb7e-545">The GC root type.</span></span><br/><br/><span data-ttu-id="7bb7e-546">`0x0`: Yığın</span><span class="sxs-lookup"><span data-stu-id="7bb7e-546">`0x0`: Stack</span></span><br/><br/><span data-ttu-id="7bb7e-547">`0x1`: Sonlandırıcı</span><span class="sxs-lookup"><span data-stu-id="7bb7e-547">`0x1`: Finalizer</span></span><br/><br/><span data-ttu-id="7bb7e-548">`0x2`: Tanıtıcı</span><span class="sxs-lookup"><span data-stu-id="7bb7e-548">`0x2`: Handle</span></span><br/><br/><span data-ttu-id="7bb7e-549">`0x3`: Daha eski</span><span class="sxs-lookup"><span data-stu-id="7bb7e-549">`0x3`: Older</span></span><br/><br/><span data-ttu-id="7bb7e-550">`0x4`: SizedRef</span><span class="sxs-lookup"><span data-stu-id="7bb7e-550">`0x4`: SizedRef</span></span><br/><br/><span data-ttu-id="7bb7e-551">`0x5`: Taşma</span><span class="sxs-lookup"><span data-stu-id="7bb7e-551">`0x5`: Overflow</span></span><br/><br/>|
|`Bytes`|`win:UInt64`|<span data-ttu-id="7bb7e-552">İşaretlenmiş baytların sayısı.</span><span class="sxs-lookup"><span data-stu-id="7bb7e-552">The number of bytes marked.</span></span>|

## <a name="gcjoin_v2-event"></a><span data-ttu-id="7bb7e-553">GCJoin_V2 olayı</span><span class="sxs-lookup"><span data-stu-id="7bb7e-553">GCJoin_V2 event</span></span>

<span data-ttu-id="7bb7e-554">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="7bb7e-554">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="7bb7e-555">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="7bb7e-555">Keyword for raising the event</span></span>|<span data-ttu-id="7bb7e-556">Level</span><span class="sxs-lookup"><span data-stu-id="7bb7e-556">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="7bb7e-557">`GCKeyword` 0x1</span><span class="sxs-lookup"><span data-stu-id="7bb7e-557">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="7bb7e-558">Verbose (5)</span><span class="sxs-lookup"><span data-stu-id="7bb7e-558">Verbose (5)</span></span>|

<span data-ttu-id="7bb7e-559">Aşağıdaki tabloda olay bilgileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="7bb7e-559">The following table shows the event information:</span></span>

|<span data-ttu-id="7bb7e-560">Olay</span><span class="sxs-lookup"><span data-stu-id="7bb7e-560">Event</span></span>|<span data-ttu-id="7bb7e-561">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="7bb7e-561">Event ID</span></span>|<span data-ttu-id="7bb7e-562">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="7bb7e-562">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCJoin_V2`|<span data-ttu-id="7bb7e-563">203</span><span class="sxs-lookup"><span data-stu-id="7bb7e-563">203</span></span>|<span data-ttu-id="7bb7e-564">Birleştirilmiş bir GC iş parçacığı.</span><span class="sxs-lookup"><span data-stu-id="7bb7e-564">A GC thread joined.</span></span>|

<span data-ttu-id="7bb7e-565">Aşağıdaki tabloda olay verileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="7bb7e-565">The following table shows the event data:</span></span>

|<span data-ttu-id="7bb7e-566">Alan adı</span><span class="sxs-lookup"><span data-stu-id="7bb7e-566">Field name</span></span>|<span data-ttu-id="7bb7e-567">Veri türü</span><span class="sxs-lookup"><span data-stu-id="7bb7e-567">Data type</span></span>|<span data-ttu-id="7bb7e-568">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7bb7e-568">Description</span></span>|
|----------------|---------------|-----------------|
|`Heap`|`win:UInt32`|<span data-ttu-id="7bb7e-569">Yığın numarası</span><span class="sxs-lookup"><span data-stu-id="7bb7e-569">The heap number</span></span>|
|`JoinTime`|`win:UInt32`|<span data-ttu-id="7bb7e-570">Bu olayın birleştirmenin başlangıcında mi, yoksa bir birleşimin sonunda mi tetiklendiğini belirtir (JOIN `0x0` için, `0x1` JOIN End for JOIN için)</span><span class="sxs-lookup"><span data-stu-id="7bb7e-570">Indicates whether this event is fired at the start of a join or end of a join (`0x0` for join start, `0x1` for join end)</span></span>|
|`JoinType`|`win:UInt32`|<span data-ttu-id="7bb7e-571">JOIN türü.</span><span class="sxs-lookup"><span data-stu-id="7bb7e-571">The join type.</span></span> <br/><br/><span data-ttu-id="7bb7e-572">`0x0`: Son ekleme</span><span class="sxs-lookup"><span data-stu-id="7bb7e-572">`0x0`: Last Join</span></span><br/><br/><span data-ttu-id="7bb7e-573">`0x1`: Birleştir</span><span class="sxs-lookup"><span data-stu-id="7bb7e-573">`0x1`: Join</span></span> <br/><br/><span data-ttu-id="7bb7e-574">`0x2`: Yeniden Başlat</span><span class="sxs-lookup"><span data-stu-id="7bb7e-574">`0x2`: Restart</span></span> <br/><br/><span data-ttu-id="7bb7e-575">`0x3`: İlk olarak katılmayı geri çevir</span><span class="sxs-lookup"><span data-stu-id="7bb7e-575">`0x3`: First Reverse Join</span></span><br/><br/><span data-ttu-id="7bb7e-576">`0x4`: Ters Birleştir</span><span class="sxs-lookup"><span data-stu-id="7bb7e-576">`0x4`: Reverse Join</span></span><br/><br/>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="7bb7e-577">CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="7bb7e-577">Unique ID for the instance of CoreCLR.</span></span>|
