---
title: ThreadPool çalışma zamanı olayları
description: .NET Core 'da iş parçacığı havuzu hakkında tanılama bilgilerini toplayacak .NET Runtime iş parçacığı havuzu olayları bölümüne bakın. İş parçacığı havuzu olayları, çalışan iş parçacığı havuzu olayları veya g/ç iş parçacığı havuzu olaylardır.
ms.date: 11/13/2020
ms.topic: reference
helpviewer_keywords:
- ThreadPool events (CoreCLR)
- ETW, thread pool events (CoreCLR)
ms.openlocfilehash: cdd6041c5842d4922c60e33daf6db366f7d35327
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96590045"
---
# <a name="net-runtime-thread-pool-events"></a><span data-ttu-id="1f7dd-104">.NET çalışma zamanı iş parçacığı havuzu olayları</span><span class="sxs-lookup"><span data-stu-id="1f7dd-104">.NET runtime thread pool events</span></span>

<span data-ttu-id="1f7dd-105">Bu olaylar, ThreadPool içindeki çalışan ve g/ç iş parçacıkları hakkında bilgi toplar.</span><span class="sxs-lookup"><span data-stu-id="1f7dd-105">These events collect information about worker and I/O threads in the threadpool.</span></span> <span data-ttu-id="1f7dd-106">Bu olayların tanılama amacıyla nasıl kullanılacağı hakkında daha fazla bilgi için bkz. [.NET uygulamalarını günlüğe kaydetme ve izleme](../../core/diagnostics/logging-tracing.md)</span><span class="sxs-lookup"><span data-stu-id="1f7dd-106">For more information about how to use these events for diagnostic purposes, see [logging and tracing .NET applications](../../core/diagnostics/logging-tracing.md)</span></span>

## <a name="iothreadcreate_v1-event"></a><span data-ttu-id="1f7dd-107">IOThreadCreate_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="1f7dd-107">IOThreadCreate_V1 event</span></span>

 <span data-ttu-id="1f7dd-108">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1f7dd-108">The following table shows the keyword and level.</span></span>

|<span data-ttu-id="1f7dd-109">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="1f7dd-109">Keyword for raising the event</span></span>|<span data-ttu-id="1f7dd-110">Level</span><span class="sxs-lookup"><span data-stu-id="1f7dd-110">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="1f7dd-111">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="1f7dd-111">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="1f7dd-112">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="1f7dd-112">Informational (4)</span></span>|

 <span data-ttu-id="1f7dd-113">Aşağıdaki tabloda olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1f7dd-113">The following table shows the event information.</span></span>

|<span data-ttu-id="1f7dd-114">Olay</span><span class="sxs-lookup"><span data-stu-id="1f7dd-114">Event</span></span>|<span data-ttu-id="1f7dd-115">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="1f7dd-115">Event ID</span></span>|<span data-ttu-id="1f7dd-116">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="1f7dd-116">Raised when</span></span>|
|-----------------------------------|-----------|
|`IOThreadCreate_V1`|<span data-ttu-id="1f7dd-117">44</span><span class="sxs-lookup"><span data-stu-id="1f7dd-117">44</span></span>|<span data-ttu-id="1f7dd-118">İş parçacığı havuzunda bir g/ç iş parçacığı oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="1f7dd-118">An I/O thread is created in the thread pool.</span></span>|

 <span data-ttu-id="1f7dd-119">Aşağıdaki tabloda olay verileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1f7dd-119">The following table shows the event data.</span></span>

|<span data-ttu-id="1f7dd-120">Alan adı</span><span class="sxs-lookup"><span data-stu-id="1f7dd-120">Field name</span></span>|<span data-ttu-id="1f7dd-121">Veri türü</span><span class="sxs-lookup"><span data-stu-id="1f7dd-121">Data type</span></span>|<span data-ttu-id="1f7dd-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1f7dd-122">Description</span></span>|
|----------------|---------------|-----------------|
|`Count`|`win:UInt64`|<span data-ttu-id="1f7dd-123">Yeni oluşturulan iş parçacığı dahil olmak üzere g/ç iş parçacıklarının sayısı.</span><span class="sxs-lookup"><span data-stu-id="1f7dd-123">Number of I/O threads, including the newly created thread.</span></span>|
|`NumRetired`|`win:UInt64`|<span data-ttu-id="1f7dd-124">Kullanımdan kaldırılan çalışan iş parçacıklarının sayısı.</span><span class="sxs-lookup"><span data-stu-id="1f7dd-124">Number of retired worker threads.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="1f7dd-125">CLR veya CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="1f7dd-125">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="iothreadterminate_v1-event"></a><span data-ttu-id="1f7dd-126">IOThreadTerminate_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="1f7dd-126">IOThreadTerminate_V1 event</span></span>

 <span data-ttu-id="1f7dd-127">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir</span><span class="sxs-lookup"><span data-stu-id="1f7dd-127">The following table shows the keyword and level</span></span>

|<span data-ttu-id="1f7dd-128">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="1f7dd-128">Keyword for raising the event</span></span>|<span data-ttu-id="1f7dd-129">Level</span><span class="sxs-lookup"><span data-stu-id="1f7dd-129">Level</span></span>
|-----------------------------------|-----------
|<span data-ttu-id="1f7dd-130">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="1f7dd-130">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="1f7dd-131">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="1f7dd-131">Informational (4)</span></span>

 <span data-ttu-id="1f7dd-132">Aşağıdaki tabloda olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1f7dd-132">The following table shows the event information.</span></span>

|<span data-ttu-id="1f7dd-133">Olay</span><span class="sxs-lookup"><span data-stu-id="1f7dd-133">Event</span></span>|<span data-ttu-id="1f7dd-134">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="1f7dd-134">Event ID</span></span>|<span data-ttu-id="1f7dd-135">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="1f7dd-135">Raised when</span></span>|
|-----------|--------------|-----------------|
|`IOThreadTerminate`|<span data-ttu-id="1f7dd-136">45</span><span class="sxs-lookup"><span data-stu-id="1f7dd-136">45</span></span>|<span data-ttu-id="1f7dd-137">İş parçacığı havuzunda bir g/ç iş parçacığı sonlandırılır.</span><span class="sxs-lookup"><span data-stu-id="1f7dd-137">An I/O thread is terminated in the thread pool.</span></span>|

 <span data-ttu-id="1f7dd-138">Aşağıdaki tabloda olay verileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1f7dd-138">The following table shows the event data.</span></span>

|<span data-ttu-id="1f7dd-139">Alan adı</span><span class="sxs-lookup"><span data-stu-id="1f7dd-139">Field name</span></span>|<span data-ttu-id="1f7dd-140">Veri türü</span><span class="sxs-lookup"><span data-stu-id="1f7dd-140">Data type</span></span>|<span data-ttu-id="1f7dd-141">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1f7dd-141">Description</span></span>|
|----------------|---------------|-----------------|
|`Count`|`win:UInt64`|<span data-ttu-id="1f7dd-142">İş parçacığı havuzunda kalan g/ç iş parçacığı sayısı.</span><span class="sxs-lookup"><span data-stu-id="1f7dd-142">Number of I/O threads remaining in the thread pool.</span></span>|
|`NumRetired`|`win:UInt64`|<span data-ttu-id="1f7dd-143">Kullanımdan kaldırılan g/ç iş parçacığı sayısı.</span><span class="sxs-lookup"><span data-stu-id="1f7dd-143">Number of retired I/O threads.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="1f7dd-144">CLR veya CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="1f7dd-144">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="iothreadretire_v1-event"></a><span data-ttu-id="1f7dd-145">IOThreadRetire_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="1f7dd-145">IOThreadRetire_V1 event</span></span>

 <span data-ttu-id="1f7dd-146">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1f7dd-146">The following table shows the keyword and level.</span></span>

