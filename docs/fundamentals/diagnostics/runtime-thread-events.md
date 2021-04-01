---
title: ThreadPool çalışma zamanı olayları
description: .NET Core 'da iş parçacığı havuzu hakkında tanılama bilgilerini toplayacak .NET Runtime iş parçacığı havuzu olayları bölümüne bakın. İş parçacığı havuzu olayları, çalışan iş parçacığı havuzu olayları veya g/ç iş parçacığı havuzu olaylardır.
ms.date: 11/13/2020
ms.topic: reference
helpviewer_keywords:
- ThreadPool events (CoreCLR)
- ETW, thread pool events (CoreCLR)
ms.openlocfilehash: cdd6041c5842d4922c60e33daf6db366f7d35327
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/30/2021
ms.locfileid: "96590045"
---
# <a name="net-runtime-thread-pool-events"></a><span data-ttu-id="1424b-104">.NET çalışma zamanı iş parçacığı havuzu olayları</span><span class="sxs-lookup"><span data-stu-id="1424b-104">.NET runtime thread pool events</span></span>

<span data-ttu-id="1424b-105">Bu olaylar, ThreadPool içindeki çalışan ve g/ç iş parçacıkları hakkında bilgi toplar.</span><span class="sxs-lookup"><span data-stu-id="1424b-105">These events collect information about worker and I/O threads in the threadpool.</span></span> <span data-ttu-id="1424b-106">Bu olayların tanılama amacıyla nasıl kullanılacağı hakkında daha fazla bilgi için bkz. [.NET uygulamalarını günlüğe kaydetme ve izleme](../../core/diagnostics/logging-tracing.md)</span><span class="sxs-lookup"><span data-stu-id="1424b-106">For more information about how to use these events for diagnostic purposes, see [logging and tracing .NET applications](../../core/diagnostics/logging-tracing.md)</span></span>

## <a name="iothreadcreate_v1-event"></a><span data-ttu-id="1424b-107">IOThreadCreate_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="1424b-107">IOThreadCreate_V1 event</span></span>

 <span data-ttu-id="1424b-108">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1424b-108">The following table shows the keyword and level.</span></span>

|<span data-ttu-id="1424b-109">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="1424b-109">Keyword for raising the event</span></span>|<span data-ttu-id="1424b-110">Level</span><span class="sxs-lookup"><span data-stu-id="1424b-110">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="1424b-111">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="1424b-111">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="1424b-112">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="1424b-112">Informational (4)</span></span>|

 <span data-ttu-id="1424b-113">Aşağıdaki tabloda olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1424b-113">The following table shows the event information.</span></span>

|<span data-ttu-id="1424b-114">Olay</span><span class="sxs-lookup"><span data-stu-id="1424b-114">Event</span></span>|<span data-ttu-id="1424b-115">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="1424b-115">Event ID</span></span>|<span data-ttu-id="1424b-116">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="1424b-116">Raised when</span></span>|
|-----------------------------------|-----------|
|`IOThreadCreate_V1`|<span data-ttu-id="1424b-117">44</span><span class="sxs-lookup"><span data-stu-id="1424b-117">44</span></span>|<span data-ttu-id="1424b-118">İş parçacığı havuzunda bir g/ç iş parçacığı oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="1424b-118">An I/O thread is created in the thread pool.</span></span>|

 <span data-ttu-id="1424b-119">Aşağıdaki tabloda olay verileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1424b-119">The following table shows the event data.</span></span>

|<span data-ttu-id="1424b-120">Alan adı</span><span class="sxs-lookup"><span data-stu-id="1424b-120">Field name</span></span>|<span data-ttu-id="1424b-121">Veri türü</span><span class="sxs-lookup"><span data-stu-id="1424b-121">Data type</span></span>|<span data-ttu-id="1424b-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1424b-122">Description</span></span>|
|----------------|---------------|-----------------|
|`Count`|`win:UInt64`|<span data-ttu-id="1424b-123">Yeni oluşturulan iş parçacığı dahil olmak üzere g/ç iş parçacıklarının sayısı.</span><span class="sxs-lookup"><span data-stu-id="1424b-123">Number of I/O threads, including the newly created thread.</span></span>|
|`NumRetired`|`win:UInt64`|<span data-ttu-id="1424b-124">Kullanımdan kaldırılan çalışan iş parçacıklarının sayısı.</span><span class="sxs-lookup"><span data-stu-id="1424b-124">Number of retired worker threads.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="1424b-125">CLR veya CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="1424b-125">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="iothreadterminate_v1-event"></a><span data-ttu-id="1424b-126">IOThreadTerminate_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="1424b-126">IOThreadTerminate_V1 event</span></span>

 <span data-ttu-id="1424b-127">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir</span><span class="sxs-lookup"><span data-stu-id="1424b-127">The following table shows the keyword and level</span></span>

|<span data-ttu-id="1424b-128">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="1424b-128">Keyword for raising the event</span></span>|<span data-ttu-id="1424b-129">Level</span><span class="sxs-lookup"><span data-stu-id="1424b-129">Level</span></span>
|-----------------------------------|-----------
|<span data-ttu-id="1424b-130">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="1424b-130">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="1424b-131">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="1424b-131">Informational (4)</span></span>

 <span data-ttu-id="1424b-132">Aşağıdaki tabloda olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1424b-132">The following table shows the event information.</span></span>

|<span data-ttu-id="1424b-133">Olay</span><span class="sxs-lookup"><span data-stu-id="1424b-133">Event</span></span>|<span data-ttu-id="1424b-134">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="1424b-134">Event ID</span></span>|<span data-ttu-id="1424b-135">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="1424b-135">Raised when</span></span>|
|-----------|--------------|-----------------|
|`IOThreadTerminate`|<span data-ttu-id="1424b-136">45</span><span class="sxs-lookup"><span data-stu-id="1424b-136">45</span></span>|<span data-ttu-id="1424b-137">İş parçacığı havuzunda bir g/ç iş parçacığı sonlandırılır.</span><span class="sxs-lookup"><span data-stu-id="1424b-137">An I/O thread is terminated in the thread pool.</span></span>|

 <span data-ttu-id="1424b-138">Aşağıdaki tabloda olay verileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1424b-138">The following table shows the event data.</span></span>

|<span data-ttu-id="1424b-139">Alan adı</span><span class="sxs-lookup"><span data-stu-id="1424b-139">Field name</span></span>|<span data-ttu-id="1424b-140">Veri türü</span><span class="sxs-lookup"><span data-stu-id="1424b-140">Data type</span></span>|<span data-ttu-id="1424b-141">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1424b-141">Description</span></span>|
|----------------|---------------|-----------------|
|`Count`|`win:UInt64`|<span data-ttu-id="1424b-142">İş parçacığı havuzunda kalan g/ç iş parçacığı sayısı.</span><span class="sxs-lookup"><span data-stu-id="1424b-142">Number of I/O threads remaining in the thread pool.</span></span>|
|`NumRetired`|`win:UInt64`|<span data-ttu-id="1424b-143">Kullanımdan kaldırılan g/ç iş parçacığı sayısı.</span><span class="sxs-lookup"><span data-stu-id="1424b-143">Number of retired I/O threads.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="1424b-144">CLR veya CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="1424b-144">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="iothreadretire_v1-event"></a><span data-ttu-id="1424b-145">IOThreadRetire_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="1424b-145">IOThreadRetire_V1 event</span></span>

 <span data-ttu-id="1424b-146">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1424b-146">The following table shows the keyword and level.</span></span>

