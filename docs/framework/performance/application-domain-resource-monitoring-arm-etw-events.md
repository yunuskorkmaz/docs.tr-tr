---
title: Uygulama Etki Alanı Kaynak İzleme (ARM) ETW Olayları
ms.date: 03/30/2017
helpviewer_keywords:
- ETW, application domain monitoring events
- application domain monitoring events [.NET Framework]
ms.assetid: d38ff268-a2ee-434e-b504-d570880e0289
ms.openlocfilehash: 0e453b2bafffd9e07a1bdddd97282c5b97f5483d
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75716224"
---
# <a name="application-domain-resource-monitoring-arm-etw-events"></a><span data-ttu-id="2bbfa-102">Uygulama Etki Alanı Kaynak İzleme (ARM) ETW Olayları</span><span class="sxs-lookup"><span data-stu-id="2bbfa-102">Application Domain Resource Monitoring (ARM) ETW Events</span></span>

<span data-ttu-id="2bbfa-103">Bu olaylar, bir uygulama etki alanının durumu hakkında ayrıntılı tanılama bilgileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="2bbfa-103">These events provide detailed diagnostic information about the state of an application domain.</span></span> <span data-ttu-id="2bbfa-104">Aynı bilgileri elde etmek için bu olayları kullanabilir veya uygulama etki alanı kaynak izleme (ARM) özelliğini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2bbfa-104">You can use these events or use the application domain resource monitoring (ARM) feature to obtain the same information.</span></span>

## <a name="threadcreated-event"></a><span data-ttu-id="2bbfa-105">ThreadCreated olayı</span><span class="sxs-lookup"><span data-stu-id="2bbfa-105">ThreadCreated Event</span></span>

<span data-ttu-id="2bbfa-106">Bu olay Ayrıca, `ThreadDC` (`AppDomainResourceManagementRundownKeyword` anahtar sözcüğünün altında) olarak runaşağı sağlayıcı altında da oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="2bbfa-106">This event is also raised  under the rundown provider as `ThreadDC` (under the `AppDomainResourceManagementRundownKeyword` keyword).</span></span> <span data-ttu-id="2bbfa-107">Bu, bu kategorideki özet sağlayıcı altında oluşturulan tek olaydır.</span><span class="sxs-lookup"><span data-stu-id="2bbfa-107">This is the only event that is raised under the rundown provider in this category.</span></span>

<span data-ttu-id="2bbfa-108">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="2bbfa-108">The following table shows the keyword and level.</span></span> <span data-ttu-id="2bbfa-109">Daha fazla bilgi için bkz. [CLR ETW anahtar sözcükleri ve düzeyleri](clr-etw-keywords-and-levels.md).</span><span class="sxs-lookup"><span data-stu-id="2bbfa-109">For more information, see [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).</span></span>

|<span data-ttu-id="2bbfa-110">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="2bbfa-110">Keyword for raising the event</span></span>|<span data-ttu-id="2bbfa-111">Düzey</span><span class="sxs-lookup"><span data-stu-id="2bbfa-111">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="2bbfa-112">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="2bbfa-112">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="2bbfa-113">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="2bbfa-113">Informational(4)</span></span>|
|<span data-ttu-id="2bbfa-114">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="2bbfa-114">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="2bbfa-115">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="2bbfa-115">Informational(4)</span></span>|

<span data-ttu-id="2bbfa-116">Aşağıdaki tabloda olay bilgileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="2bbfa-116">The following table shows the event information:</span></span>

