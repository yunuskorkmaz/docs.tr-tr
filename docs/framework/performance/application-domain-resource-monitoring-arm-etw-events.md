---
title: Uygulama Etki Alanı Kaynak İzleme (ARM) ETW Olayları
description: .NET 'te ThreadCreated, Appdomainmemalkonumlandırılan, Appdomainmemsurvi, ve daha fazlası gibi uygulama etki alanı kaynak izleme (ARM) ETW olayları hakkında bilgi edinin.
ms.date: 03/30/2017
helpviewer_keywords:
- ETW, application domain monitoring events
- application domain monitoring events [.NET Framework]
ms.assetid: d38ff268-a2ee-434e-b504-d570880e0289
ms.openlocfilehash: d118b3196b019a804df5399464cb86f7492c61b0
ms.sourcegitcommit: 0fa2b7b658bf137e813a7f4d09589d64c148ebf5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/14/2020
ms.locfileid: "86309787"
---
# <a name="application-domain-resource-monitoring-arm-etw-events"></a><span data-ttu-id="ffcf6-103">Uygulama Etki Alanı Kaynak İzleme (ARM) ETW Olayları</span><span class="sxs-lookup"><span data-stu-id="ffcf6-103">Application Domain Resource Monitoring (ARM) ETW Events</span></span>

<span data-ttu-id="ffcf6-104">Bu olaylar, bir uygulama etki alanının durumu hakkında ayrıntılı tanılama bilgileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="ffcf6-104">These events provide detailed diagnostic information about the state of an application domain.</span></span> <span data-ttu-id="ffcf6-105">Aynı bilgileri elde etmek için bu olayları kullanabilir veya uygulama etki alanı kaynak izleme (ARM) özelliğini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ffcf6-105">You can use these events or use the application domain resource monitoring (ARM) feature to obtain the same information.</span></span>

## <a name="threadcreated-event"></a><span data-ttu-id="ffcf6-106">ThreadCreated olayı</span><span class="sxs-lookup"><span data-stu-id="ffcf6-106">ThreadCreated Event</span></span>

<span data-ttu-id="ffcf6-107">Bu olay Ayrıca, Özet sağlayıcının altında `ThreadDC` (anahtar sözcüğünün altında) de oluşturulur `AppDomainResourceManagementRundownKeyword` .</span><span class="sxs-lookup"><span data-stu-id="ffcf6-107">This event is also raised  under the rundown provider as `ThreadDC` (under the `AppDomainResourceManagementRundownKeyword` keyword).</span></span> <span data-ttu-id="ffcf6-108">Bu, bu kategorideki özet sağlayıcı altında oluşturulan tek olaydır.</span><span class="sxs-lookup"><span data-stu-id="ffcf6-108">This is the only event that is raised under the rundown provider in this category.</span></span>

<span data-ttu-id="ffcf6-109">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="ffcf6-109">The following table shows the keyword and level.</span></span> <span data-ttu-id="ffcf6-110">Daha fazla bilgi için bkz. [CLR ETW anahtar sözcükleri ve düzeyleri](clr-etw-keywords-and-levels.md).</span><span class="sxs-lookup"><span data-stu-id="ffcf6-110">For more information, see [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).</span></span>

|<span data-ttu-id="ffcf6-111">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="ffcf6-111">Keyword for raising the event</span></span>|<span data-ttu-id="ffcf6-112">Düzey</span><span class="sxs-lookup"><span data-stu-id="ffcf6-112">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="ffcf6-113">`AppDomainResourceManagementKeyword`0x800</span><span class="sxs-lookup"><span data-stu-id="ffcf6-113">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="ffcf6-114">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="ffcf6-114">Informational(4)</span></span>|
|<span data-ttu-id="ffcf6-115">`ThreadingKeyword`(0x10000)</span><span class="sxs-lookup"><span data-stu-id="ffcf6-115">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="ffcf6-116">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="ffcf6-116">Informational(4)</span></span>|