|<span data-ttu-id="1424b-147">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="1424b-147">Keyword for raising the event</span></span>|<span data-ttu-id="1424b-148">Level</span><span class="sxs-lookup"><span data-stu-id="1424b-148">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="1424b-149">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="1424b-149">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="1424b-150">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="1424b-150">Informational (4)</span></span>|

 <span data-ttu-id="1424b-151">Aşağıdaki tabloda olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1424b-151">The following table shows the event information.</span></span>

|<span data-ttu-id="1424b-152">Olay</span><span class="sxs-lookup"><span data-stu-id="1424b-152">Event</span></span>|<span data-ttu-id="1424b-153">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="1424b-153">Event ID</span></span>|<span data-ttu-id="1424b-154">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="1424b-154">Raised when</span></span>|
|-----------|--------------|-----------------|
|`IOThreadRetire_V1`|<span data-ttu-id="1424b-155">46</span><span class="sxs-lookup"><span data-stu-id="1424b-155">46</span></span>|<span data-ttu-id="1424b-156">Bir g/ç iş parçacığı bir kullanımdan kaldırma adayı haline gelir.</span><span class="sxs-lookup"><span data-stu-id="1424b-156">An I/O thread becomes a retirement candidate.</span></span>|

 <span data-ttu-id="1424b-157">Aşağıdaki tabloda olay verileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1424b-157">The following table shows the event data.</span></span>

|<span data-ttu-id="1424b-158">Alan adı</span><span class="sxs-lookup"><span data-stu-id="1424b-158">Field name</span></span>|<span data-ttu-id="1424b-159">Veri türü</span><span class="sxs-lookup"><span data-stu-id="1424b-159">Data type</span></span>|<span data-ttu-id="1424b-160">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1424b-160">Description</span></span>|
|----------------|---------------|-----------------|
|`Count`|`win:UInt64`|<span data-ttu-id="1424b-161">İş parçacığı havuzunda kalan g/ç iş parçacığı sayısı.</span><span class="sxs-lookup"><span data-stu-id="1424b-161">Number of I/O threads remaining in the thread pool.</span></span>|
|`NumRetired`|`win:UInt64`|<span data-ttu-id="1424b-162">Kullanımdan kaldırılan g/ç iş parçacığı sayısı.</span><span class="sxs-lookup"><span data-stu-id="1424b-162">Number of retired I/O threads.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="1424b-163">CLR veya CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="1424b-163">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="iothreadunretire_v1-event"></a><span data-ttu-id="1424b-164">IOThreadUnretire_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="1424b-164">IOThreadUnretire_V1 event</span></span>

 <span data-ttu-id="1424b-165">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1424b-165">The following table shows the keyword and level.</span></span>

|<span data-ttu-id="1424b-166">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="1424b-166">Keyword for raising the event</span></span>|<span data-ttu-id="1424b-167">Level</span><span class="sxs-lookup"><span data-stu-id="1424b-167">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="1424b-168">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="1424b-168">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="1424b-169">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="1424b-169">Informational (4)</span></span>|

 <span data-ttu-id="1424b-170">Aşağıdaki tabloda olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1424b-170">The following table shows the event information.</span></span>

|<span data-ttu-id="1424b-171">Olay</span><span class="sxs-lookup"><span data-stu-id="1424b-171">Event</span></span>|<span data-ttu-id="1424b-172">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="1424b-172">Event ID</span></span>|<span data-ttu-id="1424b-173">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="1424b-173">Raised when</span></span>|
|-----------|--------------|-----------------|
|`IOThreadUnretire_V1`|<span data-ttu-id="1424b-174">47</span><span class="sxs-lookup"><span data-stu-id="1424b-174">47</span></span>|<span data-ttu-id="1424b-175">Bir g/ç iş parçacığı, iş parçacığı bir kullanımdan kaldırma adayı olduktan sonra bekleme süresi içinde ulaşan g/ç nedeniyle kullanımdan kaldırıldı.</span><span class="sxs-lookup"><span data-stu-id="1424b-175">An I/O thread is unretired because of I/O that arrives within a waiting period after the thread becomes a retirement candidate.</span></span>|

 <span data-ttu-id="1424b-176">Aşağıdaki tabloda olay verileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1424b-176">The following table shows the event data.</span></span>

|<span data-ttu-id="1424b-177">Alan adı</span><span class="sxs-lookup"><span data-stu-id="1424b-177">Field name</span></span>|<span data-ttu-id="1424b-178">Veri türü</span><span class="sxs-lookup"><span data-stu-id="1424b-178">Data type</span></span>|<span data-ttu-id="1424b-179">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1424b-179">Description</span></span>|
|----------------|---------------|-----------------|
|`Count`|`win:UInt64`|<span data-ttu-id="1424b-180">Bu dahil iş parçacığı havuzundaki g/ç iş parçacıklarının sayısı.</span><span class="sxs-lookup"><span data-stu-id="1424b-180">Number of I/O threads in the thread pool, including this one.</span></span>|
|`NumRetired`|`win:UInt64`|<span data-ttu-id="1424b-181">Kullanımdan kaldırılan g/ç iş parçacığı sayısı.</span><span class="sxs-lookup"><span data-stu-id="1424b-181">Number of retired I/O threads.</span></span>|
|`ClrInstanceID`|`Win:UInt16`|<span data-ttu-id="1424b-182">CLR veya CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="1424b-182">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="threadpoolworkerthreadstart-event"></a><span data-ttu-id="1424b-183">ThreadPoolWorkerThreadStart olayı</span><span class="sxs-lookup"><span data-stu-id="1424b-183">ThreadPoolWorkerThreadStart event</span></span>

|<span data-ttu-id="1424b-184">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="1424b-184">Keyword for raising the event</span></span>|<span data-ttu-id="1424b-185">Level</span><span class="sxs-lookup"><span data-stu-id="1424b-185">Level</span></span>|
|-----------------------------------|-----------|-----------|
|<span data-ttu-id="1424b-186">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="1424b-186">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="1424b-187">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="1424b-187">Informational (4)</span></span>|

|<span data-ttu-id="1424b-188">Olay</span><span class="sxs-lookup"><span data-stu-id="1424b-188">Event</span></span>|<span data-ttu-id="1424b-189">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="1424b-189">Event ID</span></span>|<span data-ttu-id="1424b-190">Description</span><span class="sxs-lookup"><span data-stu-id="1424b-190">Description</span></span>|
|-----------|--------------|-----------------|
|`ThreadPoolWorkerThreadStart`|<span data-ttu-id="1424b-191">50</span><span class="sxs-lookup"><span data-stu-id="1424b-191">50</span></span>|<span data-ttu-id="1424b-192">Bir çalışan iş parçacığı oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="1424b-192">A worker thread is created.</span></span>|