|<span data-ttu-id="1f7dd-147">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="1f7dd-147">Keyword for raising the event</span></span>|<span data-ttu-id="1f7dd-148">Level</span><span class="sxs-lookup"><span data-stu-id="1f7dd-148">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="1f7dd-149">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="1f7dd-149">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="1f7dd-150">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="1f7dd-150">Informational (4)</span></span>|

 <span data-ttu-id="1f7dd-151">Aşağıdaki tabloda olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1f7dd-151">The following table shows the event information.</span></span>

|<span data-ttu-id="1f7dd-152">Olay</span><span class="sxs-lookup"><span data-stu-id="1f7dd-152">Event</span></span>|<span data-ttu-id="1f7dd-153">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="1f7dd-153">Event ID</span></span>|<span data-ttu-id="1f7dd-154">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="1f7dd-154">Raised when</span></span>|
|-----------|--------------|-----------------|
|`IOThreadRetire_V1`|<span data-ttu-id="1f7dd-155">46</span><span class="sxs-lookup"><span data-stu-id="1f7dd-155">46</span></span>|<span data-ttu-id="1f7dd-156">Bir g/ç iş parçacığı bir kullanımdan kaldırma adayı haline gelir.</span><span class="sxs-lookup"><span data-stu-id="1f7dd-156">An I/O thread becomes a retirement candidate.</span></span>|

 <span data-ttu-id="1f7dd-157">Aşağıdaki tabloda olay verileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1f7dd-157">The following table shows the event data.</span></span>

|<span data-ttu-id="1f7dd-158">Alan adı</span><span class="sxs-lookup"><span data-stu-id="1f7dd-158">Field name</span></span>|<span data-ttu-id="1f7dd-159">Veri türü</span><span class="sxs-lookup"><span data-stu-id="1f7dd-159">Data type</span></span>|<span data-ttu-id="1f7dd-160">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1f7dd-160">Description</span></span>|
|----------------|---------------|-----------------|
|`Count`|`win:UInt64`|<span data-ttu-id="1f7dd-161">İş parçacığı havuzunda kalan g/ç iş parçacığı sayısı.</span><span class="sxs-lookup"><span data-stu-id="1f7dd-161">Number of I/O threads remaining in the thread pool.</span></span>|
|`NumRetired`|`win:UInt64`|<span data-ttu-id="1f7dd-162">Kullanımdan kaldırılan g/ç iş parçacığı sayısı.</span><span class="sxs-lookup"><span data-stu-id="1f7dd-162">Number of retired I/O threads.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="1f7dd-163">CLR veya CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="1f7dd-163">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="iothreadunretire_v1-event"></a><span data-ttu-id="1f7dd-164">IOThreadUnretire_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="1f7dd-164">IOThreadUnretire_V1 event</span></span>

 <span data-ttu-id="1f7dd-165">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1f7dd-165">The following table shows the keyword and level.</span></span>

|<span data-ttu-id="1f7dd-166">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="1f7dd-166">Keyword for raising the event</span></span>|<span data-ttu-id="1f7dd-167">Level</span><span class="sxs-lookup"><span data-stu-id="1f7dd-167">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="1f7dd-168">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="1f7dd-168">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="1f7dd-169">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="1f7dd-169">Informational (4)</span></span>|

 <span data-ttu-id="1f7dd-170">Aşağıdaki tabloda olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1f7dd-170">The following table shows the event information.</span></span>

|<span data-ttu-id="1f7dd-171">Olay</span><span class="sxs-lookup"><span data-stu-id="1f7dd-171">Event</span></span>|<span data-ttu-id="1f7dd-172">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="1f7dd-172">Event ID</span></span>|<span data-ttu-id="1f7dd-173">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="1f7dd-173">Raised when</span></span>|
|-----------|--------------|-----------------|
|`IOThreadUnretire_V1`|<span data-ttu-id="1f7dd-174">47</span><span class="sxs-lookup"><span data-stu-id="1f7dd-174">47</span></span>|<span data-ttu-id="1f7dd-175">Bir g/ç iş parçacığı, iş parçacığı bir kullanımdan kaldırma adayı olduktan sonra bekleme süresi içinde ulaşan g/ç nedeniyle kullanımdan kaldırıldı.</span><span class="sxs-lookup"><span data-stu-id="1f7dd-175">An I/O thread is unretired because of I/O that arrives within a waiting period after the thread becomes a retirement candidate.</span></span>|

 <span data-ttu-id="1f7dd-176">Aşağıdaki tabloda olay verileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1f7dd-176">The following table shows the event data.</span></span>

|<span data-ttu-id="1f7dd-177">Alan adı</span><span class="sxs-lookup"><span data-stu-id="1f7dd-177">Field name</span></span>|<span data-ttu-id="1f7dd-178">Veri türü</span><span class="sxs-lookup"><span data-stu-id="1f7dd-178">Data type</span></span>|<span data-ttu-id="1f7dd-179">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1f7dd-179">Description</span></span>|
|----------------|---------------|-----------------|
|`Count`|`win:UInt64`|<span data-ttu-id="1f7dd-180">Bu dahil iş parçacığı havuzundaki g/ç iş parçacıklarının sayısı.</span><span class="sxs-lookup"><span data-stu-id="1f7dd-180">Number of I/O threads in the thread pool, including this one.</span></span>|
|`NumRetired`|`win:UInt64`|<span data-ttu-id="1f7dd-181">Kullanımdan kaldırılan g/ç iş parçacığı sayısı.</span><span class="sxs-lookup"><span data-stu-id="1f7dd-181">Number of retired I/O threads.</span></span>|
|`ClrInstanceID`|`Win:UInt16`|<span data-ttu-id="1f7dd-182">CLR veya CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="1f7dd-182">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="threadpoolworkerthreadstart-event"></a><span data-ttu-id="1f7dd-183">ThreadPoolWorkerThreadStart olayı</span><span class="sxs-lookup"><span data-stu-id="1f7dd-183">ThreadPoolWorkerThreadStart event</span></span>

|<span data-ttu-id="1f7dd-184">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="1f7dd-184">Keyword for raising the event</span></span>|<span data-ttu-id="1f7dd-185">Level</span><span class="sxs-lookup"><span data-stu-id="1f7dd-185">Level</span></span>|
|-----------------------------------|-----------|-----------|
|<span data-ttu-id="1f7dd-186">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="1f7dd-186">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="1f7dd-187">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="1f7dd-187">Informational (4)</span></span>|

|<span data-ttu-id="1f7dd-188">Olay</span><span class="sxs-lookup"><span data-stu-id="1f7dd-188">Event</span></span>|<span data-ttu-id="1f7dd-189">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="1f7dd-189">Event ID</span></span>|<span data-ttu-id="1f7dd-190">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1f7dd-190">Description</span></span>|
|-----------|--------------|-----------------|
|`ThreadPoolWorkerThreadStart`|<span data-ttu-id="1f7dd-191">50</span><span class="sxs-lookup"><span data-stu-id="1f7dd-191">50</span></span>|<span data-ttu-id="1f7dd-192">Bir çalışan iş parçacığı oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="1f7dd-192">A worker thread is created.</span></span>|