<span data-ttu-id="ffcf6-117">Aşağıdaki tabloda olay bilgileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="ffcf6-117">The following table shows the event information:</span></span>

|<span data-ttu-id="ffcf6-118">Olay</span><span class="sxs-lookup"><span data-stu-id="ffcf6-118">Event</span></span>|<span data-ttu-id="ffcf6-119">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="ffcf6-119">Event ID</span></span>|<span data-ttu-id="ffcf6-120">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="ffcf6-120">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ThreadCreated`|<span data-ttu-id="ffcf6-121">85</span><span class="sxs-lookup"><span data-stu-id="ffcf6-121">85</span></span>|<span data-ttu-id="ffcf6-122">Uygulama etki alanı için bir iş parçacığı oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="ffcf6-122">A thread was created for the application domain.</span></span>|

<span data-ttu-id="ffcf6-123">Aşağıdaki tabloda olay verileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="ffcf6-123">The following table shows the event data:</span></span>

|<span data-ttu-id="ffcf6-124">Alan adı</span><span class="sxs-lookup"><span data-stu-id="ffcf6-124">Field name</span></span>|<span data-ttu-id="ffcf6-125">Veri türü</span><span class="sxs-lookup"><span data-stu-id="ffcf6-125">Data type</span></span>|<span data-ttu-id="ffcf6-126">Description</span><span class="sxs-lookup"><span data-stu-id="ffcf6-126">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="ffcf6-127">ThreadID</span><span class="sxs-lookup"><span data-stu-id="ffcf6-127">ThreadID</span></span>|<span data-ttu-id="ffcf6-128">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="ffcf6-128">win:UInt64</span></span>|<span data-ttu-id="ffcf6-129">Oluşturulan iş parçacığının KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="ffcf6-129">ID of the thread that was created.</span></span>|
|<span data-ttu-id="ffcf6-130">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="ffcf6-130">AppDomainID</span></span>|<span data-ttu-id="ffcf6-131">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="ffcf6-131">win:UInt64</span></span>|<span data-ttu-id="ffcf6-132">İş parçacığı etkinliğinin bildirildiği uygulama etki alanının tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="ffcf6-132">Identifier of the application domain for which thread activity is being reported.</span></span>|
|<span data-ttu-id="ffcf6-133">Bayraklar</span><span class="sxs-lookup"><span data-stu-id="ffcf6-133">Flags</span></span>|<span data-ttu-id="ffcf6-134">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="ffcf6-134">win:UInt32</span></span>|<span data-ttu-id="ffcf6-135">İş parçacığı oluşturma bayrakları.</span><span class="sxs-lookup"><span data-stu-id="ffcf6-135">Thread creation flags.</span></span>|
|<span data-ttu-id="ffcf6-136">Managedthreadındex</span><span class="sxs-lookup"><span data-stu-id="ffcf6-136">ManagedThreadIndex</span></span>|<span data-ttu-id="ffcf6-137">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="ffcf6-137">win:UInt32</span></span>|<span data-ttu-id="ffcf6-138">Oluşturulan iş parçacığının yönetilen dizini.</span><span class="sxs-lookup"><span data-stu-id="ffcf6-138">Managed index of the thread that was created.</span></span>|
|<span data-ttu-id="ffcf6-139">OSThreadId</span><span class="sxs-lookup"><span data-stu-id="ffcf6-139">OSThreadID</span></span>|<span data-ttu-id="ffcf6-140">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="ffcf6-140">win:UInt32</span></span>|<span data-ttu-id="ffcf6-141">Oluşturulan iş parçacığının işletim sistemi KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="ffcf6-141">Operating system ID of the thread that was created.</span></span>|
|<span data-ttu-id="ffcf6-142">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="ffcf6-142">ClrInstanceID</span></span>|<span data-ttu-id="ffcf6-143">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="ffcf6-143">win:UInt16</span></span>|<span data-ttu-id="ffcf6-144">CLR veya CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="ffcf6-144">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="appdomainmemallocated-event"></a><span data-ttu-id="ffcf6-145">Appdomainmemalbulunan olay</span><span class="sxs-lookup"><span data-stu-id="ffcf6-145">AppDomainMemAllocated Event</span></span>

<span data-ttu-id="ffcf6-146">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="ffcf6-146">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="ffcf6-147">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="ffcf6-147">Keyword for raising the event</span></span>|<span data-ttu-id="ffcf6-148">Düzey</span><span class="sxs-lookup"><span data-stu-id="ffcf6-148">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="ffcf6-149">`AppDomainResourceManagementKeyword`0x800</span><span class="sxs-lookup"><span data-stu-id="ffcf6-149">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="ffcf6-150">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="ffcf6-150">Informational(4)</span></span>|

<span data-ttu-id="ffcf6-151">Aşağıdaki tabloda olay bilgileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="ffcf6-151">The following table shows the event information:</span></span>

|<span data-ttu-id="ffcf6-152">Olay</span><span class="sxs-lookup"><span data-stu-id="ffcf6-152">Event</span></span>|<span data-ttu-id="ffcf6-153">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="ffcf6-153">Event ID</span></span>|<span data-ttu-id="ffcf6-154">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="ffcf6-154">Raised when</span></span>|
|-----------|--------------|-----------------|
|`AppDomainMemAllocated`|<span data-ttu-id="ffcf6-155">83</span><span class="sxs-lookup"><span data-stu-id="ffcf6-155">83</span></span>|<span data-ttu-id="ffcf6-156">Uygulama etki alanında her 4 MB bellek (yaklaşık olarak) ayrılır.</span><span class="sxs-lookup"><span data-stu-id="ffcf6-156">Every 4 MB of memory (approximately) is allocated in the application domain.</span></span>|

<span data-ttu-id="ffcf6-157">Aşağıdaki tabloda olay verileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="ffcf6-157">The following table shows the event data:</span></span>

|<span data-ttu-id="ffcf6-158">Alan adı</span><span class="sxs-lookup"><span data-stu-id="ffcf6-158">Field name</span></span>|<span data-ttu-id="ffcf6-159">Veri türü</span><span class="sxs-lookup"><span data-stu-id="ffcf6-159">Data type</span></span>|<span data-ttu-id="ffcf6-160">Description</span><span class="sxs-lookup"><span data-stu-id="ffcf6-160">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="ffcf6-161">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="ffcf6-161">AppDomainID</span></span>|<span data-ttu-id="ffcf6-162">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="ffcf6-162">win:UInt64</span></span>|<span data-ttu-id="ffcf6-163">Kaynak kullanımının bildirildiği uygulama etki alanının tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="ffcf6-163">Identifier of the application domain for which resource usage is being reported.</span></span>|
|<span data-ttu-id="ffcf6-164">Ayrılabilir</span><span class="sxs-lookup"><span data-stu-id="ffcf6-164">Allocated</span></span>|<span data-ttu-id="ffcf6-165">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="ffcf6-165">win:UInt64</span></span>|<span data-ttu-id="ffcf6-166">Uygulama etki alanı oluşturulduğundan bu yana bu uygulama etki alanında ayrılan toplam bayt sayısı (serbest bırakılan bellek miktarı çıkarıldı).</span><span class="sxs-lookup"><span data-stu-id="ffcf6-166">The total number of bytes allocated in this application domain since the application domain was created (the amount of freed memory is not subtracted).</span></span>|
|<span data-ttu-id="ffcf6-167">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="ffcf6-167">ClrInstanceID</span></span>|<span data-ttu-id="ffcf6-168">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="ffcf6-168">win:UInt16</span></span>|<span data-ttu-id="ffcf6-169">CLR veya CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="ffcf6-169">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="appdomainmemsurvived-event"></a><span data-ttu-id="ffcf6-170">Appdomainmemsurvilenmiş olay</span><span class="sxs-lookup"><span data-stu-id="ffcf6-170">AppDomainMemSurvived Event</span></span>

<span data-ttu-id="ffcf6-171">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="ffcf6-171">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="ffcf6-172">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="ffcf6-172">Keyword for raising the event</span></span>|<span data-ttu-id="ffcf6-173">Düzey</span><span class="sxs-lookup"><span data-stu-id="ffcf6-173">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="ffcf6-174">`AppDomainResourceManagementKeyword`0x800</span><span class="sxs-lookup"><span data-stu-id="ffcf6-174">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="ffcf6-175">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="ffcf6-175">Informational(4)</span></span>|

<span data-ttu-id="ffcf6-176">Aşağıdaki tabloda olay bilgileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="ffcf6-176">The following table shows the event information:</span></span>

|<span data-ttu-id="ffcf6-177">Olay</span><span class="sxs-lookup"><span data-stu-id="ffcf6-177">Event</span></span>|<span data-ttu-id="ffcf6-178">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="ffcf6-178">Event ID</span></span>|<span data-ttu-id="ffcf6-179">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="ffcf6-179">Raised when</span></span>|
|-----------|--------------|-----------------|
|`AppDomainMemSurvived`|<span data-ttu-id="ffcf6-180">84</span><span class="sxs-lookup"><span data-stu-id="ffcf6-180">84</span></span>|<span data-ttu-id="ffcf6-181">Her çöp toplama işlemi sona erdi.</span><span class="sxs-lookup"><span data-stu-id="ffcf6-181">Each garbage collection has ended.</span></span>|

<span data-ttu-id="ffcf6-182">Aşağıdaki tabloda olay verileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="ffcf6-182">The following table shows the event data:</span></span>

|<span data-ttu-id="ffcf6-183">Alan adı</span><span class="sxs-lookup"><span data-stu-id="ffcf6-183">Field name</span></span>|<span data-ttu-id="ffcf6-184">Veri türü</span><span class="sxs-lookup"><span data-stu-id="ffcf6-184">Data type</span></span>|<span data-ttu-id="ffcf6-185">Description</span><span class="sxs-lookup"><span data-stu-id="ffcf6-185">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="ffcf6-186">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="ffcf6-186">AppDomainID</span></span>|<span data-ttu-id="ffcf6-187">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="ffcf6-187">win:UInt64</span></span>|<span data-ttu-id="ffcf6-188">Kaynak kullanımının bildirildiği etki alanının tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="ffcf6-188">Identifier of the domain for which resource usage is being reported.</span></span>|
|<span data-ttu-id="ffcf6-189">Kalan</span><span class="sxs-lookup"><span data-stu-id="ffcf6-189">Survived</span></span>|<span data-ttu-id="ffcf6-190">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="ffcf6-190">win:UInt64</span></span>|<span data-ttu-id="ffcf6-191">Son koleksiyondan sonra kalan ve bu uygulama etki alanı tarafından tutulması bilinen bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="ffcf6-191">The number of bytes that survived after the last collection and that are known to be held by this application domain.</span></span> <span data-ttu-id="ffcf6-192">Bu sayı doğru ve tam bir koleksiyon sonrasında tamamlanır, ancak kısa ömürlü bir koleksiyon sonrasında tamamlanmamış olabilir.</span><span class="sxs-lookup"><span data-stu-id="ffcf6-192">This number is accurate and complete after a full collection, but may be incomplete after an ephemeral collection.</span></span>|
|<span data-ttu-id="ffcf6-193">Processsurviks</span><span class="sxs-lookup"><span data-stu-id="ffcf6-193">ProcessSurvived</span></span>|<span data-ttu-id="ffcf6-194">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="ffcf6-194">win:UInt64</span></span>|<span data-ttu-id="ffcf6-195">Son koleksiyondan kalan toplam bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="ffcf6-195">The total bytes that survived from the last collection.</span></span> <span data-ttu-id="ffcf6-196">Tam bir koleksiyon sonrasında bu sayı, yönetilen yığınlardaki etkin tutulan bayt sayısını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="ffcf6-196">After a full collection, this number represents the number of bytes being held live in managed heaps.</span></span> <span data-ttu-id="ffcf6-197">Kısa ömürlü bir koleksiyondan sonra bu sayı, kısa ömürlü neslerde bulunan baytların sayısını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="ffcf6-197">After an ephemeral collection, this number represents the number of bytes held live in ephemeral generations.</span></span>|
|<span data-ttu-id="ffcf6-198">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="ffcf6-198">ClrInstanceID</span></span>|<span data-ttu-id="ffcf6-199">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="ffcf6-199">win:UInt16</span></span>|<span data-ttu-id="ffcf6-200">CLR veya CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="ffcf6-200">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="threadappdomainenter-event"></a><span data-ttu-id="ffcf6-201">ThreadAppDomainEnter olayı</span><span class="sxs-lookup"><span data-stu-id="ffcf6-201">ThreadAppDomainEnter Event</span></span>

<span data-ttu-id="ffcf6-202">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="ffcf6-202">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="ffcf6-203">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="ffcf6-203">Keyword for raising the event</span></span>|<span data-ttu-id="ffcf6-204">Düzey</span><span class="sxs-lookup"><span data-stu-id="ffcf6-204">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="ffcf6-205">`AppDomainResourceManagementKeyword`0x800</span><span class="sxs-lookup"><span data-stu-id="ffcf6-205">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="ffcf6-206">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="ffcf6-206">Informational(4)</span></span>|
|<span data-ttu-id="ffcf6-207">`ThreadingKeyword`(0x10000)</span><span class="sxs-lookup"><span data-stu-id="ffcf6-207">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="ffcf6-208">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="ffcf6-208">Informational(4)</span></span>|

<span data-ttu-id="ffcf6-209">Aşağıdaki tabloda olay bilgileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="ffcf6-209">The following table shows the event information:</span></span>

|<span data-ttu-id="ffcf6-210">Olay</span><span class="sxs-lookup"><span data-stu-id="ffcf6-210">Event</span></span>|<span data-ttu-id="ffcf6-211">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="ffcf6-211">Event ID</span></span>|<span data-ttu-id="ffcf6-212">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="ffcf6-212">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ThreadAppDomainEnter`|<span data-ttu-id="ffcf6-213">87</span><span class="sxs-lookup"><span data-stu-id="ffcf6-213">87</span></span>|<span data-ttu-id="ffcf6-214">Bir iş parçacığı bir uygulama etki alanı girer.</span><span class="sxs-lookup"><span data-stu-id="ffcf6-214">A thread enters an application domain.</span></span>|