|<span data-ttu-id="2bbfa-117">Olay</span><span class="sxs-lookup"><span data-stu-id="2bbfa-117">Event</span></span>|<span data-ttu-id="2bbfa-118">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="2bbfa-118">Event ID</span></span>|<span data-ttu-id="2bbfa-119">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="2bbfa-119">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ThreadCreated`|<span data-ttu-id="2bbfa-120">85</span><span class="sxs-lookup"><span data-stu-id="2bbfa-120">85</span></span>|<span data-ttu-id="2bbfa-121">Uygulama etki alanı için bir iş parçacığı oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="2bbfa-121">A thread was created for the application domain.</span></span>|

<span data-ttu-id="2bbfa-122">Aşağıdaki tabloda olay verileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="2bbfa-122">The following table shows the event data:</span></span>

|<span data-ttu-id="2bbfa-123">Alan adı</span><span class="sxs-lookup"><span data-stu-id="2bbfa-123">Field name</span></span>|<span data-ttu-id="2bbfa-124">Veri türü</span><span class="sxs-lookup"><span data-stu-id="2bbfa-124">Data type</span></span>|<span data-ttu-id="2bbfa-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2bbfa-125">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="2bbfa-126">ThreadID</span><span class="sxs-lookup"><span data-stu-id="2bbfa-126">ThreadID</span></span>|<span data-ttu-id="2bbfa-127">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="2bbfa-127">win:UInt64</span></span>|<span data-ttu-id="2bbfa-128">Oluşturulan iş parçacığının KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="2bbfa-128">ID of the thread that was created.</span></span>|
|<span data-ttu-id="2bbfa-129">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="2bbfa-129">AppDomainID</span></span>|<span data-ttu-id="2bbfa-130">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="2bbfa-130">win:UInt64</span></span>|<span data-ttu-id="2bbfa-131">İş parçacığı etkinliğinin bildirildiği uygulama etki alanının tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="2bbfa-131">Identifier of the application domain for which thread activity is being reported.</span></span>|
|<span data-ttu-id="2bbfa-132">Bayraklar</span><span class="sxs-lookup"><span data-stu-id="2bbfa-132">Flags</span></span>|<span data-ttu-id="2bbfa-133">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="2bbfa-133">win:UInt32</span></span>|<span data-ttu-id="2bbfa-134">İş parçacığı oluşturma bayrakları.</span><span class="sxs-lookup"><span data-stu-id="2bbfa-134">Thread creation flags.</span></span>|
|<span data-ttu-id="2bbfa-135">Managedthreadındex</span><span class="sxs-lookup"><span data-stu-id="2bbfa-135">ManagedThreadIndex</span></span>|<span data-ttu-id="2bbfa-136">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="2bbfa-136">win:UInt32</span></span>|<span data-ttu-id="2bbfa-137">Oluşturulan iş parçacığının yönetilen dizini.</span><span class="sxs-lookup"><span data-stu-id="2bbfa-137">Managed index of the thread that was created.</span></span>|
|<span data-ttu-id="2bbfa-138">OSThreadId</span><span class="sxs-lookup"><span data-stu-id="2bbfa-138">OSThreadID</span></span>|<span data-ttu-id="2bbfa-139">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="2bbfa-139">win:UInt32</span></span>|<span data-ttu-id="2bbfa-140">Oluşturulan iş parçacığının işletim sistemi KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="2bbfa-140">Operating system ID of the thread that was created.</span></span>|
|<span data-ttu-id="2bbfa-141">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="2bbfa-141">ClrInstanceID</span></span>|<span data-ttu-id="2bbfa-142">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="2bbfa-142">win:UInt16</span></span>|<span data-ttu-id="2bbfa-143">CLR veya CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="2bbfa-143">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="appdomainmemallocated-event"></a><span data-ttu-id="2bbfa-144">Appdomainmemalbulunan olay</span><span class="sxs-lookup"><span data-stu-id="2bbfa-144">AppDomainMemAllocated Event</span></span>

<span data-ttu-id="2bbfa-145">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="2bbfa-145">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="2bbfa-146">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="2bbfa-146">Keyword for raising the event</span></span>|<span data-ttu-id="2bbfa-147">Düzey</span><span class="sxs-lookup"><span data-stu-id="2bbfa-147">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="2bbfa-148">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="2bbfa-148">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="2bbfa-149">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="2bbfa-149">Informational(4)</span></span>|

<span data-ttu-id="2bbfa-150">Aşağıdaki tabloda olay bilgileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="2bbfa-150">The following table shows the event information:</span></span>

|<span data-ttu-id="2bbfa-151">Olay</span><span class="sxs-lookup"><span data-stu-id="2bbfa-151">Event</span></span>|<span data-ttu-id="2bbfa-152">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="2bbfa-152">Event ID</span></span>|<span data-ttu-id="2bbfa-153">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="2bbfa-153">Raised when</span></span>|
|-----------|--------------|-----------------|
|`AppDomainMemAllocated`|<span data-ttu-id="2bbfa-154">83</span><span class="sxs-lookup"><span data-stu-id="2bbfa-154">83</span></span>|<span data-ttu-id="2bbfa-155">Uygulama etki alanında her 4 MB bellek (yaklaşık olarak) ayrılır.</span><span class="sxs-lookup"><span data-stu-id="2bbfa-155">Every 4 MB of memory (approximately) is allocated in the application domain.</span></span>|

<span data-ttu-id="2bbfa-156">Aşağıdaki tabloda olay verileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="2bbfa-156">The following table shows the event data:</span></span>

|<span data-ttu-id="2bbfa-157">Alan adı</span><span class="sxs-lookup"><span data-stu-id="2bbfa-157">Field name</span></span>|<span data-ttu-id="2bbfa-158">Veri türü</span><span class="sxs-lookup"><span data-stu-id="2bbfa-158">Data type</span></span>|<span data-ttu-id="2bbfa-159">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2bbfa-159">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="2bbfa-160">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="2bbfa-160">AppDomainID</span></span>|<span data-ttu-id="2bbfa-161">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="2bbfa-161">win:UInt64</span></span>|<span data-ttu-id="2bbfa-162">Kaynak kullanımının bildirildiği uygulama etki alanının tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="2bbfa-162">Identifier of the application domain for which resource usage is being reported.</span></span>|
|<span data-ttu-id="2bbfa-163">Ayrılabilir</span><span class="sxs-lookup"><span data-stu-id="2bbfa-163">Allocated</span></span>|<span data-ttu-id="2bbfa-164">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="2bbfa-164">win:UInt64</span></span>|<span data-ttu-id="2bbfa-165">Uygulama etki alanı oluşturulduğundan bu yana bu uygulama etki alanında ayrılan toplam bayt sayısı (serbest bırakılan bellek miktarı çıkarıldı).</span><span class="sxs-lookup"><span data-stu-id="2bbfa-165">The total number of bytes allocated in this application domain since the application domain was created (the amount of freed memory is not subtracted).</span></span>|
|<span data-ttu-id="2bbfa-166">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="2bbfa-166">ClrInstanceID</span></span>|<span data-ttu-id="2bbfa-167">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="2bbfa-167">win:UInt16</span></span>|<span data-ttu-id="2bbfa-168">CLR veya CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="2bbfa-168">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="appdomainmemsurvived-event"></a><span data-ttu-id="2bbfa-169">Appdomainmemsurvilenmiş olay</span><span class="sxs-lookup"><span data-stu-id="2bbfa-169">AppDomainMemSurvived Event</span></span>

<span data-ttu-id="2bbfa-170">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="2bbfa-170">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="2bbfa-171">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="2bbfa-171">Keyword for raising the event</span></span>|<span data-ttu-id="2bbfa-172">Düzey</span><span class="sxs-lookup"><span data-stu-id="2bbfa-172">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="2bbfa-173">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="2bbfa-173">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="2bbfa-174">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="2bbfa-174">Informational(4)</span></span>|

<span data-ttu-id="2bbfa-175">Aşağıdaki tabloda olay bilgileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="2bbfa-175">The following table shows the event information:</span></span>

|<span data-ttu-id="2bbfa-176">Olay</span><span class="sxs-lookup"><span data-stu-id="2bbfa-176">Event</span></span>|<span data-ttu-id="2bbfa-177">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="2bbfa-177">Event ID</span></span>|<span data-ttu-id="2bbfa-178">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="2bbfa-178">Raised when</span></span>|
|-----------|--------------|-----------------|
|`AppDomainMemSurvived`|<span data-ttu-id="2bbfa-179">84</span><span class="sxs-lookup"><span data-stu-id="2bbfa-179">84</span></span>|<span data-ttu-id="2bbfa-180">Her çöp toplama işlemi sona erdi.</span><span class="sxs-lookup"><span data-stu-id="2bbfa-180">Each garbage collection has ended.</span></span>|

<span data-ttu-id="2bbfa-181">Aşağıdaki tabloda olay verileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="2bbfa-181">The following table shows the event data:</span></span>

|<span data-ttu-id="2bbfa-182">Alan adı</span><span class="sxs-lookup"><span data-stu-id="2bbfa-182">Field name</span></span>|<span data-ttu-id="2bbfa-183">Veri türü</span><span class="sxs-lookup"><span data-stu-id="2bbfa-183">Data type</span></span>|<span data-ttu-id="2bbfa-184">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2bbfa-184">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="2bbfa-185">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="2bbfa-185">AppDomainID</span></span>|<span data-ttu-id="2bbfa-186">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="2bbfa-186">win:UInt64</span></span>|<span data-ttu-id="2bbfa-187">Kaynak kullanımının bildirildiği etki alanının tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="2bbfa-187">Identifier of the domain for which resource usage is being reported.</span></span>|
|<span data-ttu-id="2bbfa-188">Kalan</span><span class="sxs-lookup"><span data-stu-id="2bbfa-188">Survived</span></span>|<span data-ttu-id="2bbfa-189">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="2bbfa-189">win:UInt64</span></span>|<span data-ttu-id="2bbfa-190">Son koleksiyondan sonra kalan ve bu uygulama etki alanı tarafından tutulması bilinen bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="2bbfa-190">The number of bytes that survived after the last collection and that are known to be held by this application domain.</span></span> <span data-ttu-id="2bbfa-191">Bu sayı doğru ve tam bir koleksiyon sonrasında tamamlanır, ancak kısa ömürlü bir koleksiyon sonrasında tamamlanmamış olabilir.</span><span class="sxs-lookup"><span data-stu-id="2bbfa-191">This number is accurate and complete after a full collection, but may be incomplete after an ephemeral collection.</span></span>|
|<span data-ttu-id="2bbfa-192">Processsurviks</span><span class="sxs-lookup"><span data-stu-id="2bbfa-192">ProcessSurvived</span></span>|<span data-ttu-id="2bbfa-193">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="2bbfa-193">win:UInt64</span></span>|<span data-ttu-id="2bbfa-194">Son koleksiyondan kalan toplam bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="2bbfa-194">The total bytes that survived from the last collection.</span></span> <span data-ttu-id="2bbfa-195">Tam bir koleksiyon sonrasında bu sayı, yönetilen yığınlardaki etkin tutulan bayt sayısını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="2bbfa-195">After a full collection, this number represents the number of bytes being held live in managed heaps.</span></span> <span data-ttu-id="2bbfa-196">Kısa ömürlü bir koleksiyondan sonra bu sayı, kısa ömürlü neslerde bulunan baytların sayısını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="2bbfa-196">After an ephemeral collection, this number represents the number of bytes held live in ephemeral generations.</span></span>|
|<span data-ttu-id="2bbfa-197">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="2bbfa-197">ClrInstanceID</span></span>|<span data-ttu-id="2bbfa-198">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="2bbfa-198">win:UInt16</span></span>|<span data-ttu-id="2bbfa-199">CLR veya CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="2bbfa-199">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="threadappdomainenter-event"></a><span data-ttu-id="2bbfa-200">ThreadAppDomainEnter olayı</span><span class="sxs-lookup"><span data-stu-id="2bbfa-200">ThreadAppDomainEnter Event</span></span>

<span data-ttu-id="2bbfa-201">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="2bbfa-201">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="2bbfa-202">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="2bbfa-202">Keyword for raising the event</span></span>|<span data-ttu-id="2bbfa-203">Düzey</span><span class="sxs-lookup"><span data-stu-id="2bbfa-203">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="2bbfa-204">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="2bbfa-204">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="2bbfa-205">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="2bbfa-205">Informational(4)</span></span>|
|<span data-ttu-id="2bbfa-206">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="2bbfa-206">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="2bbfa-207">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="2bbfa-207">Informational(4)</span></span>|

<span data-ttu-id="2bbfa-208">Aşağıdaki tabloda olay bilgileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="2bbfa-208">The following table shows the event information:</span></span>

|<span data-ttu-id="2bbfa-209">Olay</span><span class="sxs-lookup"><span data-stu-id="2bbfa-209">Event</span></span>|<span data-ttu-id="2bbfa-210">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="2bbfa-210">Event ID</span></span>|<span data-ttu-id="2bbfa-211">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="2bbfa-211">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ThreadAppDomainEnter`|<span data-ttu-id="2bbfa-212">87</span><span class="sxs-lookup"><span data-stu-id="2bbfa-212">87</span></span>|<span data-ttu-id="2bbfa-213">Bir iş parçacığı bir uygulama etki alanı girer.</span><span class="sxs-lookup"><span data-stu-id="2bbfa-213">A thread enters an application domain.</span></span>|