|<span data-ttu-id="1424b-193">Alan adı</span><span class="sxs-lookup"><span data-stu-id="1424b-193">Field name</span></span>|<span data-ttu-id="1424b-194">Veri türü</span><span class="sxs-lookup"><span data-stu-id="1424b-194">Data type</span></span>|<span data-ttu-id="1424b-195">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1424b-195">Description</span></span>|
|----------------|---------------|-----------------|
|`ActiveWorkerThreadCount`|`win:UInt32`|<span data-ttu-id="1424b-196">İşleri işlemek için kullanılabilen çalışan iş parçacığı sayısı, zaten işleme işleri de dahil olmak üzere.</span><span class="sxs-lookup"><span data-stu-id="1424b-196">Number of worker threads available to process work, including those that are already processing work.</span></span>|
|`RetiredWorkerThreadCount`|`win:UInt32`|<span data-ttu-id="1424b-197">Çalışmayı işlemek için kullanılamayan, ancak daha sonra ayrılan iş parçacığı sayısı daha sonra daha fazla iş parçacığı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="1424b-197">Number of worker threads that are not available to process work, but that are being held in reserve in case more threads are needed later.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="1424b-198">CLR veya CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="1424b-198">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="threadpoolworkerthreadstop-event"></a><span data-ttu-id="1424b-199">ThreadPoolWorkerThreadStop olayı</span><span class="sxs-lookup"><span data-stu-id="1424b-199">ThreadPoolWorkerThreadStop event</span></span>

|<span data-ttu-id="1424b-200">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="1424b-200">Keyword for raising the event</span></span>|<span data-ttu-id="1424b-201">Level</span><span class="sxs-lookup"><span data-stu-id="1424b-201">Level</span></span>|
|-----------------------------------|-----------|-----------|
|<span data-ttu-id="1424b-202">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="1424b-202">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="1424b-203">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="1424b-203">Informational (4)</span></span>|

|<span data-ttu-id="1424b-204">Olay</span><span class="sxs-lookup"><span data-stu-id="1424b-204">Event</span></span>|<span data-ttu-id="1424b-205">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="1424b-205">Event ID</span></span>|<span data-ttu-id="1424b-206">Description</span><span class="sxs-lookup"><span data-stu-id="1424b-206">Description</span></span>|
|-----------|--------------|-----------------|
|`ThreadPoolWorkerThreadStop`|<span data-ttu-id="1424b-207">51</span><span class="sxs-lookup"><span data-stu-id="1424b-207">51</span></span>|<span data-ttu-id="1424b-208">Çalışan iş parçacığı durduruldu.</span><span class="sxs-lookup"><span data-stu-id="1424b-208">A worker thread is stopped.</span></span>|

|<span data-ttu-id="1424b-209">Alan adı</span><span class="sxs-lookup"><span data-stu-id="1424b-209">Field name</span></span>|<span data-ttu-id="1424b-210">Veri türü</span><span class="sxs-lookup"><span data-stu-id="1424b-210">Data type</span></span>|<span data-ttu-id="1424b-211">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1424b-211">Description</span></span>|
|----------------|---------------|-----------------|
|`ActiveWorkerThreadCount`|`win:UInt32`|<span data-ttu-id="1424b-212">İşleri işlemek için kullanılabilen çalışan iş parçacığı sayısı, zaten işleme işleri de dahil olmak üzere.</span><span class="sxs-lookup"><span data-stu-id="1424b-212">Number of worker threads available to process work, including those that are already processing work.</span></span>|
|`RetiredWorkerThreadCount`|`win:UInt32`|<span data-ttu-id="1424b-213">Çalışmayı işlemek için kullanılamayan, ancak daha sonra ayrılan iş parçacığı sayısı daha sonra daha fazla iş parçacığı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="1424b-213">Number of worker threads that are not available to process work, but that are being held in reserve in case more threads are needed later.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="1424b-214">CLR veya CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="1424b-214">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="threadpoolworkerthreadwait-event"></a><span data-ttu-id="1424b-215">ThreadPoolWorkerThreadWait olayı</span><span class="sxs-lookup"><span data-stu-id="1424b-215">ThreadPoolWorkerThreadWait event</span></span>

|<span data-ttu-id="1424b-216">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="1424b-216">Keyword for raising the event</span></span>|<span data-ttu-id="1424b-217">Level</span><span class="sxs-lookup"><span data-stu-id="1424b-217">Level</span></span>|
|-----------------------------------|-----------|-----------|
|<span data-ttu-id="1424b-218">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="1424b-218">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="1424b-219">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="1424b-219">Informational (4)</span></span>|

|<span data-ttu-id="1424b-220">Olay</span><span class="sxs-lookup"><span data-stu-id="1424b-220">Event</span></span>|<span data-ttu-id="1424b-221">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="1424b-221">Event ID</span></span>|<span data-ttu-id="1424b-222">Description</span><span class="sxs-lookup"><span data-stu-id="1424b-222">Description</span></span>|
|-----------|--------------|-----------------|
|`ThreadPoolWorkerThreadWait`|<span data-ttu-id="1424b-223">57</span><span class="sxs-lookup"><span data-stu-id="1424b-223">57</span></span>|<span data-ttu-id="1424b-224">Çalışan iş parçacığı çalışmaya başlar.</span><span class="sxs-lookup"><span data-stu-id="1424b-224">A worker thread starts waiting for work.</span></span>|

|<span data-ttu-id="1424b-225">Alan adı</span><span class="sxs-lookup"><span data-stu-id="1424b-225">Field name</span></span>|<span data-ttu-id="1424b-226">Veri türü</span><span class="sxs-lookup"><span data-stu-id="1424b-226">Data type</span></span>|<span data-ttu-id="1424b-227">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1424b-227">Description</span></span>|
|----------------|---------------|-----------------|
|`ActiveWorkerThreadCount`|`win:UInt32`|<span data-ttu-id="1424b-228">İşleri işlemek için kullanılabilen çalışan iş parçacığı sayısı, zaten işleme işleri de dahil olmak üzere.</span><span class="sxs-lookup"><span data-stu-id="1424b-228">Number of worker threads available to process work, including those that are already processing work.</span></span>|
|`RetiredWorkerThreadCount`|`win:UInt32`|<span data-ttu-id="1424b-229">Çalışmayı işlemek için kullanılamayan, ancak daha sonra ayrılan iş parçacığı sayısı daha sonra daha fazla iş parçacığı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="1424b-229">Number of worker threads that are not available to process work, but that are being held in reserve in case more threads are needed later.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="1424b-230">CLR veya CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="1424b-230">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="threadpoolworkerthreadretirementstart-event"></a><span data-ttu-id="1424b-231">ThreadPoolWorkerThreadRetirementStart olayı</span><span class="sxs-lookup"><span data-stu-id="1424b-231">ThreadPoolWorkerThreadRetirementStart event</span></span>

|<span data-ttu-id="1424b-232">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="1424b-232">Keyword for raising the event</span></span>|<span data-ttu-id="1424b-233">Level</span><span class="sxs-lookup"><span data-stu-id="1424b-233">Level</span></span>|
|-----------------------------------|-----------|-----------|
|<span data-ttu-id="1424b-234">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="1424b-234">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="1424b-235">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="1424b-235">Informational (4)</span></span>|