<span data-ttu-id="ffcf6-215">Aşağıdaki tabloda olay verileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="ffcf6-215">The following table shows the event data:</span></span>

|<span data-ttu-id="ffcf6-216">Alan adı</span><span class="sxs-lookup"><span data-stu-id="ffcf6-216">Field name</span></span>|<span data-ttu-id="ffcf6-217">Veri türü</span><span class="sxs-lookup"><span data-stu-id="ffcf6-217">Data type</span></span>|<span data-ttu-id="ffcf6-218">Description</span><span class="sxs-lookup"><span data-stu-id="ffcf6-218">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="ffcf6-219">ThreadID</span><span class="sxs-lookup"><span data-stu-id="ffcf6-219">ThreadID</span></span>|<span data-ttu-id="ffcf6-220">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="ffcf6-220">win:UInt64</span></span>|<span data-ttu-id="ffcf6-221">İş parçacığı tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="ffcf6-221">The thread identifier.</span></span>|
|<span data-ttu-id="ffcf6-222">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="ffcf6-222">AppDomainID</span></span>|<span data-ttu-id="ffcf6-223">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="ffcf6-223">win:UInt64</span></span>|<span data-ttu-id="ffcf6-224">Uygulama etki alanı tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="ffcf6-224">The application domain identifier.</span></span>|
|<span data-ttu-id="ffcf6-225">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="ffcf6-225">ClrInstanceID</span></span>|<span data-ttu-id="ffcf6-226">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="ffcf6-226">win:UInt16</span></span>|<span data-ttu-id="ffcf6-227">CLR veya CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="ffcf6-227">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="threadterminated-event"></a><span data-ttu-id="ffcf6-228">Threadsonlandırılmış olay</span><span class="sxs-lookup"><span data-stu-id="ffcf6-228">ThreadTerminated Event</span></span>