<span data-ttu-id="2bbfa-214">Aşağıdaki tabloda olay verileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="2bbfa-214">The following table shows the event data:</span></span>

|<span data-ttu-id="2bbfa-215">Alan adı</span><span class="sxs-lookup"><span data-stu-id="2bbfa-215">Field name</span></span>|<span data-ttu-id="2bbfa-216">Veri türü</span><span class="sxs-lookup"><span data-stu-id="2bbfa-216">Data type</span></span>|<span data-ttu-id="2bbfa-217">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2bbfa-217">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="2bbfa-218">ThreadID</span><span class="sxs-lookup"><span data-stu-id="2bbfa-218">ThreadID</span></span>|<span data-ttu-id="2bbfa-219">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="2bbfa-219">win:UInt64</span></span>|<span data-ttu-id="2bbfa-220">İş parçacığı tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="2bbfa-220">The thread identifier.</span></span>|
|<span data-ttu-id="2bbfa-221">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="2bbfa-221">AppDomainID</span></span>|<span data-ttu-id="2bbfa-222">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="2bbfa-222">win:UInt64</span></span>|<span data-ttu-id="2bbfa-223">Uygulama etki alanı tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="2bbfa-223">The application domain identifier.</span></span>|
|<span data-ttu-id="2bbfa-224">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="2bbfa-224">ClrInstanceID</span></span>|<span data-ttu-id="2bbfa-225">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="2bbfa-225">win:UInt16</span></span>|<span data-ttu-id="2bbfa-226">CLR veya CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="2bbfa-226">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="threadterminated-event"></a><span data-ttu-id="2bbfa-227">Threadsonlandırılmış olay</span><span class="sxs-lookup"><span data-stu-id="2bbfa-227">ThreadTerminated Event</span></span>