|<span data-ttu-id="1f7dd-193">Alan adı</span><span class="sxs-lookup"><span data-stu-id="1f7dd-193">Field name</span></span>|<span data-ttu-id="1f7dd-194">Veri türü</span><span class="sxs-lookup"><span data-stu-id="1f7dd-194">Data type</span></span>|<span data-ttu-id="1f7dd-195">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1f7dd-195">Description</span></span>|
|----------------|---------------|-----------------|
|`ActiveWorkerThreadCount`|`win:UInt32`|<span data-ttu-id="1f7dd-196">İşleri işlemek için kullanılabilen çalışan iş parçacığı sayısı, zaten işleme işleri de dahil olmak üzere.</span><span class="sxs-lookup"><span data-stu-id="1f7dd-196">Number of worker threads available to process work, including those that are already processing work.</span></span>|
|`RetiredWorkerThreadCount`|`win:UInt32`|<span data-ttu-id="1f7dd-197">Çalışmayı işlemek için kullanılamayan, ancak daha sonra ayrılan iş parçacığı sayısı daha sonra daha fazla iş parçacığı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="1f7dd-197">Number of worker threads that are not available to process work, but that are being held in reserve in case more threads are needed later.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="1f7dd-198">CLR veya CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="1f7dd-198">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="threadpoolworkerthreadstop-event"></a><span data-ttu-id="1f7dd-199">ThreadPoolWorkerThreadStop olayı</span><span class="sxs-lookup"><span data-stu-id="1f7dd-199">ThreadPoolWorkerThreadStop event</span></span>

|<span data-ttu-id="1f7dd-200">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="1f7dd-200">Keyword for raising the event</span></span>|<span data-ttu-id="1f7dd-201">Level</span><span class="sxs-lookup"><span data-stu-id="1f7dd-201">Level</span></span>|
|-----------------------------------|-----------|-----------|
|<span data-ttu-id="1f7dd-202">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="1f7dd-202">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="1f7dd-203">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="1f7dd-203">Informational (4)</span></span>|

|<span data-ttu-id="1f7dd-204">Olay</span><span class="sxs-lookup"><span data-stu-id="1f7dd-204">Event</span></span>|<span data-ttu-id="1f7dd-205">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="1f7dd-205">Event ID</span></span>|<span data-ttu-id="1f7dd-206">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1f7dd-206">Description</span></span>|
|-----------|--------------|-----------------|
|`ThreadPoolWorkerThreadStop`|<span data-ttu-id="1f7dd-207">51</span><span class="sxs-lookup"><span data-stu-id="1f7dd-207">51</span></span>|<span data-ttu-id="1f7dd-208">Çalışan iş parçacığı durduruldu.</span><span class="sxs-lookup"><span data-stu-id="1f7dd-208">A worker thread is stopped.</span></span>|

|<span data-ttu-id="1f7dd-209">Alan adı</span><span class="sxs-lookup"><span data-stu-id="1f7dd-209">Field name</span></span>|<span data-ttu-id="1f7dd-210">Veri türü</span><span class="sxs-lookup"><span data-stu-id="1f7dd-210">Data type</span></span>|<span data-ttu-id="1f7dd-211">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1f7dd-211">Description</span></span>|
|----------------|---------------|-----------------|
|`ActiveWorkerThreadCount`|`win:UInt32`|<span data-ttu-id="1f7dd-212">İşleri işlemek için kullanılabilen çalışan iş parçacığı sayısı, zaten işleme işleri de dahil olmak üzere.</span><span class="sxs-lookup"><span data-stu-id="1f7dd-212">Number of worker threads available to process work, including those that are already processing work.</span></span>|
|`RetiredWorkerThreadCount`|`win:UInt32`|<span data-ttu-id="1f7dd-213">Çalışmayı işlemek için kullanılamayan, ancak daha sonra ayrılan iş parçacığı sayısı daha sonra daha fazla iş parçacığı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="1f7dd-213">Number of worker threads that are not available to process work, but that are being held in reserve in case more threads are needed later.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="1f7dd-214">CLR veya CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="1f7dd-214">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="threadpoolworkerthreadwait-event"></a><span data-ttu-id="1f7dd-215">ThreadPoolWorkerThreadWait olayı</span><span class="sxs-lookup"><span data-stu-id="1f7dd-215">ThreadPoolWorkerThreadWait event</span></span>

|<span data-ttu-id="1f7dd-216">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="1f7dd-216">Keyword for raising the event</span></span>|<span data-ttu-id="1f7dd-217">Level</span><span class="sxs-lookup"><span data-stu-id="1f7dd-217">Level</span></span>|
|-----------------------------------|-----------|-----------|
|<span data-ttu-id="1f7dd-218">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="1f7dd-218">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="1f7dd-219">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="1f7dd-219">Informational (4)</span></span>|

|<span data-ttu-id="1f7dd-220">Olay</span><span class="sxs-lookup"><span data-stu-id="1f7dd-220">Event</span></span>|<span data-ttu-id="1f7dd-221">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="1f7dd-221">Event ID</span></span>|<span data-ttu-id="1f7dd-222">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1f7dd-222">Description</span></span>|
|-----------|--------------|-----------------|
|`ThreadPoolWorkerThreadWait`|<span data-ttu-id="1f7dd-223">57</span><span class="sxs-lookup"><span data-stu-id="1f7dd-223">57</span></span>|<span data-ttu-id="1f7dd-224">Çalışan iş parçacığı çalışmaya başlar.</span><span class="sxs-lookup"><span data-stu-id="1f7dd-224">A worker thread starts waiting for work.</span></span>|

|<span data-ttu-id="1f7dd-225">Alan adı</span><span class="sxs-lookup"><span data-stu-id="1f7dd-225">Field name</span></span>|<span data-ttu-id="1f7dd-226">Veri türü</span><span class="sxs-lookup"><span data-stu-id="1f7dd-226">Data type</span></span>|<span data-ttu-id="1f7dd-227">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1f7dd-227">Description</span></span>|
|----------------|---------------|-----------------|
|`ActiveWorkerThreadCount`|`win:UInt32`|<span data-ttu-id="1f7dd-228">İşleri işlemek için kullanılabilen çalışan iş parçacığı sayısı, zaten işleme işleri de dahil olmak üzere.</span><span class="sxs-lookup"><span data-stu-id="1f7dd-228">Number of worker threads available to process work, including those that are already processing work.</span></span>|
|`RetiredWorkerThreadCount`|`win:UInt32`|<span data-ttu-id="1f7dd-229">Çalışmayı işlemek için kullanılamayan, ancak daha sonra ayrılan iş parçacığı sayısı daha sonra daha fazla iş parçacığı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="1f7dd-229">Number of worker threads that are not available to process work, but that are being held in reserve in case more threads are needed later.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="1f7dd-230">CLR veya CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="1f7dd-230">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="threadpoolworkerthreadretirementstart-event"></a><span data-ttu-id="1f7dd-231">ThreadPoolWorkerThreadRetirementStart olayı</span><span class="sxs-lookup"><span data-stu-id="1f7dd-231">ThreadPoolWorkerThreadRetirementStart event</span></span>

|<span data-ttu-id="1f7dd-232">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="1f7dd-232">Keyword for raising the event</span></span>|<span data-ttu-id="1f7dd-233">Level</span><span class="sxs-lookup"><span data-stu-id="1f7dd-233">Level</span></span>|
|-----------------------------------|-----------|-----------|
|<span data-ttu-id="1f7dd-234">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="1f7dd-234">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="1f7dd-235">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="1f7dd-235">Informational (4)</span></span>|