|<span data-ttu-id="1424b-236">Olay</span><span class="sxs-lookup"><span data-stu-id="1424b-236">Event</span></span>|<span data-ttu-id="1424b-237">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="1424b-237">Event ID</span></span>|<span data-ttu-id="1424b-238">Description</span><span class="sxs-lookup"><span data-stu-id="1424b-238">Description</span></span>|
|-----------|--------------|-----------------|
|`ThreadPoolWorkerThreadRetirementStart`|<span data-ttu-id="1424b-239">52</span><span class="sxs-lookup"><span data-stu-id="1424b-239">52</span></span>|<span data-ttu-id="1424b-240">Bir çalışan iş parçacığı yeniden oluşturma.</span><span class="sxs-lookup"><span data-stu-id="1424b-240">A worker thread retires.</span></span>|

|<span data-ttu-id="1424b-241">Alan adı</span><span class="sxs-lookup"><span data-stu-id="1424b-241">Field name</span></span>|<span data-ttu-id="1424b-242">Veri türü</span><span class="sxs-lookup"><span data-stu-id="1424b-242">Data type</span></span>|<span data-ttu-id="1424b-243">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1424b-243">Description</span></span>|
|----------------|---------------|-----------------|
|`ActiveWorkerThreadCount`|`win:UInt32`|<span data-ttu-id="1424b-244">İşleri işlemek için kullanılabilen çalışan iş parçacığı sayısı, zaten işleme işleri de dahil olmak üzere.</span><span class="sxs-lookup"><span data-stu-id="1424b-244">Number of worker threads available to process work, including those that are already processing work.</span></span>|
|`RetiredWorkerThreadCount`|`win:UInt32`|<span data-ttu-id="1424b-245">Çalışmayı işlemek için kullanılamayan, ancak daha sonra ayrılan iş parçacığı sayısı daha sonra daha fazla iş parçacığı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="1424b-245">Number of worker threads that are not available to process work, but that are being held in reserve in case more threads are needed later.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="1424b-246">CLR veya CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="1424b-246">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="threadpoolworkerthreadretirementstop-event"></a><span data-ttu-id="1424b-247">ThreadPoolWorkerThreadRetirementStop olayı</span><span class="sxs-lookup"><span data-stu-id="1424b-247">ThreadPoolWorkerThreadRetirementStop event</span></span>

|<span data-ttu-id="1424b-248">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="1424b-248">Keyword for raising the event</span></span>|<span data-ttu-id="1424b-249">Level</span><span class="sxs-lookup"><span data-stu-id="1424b-249">Level</span></span>|
|-----------------------------------|-----------|-----------|
|<span data-ttu-id="1424b-250">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="1424b-250">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="1424b-251">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="1424b-251">Informational (4)</span></span>|

|<span data-ttu-id="1424b-252">Olay</span><span class="sxs-lookup"><span data-stu-id="1424b-252">Event</span></span>|<span data-ttu-id="1424b-253">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="1424b-253">Event ID</span></span>|<span data-ttu-id="1424b-254">Description</span><span class="sxs-lookup"><span data-stu-id="1424b-254">Description</span></span>|
|-----------|--------------|-----------------|
|`ThreadPoolWorkerThreadRetirementStop`|<span data-ttu-id="1424b-255">53</span><span class="sxs-lookup"><span data-stu-id="1424b-255">53</span></span>|<span data-ttu-id="1424b-256">Kullanımdan kaldırılan bir çalışan iş parçacığı yeniden etkin hale gelir.</span><span class="sxs-lookup"><span data-stu-id="1424b-256">A retired worker thread becomes active again.</span></span>|

|<span data-ttu-id="1424b-257">Alan adı</span><span class="sxs-lookup"><span data-stu-id="1424b-257">Field name</span></span>|<span data-ttu-id="1424b-258">Veri türü</span><span class="sxs-lookup"><span data-stu-id="1424b-258">Data type</span></span>|<span data-ttu-id="1424b-259">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1424b-259">Description</span></span>|
|----------------|---------------|-----------------|
|`ActiveWorkerThreadCount`|`win:UInt32`|<span data-ttu-id="1424b-260">İşleri işlemek için kullanılabilen çalışan iş parçacığı sayısı, zaten işleme işleri de dahil olmak üzere.</span><span class="sxs-lookup"><span data-stu-id="1424b-260">Number of worker threads available to process work, including those that are already processing work.</span></span>|
|`RetiredWorkerThreadCount`|`win:UInt32`|<span data-ttu-id="1424b-261">Çalışmayı işlemek için kullanılamayan, ancak daha sonra ayrılan iş parçacığı sayısı daha sonra daha fazla iş parçacığı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="1424b-261">Number of worker threads that are not available to process work, but that are being held in reserve in case more threads are needed later.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="1424b-262">CLR veya CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="1424b-262">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="threadpoolworkerthreadadjustmentsample-event"></a><span data-ttu-id="1424b-263">Threadpoolworkerthreadadadatmentsample olayı</span><span class="sxs-lookup"><span data-stu-id="1424b-263">ThreadPoolWorkerThreadAdjustmentSample event</span></span>

 <span data-ttu-id="1424b-264">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1424b-264">The following table shows the keyword and level.</span></span>

|<span data-ttu-id="1424b-265">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="1424b-265">Keyword for raising the event</span></span>|<span data-ttu-id="1424b-266">Level</span><span class="sxs-lookup"><span data-stu-id="1424b-266">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="1424b-267">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="1424b-267">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="1424b-268">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="1424b-268">Informational (4)</span></span>|

 <span data-ttu-id="1424b-269">Aşağıdaki tabloda olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1424b-269">The following table shows the event information.</span></span>

|<span data-ttu-id="1424b-270">Olay</span><span class="sxs-lookup"><span data-stu-id="1424b-270">Event</span></span>|<span data-ttu-id="1424b-271">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="1424b-271">Event ID</span></span>|<span data-ttu-id="1424b-272">Description</span><span class="sxs-lookup"><span data-stu-id="1424b-272">Description</span></span>|
|-----------|--------------|-----------------|
|`ThreadPoolWorkerThreadAdjustmentSample`|<span data-ttu-id="1424b-273">54</span><span class="sxs-lookup"><span data-stu-id="1424b-273">54</span></span>|<span data-ttu-id="1424b-274">Bir örnek için bilgi toplamayı ifade eder; diğer bir deyişle, belirli bir eşzamanlılık düzeyi olan aktarım hızı, zaman içinde bir ölçümdür.</span><span class="sxs-lookup"><span data-stu-id="1424b-274">Refers to the collection of information for one sample; that is, a measurement of throughput with a certain concurrency level, in an instant of time.</span></span>|

 <span data-ttu-id="1424b-275">Aşağıdaki tabloda olay verileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1424b-275">The following table shows the event data.</span></span>

