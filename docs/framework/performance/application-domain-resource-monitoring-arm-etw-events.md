---
title: Uygulama Etki Alanı Kaynak İzleme (ARM) ETW Olayları
ms.date: 03/30/2017
helpviewer_keywords:
- ETW, application domain monitoring events
- application domain monitoring events [.NET Framework]
ms.assetid: d38ff268-a2ee-434e-b504-d570880e0289
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f0e4002ae248022a9e4380c79174109494b5e4ca
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71046775"
---
# <a name="application-domain-resource-monitoring-arm-etw-events"></a><span data-ttu-id="6f28e-102">Uygulama Etki Alanı Kaynak İzleme (ARM) ETW Olayları</span><span class="sxs-lookup"><span data-stu-id="6f28e-102">Application Domain Resource Monitoring (ARM) ETW Events</span></span>
<a name="top"></a><span data-ttu-id="6f28e-103">Bu olaylar, bir uygulama etki alanının durumu hakkında ayrıntılı tanılama bilgileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="6f28e-103">These events provide detailed diagnostic information about the state of an application domain.</span></span> <span data-ttu-id="6f28e-104">Aynı bilgileri elde etmek için bu olayları kullanabilir veya uygulama etki alanı kaynak izleme (ARM) özelliğini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6f28e-104">You can use these events or use the application domain resource monitoring (ARM) feature to obtain the same information.</span></span>  
  
 <span data-ttu-id="6f28e-105">Bu kategori aşağıdaki olaylardan oluşur:</span><span class="sxs-lookup"><span data-stu-id="6f28e-105">This category consists of the following events:</span></span>  
  