|<span data-ttu-id="1f7dd-236">Olay</span><span class="sxs-lookup"><span data-stu-id="1f7dd-236">Event</span></span>|<span data-ttu-id="1f7dd-237">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="1f7dd-237">Event ID</span></span>|<span data-ttu-id="1f7dd-238">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1f7dd-238">Description</span></span>|
|-----------|--------------|-----------------|
|`ThreadPoolWorkerThreadRetirementStart`|<span data-ttu-id="1f7dd-239">52</span><span class="sxs-lookup"><span data-stu-id="1f7dd-239">52</span></span>|<span data-ttu-id="1f7dd-240">Bir çalışan iş parçacığı yeniden oluşturma.</span><span class="sxs-lookup"><span data-stu-id="1f7dd-240">A worker thread retires.</span></span>|

|<span data-ttu-id="1f7dd-241">Alan adı</span><span class="sxs-lookup"><span data-stu-id="1f7dd-241">Field name</span></span>|<span data-ttu-id="1f7dd-242">Veri türü</span><span class="sxs-lookup"><span data-stu-id="1f7dd-242">Data type</span></span>|<span data-ttu-id="1f7dd-243">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1f7dd-243">Description</span></span>|
|----------------|---------------|-----------------|
|`ActiveWorkerThreadCount`|`win:UInt32`|<span data-ttu-id="1f7dd-244">İşleri işlemek için kullanılabilen çalışan iş parçacığı sayısı, zaten işleme işleri de dahil olmak üzere.</span><span class="sxs-lookup"><span data-stu-id="1f7dd-244">Number of worker threads available to process work, including those that are already processing work.</span></span>|
|`RetiredWorkerThreadCount`|`win:UInt32`|<span data-ttu-id="1f7dd-245">Çalışmayı işlemek için kullanılamayan, ancak daha sonra ayrılan iş parçacığı sayısı daha sonra daha fazla iş parçacığı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="1f7dd-245">Number of worker threads that are not available to process work, but that are being held in reserve in case more threads are needed later.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="1f7dd-246">CLR veya CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="1f7dd-246">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="threadpoolworkerthreadretirementstop-event"></a><span data-ttu-id="1f7dd-247">ThreadPoolWorkerThreadRetirementStop olayı</span><span class="sxs-lookup"><span data-stu-id="1f7dd-247">ThreadPoolWorkerThreadRetirementStop event</span></span>

|<span data-ttu-id="1f7dd-248">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="1f7dd-248">Keyword for raising the event</span></span>|<span data-ttu-id="1f7dd-249">Level</span><span class="sxs-lookup"><span data-stu-id="1f7dd-249">Level</span></span>|
|-----------------------------------|-----------|-----------|
|<span data-ttu-id="1f7dd-250">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="1f7dd-250">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="1f7dd-251">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="1f7dd-251">Informational (4)</span></span>|

|<span data-ttu-id="1f7dd-252">Olay</span><span class="sxs-lookup"><span data-stu-id="1f7dd-252">Event</span></span>|<span data-ttu-id="1f7dd-253">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="1f7dd-253">Event ID</span></span>|<span data-ttu-id="1f7dd-254">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1f7dd-254">Description</span></span>|
|-----------|--------------|-----------------|
|`ThreadPoolWorkerThreadRetirementStop`|<span data-ttu-id="1f7dd-255">53</span><span class="sxs-lookup"><span data-stu-id="1f7dd-255">53</span></span>|<span data-ttu-id="1f7dd-256">Kullanımdan kaldırılan bir çalışan iş parçacığı yeniden etkin hale gelir.</span><span class="sxs-lookup"><span data-stu-id="1f7dd-256">A retired worker thread becomes active again.</span></span>|

|<span data-ttu-id="1f7dd-257">Alan adı</span><span class="sxs-lookup"><span data-stu-id="1f7dd-257">Field name</span></span>|<span data-ttu-id="1f7dd-258">Veri türü</span><span class="sxs-lookup"><span data-stu-id="1f7dd-258">Data type</span></span>|<span data-ttu-id="1f7dd-259">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1f7dd-259">Description</span></span>|
|----------------|---------------|-----------------|
|`ActiveWorkerThreadCount`|`win:UInt32`|<span data-ttu-id="1f7dd-260">İşleri işlemek için kullanılabilen çalışan iş parçacığı sayısı, zaten işleme işleri de dahil olmak üzere.</span><span class="sxs-lookup"><span data-stu-id="1f7dd-260">Number of worker threads available to process work, including those that are already processing work.</span></span>|
|`RetiredWorkerThreadCount`|`win:UInt32`|<span data-ttu-id="1f7dd-261">Çalışmayı işlemek için kullanılamayan, ancak daha sonra ayrılan iş parçacığı sayısı daha sonra daha fazla iş parçacığı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="1f7dd-261">Number of worker threads that are not available to process work, but that are being held in reserve in case more threads are needed later.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="1f7dd-262">CLR veya CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="1f7dd-262">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="threadpoolworkerthreadadjustmentsample-event"></a><span data-ttu-id="1f7dd-263">Threadpoolworkerthreadadadatmentsample olayı</span><span class="sxs-lookup"><span data-stu-id="1f7dd-263">ThreadPoolWorkerThreadAdjustmentSample event</span></span>

 <span data-ttu-id="1f7dd-264">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1f7dd-264">The following table shows the keyword and level.</span></span>

|<span data-ttu-id="1f7dd-265">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="1f7dd-265">Keyword for raising the event</span></span>|<span data-ttu-id="1f7dd-266">Level</span><span class="sxs-lookup"><span data-stu-id="1f7dd-266">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="1f7dd-267">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="1f7dd-267">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="1f7dd-268">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="1f7dd-268">Informational (4)</span></span>|

 <span data-ttu-id="1f7dd-269">Aşağıdaki tabloda olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1f7dd-269">The following table shows the event information.</span></span>

|<span data-ttu-id="1f7dd-270">Olay</span><span class="sxs-lookup"><span data-stu-id="1f7dd-270">Event</span></span>|<span data-ttu-id="1f7dd-271">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="1f7dd-271">Event ID</span></span>|<span data-ttu-id="1f7dd-272">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1f7dd-272">Description</span></span>|
|-----------|--------------|-----------------|
|`ThreadPoolWorkerThreadAdjustmentSample`|<span data-ttu-id="1f7dd-273">54</span><span class="sxs-lookup"><span data-stu-id="1f7dd-273">54</span></span>|<span data-ttu-id="1f7dd-274">Bir örnek için bilgi toplamayı ifade eder; diğer bir deyişle, belirli bir eşzamanlılık düzeyi olan aktarım hızı, zaman içinde bir ölçümdür.</span><span class="sxs-lookup"><span data-stu-id="1f7dd-274">Refers to the collection of information for one sample; that is, a measurement of throughput with a certain concurrency level, in an instant of time.</span></span>|

 <span data-ttu-id="1f7dd-275">Aşağıdaki tabloda olay verileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1f7dd-275">The following table shows the event data.</span></span>