|<span data-ttu-id="1424b-276">Alan adı</span><span class="sxs-lookup"><span data-stu-id="1424b-276">Field name</span></span>|<span data-ttu-id="1424b-277">Veri türü</span><span class="sxs-lookup"><span data-stu-id="1424b-277">Data type</span></span>|<span data-ttu-id="1424b-278">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1424b-278">Description</span></span>|
|----------------|---------------|-----------------|
|`Throughput`|`win:Double`|<span data-ttu-id="1424b-279">Zaman birimi başına tamamlama sayısı.</span><span class="sxs-lookup"><span data-stu-id="1424b-279">Number of completions per unit of time.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="1424b-280">CLR veya CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="1424b-280">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="threadpoolworkerthreadadjustmentadjustment-event"></a><span data-ttu-id="1424b-281">Threadpoolworkerthreadadyatmentadolayını ayarlama olayı</span><span class="sxs-lookup"><span data-stu-id="1424b-281">ThreadPoolWorkerThreadAdjustmentAdjustment event</span></span>

 <span data-ttu-id="1424b-282">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1424b-282">The following table shows the keyword and level.</span></span>

|<span data-ttu-id="1424b-283">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="1424b-283">Keyword for raising the event</span></span>|<span data-ttu-id="1424b-284">Level</span><span class="sxs-lookup"><span data-stu-id="1424b-284">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="1424b-285">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="1424b-285">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="1424b-286">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="1424b-286">Informational (4)</span></span>|

 <span data-ttu-id="1424b-287">Aşağıdaki tabloda olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1424b-287">The following table shows the event information.</span></span>

|<span data-ttu-id="1424b-288">Olay</span><span class="sxs-lookup"><span data-stu-id="1424b-288">Event</span></span>|<span data-ttu-id="1424b-289">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="1424b-289">Event ID</span></span>|<span data-ttu-id="1424b-290">Description</span><span class="sxs-lookup"><span data-stu-id="1424b-290">Description</span></span>|
|-----------|--------------|-----------------|
|`ThreadPoolWorkerThreadAdjustmentAdjustment`|<span data-ttu-id="1424b-291">55</span><span class="sxs-lookup"><span data-stu-id="1424b-291">55</span></span>|<span data-ttu-id="1424b-292">İş parçacığı ekleme (Hill-climbing) algoritması eşzamanlılık düzeyindeki bir değişikliğin yerinde olduğunu belirlediğinde denetimdeki bir değişikliği kaydeder.</span><span class="sxs-lookup"><span data-stu-id="1424b-292">Records a change in control, when the thread injection (hill-climbing) algorithm determines that a change in concurrency level is in place.</span></span>|

 <span data-ttu-id="1424b-293">Aşağıdaki tabloda olay verileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1424b-293">The following table shows the event data.</span></span>

|<span data-ttu-id="1424b-294">Alan adı</span><span class="sxs-lookup"><span data-stu-id="1424b-294">Field name</span></span>|<span data-ttu-id="1424b-295">Veri türü</span><span class="sxs-lookup"><span data-stu-id="1424b-295">Data type</span></span>|<span data-ttu-id="1424b-296">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1424b-296">Description</span></span>|
|----------------|---------------|-----------------|
|`AverageThroughput`|`win:Double`|<span data-ttu-id="1424b-297">Ölçüm örneğinin ortalama performansı.</span><span class="sxs-lookup"><span data-stu-id="1424b-297">Average throughput of a sample of measurements.</span></span>|
|`NewWorkerThreadCount`|`win:UInt32`|<span data-ttu-id="1424b-298">Yeni etkin çalışan iş parçacığı sayısı.</span><span class="sxs-lookup"><span data-stu-id="1424b-298">New number of active worker threads.</span></span>|
|`Reason`|`win:UInt32`|<span data-ttu-id="1424b-299">Ayarlamanın nedeni.</span><span class="sxs-lookup"><span data-stu-id="1424b-299">Reason for the adjustment.</span></span><br /><br /> <span data-ttu-id="1424b-300">`0x0` Isınma.</span><span class="sxs-lookup"><span data-stu-id="1424b-300">`0x0` - Warmup.</span></span><br /><br /> <span data-ttu-id="1424b-301">`0x1` Başlatarak.</span><span class="sxs-lookup"><span data-stu-id="1424b-301">`0x1` - Initializing.</span></span><br /><br /> <span data-ttu-id="1424b-302">`0x2` -Rastgele taşı.</span><span class="sxs-lookup"><span data-stu-id="1424b-302">`0x2` - Random move.</span></span><br /><br /> <span data-ttu-id="1424b-303">`0x3` -Geçiş taşı.</span><span class="sxs-lookup"><span data-stu-id="1424b-303">`0x3` - Climbing move.</span></span><br /><br /> <span data-ttu-id="1424b-304">`0x4` -Değişiklik noktası.</span><span class="sxs-lookup"><span data-stu-id="1424b-304">`0x4` - Change point.</span></span><br /><br /> <span data-ttu-id="1424b-305">`0x5` Sabitleniyor.</span><span class="sxs-lookup"><span data-stu-id="1424b-305">`0x5` - Stabilizing.</span></span><br /><br /> <span data-ttu-id="1424b-306">`0x6` Yetersizliğine neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="1424b-306">`0x6` - Starvation.</span></span><br /><br /> <span data-ttu-id="1424b-307">`0x7` -İş parçacığı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="1424b-307">`0x7` - Thread timed out.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="1424b-308">CLR veya CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="1424b-308">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="threadpoolworkerthreadadjustmentstats-event"></a><span data-ttu-id="1424b-309">Threadpoolworkerthreadadadatmentstats olayı</span><span class="sxs-lookup"><span data-stu-id="1424b-309">ThreadPoolWorkerThreadAdjustmentStats event</span></span>

 <span data-ttu-id="1424b-310">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1424b-310">The following table shows the keyword and level.</span></span>

|<span data-ttu-id="1424b-311">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="1424b-311">Keyword for raising the event</span></span>|<span data-ttu-id="1424b-312">Level</span><span class="sxs-lookup"><span data-stu-id="1424b-312">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="1424b-313">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="1424b-313">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="1424b-314">Verbose (5)</span><span class="sxs-lookup"><span data-stu-id="1424b-314">Verbose (5)</span></span>

 <span data-ttu-id="1424b-315">Aşağıdaki tabloda olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1424b-315">The following table shows the event information.</span></span>

|<span data-ttu-id="1424b-316">Olay</span><span class="sxs-lookup"><span data-stu-id="1424b-316">Event</span></span>|<span data-ttu-id="1424b-317">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="1424b-317">Event ID</span></span>|<span data-ttu-id="1424b-318">Description</span><span class="sxs-lookup"><span data-stu-id="1424b-318">Description</span></span>|
|-----------|--------------|-----------------|
|`ThreadPoolWorkerThreadAdjustmentStats`|<span data-ttu-id="1424b-319">56</span><span class="sxs-lookup"><span data-stu-id="1424b-319">56</span></span>|<span data-ttu-id="1424b-320">İş parçacığı havuzundaki verileri toplar.</span><span class="sxs-lookup"><span data-stu-id="1424b-320">Gathers data on the thread pool.</span></span>|

 <span data-ttu-id="1424b-321">Aşağıdaki tabloda olay verileri gösterilmektedir</span><span class="sxs-lookup"><span data-stu-id="1424b-321">The following table shows the event data</span></span>