<span data-ttu-id="2bbfa-228">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="2bbfa-228">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="2bbfa-229">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="2bbfa-229">Keyword for raising the event</span></span>|<span data-ttu-id="2bbfa-230">Düzey</span><span class="sxs-lookup"><span data-stu-id="2bbfa-230">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="2bbfa-231">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="2bbfa-231">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="2bbfa-232">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="2bbfa-232">Informational(4)</span></span>|
|<span data-ttu-id="2bbfa-233">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="2bbfa-233">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="2bbfa-234">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="2bbfa-234">Informational(4)</span></span>|

<span data-ttu-id="2bbfa-235">Aşağıdaki tabloda olay bilgileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="2bbfa-235">The following table shows the event information:</span></span>

|<span data-ttu-id="2bbfa-236">Olay</span><span class="sxs-lookup"><span data-stu-id="2bbfa-236">Event</span></span>|<span data-ttu-id="2bbfa-237">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="2bbfa-237">Event ID</span></span>|<span data-ttu-id="2bbfa-238">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="2bbfa-238">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ThreadTerminated`|<span data-ttu-id="2bbfa-239">86</span><span class="sxs-lookup"><span data-stu-id="2bbfa-239">86</span></span>|<span data-ttu-id="2bbfa-240">Bir iş parçacığı sonlanır.</span><span class="sxs-lookup"><span data-stu-id="2bbfa-240">A thread terminates.</span></span>|

<span data-ttu-id="2bbfa-241">Aşağıdaki tabloda olay verileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="2bbfa-241">The following table shows the event data:</span></span>

|<span data-ttu-id="2bbfa-242">Alan adı</span><span class="sxs-lookup"><span data-stu-id="2bbfa-242">Field name</span></span>|<span data-ttu-id="2bbfa-243">Veri türü</span><span class="sxs-lookup"><span data-stu-id="2bbfa-243">Data type</span></span>|<span data-ttu-id="2bbfa-244">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2bbfa-244">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="2bbfa-245">ThreadID</span><span class="sxs-lookup"><span data-stu-id="2bbfa-245">ThreadID</span></span>|<span data-ttu-id="2bbfa-246">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="2bbfa-246">win:UInt64</span></span>|<span data-ttu-id="2bbfa-247">İş parçacığı tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="2bbfa-247">The thread identifier.</span></span>|
|<span data-ttu-id="2bbfa-248">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="2bbfa-248">AppDomainID</span></span>|<span data-ttu-id="2bbfa-249">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="2bbfa-249">win:UInt64</span></span>|<span data-ttu-id="2bbfa-250">Uygulama etki alanı tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="2bbfa-250">The application domain identifier.</span></span>|
|<span data-ttu-id="2bbfa-251">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="2bbfa-251">ClrInstanceID</span></span>|<span data-ttu-id="2bbfa-252">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="2bbfa-252">win:UInt16</span></span>|<span data-ttu-id="2bbfa-253">CLR veya CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="2bbfa-253">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="see-also"></a><span data-ttu-id="2bbfa-254">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2bbfa-254">See also</span></span>

- [<span data-ttu-id="2bbfa-255">CLR ETW Olayları</span><span class="sxs-lookup"><span data-stu-id="2bbfa-255">CLR ETW Events</span></span>](clr-etw-events.md)