|<span data-ttu-id="1f7dd-276">Alan adı</span><span class="sxs-lookup"><span data-stu-id="1f7dd-276">Field name</span></span>|<span data-ttu-id="1f7dd-277">Veri türü</span><span class="sxs-lookup"><span data-stu-id="1f7dd-277">Data type</span></span>|<span data-ttu-id="1f7dd-278">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1f7dd-278">Description</span></span>|
|----------------|---------------|-----------------|
|`Throughput`|`win:Double`|<span data-ttu-id="1f7dd-279">Zaman birimi başına tamamlama sayısı.</span><span class="sxs-lookup"><span data-stu-id="1f7dd-279">Number of completions per unit of time.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="1f7dd-280">CLR veya CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="1f7dd-280">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="threadpoolworkerthreadadjustmentadjustment-event"></a><span data-ttu-id="1f7dd-281">Threadpoolworkerthreadadyatmentadolayını ayarlama olayı</span><span class="sxs-lookup"><span data-stu-id="1f7dd-281">ThreadPoolWorkerThreadAdjustmentAdjustment event</span></span>

 <span data-ttu-id="1f7dd-282">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1f7dd-282">The following table shows the keyword and level.</span></span>

|<span data-ttu-id="1f7dd-283">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="1f7dd-283">Keyword for raising the event</span></span>|<span data-ttu-id="1f7dd-284">Level</span><span class="sxs-lookup"><span data-stu-id="1f7dd-284">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="1f7dd-285">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="1f7dd-285">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="1f7dd-286">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="1f7dd-286">Informational (4)</span></span>|

 <span data-ttu-id="1f7dd-287">Aşağıdaki tabloda olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1f7dd-287">The following table shows the event information.</span></span>

|<span data-ttu-id="1f7dd-288">Olay</span><span class="sxs-lookup"><span data-stu-id="1f7dd-288">Event</span></span>|<span data-ttu-id="1f7dd-289">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="1f7dd-289">Event ID</span></span>|<span data-ttu-id="1f7dd-290">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1f7dd-290">Description</span></span>|
|-----------|--------------|-----------------|
|`ThreadPoolWorkerThreadAdjustmentAdjustment`|<span data-ttu-id="1f7dd-291">55</span><span class="sxs-lookup"><span data-stu-id="1f7dd-291">55</span></span>|<span data-ttu-id="1f7dd-292">İş parçacığı ekleme (Hill-climbing) algoritması eşzamanlılık düzeyindeki bir değişikliğin yerinde olduğunu belirlediğinde denetimdeki bir değişikliği kaydeder.</span><span class="sxs-lookup"><span data-stu-id="1f7dd-292">Records a change in control, when the thread injection (hill-climbing) algorithm determines that a change in concurrency level is in place.</span></span>|

 <span data-ttu-id="1f7dd-293">Aşağıdaki tabloda olay verileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1f7dd-293">The following table shows the event data.</span></span>

|<span data-ttu-id="1f7dd-294">Alan adı</span><span class="sxs-lookup"><span data-stu-id="1f7dd-294">Field name</span></span>|<span data-ttu-id="1f7dd-295">Veri türü</span><span class="sxs-lookup"><span data-stu-id="1f7dd-295">Data type</span></span>|<span data-ttu-id="1f7dd-296">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1f7dd-296">Description</span></span>|
|----------------|---------------|-----------------|
|`AverageThroughput`|`win:Double`|<span data-ttu-id="1f7dd-297">Ölçüm örneğinin ortalama performansı.</span><span class="sxs-lookup"><span data-stu-id="1f7dd-297">Average throughput of a sample of measurements.</span></span>|
|`NewWorkerThreadCount`|`win:UInt32`|<span data-ttu-id="1f7dd-298">Yeni etkin çalışan iş parçacığı sayısı.</span><span class="sxs-lookup"><span data-stu-id="1f7dd-298">New number of active worker threads.</span></span>|
|`Reason`|`win:UInt32`|<span data-ttu-id="1f7dd-299">Ayarlamanın nedeni.</span><span class="sxs-lookup"><span data-stu-id="1f7dd-299">Reason for the adjustment.</span></span><br /><br /> <span data-ttu-id="1f7dd-300">`0x0` Isınma.</span><span class="sxs-lookup"><span data-stu-id="1f7dd-300">`0x0` - Warmup.</span></span><br /><br /> <span data-ttu-id="1f7dd-301">`0x1` Başlatarak.</span><span class="sxs-lookup"><span data-stu-id="1f7dd-301">`0x1` - Initializing.</span></span><br /><br /> <span data-ttu-id="1f7dd-302">`0x2` -Rastgele taşı.</span><span class="sxs-lookup"><span data-stu-id="1f7dd-302">`0x2` - Random move.</span></span><br /><br /> <span data-ttu-id="1f7dd-303">`0x3` -Geçiş taşı.</span><span class="sxs-lookup"><span data-stu-id="1f7dd-303">`0x3` - Climbing move.</span></span><br /><br /> <span data-ttu-id="1f7dd-304">`0x4` -Değişiklik noktası.</span><span class="sxs-lookup"><span data-stu-id="1f7dd-304">`0x4` - Change point.</span></span><br /><br /> <span data-ttu-id="1f7dd-305">`0x5` Sabitleniyor.</span><span class="sxs-lookup"><span data-stu-id="1f7dd-305">`0x5` - Stabilizing.</span></span><br /><br /> <span data-ttu-id="1f7dd-306">`0x6` Yetersizliğine neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="1f7dd-306">`0x6` - Starvation.</span></span><br /><br /> <span data-ttu-id="1f7dd-307">`0x7` -İş parçacığı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="1f7dd-307">`0x7` - Thread timed out.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="1f7dd-308">CLR veya CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="1f7dd-308">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="threadpoolworkerthreadadjustmentstats-event"></a><span data-ttu-id="1f7dd-309">Threadpoolworkerthreadadadatmentstats olayı</span><span class="sxs-lookup"><span data-stu-id="1f7dd-309">ThreadPoolWorkerThreadAdjustmentStats event</span></span>

 <span data-ttu-id="1f7dd-310">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1f7dd-310">The following table shows the keyword and level.</span></span>

|<span data-ttu-id="1f7dd-311">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="1f7dd-311">Keyword for raising the event</span></span>|<span data-ttu-id="1f7dd-312">Level</span><span class="sxs-lookup"><span data-stu-id="1f7dd-312">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="1f7dd-313">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="1f7dd-313">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="1f7dd-314">Verbose (5)</span><span class="sxs-lookup"><span data-stu-id="1f7dd-314">Verbose (5)</span></span>

 <span data-ttu-id="1f7dd-315">Aşağıdaki tabloda olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1f7dd-315">The following table shows the event information.</span></span>

|<span data-ttu-id="1f7dd-316">Olay</span><span class="sxs-lookup"><span data-stu-id="1f7dd-316">Event</span></span>|<span data-ttu-id="1f7dd-317">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="1f7dd-317">Event ID</span></span>|<span data-ttu-id="1f7dd-318">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1f7dd-318">Description</span></span>|
|-----------|--------------|-----------------|
|`ThreadPoolWorkerThreadAdjustmentStats`|<span data-ttu-id="1f7dd-319">56</span><span class="sxs-lookup"><span data-stu-id="1f7dd-319">56</span></span>|<span data-ttu-id="1f7dd-320">İş parçacığı havuzundaki verileri toplar.</span><span class="sxs-lookup"><span data-stu-id="1f7dd-320">Gathers data on the thread pool.</span></span>|

 <span data-ttu-id="1f7dd-321">Aşağıdaki tabloda olay verileri gösterilmektedir</span><span class="sxs-lookup"><span data-stu-id="1f7dd-321">The following table shows the event data</span></span>