|<span data-ttu-id="1424b-322">Alan adı</span><span class="sxs-lookup"><span data-stu-id="1424b-322">Field name</span></span>|<span data-ttu-id="1424b-323">Veri türü</span><span class="sxs-lookup"><span data-stu-id="1424b-323">Data type</span></span>|<span data-ttu-id="1424b-324">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1424b-324">Description</span></span>|
|----------------|---------------|-----------------|
|`Duration`|`win:Double`|<span data-ttu-id="1424b-325">Bu istatistiklerin toplandığı sürenin saniye cinsinden miktarı.</span><span class="sxs-lookup"><span data-stu-id="1424b-325">Amount of time, in seconds, during which these statistics were collected.</span></span>|
|`Throughput`|`win:Double`|<span data-ttu-id="1424b-326">Bu Aralık sırasında saniye başına ortalama tamamlama sayısı.</span><span class="sxs-lookup"><span data-stu-id="1424b-326">Average number of completions per second during this interval.</span></span>|
|`ThreadWave`|`win:Double`|<span data-ttu-id="1424b-327">Dahili kullanım için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="1424b-327">Reserved for internal use.</span></span>|
|`ThroughputWave`|`win:Double`|<span data-ttu-id="1424b-328">Dahili kullanım için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="1424b-328">Reserved for internal use.</span></span>|
|`ThroughputErrorEstimate`|`win:Double`|<span data-ttu-id="1424b-329">Dahili kullanım için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="1424b-329">Reserved for internal use.</span></span>|
|`AverageThroughputErrorEstimate`|`win:Double`|<span data-ttu-id="1424b-330">Dahili kullanım için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="1424b-330">Reserved for internal use.</span></span>|
|`ThroughputRatio`|`win:Double`|<span data-ttu-id="1424b-331">Bu zaman aralığı boyunca etkin çalışan iş parçacığı sayısında değişimler nedeniyle üretilen iş akışındaki göreli geliştirme.</span><span class="sxs-lookup"><span data-stu-id="1424b-331">The relative improvement in throughput caused by variations in active worker thread count during this interval.</span></span>|
|`Confidence`|`win:Double`|<span data-ttu-id="1424b-332">ThroughputRatio alanının geçerlilik süresinin ölçüsü.</span><span class="sxs-lookup"><span data-stu-id="1424b-332">A measure of the validity of the ThroughputRatio field.</span></span>|
|`NewcontrolSetting`|`win:Double`|<span data-ttu-id="1424b-333">Etkin iş parçacığı sayısında gelecekteki Çeşitlemeler için temel olarak görev yapacak etkin çalışan iş parçacıklarının sayısı.</span><span class="sxs-lookup"><span data-stu-id="1424b-333">The number of active worker threads that will serve as the baseline for future variations in active thread count.</span></span>|
|`NewThreadWaveMagnitude`|`win:UInt16`|<span data-ttu-id="1424b-334">Etkin iş parçacığı sayısı ' nda gelecekteki varyasyonların büyüklüğü.</span><span class="sxs-lookup"><span data-stu-id="1424b-334">The magnitude of future variations in active thread count.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="1424b-335">CLR veya CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="1424b-335">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="threadpoolenqueue-event"></a><span data-ttu-id="1424b-336">ThreadPoolEnqueue olayı</span><span class="sxs-lookup"><span data-stu-id="1424b-336">ThreadPoolEnqueue event</span></span>

 <span data-ttu-id="1424b-337">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1424b-337">The following table shows the keyword and level.</span></span>

|<span data-ttu-id="1424b-338">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="1424b-338">Keyword for raising the event</span></span>|<span data-ttu-id="1424b-339">Level</span><span class="sxs-lookup"><span data-stu-id="1424b-339">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="1424b-340">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="1424b-340">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="1424b-341">Verbose (5)</span><span class="sxs-lookup"><span data-stu-id="1424b-341">Verbose (5)</span></span>

 <span data-ttu-id="1424b-342">Aşağıdaki tabloda olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1424b-342">The following table shows the event information.</span></span>

|<span data-ttu-id="1424b-343">Olay</span><span class="sxs-lookup"><span data-stu-id="1424b-343">Event</span></span>|<span data-ttu-id="1424b-344">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="1424b-344">Event ID</span></span>|<span data-ttu-id="1424b-345">Description</span><span class="sxs-lookup"><span data-stu-id="1424b-345">Description</span></span>|
|-----------|--------------|-----------------|
|`ThreadPoolEnqueue`|<span data-ttu-id="1424b-346">61</span><span class="sxs-lookup"><span data-stu-id="1424b-346">61</span></span>|<span data-ttu-id="1424b-347">İş öğesi, iş parçacığı havuzu kuyruğunda sıraya alındı.</span><span class="sxs-lookup"><span data-stu-id="1424b-347">A work item was enqueued in the thread pool queue.</span></span>|

 <span data-ttu-id="1424b-348">Aşağıdaki tabloda olay verileri gösterilmektedir</span><span class="sxs-lookup"><span data-stu-id="1424b-348">The following table shows the event data</span></span>

|<span data-ttu-id="1424b-349">Alan adı</span><span class="sxs-lookup"><span data-stu-id="1424b-349">Field name</span></span>|<span data-ttu-id="1424b-350">Veri türü</span><span class="sxs-lookup"><span data-stu-id="1424b-350">Data type</span></span>|<span data-ttu-id="1424b-351">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1424b-351">Description</span></span>|
|----------------|---------------|-----------------|
|`WorkID`|`win:Pointer`|<span data-ttu-id="1424b-352">İş isteğine yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="1424b-352">Pointer to the work request.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="1424b-353">CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="1424b-353">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="threadpooldequeue-event"></a><span data-ttu-id="1424b-354">Threadpoolsıradan çıkarma olayı</span><span class="sxs-lookup"><span data-stu-id="1424b-354">ThreadPoolDequeue event</span></span>

 <span data-ttu-id="1424b-355">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1424b-355">The following table shows the keyword and level.</span></span>

|<span data-ttu-id="1424b-356">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="1424b-356">Keyword for raising the event</span></span>|<span data-ttu-id="1424b-357">Level</span><span class="sxs-lookup"><span data-stu-id="1424b-357">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="1424b-358">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="1424b-358">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="1424b-359">Verbose (5)</span><span class="sxs-lookup"><span data-stu-id="1424b-359">Verbose (5)</span></span>

 <span data-ttu-id="1424b-360">Aşağıdaki tabloda olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1424b-360">The following table shows the event information.</span></span>

|<span data-ttu-id="1424b-361">Olay</span><span class="sxs-lookup"><span data-stu-id="1424b-361">Event</span></span>|<span data-ttu-id="1424b-362">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="1424b-362">Event ID</span></span>|<span data-ttu-id="1424b-363">Description</span><span class="sxs-lookup"><span data-stu-id="1424b-363">Description</span></span>|
|-----------|--------------|-----------------|
|`ThreadPoolDequeue`|<span data-ttu-id="1424b-364">62</span><span class="sxs-lookup"><span data-stu-id="1424b-364">62</span></span>|<span data-ttu-id="1424b-365">İş öğesi, iş parçacığı havuzu sırasından kuyruğa alındı.</span><span class="sxs-lookup"><span data-stu-id="1424b-365">A work item was dequeued from the thread pool queue.</span></span>|

 <span data-ttu-id="1424b-366">Aşağıdaki tabloda olay verileri gösterilmektedir</span><span class="sxs-lookup"><span data-stu-id="1424b-366">The following table shows the event data</span></span>