- [<span data-ttu-id="6f28e-106">ThreadCreated olayı</span><span class="sxs-lookup"><span data-stu-id="6f28e-106">ThreadCreated Event</span></span>](#threadcreated_event)  
  
- [<span data-ttu-id="6f28e-107">Appdomainmemalbulunan olay</span><span class="sxs-lookup"><span data-stu-id="6f28e-107">AppDomainMemAllocated Event</span></span>](#appdomainmemallocated_event)  
  
- [<span data-ttu-id="6f28e-108">Appdomainmemsurvilenmiş olay</span><span class="sxs-lookup"><span data-stu-id="6f28e-108">AppDomainMemSurvived Event</span></span>](#appdomainmemsurvived_event)  
  
- [<span data-ttu-id="6f28e-109">ThreadAppDomainEnter olayı</span><span class="sxs-lookup"><span data-stu-id="6f28e-109">ThreadAppDomainEnter Event</span></span>](#threadappdomainenter_event)  
  
- [<span data-ttu-id="6f28e-110">Threadsonlandırılmış olay</span><span class="sxs-lookup"><span data-stu-id="6f28e-110">ThreadTerminated Event</span></span>](#threadterminated_event)  
  
<a name="threadcreated_event"></a>   
## <a name="threadcreated-event"></a><span data-ttu-id="6f28e-111">ThreadCreated olayı</span><span class="sxs-lookup"><span data-stu-id="6f28e-111">ThreadCreated Event</span></span>  
 <span data-ttu-id="6f28e-112">Bu olay Ayrıca, Özet sağlayıcının `ThreadDC` altında ( `AppDomainResourceManagementRundownKeyword` anahtar sözcüğünün altında) de oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="6f28e-112">This event is also raised  under the rundown provider as `ThreadDC` (under the `AppDomainResourceManagementRundownKeyword` keyword).</span></span> <span data-ttu-id="6f28e-113">Bu, bu kategorideki özet sağlayıcı altında oluşturulan tek olaydır.</span><span class="sxs-lookup"><span data-stu-id="6f28e-113">This is the only event that is raised under the rundown provider in this category.</span></span>  
  
 <span data-ttu-id="6f28e-114">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="6f28e-114">The following table shows the keyword and level.</span></span> <span data-ttu-id="6f28e-115">(Daha fazla bilgi için bkz. [CLR ETW anahtar sözcükleri ve düzeyleri](clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="6f28e-115">(For more information, see [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="6f28e-116">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="6f28e-116">Keyword for raising the event</span></span>|<span data-ttu-id="6f28e-117">Düzey</span><span class="sxs-lookup"><span data-stu-id="6f28e-117">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="6f28e-118">`AppDomainResourceManagementKeyword`0x800</span><span class="sxs-lookup"><span data-stu-id="6f28e-118">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="6f28e-119">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="6f28e-119">Informational(4)</span></span>|  
|<span data-ttu-id="6f28e-120">`ThreadingKeyword`(0x10000)</span><span class="sxs-lookup"><span data-stu-id="6f28e-120">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="6f28e-121">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="6f28e-121">Informational(4)</span></span>|  
  
 <span data-ttu-id="6f28e-122">Aşağıdaki tabloda olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="6f28e-122">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="6f28e-123">Olay</span><span class="sxs-lookup"><span data-stu-id="6f28e-123">Event</span></span>|<span data-ttu-id="6f28e-124">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="6f28e-124">Event ID</span></span>|<span data-ttu-id="6f28e-125">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="6f28e-125">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ThreadCreated`|<span data-ttu-id="6f28e-126">85</span><span class="sxs-lookup"><span data-stu-id="6f28e-126">85</span></span>|<span data-ttu-id="6f28e-127">Uygulama etki alanı için bir iş parçacığı oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="6f28e-127">A thread was created for the application domain.</span></span>|  
  
 <span data-ttu-id="6f28e-128">Aşağıdaki tabloda olay verileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="6f28e-128">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="6f28e-129">Alan adı</span><span class="sxs-lookup"><span data-stu-id="6f28e-129">Field name</span></span>|<span data-ttu-id="6f28e-130">Veri türü</span><span class="sxs-lookup"><span data-stu-id="6f28e-130">Data type</span></span>|<span data-ttu-id="6f28e-131">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6f28e-131">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="6f28e-132">ThreadID</span><span class="sxs-lookup"><span data-stu-id="6f28e-132">ThreadID</span></span>|<span data-ttu-id="6f28e-133">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="6f28e-133">win:UInt64</span></span>|<span data-ttu-id="6f28e-134">Oluşturulan iş parçacığının KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="6f28e-134">ID of the thread that was created.</span></span>|  
|<span data-ttu-id="6f28e-135">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="6f28e-135">AppDomainID</span></span>|<span data-ttu-id="6f28e-136">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="6f28e-136">win:UInt64</span></span>|<span data-ttu-id="6f28e-137">İş parçacığı etkinliğinin bildirildiği uygulama etki alanının tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="6f28e-137">Identifier of the application domain for which thread activity is being reported.</span></span>|  
|<span data-ttu-id="6f28e-138">Bayraklar</span><span class="sxs-lookup"><span data-stu-id="6f28e-138">Flags</span></span>|<span data-ttu-id="6f28e-139">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="6f28e-139">win:UInt32</span></span>|<span data-ttu-id="6f28e-140">İş parçacığı oluşturma bayrakları.</span><span class="sxs-lookup"><span data-stu-id="6f28e-140">Thread creation flags.</span></span>|  
|<span data-ttu-id="6f28e-141">Managedthreadındex</span><span class="sxs-lookup"><span data-stu-id="6f28e-141">ManagedThreadIndex</span></span>|<span data-ttu-id="6f28e-142">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="6f28e-142">win:UInt32</span></span>|<span data-ttu-id="6f28e-143">Oluşturulan iş parçacığının yönetilen dizini.</span><span class="sxs-lookup"><span data-stu-id="6f28e-143">Managed index of the thread that was created.</span></span>|  
|<span data-ttu-id="6f28e-144">OSThreadId</span><span class="sxs-lookup"><span data-stu-id="6f28e-144">OSThreadID</span></span>|<span data-ttu-id="6f28e-145">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="6f28e-145">win:UInt32</span></span>|<span data-ttu-id="6f28e-146">Oluşturulan iş parçacığının işletim sistemi KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="6f28e-146">Operating system ID of the thread that was created.</span></span>|  
|<span data-ttu-id="6f28e-147">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="6f28e-147">ClrInstanceID</span></span>|<span data-ttu-id="6f28e-148">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="6f28e-148">win:UInt16</span></span>|<span data-ttu-id="6f28e-149">CLR veya CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="6f28e-149">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="6f28e-150">Başa dön</span><span class="sxs-lookup"><span data-stu-id="6f28e-150">Back to top</span></span>](#top)  
  
<a name="appdomainmemallocated_event"></a>   
## <a name="appdomainmemallocated-event"></a><span data-ttu-id="6f28e-151">Appdomainmemalbulunan olay</span><span class="sxs-lookup"><span data-stu-id="6f28e-151">AppDomainMemAllocated Event</span></span>  
 <span data-ttu-id="6f28e-152">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="6f28e-152">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="6f28e-153">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="6f28e-153">Keyword for raising the event</span></span>|<span data-ttu-id="6f28e-154">Düzey</span><span class="sxs-lookup"><span data-stu-id="6f28e-154">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="6f28e-155">`AppDomainResourceManagementKeyword`0x800</span><span class="sxs-lookup"><span data-stu-id="6f28e-155">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="6f28e-156">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="6f28e-156">Informational(4)</span></span>|  
  
 <span data-ttu-id="6f28e-157">Aşağıdaki tabloda olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="6f28e-157">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="6f28e-158">Olay</span><span class="sxs-lookup"><span data-stu-id="6f28e-158">Event</span></span>|<span data-ttu-id="6f28e-159">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="6f28e-159">Event ID</span></span>|<span data-ttu-id="6f28e-160">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="6f28e-160">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`AppDomainMemAllocated`|<span data-ttu-id="6f28e-161">83</span><span class="sxs-lookup"><span data-stu-id="6f28e-161">83</span></span>|<span data-ttu-id="6f28e-162">Uygulama etki alanında her 4 MB bellek (yaklaşık olarak) ayrılır.</span><span class="sxs-lookup"><span data-stu-id="6f28e-162">Every 4 MB of memory (approximately) is allocated in the application domain.</span></span>|  
  
 <span data-ttu-id="6f28e-163">Aşağıdaki tabloda olay verileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="6f28e-163">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="6f28e-164">Alan adı</span><span class="sxs-lookup"><span data-stu-id="6f28e-164">Field name</span></span>|<span data-ttu-id="6f28e-165">Veri türü</span><span class="sxs-lookup"><span data-stu-id="6f28e-165">Data type</span></span>|<span data-ttu-id="6f28e-166">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6f28e-166">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="6f28e-167">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="6f28e-167">AppDomainID</span></span>|<span data-ttu-id="6f28e-168">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="6f28e-168">win:UInt64</span></span>|<span data-ttu-id="6f28e-169">Kaynak kullanımının bildirildiği uygulama etki alanının tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="6f28e-169">Identifier of the application domain for which resource usage is being reported.</span></span>|  
|<span data-ttu-id="6f28e-170">Ayrılabilir</span><span class="sxs-lookup"><span data-stu-id="6f28e-170">Allocated</span></span>|<span data-ttu-id="6f28e-171">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="6f28e-171">win:UInt64</span></span>|<span data-ttu-id="6f28e-172">Uygulama etki alanı oluşturulduğundan bu yana bu uygulama etki alanında ayrılan toplam bayt sayısı (serbest bırakılan bellek miktarı çıkarıldı).</span><span class="sxs-lookup"><span data-stu-id="6f28e-172">The total number of bytes allocated in this application domain since the application domain was created (the amount of freed memory is not subtracted).</span></span>|  
|<span data-ttu-id="6f28e-173">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="6f28e-173">ClrInstanceID</span></span>|<span data-ttu-id="6f28e-174">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="6f28e-174">win:UInt16</span></span>|<span data-ttu-id="6f28e-175">CLR veya CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="6f28e-175">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="6f28e-176">Başa dön</span><span class="sxs-lookup"><span data-stu-id="6f28e-176">Back to top</span></span>](#top)  
  
<a name="appdomainmemsurvived_event"></a>   
## <a name="appdomainmemsurvived-event"></a><span data-ttu-id="6f28e-177">Appdomainmemsurvilenmiş olay</span><span class="sxs-lookup"><span data-stu-id="6f28e-177">AppDomainMemSurvived Event</span></span>  
 <span data-ttu-id="6f28e-178">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="6f28e-178">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="6f28e-179">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="6f28e-179">Keyword for raising the event</span></span>|<span data-ttu-id="6f28e-180">Düzey</span><span class="sxs-lookup"><span data-stu-id="6f28e-180">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="6f28e-181">`AppDomainResourceManagementKeyword`0x800</span><span class="sxs-lookup"><span data-stu-id="6f28e-181">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="6f28e-182">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="6f28e-182">Informational(4)</span></span>|  
  
 <span data-ttu-id="6f28e-183">Aşağıdaki tabloda olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="6f28e-183">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="6f28e-184">Olay</span><span class="sxs-lookup"><span data-stu-id="6f28e-184">Event</span></span>|<span data-ttu-id="6f28e-185">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="6f28e-185">Event ID</span></span>|<span data-ttu-id="6f28e-186">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="6f28e-186">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`AppDomainMemSurvived`|<span data-ttu-id="6f28e-187">84</span><span class="sxs-lookup"><span data-stu-id="6f28e-187">84</span></span>|<span data-ttu-id="6f28e-188">Her çöp toplama işlemi sona erdi.</span><span class="sxs-lookup"><span data-stu-id="6f28e-188">Each garbage collection has ended.</span></span>|  
  
 <span data-ttu-id="6f28e-189">Aşağıdaki tabloda olay verileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="6f28e-189">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="6f28e-190">Alan adı</span><span class="sxs-lookup"><span data-stu-id="6f28e-190">Field name</span></span>|<span data-ttu-id="6f28e-191">Veri türü</span><span class="sxs-lookup"><span data-stu-id="6f28e-191">Data type</span></span>|<span data-ttu-id="6f28e-192">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6f28e-192">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="6f28e-193">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="6f28e-193">AppDomainID</span></span>|<span data-ttu-id="6f28e-194">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="6f28e-194">win:UInt64</span></span>|<span data-ttu-id="6f28e-195">Kaynak kullanımının bildirildiği etki alanının tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="6f28e-195">Identifier of the domain for which resource usage is being reported.</span></span>|  
|<span data-ttu-id="6f28e-196">Kalan</span><span class="sxs-lookup"><span data-stu-id="6f28e-196">Survived</span></span>|<span data-ttu-id="6f28e-197">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="6f28e-197">win:UInt64</span></span>|<span data-ttu-id="6f28e-198">Son koleksiyondan sonra kalan ve bu uygulama etki alanı tarafından tutulması bilinen bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="6f28e-198">The number of bytes that survived after the last collection and that are known to be held by this application domain.</span></span> <span data-ttu-id="6f28e-199">Bu sayı doğru ve tam bir koleksiyon sonrasında tamamlanır, ancak kısa ömürlü bir koleksiyon sonrasında tamamlanmamış olabilir.</span><span class="sxs-lookup"><span data-stu-id="6f28e-199">This number is accurate and complete after a full collection, but may be incomplete after an ephemeral collection.</span></span>|  
|<span data-ttu-id="6f28e-200">Processsurviks</span><span class="sxs-lookup"><span data-stu-id="6f28e-200">ProcessSurvived</span></span>|<span data-ttu-id="6f28e-201">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="6f28e-201">win:UInt64</span></span>|<span data-ttu-id="6f28e-202">Son koleksiyondan kalan toplam bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="6f28e-202">The total bytes that survived from the last collection.</span></span> <span data-ttu-id="6f28e-203">Tam bir koleksiyon sonrasında bu sayı, yönetilen yığınlardaki etkin tutulan bayt sayısını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="6f28e-203">After a full collection, this number represents the number of bytes being held live in managed heaps.</span></span> <span data-ttu-id="6f28e-204">Kısa ömürlü bir koleksiyondan sonra bu sayı, kısa ömürlü neslerde bulunan baytların sayısını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="6f28e-204">After an ephemeral collection, this number represents the number of bytes held live in ephemeral generations.</span></span>|  
|<span data-ttu-id="6f28e-205">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="6f28e-205">ClrInstanceID</span></span>|<span data-ttu-id="6f28e-206">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="6f28e-206">win:UInt16</span></span>|<span data-ttu-id="6f28e-207">CLR veya CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="6f28e-207">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="6f28e-208">Başa dön</span><span class="sxs-lookup"><span data-stu-id="6f28e-208">Back to top</span></span>](#top)  
  
<a name="threadappdomainenter_event"></a>   
## <a name="threadappdomainenter-event"></a><span data-ttu-id="6f28e-209">ThreadAppDomainEnter olayı</span><span class="sxs-lookup"><span data-stu-id="6f28e-209">ThreadAppDomainEnter Event</span></span>  
 <span data-ttu-id="6f28e-210">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="6f28e-210">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="6f28e-211">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="6f28e-211">Keyword for raising the event</span></span>|<span data-ttu-id="6f28e-212">Düzey</span><span class="sxs-lookup"><span data-stu-id="6f28e-212">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="6f28e-213">`AppDomainResourceManagementKeyword`0x800</span><span class="sxs-lookup"><span data-stu-id="6f28e-213">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="6f28e-214">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="6f28e-214">Informational(4)</span></span>|  
|<span data-ttu-id="6f28e-215">`ThreadingKeyword`(0x10000)</span><span class="sxs-lookup"><span data-stu-id="6f28e-215">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="6f28e-216">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="6f28e-216">Informational(4)</span></span>|  
  
 <span data-ttu-id="6f28e-217">Aşağıdaki tabloda olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="6f28e-217">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="6f28e-218">Olay</span><span class="sxs-lookup"><span data-stu-id="6f28e-218">Event</span></span>|<span data-ttu-id="6f28e-219">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="6f28e-219">Event ID</span></span>|<span data-ttu-id="6f28e-220">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="6f28e-220">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ThreadAppDomainEnter`|<span data-ttu-id="6f28e-221">87</span><span class="sxs-lookup"><span data-stu-id="6f28e-221">87</span></span>|<span data-ttu-id="6f28e-222">Bir iş parçacığı bir uygulama etki alanı girer.</span><span class="sxs-lookup"><span data-stu-id="6f28e-222">A thread enters an application domain.</span></span>|  
  
 <span data-ttu-id="6f28e-223">Aşağıdaki tabloda olay verileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="6f28e-223">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="6f28e-224">Alan adı</span><span class="sxs-lookup"><span data-stu-id="6f28e-224">Field name</span></span>|<span data-ttu-id="6f28e-225">Veri türü</span><span class="sxs-lookup"><span data-stu-id="6f28e-225">Data type</span></span>|<span data-ttu-id="6f28e-226">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6f28e-226">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="6f28e-227">ThreadID</span><span class="sxs-lookup"><span data-stu-id="6f28e-227">ThreadID</span></span>|<span data-ttu-id="6f28e-228">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="6f28e-228">win:UInt64</span></span>|<span data-ttu-id="6f28e-229">İş parçacığı tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="6f28e-229">The thread identifier.</span></span>|  
|<span data-ttu-id="6f28e-230">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="6f28e-230">AppDomainID</span></span>|<span data-ttu-id="6f28e-231">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="6f28e-231">win:UInt64</span></span>|<span data-ttu-id="6f28e-232">Uygulama etki alanı tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="6f28e-232">The application domain identifier.</span></span>|  
|<span data-ttu-id="6f28e-233">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="6f28e-233">ClrInstanceID</span></span>|<span data-ttu-id="6f28e-234">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="6f28e-234">win:UInt16</span></span>|<span data-ttu-id="6f28e-235">CLR veya CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="6f28e-235">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="6f28e-236">Başa dön</span><span class="sxs-lookup"><span data-stu-id="6f28e-236">Back to top</span></span>](#top)  
  
<a name="threadterminated_event"></a>   
## <a name="threadterminated-event"></a><span data-ttu-id="6f28e-237">Threadsonlandırılmış olay</span><span class="sxs-lookup"><span data-stu-id="6f28e-237">ThreadTerminated Event</span></span>  
 <span data-ttu-id="6f28e-238">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="6f28e-238">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="6f28e-239">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="6f28e-239">Keyword for raising the event</span></span>|<span data-ttu-id="6f28e-240">Düzey</span><span class="sxs-lookup"><span data-stu-id="6f28e-240">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="6f28e-241">`AppDomainResourceManagementKeyword`0x800</span><span class="sxs-lookup"><span data-stu-id="6f28e-241">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="6f28e-242">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="6f28e-242">Informational(4)</span></span>|  
|<span data-ttu-id="6f28e-243">`ThreadingKeyword`(0x10000)</span><span class="sxs-lookup"><span data-stu-id="6f28e-243">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="6f28e-244">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="6f28e-244">Informational(4)</span></span>|  
  
 <span data-ttu-id="6f28e-245">Aşağıdaki tabloda olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="6f28e-245">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="6f28e-246">Olay</span><span class="sxs-lookup"><span data-stu-id="6f28e-246">Event</span></span>|<span data-ttu-id="6f28e-247">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="6f28e-247">Event ID</span></span>|<span data-ttu-id="6f28e-248">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="6f28e-248">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ThreadTerminated`|<span data-ttu-id="6f28e-249">86</span><span class="sxs-lookup"><span data-stu-id="6f28e-249">86</span></span>|<span data-ttu-id="6f28e-250">Bir iş parçacığı sonlanır.</span><span class="sxs-lookup"><span data-stu-id="6f28e-250">A thread terminates.</span></span>|  
  
 <span data-ttu-id="6f28e-251">Aşağıdaki tabloda olay verileri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="6f28e-251">The following table shows the event data:</span></span>  
  
|<span data-ttu-id="6f28e-252">Alan adı</span><span class="sxs-lookup"><span data-stu-id="6f28e-252">Field name</span></span>|<span data-ttu-id="6f28e-253">Veri türü</span><span class="sxs-lookup"><span data-stu-id="6f28e-253">Data type</span></span>|<span data-ttu-id="6f28e-254">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6f28e-254">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="6f28e-255">ThreadID</span><span class="sxs-lookup"><span data-stu-id="6f28e-255">ThreadID</span></span>|<span data-ttu-id="6f28e-256">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="6f28e-256">win:UInt64</span></span>|<span data-ttu-id="6f28e-257">İş parçacığı tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="6f28e-257">The thread identifier.</span></span>|  
|<span data-ttu-id="6f28e-258">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="6f28e-258">AppDomainID</span></span>|<span data-ttu-id="6f28e-259">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="6f28e-259">win:UInt64</span></span>|<span data-ttu-id="6f28e-260">Uygulama etki alanı tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="6f28e-260">The application domain identifier.</span></span>|  
|<span data-ttu-id="6f28e-261">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="6f28e-261">ClrInstanceID</span></span>|<span data-ttu-id="6f28e-262">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="6f28e-262">win:UInt16</span></span>|<span data-ttu-id="6f28e-263">CLR veya CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="6f28e-263">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6f28e-264">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6f28e-264">See also</span></span>

- [<span data-ttu-id="6f28e-265">CLR ETW Olayları</span><span class="sxs-lookup"><span data-stu-id="6f28e-265">CLR ETW Events</span></span>](clr-etw-events.md)