|<span data-ttu-id="1f7dd-322">Alan adı</span><span class="sxs-lookup"><span data-stu-id="1f7dd-322">Field name</span></span>|<span data-ttu-id="1f7dd-323">Veri türü</span><span class="sxs-lookup"><span data-stu-id="1f7dd-323">Data type</span></span>|<span data-ttu-id="1f7dd-324">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1f7dd-324">Description</span></span>|
|----------------|---------------|-----------------|
|`Duration`|`win:Double`|<span data-ttu-id="1f7dd-325">Bu istatistiklerin toplandığı sürenin saniye cinsinden miktarı.</span><span class="sxs-lookup"><span data-stu-id="1f7dd-325">Amount of time, in seconds, during which these statistics were collected.</span></span>|
|`Throughput`|`win:Double`|<span data-ttu-id="1f7dd-326">Bu Aralık sırasında saniye başına ortalama tamamlama sayısı.</span><span class="sxs-lookup"><span data-stu-id="1f7dd-326">Average number of completions per second during this interval.</span></span>|
|`ThreadWave`|`win:Double`|<span data-ttu-id="1f7dd-327">Dahili kullanım için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="1f7dd-327">Reserved for internal use.</span></span>|
|`ThroughputWave`|`win:Double`|<span data-ttu-id="1f7dd-328">Dahili kullanım için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="1f7dd-328">Reserved for internal use.</span></span>|
|`ThroughputErrorEstimate`|`win:Double`|<span data-ttu-id="1f7dd-329">Dahili kullanım için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="1f7dd-329">Reserved for internal use.</span></span>|
|`AverageThroughputErrorEstimate`|`win:Double`|<span data-ttu-id="1f7dd-330">Dahili kullanım için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="1f7dd-330">Reserved for internal use.</span></span>|
|`ThroughputRatio`|`win:Double`|<span data-ttu-id="1f7dd-331">Bu zaman aralığı boyunca etkin çalışan iş parçacığı sayısında değişimler nedeniyle üretilen iş akışındaki göreli geliştirme.</span><span class="sxs-lookup"><span data-stu-id="1f7dd-331">The relative improvement in throughput caused by variations in active worker thread count during this interval.</span></span>|
|`Confidence`|`win:Double`|<span data-ttu-id="1f7dd-332">ThroughputRatio alanının geçerlilik süresinin ölçüsü.</span><span class="sxs-lookup"><span data-stu-id="1f7dd-332">A measure of the validity of the ThroughputRatio field.</span></span>|
|`NewcontrolSetting`|`win:Double`|<span data-ttu-id="1f7dd-333">Etkin iş parçacığı sayısında gelecekteki Çeşitlemeler için temel olarak görev yapacak etkin çalışan iş parçacıklarının sayısı.</span><span class="sxs-lookup"><span data-stu-id="1f7dd-333">The number of active worker threads that will serve as the baseline for future variations in active thread count.</span></span>|
|`NewThreadWaveMagnitude`|`win:UInt16`|<span data-ttu-id="1f7dd-334">Etkin iş parçacığı sayısı ' nda gelecekteki varyasyonların büyüklüğü.</span><span class="sxs-lookup"><span data-stu-id="1f7dd-334">The magnitude of future variations in active thread count.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="1f7dd-335">CLR veya CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="1f7dd-335">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="threadpoolenqueue-event"></a><span data-ttu-id="1f7dd-336">ThreadPoolEnqueue olayı</span><span class="sxs-lookup"><span data-stu-id="1f7dd-336">ThreadPoolEnqueue event</span></span>

 <span data-ttu-id="1f7dd-337">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1f7dd-337">The following table shows the keyword and level.</span></span>

|<span data-ttu-id="1f7dd-338">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="1f7dd-338">Keyword for raising the event</span></span>|<span data-ttu-id="1f7dd-339">Level</span><span class="sxs-lookup"><span data-stu-id="1f7dd-339">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="1f7dd-340">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="1f7dd-340">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="1f7dd-341">Verbose (5)</span><span class="sxs-lookup"><span data-stu-id="1f7dd-341">Verbose (5)</span></span>

 <span data-ttu-id="1f7dd-342">Aşağıdaki tabloda olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1f7dd-342">The following table shows the event information.</span></span>

|<span data-ttu-id="1f7dd-343">Olay</span><span class="sxs-lookup"><span data-stu-id="1f7dd-343">Event</span></span>|<span data-ttu-id="1f7dd-344">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="1f7dd-344">Event ID</span></span>|<span data-ttu-id="1f7dd-345">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1f7dd-345">Description</span></span>|
|-----------|--------------|-----------------|
|`ThreadPoolEnqueue`|<span data-ttu-id="1f7dd-346">61</span><span class="sxs-lookup"><span data-stu-id="1f7dd-346">61</span></span>|<span data-ttu-id="1f7dd-347">İş öğesi, iş parçacığı havuzu kuyruğunda sıraya alındı.</span><span class="sxs-lookup"><span data-stu-id="1f7dd-347">A work item was enqueued in the thread pool queue.</span></span>|

 <span data-ttu-id="1f7dd-348">Aşağıdaki tabloda olay verileri gösterilmektedir</span><span class="sxs-lookup"><span data-stu-id="1f7dd-348">The following table shows the event data</span></span>

|<span data-ttu-id="1f7dd-349">Alan adı</span><span class="sxs-lookup"><span data-stu-id="1f7dd-349">Field name</span></span>|<span data-ttu-id="1f7dd-350">Veri türü</span><span class="sxs-lookup"><span data-stu-id="1f7dd-350">Data type</span></span>|<span data-ttu-id="1f7dd-351">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1f7dd-351">Description</span></span>|
|----------------|---------------|-----------------|
|`WorkID`|`win:Pointer`|<span data-ttu-id="1f7dd-352">İş isteğine yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="1f7dd-352">Pointer to the work request.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="1f7dd-353">CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="1f7dd-353">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="threadpooldequeue-event"></a><span data-ttu-id="1f7dd-354">Threadpoolsıradan çıkarma olayı</span><span class="sxs-lookup"><span data-stu-id="1f7dd-354">ThreadPoolDequeue event</span></span>

 <span data-ttu-id="1f7dd-355">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1f7dd-355">The following table shows the keyword and level.</span></span>

|<span data-ttu-id="1f7dd-356">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="1f7dd-356">Keyword for raising the event</span></span>|<span data-ttu-id="1f7dd-357">Level</span><span class="sxs-lookup"><span data-stu-id="1f7dd-357">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="1f7dd-358">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="1f7dd-358">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="1f7dd-359">Verbose (5)</span><span class="sxs-lookup"><span data-stu-id="1f7dd-359">Verbose (5)</span></span>

 <span data-ttu-id="1f7dd-360">Aşağıdaki tabloda olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1f7dd-360">The following table shows the event information.</span></span>

|<span data-ttu-id="1f7dd-361">Olay</span><span class="sxs-lookup"><span data-stu-id="1f7dd-361">Event</span></span>|<span data-ttu-id="1f7dd-362">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="1f7dd-362">Event ID</span></span>|<span data-ttu-id="1f7dd-363">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1f7dd-363">Description</span></span>|
|-----------|--------------|-----------------|
|`ThreadPoolDequeue`|<span data-ttu-id="1f7dd-364">62</span><span class="sxs-lookup"><span data-stu-id="1f7dd-364">62</span></span>|<span data-ttu-id="1f7dd-365">İş öğesi, iş parçacığı havuzu sırasından kuyruğa alındı.</span><span class="sxs-lookup"><span data-stu-id="1f7dd-365">A work item was dequeued from the thread pool queue.</span></span>|

 <span data-ttu-id="1f7dd-366">Aşağıdaki tabloda olay verileri gösterilmektedir</span><span class="sxs-lookup"><span data-stu-id="1f7dd-366">The following table shows the event data</span></span>