|<span data-ttu-id="1424b-367">Alan adı</span><span class="sxs-lookup"><span data-stu-id="1424b-367">Field name</span></span>|<span data-ttu-id="1424b-368">Veri türü</span><span class="sxs-lookup"><span data-stu-id="1424b-368">Data type</span></span>|<span data-ttu-id="1424b-369">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1424b-369">Description</span></span>|
|----------------|---------------|-----------------|
|`WorkID`|`win:Pointer`|<span data-ttu-id="1424b-370">İş isteğine yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="1424b-370">Pointer to the work request.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="1424b-371">CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="1424b-371">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="threadpoolioenqueue-event"></a><span data-ttu-id="1424b-372">Threadpokayokuyruğa alma olayı</span><span class="sxs-lookup"><span data-stu-id="1424b-372">ThreadPoolIOEnqueue event</span></span>

 <span data-ttu-id="1424b-373">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1424b-373">The following table shows the keyword and level.</span></span>

|<span data-ttu-id="1424b-374">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="1424b-374">Keyword for raising the event</span></span>|<span data-ttu-id="1424b-375">Level</span><span class="sxs-lookup"><span data-stu-id="1424b-375">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="1424b-376">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="1424b-376">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="1424b-377">Verbose (5)</span><span class="sxs-lookup"><span data-stu-id="1424b-377">Verbose (5)</span></span>

 <span data-ttu-id="1424b-378">Aşağıdaki tabloda olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1424b-378">The following table shows the event information.</span></span>

|<span data-ttu-id="1424b-379">Olay</span><span class="sxs-lookup"><span data-stu-id="1424b-379">Event</span></span>|<span data-ttu-id="1424b-380">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="1424b-380">Event ID</span></span>|<span data-ttu-id="1424b-381">Description</span><span class="sxs-lookup"><span data-stu-id="1424b-381">Description</span></span>|
|-----------|--------------|-----------------|
|`ThreadPoolIOEnqueue`|<span data-ttu-id="1424b-382">63</span><span class="sxs-lookup"><span data-stu-id="1424b-382">63</span></span>|<span data-ttu-id="1424b-383">Bir iş parçacığı, zaman uyumsuz GÇ tamamlandıktan sonra bir GÇ tamamlama bildirimini sıraya alır.</span><span class="sxs-lookup"><span data-stu-id="1424b-383">A thread enqueues an IO completion notification after an async IO completion occurs.</span></span>|

 <span data-ttu-id="1424b-384">Aşağıdaki tabloda olay verileri gösterilmektedir</span><span class="sxs-lookup"><span data-stu-id="1424b-384">The following table shows the event data</span></span>

|<span data-ttu-id="1424b-385">Alan adı</span><span class="sxs-lookup"><span data-stu-id="1424b-385">Field name</span></span>|<span data-ttu-id="1424b-386">Veri türü</span><span class="sxs-lookup"><span data-stu-id="1424b-386">Data type</span></span>|<span data-ttu-id="1424b-387">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1424b-387">Description</span></span>|
|----------------|---------------|-----------------|
|`NativeOverlapped`|`win:Pointer`|<span data-ttu-id="1424b-388">Dahili kullanım için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="1424b-388">Reserved for internal use.</span></span>|
|`Overlapped`|`win:Pointer`|<span data-ttu-id="1424b-389">Dahili kullanım için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="1424b-389">Reserved for internal use.</span></span>|
|`MultiDequeues`|`win:Boolean`|<span data-ttu-id="1424b-390">Dahili kullanım için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="1424b-390">Reserved for internal use.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="1424b-391">CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="1424b-391">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="threadpooliodequeue-event"></a><span data-ttu-id="1424b-392">Threadpokaykıosıradan çıkarma olayı</span><span class="sxs-lookup"><span data-stu-id="1424b-392">ThreadPoolIODequeue event</span></span>

 <span data-ttu-id="1424b-393">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1424b-393">The following table shows the keyword and level.</span></span>

|<span data-ttu-id="1424b-394">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="1424b-394">Keyword for raising the event</span></span>|<span data-ttu-id="1424b-395">Level</span><span class="sxs-lookup"><span data-stu-id="1424b-395">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="1424b-396">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="1424b-396">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="1424b-397">Verbose (5)</span><span class="sxs-lookup"><span data-stu-id="1424b-397">Verbose (5)</span></span>

 <span data-ttu-id="1424b-398">Aşağıdaki tabloda olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1424b-398">The following table shows the event information.</span></span>

|<span data-ttu-id="1424b-399">Olay</span><span class="sxs-lookup"><span data-stu-id="1424b-399">Event</span></span>|<span data-ttu-id="1424b-400">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="1424b-400">Event ID</span></span>|<span data-ttu-id="1424b-401">Description</span><span class="sxs-lookup"><span data-stu-id="1424b-401">Description</span></span>|
|-----------|--------------|-----------------|
|`ThreadPoolIODequeue`|<span data-ttu-id="1424b-402">64</span><span class="sxs-lookup"><span data-stu-id="1424b-402">64</span></span>|<span data-ttu-id="1424b-403">Bir iş parçacığı GÇ tamamlama bildirimini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="1424b-403">A thread dequeues the IO completion notification.</span></span>|

 <span data-ttu-id="1424b-404">Aşağıdaki tabloda olay verileri gösterilmektedir</span><span class="sxs-lookup"><span data-stu-id="1424b-404">The following table shows the event data</span></span>

|<span data-ttu-id="1424b-405">Alan adı</span><span class="sxs-lookup"><span data-stu-id="1424b-405">Field name</span></span>|<span data-ttu-id="1424b-406">Veri türü</span><span class="sxs-lookup"><span data-stu-id="1424b-406">Data type</span></span>|<span data-ttu-id="1424b-407">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1424b-407">Description</span></span>|
|----------------|---------------|-----------------|
|`NativeOverlapped`|`win:Pointer`|<span data-ttu-id="1424b-408">Dahili kullanım için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="1424b-408">Reserved for internal use.</span></span>|
|`Overlapped`|`win:Pointer`|<span data-ttu-id="1424b-409">Dahili kullanım için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="1424b-409">Reserved for internal use.</span></span>|
|`MultiDequeues`|`win:Boolean`|<span data-ttu-id="1424b-410">Dahili kullanım için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="1424b-410">Reserved for internal use.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="1424b-411">CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="1424b-411">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="threadpooliopack-event"></a><span data-ttu-id="1424b-412">ThreadPoolIOPack olayı</span><span class="sxs-lookup"><span data-stu-id="1424b-412">ThreadPoolIOPack event</span></span>

 <span data-ttu-id="1424b-413">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1424b-413">The following table shows the keyword and level.</span></span>