<span data-ttu-id="ffcf6-229">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="ffcf6-229">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="ffcf6-230">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="ffcf6-230">Keyword for raising the event</span></span>|<span data-ttu-id="ffcf6-231">Düzey</span><span class="sxs-lookup"><span data-stu-id="ffcf6-231">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="ffcf6-232">`AppDomainResourceManagementKeyword`0x800</span><span class="sxs-lookup"><span data-stu-id="ffcf6-232">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="ffcf6-233">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="ffcf6-233">Informational(4)</span></span>|
|<span data-ttu-id="ffcf6-234">`ThreadingKeyword`(0x10000)</span><span class="sxs-lookup"><span data-stu-id="ffcf6-234">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="ffcf6-235">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="ffcf6-235">Informational(4)</span></span>|

<span data-ttu-id="ffcf6-236">Aşağıdaki tabloda olay bilgileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="ffcf6-236">The following table shows the event information:</span></span>

|<span data-ttu-id="ffcf6-237">Olay</span><span class="sxs-lookup"><span data-stu-id="ffcf6-237">Event</span></span>|<span data-ttu-id="ffcf6-238">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="ffcf6-238">Event ID</span></span>|<span data-ttu-id="ffcf6-239">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="ffcf6-239">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ThreadTerminated`|<span data-ttu-id="ffcf6-240">86</span><span class="sxs-lookup"><span data-stu-id="ffcf6-240">86</span></span>|<span data-ttu-id="ffcf6-241">Bir iş parçacığı sonlanır.</span><span class="sxs-lookup"><span data-stu-id="ffcf6-241">A thread terminates.</span></span>|

<span data-ttu-id="ffcf6-242">Aşağıdaki tabloda olay verileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="ffcf6-242">The following table shows the event data:</span></span>

|<span data-ttu-id="ffcf6-243">Alan adı</span><span class="sxs-lookup"><span data-stu-id="ffcf6-243">Field name</span></span>|<span data-ttu-id="ffcf6-244">Veri türü</span><span class="sxs-lookup"><span data-stu-id="ffcf6-244">Data type</span></span>|<span data-ttu-id="ffcf6-245">Description</span><span class="sxs-lookup"><span data-stu-id="ffcf6-245">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="ffcf6-246">ThreadID</span><span class="sxs-lookup"><span data-stu-id="ffcf6-246">ThreadID</span></span>|<span data-ttu-id="ffcf6-247">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="ffcf6-247">win:UInt64</span></span>|<span data-ttu-id="ffcf6-248">İş parçacığı tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="ffcf6-248">The thread identifier.</span></span>|
|<span data-ttu-id="ffcf6-249">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="ffcf6-249">AppDomainID</span></span>|<span data-ttu-id="ffcf6-250">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="ffcf6-250">win:UInt64</span></span>|<span data-ttu-id="ffcf6-251">Uygulama etki alanı tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="ffcf6-251">The application domain identifier.</span></span>|
|<span data-ttu-id="ffcf6-252">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="ffcf6-252">ClrInstanceID</span></span>|<span data-ttu-id="ffcf6-253">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="ffcf6-253">win:UInt16</span></span>|<span data-ttu-id="ffcf6-254">CLR veya CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="ffcf6-254">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="see-also"></a><span data-ttu-id="ffcf6-255">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ffcf6-255">See also</span></span>

- [<span data-ttu-id="ffcf6-256">CLR ETW Olayları</span><span class="sxs-lookup"><span data-stu-id="ffcf6-256">CLR ETW Events</span></span>](clr-etw-events.md)