|<span data-ttu-id="1f7dd-367">Alan adı</span><span class="sxs-lookup"><span data-stu-id="1f7dd-367">Field name</span></span>|<span data-ttu-id="1f7dd-368">Veri türü</span><span class="sxs-lookup"><span data-stu-id="1f7dd-368">Data type</span></span>|<span data-ttu-id="1f7dd-369">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1f7dd-369">Description</span></span>|
|----------------|---------------|-----------------|
|`WorkID`|`win:Pointer`|<span data-ttu-id="1f7dd-370">İş isteğine yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="1f7dd-370">Pointer to the work request.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="1f7dd-371">CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="1f7dd-371">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="threadpoolioenqueue-event"></a><span data-ttu-id="1f7dd-372">Threadpokayokuyruğa alma olayı</span><span class="sxs-lookup"><span data-stu-id="1f7dd-372">ThreadPoolIOEnqueue event</span></span>

 <span data-ttu-id="1f7dd-373">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1f7dd-373">The following table shows the keyword and level.</span></span>

|<span data-ttu-id="1f7dd-374">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="1f7dd-374">Keyword for raising the event</span></span>|<span data-ttu-id="1f7dd-375">Level</span><span class="sxs-lookup"><span data-stu-id="1f7dd-375">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="1f7dd-376">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="1f7dd-376">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="1f7dd-377">Verbose (5)</span><span class="sxs-lookup"><span data-stu-id="1f7dd-377">Verbose (5)</span></span>

 <span data-ttu-id="1f7dd-378">Aşağıdaki tabloda olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1f7dd-378">The following table shows the event information.</span></span>

|<span data-ttu-id="1f7dd-379">Olay</span><span class="sxs-lookup"><span data-stu-id="1f7dd-379">Event</span></span>|<span data-ttu-id="1f7dd-380">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="1f7dd-380">Event ID</span></span>|<span data-ttu-id="1f7dd-381">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1f7dd-381">Description</span></span>|
|-----------|--------------|-----------------|
|`ThreadPoolIOEnqueue`|<span data-ttu-id="1f7dd-382">63</span><span class="sxs-lookup"><span data-stu-id="1f7dd-382">63</span></span>|<span data-ttu-id="1f7dd-383">Bir iş parçacığı, zaman uyumsuz GÇ tamamlandıktan sonra bir GÇ tamamlama bildirimini sıraya alır.</span><span class="sxs-lookup"><span data-stu-id="1f7dd-383">A thread enqueues an IO completion notification after an async IO completion occurs.</span></span>|

 <span data-ttu-id="1f7dd-384">Aşağıdaki tabloda olay verileri gösterilmektedir</span><span class="sxs-lookup"><span data-stu-id="1f7dd-384">The following table shows the event data</span></span>

|<span data-ttu-id="1f7dd-385">Alan adı</span><span class="sxs-lookup"><span data-stu-id="1f7dd-385">Field name</span></span>|<span data-ttu-id="1f7dd-386">Veri türü</span><span class="sxs-lookup"><span data-stu-id="1f7dd-386">Data type</span></span>|<span data-ttu-id="1f7dd-387">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1f7dd-387">Description</span></span>|
|----------------|---------------|-----------------|
|`NativeOverlapped`|`win:Pointer`|<span data-ttu-id="1f7dd-388">Dahili kullanım için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="1f7dd-388">Reserved for internal use.</span></span>|
|`Overlapped`|`win:Pointer`|<span data-ttu-id="1f7dd-389">Dahili kullanım için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="1f7dd-389">Reserved for internal use.</span></span>|
|`MultiDequeues`|`win:Boolean`|<span data-ttu-id="1f7dd-390">Dahili kullanım için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="1f7dd-390">Reserved for internal use.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="1f7dd-391">CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="1f7dd-391">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="threadpooliodequeue-event"></a><span data-ttu-id="1f7dd-392">Threadpokaykıosıradan çıkarma olayı</span><span class="sxs-lookup"><span data-stu-id="1f7dd-392">ThreadPoolIODequeue event</span></span>

 <span data-ttu-id="1f7dd-393">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1f7dd-393">The following table shows the keyword and level.</span></span>

|<span data-ttu-id="1f7dd-394">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="1f7dd-394">Keyword for raising the event</span></span>|<span data-ttu-id="1f7dd-395">Level</span><span class="sxs-lookup"><span data-stu-id="1f7dd-395">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="1f7dd-396">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="1f7dd-396">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="1f7dd-397">Verbose (5)</span><span class="sxs-lookup"><span data-stu-id="1f7dd-397">Verbose (5)</span></span>

 <span data-ttu-id="1f7dd-398">Aşağıdaki tabloda olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1f7dd-398">The following table shows the event information.</span></span>

|<span data-ttu-id="1f7dd-399">Olay</span><span class="sxs-lookup"><span data-stu-id="1f7dd-399">Event</span></span>|<span data-ttu-id="1f7dd-400">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="1f7dd-400">Event ID</span></span>|<span data-ttu-id="1f7dd-401">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1f7dd-401">Description</span></span>|
|-----------|--------------|-----------------|
|`ThreadPoolIODequeue`|<span data-ttu-id="1f7dd-402">64</span><span class="sxs-lookup"><span data-stu-id="1f7dd-402">64</span></span>|<span data-ttu-id="1f7dd-403">Bir iş parçacığı GÇ tamamlama bildirimini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="1f7dd-403">A thread dequeues the IO completion notification.</span></span>|

 <span data-ttu-id="1f7dd-404">Aşağıdaki tabloda olay verileri gösterilmektedir</span><span class="sxs-lookup"><span data-stu-id="1f7dd-404">The following table shows the event data</span></span>

|<span data-ttu-id="1f7dd-405">Alan adı</span><span class="sxs-lookup"><span data-stu-id="1f7dd-405">Field name</span></span>|<span data-ttu-id="1f7dd-406">Veri türü</span><span class="sxs-lookup"><span data-stu-id="1f7dd-406">Data type</span></span>|<span data-ttu-id="1f7dd-407">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1f7dd-407">Description</span></span>|
|----------------|---------------|-----------------|
|`NativeOverlapped`|`win:Pointer`|<span data-ttu-id="1f7dd-408">Dahili kullanım için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="1f7dd-408">Reserved for internal use.</span></span>|
|`Overlapped`|`win:Pointer`|<span data-ttu-id="1f7dd-409">Dahili kullanım için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="1f7dd-409">Reserved for internal use.</span></span>|
|`MultiDequeues`|`win:Boolean`|<span data-ttu-id="1f7dd-410">Dahili kullanım için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="1f7dd-410">Reserved for internal use.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="1f7dd-411">CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="1f7dd-411">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="threadpooliopack-event"></a><span data-ttu-id="1f7dd-412">ThreadPoolIOPack olayı</span><span class="sxs-lookup"><span data-stu-id="1f7dd-412">ThreadPoolIOPack event</span></span>

 <span data-ttu-id="1f7dd-413">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1f7dd-413">The following table shows the keyword and level.</span></span>