|<span data-ttu-id="1424b-414">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="1424b-414">Keyword for raising the event</span></span>|<span data-ttu-id="1424b-415">Level</span><span class="sxs-lookup"><span data-stu-id="1424b-415">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="1424b-416">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="1424b-416">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="1424b-417">Verbose (5)</span><span class="sxs-lookup"><span data-stu-id="1424b-417">Verbose (5)</span></span>|

 <span data-ttu-id="1424b-418">Aşağıdaki tabloda olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1424b-418">The following table shows the event information.</span></span>

|<span data-ttu-id="1424b-419">Olay</span><span class="sxs-lookup"><span data-stu-id="1424b-419">Event</span></span>|<span data-ttu-id="1424b-420">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="1424b-420">Event ID</span></span>|<span data-ttu-id="1424b-421">Description</span><span class="sxs-lookup"><span data-stu-id="1424b-421">Description</span></span>|
|-----------|--------------|-----------------|
|`ThreadPoolIOPack`|<span data-ttu-id="1424b-422">65</span><span class="sxs-lookup"><span data-stu-id="1424b-422">65</span></span>|<span data-ttu-id="1424b-423">İş parçacığı çakışan GÇ paketi çağırılır.</span><span class="sxs-lookup"><span data-stu-id="1424b-423">ThreadPool overlapped IO pack is called.</span></span>|

 <span data-ttu-id="1424b-424">Aşağıdaki tabloda olay verileri gösterilmektedir</span><span class="sxs-lookup"><span data-stu-id="1424b-424">The following table shows the event data</span></span>

|<span data-ttu-id="1424b-425">Alan adı</span><span class="sxs-lookup"><span data-stu-id="1424b-425">Field name</span></span>|<span data-ttu-id="1424b-426">Veri türü</span><span class="sxs-lookup"><span data-stu-id="1424b-426">Data type</span></span>|<span data-ttu-id="1424b-427">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1424b-427">Description</span></span>|
|----------------|---------------|-----------------|
|`NativeOverlapped`|`win:Pointer`|<span data-ttu-id="1424b-428">Dahili kullanım için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="1424b-428">Reserved for internal use.</span></span>|
|`Overlapped`|`win:Pointer`|<span data-ttu-id="1424b-429">Dahili kullanım için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="1424b-429">Reserved for internal use.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="1424b-430">CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="1424b-430">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="threadcreating-event"></a><span data-ttu-id="1424b-431">Threadevent oluşturma</span><span class="sxs-lookup"><span data-stu-id="1424b-431">ThreadCreating event</span></span>

 <span data-ttu-id="1424b-432">Aşağıdaki tabloda anahtar kelimeleri ve düzeyi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1424b-432">The following table shows the keywords and level.</span></span>

|<span data-ttu-id="1424b-433">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="1424b-433">Keyword for raising the event</span></span>|<span data-ttu-id="1424b-434">Level</span><span class="sxs-lookup"><span data-stu-id="1424b-434">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="1424b-435">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="1424b-435">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="1424b-436">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="1424b-436">Informational (4)</span></span>|

 <span data-ttu-id="1424b-437">Aşağıdaki tabloda olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1424b-437">The following table shows the event information.</span></span>

|<span data-ttu-id="1424b-438">Olay</span><span class="sxs-lookup"><span data-stu-id="1424b-438">Event</span></span>|<span data-ttu-id="1424b-439">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="1424b-439">Event ID</span></span>|<span data-ttu-id="1424b-440">Description</span><span class="sxs-lookup"><span data-stu-id="1424b-440">Description</span></span>|
|----------------|---------------|-----------------|
|`ThreadCreating`|<span data-ttu-id="1424b-441">70</span><span class="sxs-lookup"><span data-stu-id="1424b-441">70</span></span>|<span data-ttu-id="1424b-442">İş parçacığı oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="1424b-442">Thread has been created.</span></span>|

 <span data-ttu-id="1424b-443">Aşağıdaki tabloda olay verileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1424b-443">The following table shows the event data.</span></span>

|<span data-ttu-id="1424b-444">Alan adı</span><span class="sxs-lookup"><span data-stu-id="1424b-444">Field name</span></span>|<span data-ttu-id="1424b-445">Veri türü</span><span class="sxs-lookup"><span data-stu-id="1424b-445">Data type</span></span>|<span data-ttu-id="1424b-446">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1424b-446">Description</span></span>|
|----------------|---------------|-----------------|
|`ID`|`win:Pointer`|<span data-ttu-id="1424b-447">İş parçacığı KIMLIĞI</span><span class="sxs-lookup"><span data-stu-id="1424b-447">Thread ID</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="1424b-448">CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="1424b-448">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="threadrunning-event"></a><span data-ttu-id="1424b-449">ThreadRunning olayı</span><span class="sxs-lookup"><span data-stu-id="1424b-449">ThreadRunning event</span></span>

 <span data-ttu-id="1424b-450">Aşağıdaki tabloda anahtar kelimeleri ve düzeyi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1424b-450">The following table shows the keywords and level.</span></span>

|<span data-ttu-id="1424b-451">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="1424b-451">Keyword for raising the event</span></span>|<span data-ttu-id="1424b-452">Level</span><span class="sxs-lookup"><span data-stu-id="1424b-452">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="1424b-453">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="1424b-453">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="1424b-454">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="1424b-454">Informational (4)</span></span>|

 <span data-ttu-id="1424b-455">Aşağıdaki tabloda olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1424b-455">The following table shows the event information.</span></span>

|<span data-ttu-id="1424b-456">Olay</span><span class="sxs-lookup"><span data-stu-id="1424b-456">Event</span></span>|<span data-ttu-id="1424b-457">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="1424b-457">Event ID</span></span>|<span data-ttu-id="1424b-458">Description</span><span class="sxs-lookup"><span data-stu-id="1424b-458">Description</span></span>|
|----------------|---------------|-----------------|
|`ThreadRunning`|<span data-ttu-id="1424b-459">71</span><span class="sxs-lookup"><span data-stu-id="1424b-459">71</span></span>|<span data-ttu-id="1424b-460">İş parçacığı çalışmaya başladı.</span><span class="sxs-lookup"><span data-stu-id="1424b-460">Thread has started running.</span></span>|

 <span data-ttu-id="1424b-461">Aşağıdaki tabloda olay verileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1424b-461">The following table shows the event data.</span></span>

|<span data-ttu-id="1424b-462">Alan adı</span><span class="sxs-lookup"><span data-stu-id="1424b-462">Field name</span></span>|<span data-ttu-id="1424b-463">Veri türü</span><span class="sxs-lookup"><span data-stu-id="1424b-463">Data type</span></span>|<span data-ttu-id="1424b-464">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1424b-464">Description</span></span>|
|----------------|---------------|-----------------|
|`ID`|`win:Pointer`|<span data-ttu-id="1424b-465">İş parçacığı KIMLIĞI</span><span class="sxs-lookup"><span data-stu-id="1424b-465">Thread ID</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="1424b-466">CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="1424b-466">Unique ID for the instance of CoreCLR.</span></span>|