|<span data-ttu-id="1f7dd-414">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="1f7dd-414">Keyword for raising the event</span></span>|<span data-ttu-id="1f7dd-415">Level</span><span class="sxs-lookup"><span data-stu-id="1f7dd-415">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="1f7dd-416">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="1f7dd-416">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="1f7dd-417">Verbose (5)</span><span class="sxs-lookup"><span data-stu-id="1f7dd-417">Verbose (5)</span></span>|

 <span data-ttu-id="1f7dd-418">Aşağıdaki tabloda olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1f7dd-418">The following table shows the event information.</span></span>

|<span data-ttu-id="1f7dd-419">Olay</span><span class="sxs-lookup"><span data-stu-id="1f7dd-419">Event</span></span>|<span data-ttu-id="1f7dd-420">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="1f7dd-420">Event ID</span></span>|<span data-ttu-id="1f7dd-421">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1f7dd-421">Description</span></span>|
|-----------|--------------|-----------------|
|`ThreadPoolIOPack`|<span data-ttu-id="1f7dd-422">65</span><span class="sxs-lookup"><span data-stu-id="1f7dd-422">65</span></span>|<span data-ttu-id="1f7dd-423">İş parçacığı çakışan GÇ paketi çağırılır.</span><span class="sxs-lookup"><span data-stu-id="1f7dd-423">ThreadPool overlapped IO pack is called.</span></span>|

 <span data-ttu-id="1f7dd-424">Aşağıdaki tabloda olay verileri gösterilmektedir</span><span class="sxs-lookup"><span data-stu-id="1f7dd-424">The following table shows the event data</span></span>

|<span data-ttu-id="1f7dd-425">Alan adı</span><span class="sxs-lookup"><span data-stu-id="1f7dd-425">Field name</span></span>|<span data-ttu-id="1f7dd-426">Veri türü</span><span class="sxs-lookup"><span data-stu-id="1f7dd-426">Data type</span></span>|<span data-ttu-id="1f7dd-427">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1f7dd-427">Description</span></span>|
|----------------|---------------|-----------------|
|`NativeOverlapped`|`win:Pointer`|<span data-ttu-id="1f7dd-428">Dahili kullanım için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="1f7dd-428">Reserved for internal use.</span></span>|
|`Overlapped`|`win:Pointer`|<span data-ttu-id="1f7dd-429">Dahili kullanım için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="1f7dd-429">Reserved for internal use.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="1f7dd-430">CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="1f7dd-430">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="threadcreating-event"></a><span data-ttu-id="1f7dd-431">Threadevent oluşturma</span><span class="sxs-lookup"><span data-stu-id="1f7dd-431">ThreadCreating event</span></span>

 <span data-ttu-id="1f7dd-432">Aşağıdaki tabloda anahtar kelimeleri ve düzeyi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1f7dd-432">The following table shows the keywords and level.</span></span>

|<span data-ttu-id="1f7dd-433">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="1f7dd-433">Keyword for raising the event</span></span>|<span data-ttu-id="1f7dd-434">Level</span><span class="sxs-lookup"><span data-stu-id="1f7dd-434">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="1f7dd-435">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="1f7dd-435">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="1f7dd-436">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="1f7dd-436">Informational (4)</span></span>|

 <span data-ttu-id="1f7dd-437">Aşağıdaki tabloda olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1f7dd-437">The following table shows the event information.</span></span>

|<span data-ttu-id="1f7dd-438">Olay</span><span class="sxs-lookup"><span data-stu-id="1f7dd-438">Event</span></span>|<span data-ttu-id="1f7dd-439">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="1f7dd-439">Event ID</span></span>|<span data-ttu-id="1f7dd-440">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1f7dd-440">Description</span></span>|
|----------------|---------------|-----------------|
|`ThreadCreating`|<span data-ttu-id="1f7dd-441">70</span><span class="sxs-lookup"><span data-stu-id="1f7dd-441">70</span></span>|<span data-ttu-id="1f7dd-442">İş parçacığı oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="1f7dd-442">Thread has been created.</span></span>|

 <span data-ttu-id="1f7dd-443">Aşağıdaki tabloda olay verileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1f7dd-443">The following table shows the event data.</span></span>

|<span data-ttu-id="1f7dd-444">Alan adı</span><span class="sxs-lookup"><span data-stu-id="1f7dd-444">Field name</span></span>|<span data-ttu-id="1f7dd-445">Veri türü</span><span class="sxs-lookup"><span data-stu-id="1f7dd-445">Data type</span></span>|<span data-ttu-id="1f7dd-446">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1f7dd-446">Description</span></span>|
|----------------|---------------|-----------------|
|`ID`|`win:Pointer`|<span data-ttu-id="1f7dd-447">İş parçacığı KIMLIĞI</span><span class="sxs-lookup"><span data-stu-id="1f7dd-447">Thread ID</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="1f7dd-448">CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="1f7dd-448">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="threadrunning-event"></a><span data-ttu-id="1f7dd-449">ThreadRunning olayı</span><span class="sxs-lookup"><span data-stu-id="1f7dd-449">ThreadRunning event</span></span>

 <span data-ttu-id="1f7dd-450">Aşağıdaki tabloda anahtar kelimeleri ve düzeyi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1f7dd-450">The following table shows the keywords and level.</span></span>

|<span data-ttu-id="1f7dd-451">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="1f7dd-451">Keyword for raising the event</span></span>|<span data-ttu-id="1f7dd-452">Level</span><span class="sxs-lookup"><span data-stu-id="1f7dd-452">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="1f7dd-453">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="1f7dd-453">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="1f7dd-454">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="1f7dd-454">Informational (4)</span></span>|

 <span data-ttu-id="1f7dd-455">Aşağıdaki tabloda olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1f7dd-455">The following table shows the event information.</span></span>

|<span data-ttu-id="1f7dd-456">Olay</span><span class="sxs-lookup"><span data-stu-id="1f7dd-456">Event</span></span>|<span data-ttu-id="1f7dd-457">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="1f7dd-457">Event ID</span></span>|<span data-ttu-id="1f7dd-458">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1f7dd-458">Description</span></span>|
|----------------|---------------|-----------------|
|`ThreadRunning`|<span data-ttu-id="1f7dd-459">71</span><span class="sxs-lookup"><span data-stu-id="1f7dd-459">71</span></span>|<span data-ttu-id="1f7dd-460">İş parçacığı çalışmaya başladı.</span><span class="sxs-lookup"><span data-stu-id="1f7dd-460">Thread has started running.</span></span>|

 <span data-ttu-id="1f7dd-461">Aşağıdaki tabloda olay verileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1f7dd-461">The following table shows the event data.</span></span>

|<span data-ttu-id="1f7dd-462">Alan adı</span><span class="sxs-lookup"><span data-stu-id="1f7dd-462">Field name</span></span>|<span data-ttu-id="1f7dd-463">Veri türü</span><span class="sxs-lookup"><span data-stu-id="1f7dd-463">Data type</span></span>|<span data-ttu-id="1f7dd-464">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1f7dd-464">Description</span></span>|
|----------------|---------------|-----------------|
|`ID`|`win:Pointer`|<span data-ttu-id="1f7dd-465">İş parçacığı KIMLIĞI</span><span class="sxs-lookup"><span data-stu-id="1f7dd-465">Thread ID</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="1f7dd-466">CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="1f7dd-466">Unique ID for the instance of CoreCLR.</span></span>|
