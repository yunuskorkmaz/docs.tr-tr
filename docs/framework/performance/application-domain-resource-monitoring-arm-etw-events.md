---
title: "Uygulama Etki Alanı Kaynak İzleme (ARM) ETW Olayları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ETW, application domain monitoring events
- application domain monitoring events [.NET Framework]
ms.assetid: d38ff268-a2ee-434e-b504-d570880e0289
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6384700c7039cb705f2db759ebd3d733bf8954ae
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="application-domain-resource-monitoring-arm-etw-events"></a><span data-ttu-id="d80f2-102">Uygulama Etki Alanı Kaynak İzleme (ARM) ETW Olayları</span><span class="sxs-lookup"><span data-stu-id="d80f2-102">Application Domain Resource Monitoring (ARM) ETW Events</span></span>
<a name="top"></a><span data-ttu-id="d80f2-103">Bu olaylar uygulama etki alanı durumu hakkında ayrıntılı tanılama bilgisi sağlayın.</span><span class="sxs-lookup"><span data-stu-id="d80f2-103">These events provide detailed diagnostic information about the state of an application domain.</span></span> <span data-ttu-id="d80f2-104">Bu olaylar kullanın ya da aynı bilgileri elde etmek için uygulama etki alanı kaynak izleme (ARM) özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="d80f2-104">You can use these events or use the application domain resource monitoring (ARM) feature to obtain the same information.</span></span>  
  
 <span data-ttu-id="d80f2-105">Bu kategori aşağıdaki olaylar oluşur:</span><span class="sxs-lookup"><span data-stu-id="d80f2-105">This category consists of the following events:</span></span>  
  
-   [<span data-ttu-id="d80f2-106">ThreadCreated olayı</span><span class="sxs-lookup"><span data-stu-id="d80f2-106">ThreadCreated Event</span></span>](#threadcreated_event)  
  
-   [<span data-ttu-id="d80f2-107">AppDomainMemAllocated olayı</span><span class="sxs-lookup"><span data-stu-id="d80f2-107">AppDomainMemAllocated Event</span></span>](#appdomainmemallocated_event)  
  
-   [<span data-ttu-id="d80f2-108">AppDomainMemSurvived olayı</span><span class="sxs-lookup"><span data-stu-id="d80f2-108">AppDomainMemSurvived Event</span></span>](#appdomainmemsurvived_event)  
  
-   [<span data-ttu-id="d80f2-109">ThreadAppDomainEnter olayı</span><span class="sxs-lookup"><span data-stu-id="d80f2-109">ThreadAppDomainEnter Event</span></span>](#threadappdomainenter_event)  
  
-   [<span data-ttu-id="d80f2-110">ThreadTerminated olayı</span><span class="sxs-lookup"><span data-stu-id="d80f2-110">ThreadTerminated Event</span></span>](#threadterminated_event)  
  
<a name="threadcreated_event"></a>   
## <a name="threadcreated-event"></a><span data-ttu-id="d80f2-111">ThreadCreated olayı</span><span class="sxs-lookup"><span data-stu-id="d80f2-111">ThreadCreated Event</span></span>  
 <span data-ttu-id="d80f2-112">Bu olay ayrıca özeti sağlayıcı altında oluşturulur `ThreadDC` (altında `AppDomainResourceManagementRundownKeyword` anahtar sözcüğü).</span><span class="sxs-lookup"><span data-stu-id="d80f2-112">This event is also raised  under the rundown provider as `ThreadDC` (under the `AppDomainResourceManagementRundownKeyword` keyword).</span></span> <span data-ttu-id="d80f2-113">Bu kategorideki özeti sağlayıcısı altında tetiklenir yalnızca olay budur.</span><span class="sxs-lookup"><span data-stu-id="d80f2-113">This is the only event that is raised under the rundown provider in this category.</span></span>  
  
 <span data-ttu-id="d80f2-114">Aşağıdaki tablo düzeyi ve anahtar sözcüğü gösterir.</span><span class="sxs-lookup"><span data-stu-id="d80f2-114">The following table shows the keyword and level.</span></span> <span data-ttu-id="d80f2-115">(Daha fazla bilgi için bkz: [CLR ETW anahtar sözcükleri ve Düzeyler](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="d80f2-115">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="d80f2-116">Olay oluşturma için anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="d80f2-116">Keyword for raising the event</span></span>|<span data-ttu-id="d80f2-117">Düzey</span><span class="sxs-lookup"><span data-stu-id="d80f2-117">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="d80f2-118">`AppDomainResourceManagementKeyword`(0x800)</span><span class="sxs-lookup"><span data-stu-id="d80f2-118">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="d80f2-119">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="d80f2-119">Informational(4)</span></span>|  
|<span data-ttu-id="d80f2-120">`ThreadingKeyword`(0x10000)</span><span class="sxs-lookup"><span data-stu-id="d80f2-120">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="d80f2-121">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="d80f2-121">Informational(4)</span></span>|  
  
 <span data-ttu-id="d80f2-122">Aşağıdaki tabloda olay bilgilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="d80f2-122">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="d80f2-123">Olay</span><span class="sxs-lookup"><span data-stu-id="d80f2-123">Event</span></span>|<span data-ttu-id="d80f2-124">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="d80f2-124">Event ID</span></span>|<span data-ttu-id="d80f2-125">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="d80f2-125">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ThreadCreated`|<span data-ttu-id="d80f2-126">85</span><span class="sxs-lookup"><span data-stu-id="d80f2-126">85</span></span>|<span data-ttu-id="d80f2-127">Uygulama etki alanı için bir iş parçacığı oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="d80f2-127">A thread was created for the application domain.</span></span>|  
  
 <span data-ttu-id="d80f2-128">Aşağıdaki tabloda olay verilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="d80f2-128">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="d80f2-129">Alan adı</span><span class="sxs-lookup"><span data-stu-id="d80f2-129">Field name</span></span>|<span data-ttu-id="d80f2-130">Veri türü</span><span class="sxs-lookup"><span data-stu-id="d80f2-130">Data type</span></span>|<span data-ttu-id="d80f2-131">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d80f2-131">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="d80f2-132">ThreadID</span><span class="sxs-lookup"><span data-stu-id="d80f2-132">ThreadID</span></span>|<span data-ttu-id="d80f2-133">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="d80f2-133">win:UInt64</span></span>|<span data-ttu-id="d80f2-134">Oluşturulan iş parçacığı kimliği.</span><span class="sxs-lookup"><span data-stu-id="d80f2-134">ID of the thread that was created.</span></span>|  
|<span data-ttu-id="d80f2-135">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="d80f2-135">AppDomainID</span></span>|<span data-ttu-id="d80f2-136">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="d80f2-136">win:UInt64</span></span>|<span data-ttu-id="d80f2-137">Hangi iş parçacığı için etkinlik bildirilen uygulama etki alanı tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="d80f2-137">Identifier of the application domain for which thread activity is being reported.</span></span>|  
|<span data-ttu-id="d80f2-138">Bayraklar</span><span class="sxs-lookup"><span data-stu-id="d80f2-138">Flags</span></span>|<span data-ttu-id="d80f2-139">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="d80f2-139">win:UInt32</span></span>|<span data-ttu-id="d80f2-140">İş parçacığı oluşturma bayrakları.</span><span class="sxs-lookup"><span data-stu-id="d80f2-140">Thread creation flags.</span></span>|  
|<span data-ttu-id="d80f2-141">ManagedThreadIndex</span><span class="sxs-lookup"><span data-stu-id="d80f2-141">ManagedThreadIndex</span></span>|<span data-ttu-id="d80f2-142">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="d80f2-142">win:UInt32</span></span>|<span data-ttu-id="d80f2-143">Dizini oluşturulan iş parçacığının yönetilen.</span><span class="sxs-lookup"><span data-stu-id="d80f2-143">Managed index of the thread that was created.</span></span>|  
|<span data-ttu-id="d80f2-144">OSThreadId</span><span class="sxs-lookup"><span data-stu-id="d80f2-144">OSThreadID</span></span>|<span data-ttu-id="d80f2-145">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="d80f2-145">win:UInt32</span></span>|<span data-ttu-id="d80f2-146">Oluşturulan iş parçacığı kimliği işletim sistemi.</span><span class="sxs-lookup"><span data-stu-id="d80f2-146">Operating system ID of the thread that was created.</span></span>|  
|<span data-ttu-id="d80f2-147">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="d80f2-147">ClrInstanceID</span></span>|<span data-ttu-id="d80f2-148">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="d80f2-148">win:UInt16</span></span>|<span data-ttu-id="d80f2-149">CLR veya CoreCLR örneği için benzersiz kimlik.</span><span class="sxs-lookup"><span data-stu-id="d80f2-149">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="d80f2-150">Başa dön</span><span class="sxs-lookup"><span data-stu-id="d80f2-150">Back to top</span></span>](#top)  
  
<a name="appdomainmemallocated_event"></a>   
## <a name="appdomainmemallocated-event"></a><span data-ttu-id="d80f2-151">AppDomainMemAllocated olayı</span><span class="sxs-lookup"><span data-stu-id="d80f2-151">AppDomainMemAllocated Event</span></span>  
 <span data-ttu-id="d80f2-152">Aşağıdaki tablo düzeyi ve anahtar sözcüğü gösterir.</span><span class="sxs-lookup"><span data-stu-id="d80f2-152">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="d80f2-153">Olay oluşturma için anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="d80f2-153">Keyword for raising the event</span></span>|<span data-ttu-id="d80f2-154">Düzey</span><span class="sxs-lookup"><span data-stu-id="d80f2-154">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="d80f2-155">`AppDomainResourceManagementKeyword`(0x800)</span><span class="sxs-lookup"><span data-stu-id="d80f2-155">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="d80f2-156">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="d80f2-156">Informational(4)</span></span>|  
  
 <span data-ttu-id="d80f2-157">Aşağıdaki tabloda olay bilgilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="d80f2-157">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="d80f2-158">Olay</span><span class="sxs-lookup"><span data-stu-id="d80f2-158">Event</span></span>|<span data-ttu-id="d80f2-159">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="d80f2-159">Event ID</span></span>|<span data-ttu-id="d80f2-160">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="d80f2-160">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`AppDomainMemAllocated`|<span data-ttu-id="d80f2-161">83</span><span class="sxs-lookup"><span data-stu-id="d80f2-161">83</span></span>|<span data-ttu-id="d80f2-162">Her 4 MB bellek (yaklaşık) uygulama etki alanında tahsis edilir.</span><span class="sxs-lookup"><span data-stu-id="d80f2-162">Every 4 MB of memory (approximately) is allocated in the application domain.</span></span>|  
  
 <span data-ttu-id="d80f2-163">Aşağıdaki tabloda olay verilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="d80f2-163">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="d80f2-164">Alan adı</span><span class="sxs-lookup"><span data-stu-id="d80f2-164">Field name</span></span>|<span data-ttu-id="d80f2-165">Veri türü</span><span class="sxs-lookup"><span data-stu-id="d80f2-165">Data type</span></span>|<span data-ttu-id="d80f2-166">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d80f2-166">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="d80f2-167">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="d80f2-167">AppDomainID</span></span>|<span data-ttu-id="d80f2-168">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="d80f2-168">win:UInt64</span></span>|<span data-ttu-id="d80f2-169">Kaynak kullanım bildirilen uygulama etki alanı tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="d80f2-169">Identifier of the application domain for which resource usage is being reported.</span></span>|  
|<span data-ttu-id="d80f2-170">Ayrılmış</span><span class="sxs-lookup"><span data-stu-id="d80f2-170">Allocated</span></span>|<span data-ttu-id="d80f2-171">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="d80f2-171">win:UInt64</span></span>|<span data-ttu-id="d80f2-172">Toplam uygulama etki alanı oluşturulduktan sonra bu uygulama etki alanında ayrılmış bayt sayısı (boşaltılmış bellek miktarını değil çıkarılır).</span><span class="sxs-lookup"><span data-stu-id="d80f2-172">The total number of bytes allocated in this application domain since the application domain was created (the amount of freed memory is not subtracted).</span></span>|  
|<span data-ttu-id="d80f2-173">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="d80f2-173">ClrInstanceID</span></span>|<span data-ttu-id="d80f2-174">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="d80f2-174">win:UInt16</span></span>|<span data-ttu-id="d80f2-175">CLR veya CoreCLR örneği için benzersiz kimlik.</span><span class="sxs-lookup"><span data-stu-id="d80f2-175">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="d80f2-176">Başa dön</span><span class="sxs-lookup"><span data-stu-id="d80f2-176">Back to top</span></span>](#top)  
  
<a name="appdomainmemsurvived_event"></a>   
## <a name="appdomainmemsurvived-event"></a><span data-ttu-id="d80f2-177">AppDomainMemSurvived olayı</span><span class="sxs-lookup"><span data-stu-id="d80f2-177">AppDomainMemSurvived Event</span></span>  
 <span data-ttu-id="d80f2-178">Aşağıdaki tablo düzeyi ve anahtar sözcüğü gösterir.</span><span class="sxs-lookup"><span data-stu-id="d80f2-178">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="d80f2-179">Olay oluşturma için anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="d80f2-179">Keyword for raising the event</span></span>|<span data-ttu-id="d80f2-180">Düzey</span><span class="sxs-lookup"><span data-stu-id="d80f2-180">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="d80f2-181">`AppDomainResourceManagementKeyword`(0x800)</span><span class="sxs-lookup"><span data-stu-id="d80f2-181">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="d80f2-182">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="d80f2-182">Informational(4)</span></span>|  
  
 <span data-ttu-id="d80f2-183">Aşağıdaki tabloda olay bilgilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="d80f2-183">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="d80f2-184">Olay</span><span class="sxs-lookup"><span data-stu-id="d80f2-184">Event</span></span>|<span data-ttu-id="d80f2-185">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="d80f2-185">Event ID</span></span>|<span data-ttu-id="d80f2-186">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="d80f2-186">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`AppDomainMemSurvived`|<span data-ttu-id="d80f2-187">84</span><span class="sxs-lookup"><span data-stu-id="d80f2-187">84</span></span>|<span data-ttu-id="d80f2-188">Her çöp toplama sona erdi.</span><span class="sxs-lookup"><span data-stu-id="d80f2-188">Each garbage collection has ended.</span></span>|  
  
 <span data-ttu-id="d80f2-189">Aşağıdaki tabloda olay verilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="d80f2-189">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="d80f2-190">Alan adı</span><span class="sxs-lookup"><span data-stu-id="d80f2-190">Field name</span></span>|<span data-ttu-id="d80f2-191">Veri türü</span><span class="sxs-lookup"><span data-stu-id="d80f2-191">Data type</span></span>|<span data-ttu-id="d80f2-192">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d80f2-192">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="d80f2-193">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="d80f2-193">AppDomainID</span></span>|<span data-ttu-id="d80f2-194">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="d80f2-194">win:UInt64</span></span>|<span data-ttu-id="d80f2-195">Kaynak kullanım bildirilen etki alanı tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="d80f2-195">Identifier of the domain for which resource usage is being reported.</span></span>|  
|<span data-ttu-id="d80f2-196">Derdi bitti</span><span class="sxs-lookup"><span data-stu-id="d80f2-196">Survived</span></span>|<span data-ttu-id="d80f2-197">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="d80f2-197">win:UInt64</span></span>|<span data-ttu-id="d80f2-198">Sonra son koleksiyon derdi bitti ve bu uygulama etki alanı tarafından tutulması için bilinen bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="d80f2-198">The number of bytes that survived after the last collection and that are known to be held by this application domain.</span></span> <span data-ttu-id="d80f2-199">Bu sayı doğru ve eksiksiz sonra tam bir koleksiyon, ancak sonra kısa ömürlü bir koleksiyonu eksik olabilir.</span><span class="sxs-lookup"><span data-stu-id="d80f2-199">This number is accurate and complete after a full collection, but may be incomplete after an ephemeral collection.</span></span>|  
|<span data-ttu-id="d80f2-200">ProcessSurvived</span><span class="sxs-lookup"><span data-stu-id="d80f2-200">ProcessSurvived</span></span>|<span data-ttu-id="d80f2-201">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="d80f2-201">win:UInt64</span></span>|<span data-ttu-id="d80f2-202">Son koleksiyondan derdi bitti toplam bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="d80f2-202">The total bytes that survived from the last collection.</span></span> <span data-ttu-id="d80f2-203">Sonra tam bir koleksiyon, bu numara temsil bayt sayısı Yönetilen yığın Canlı tutuldu.</span><span class="sxs-lookup"><span data-stu-id="d80f2-203">After a full collection, this number represents the number of bytes being held live in managed heaps.</span></span> <span data-ttu-id="d80f2-204">Kısa ömürlü bir koleksiyon sonra bu sayı temsil bayt sayısı kısa ömürlü kuşakta Canlı tutulan.</span><span class="sxs-lookup"><span data-stu-id="d80f2-204">After an ephemeral collection, this number represents the number of bytes held live in ephemeral generations.</span></span>|  
|<span data-ttu-id="d80f2-205">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="d80f2-205">ClrInstanceID</span></span>|<span data-ttu-id="d80f2-206">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="d80f2-206">win:UInt16</span></span>|<span data-ttu-id="d80f2-207">CLR veya CoreCLR örneği için benzersiz kimlik.</span><span class="sxs-lookup"><span data-stu-id="d80f2-207">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="d80f2-208">Başa dön</span><span class="sxs-lookup"><span data-stu-id="d80f2-208">Back to top</span></span>](#top)  
  
<a name="threadappdomainenter_event"></a>   
## <a name="threadappdomainenter-event"></a><span data-ttu-id="d80f2-209">ThreadAppDomainEnter olayı</span><span class="sxs-lookup"><span data-stu-id="d80f2-209">ThreadAppDomainEnter Event</span></span>  
 <span data-ttu-id="d80f2-210">Aşağıdaki tablo düzeyi ve anahtar sözcüğü gösterir.</span><span class="sxs-lookup"><span data-stu-id="d80f2-210">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="d80f2-211">Olay oluşturma için anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="d80f2-211">Keyword for raising the event</span></span>|<span data-ttu-id="d80f2-212">Düzey</span><span class="sxs-lookup"><span data-stu-id="d80f2-212">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="d80f2-213">`AppDomainResourceManagementKeyword`(0x800)</span><span class="sxs-lookup"><span data-stu-id="d80f2-213">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="d80f2-214">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="d80f2-214">Informational(4)</span></span>|  
|<span data-ttu-id="d80f2-215">`ThreadingKeyword`(0x10000)</span><span class="sxs-lookup"><span data-stu-id="d80f2-215">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="d80f2-216">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="d80f2-216">Informational(4)</span></span>|  
  
 <span data-ttu-id="d80f2-217">Aşağıdaki tabloda olay bilgilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="d80f2-217">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="d80f2-218">Olay</span><span class="sxs-lookup"><span data-stu-id="d80f2-218">Event</span></span>|<span data-ttu-id="d80f2-219">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="d80f2-219">Event ID</span></span>|<span data-ttu-id="d80f2-220">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="d80f2-220">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ThreadAppDomainEnter`|<span data-ttu-id="d80f2-221">87</span><span class="sxs-lookup"><span data-stu-id="d80f2-221">87</span></span>|<span data-ttu-id="d80f2-222">Bir iş parçacığı uygulama etki alanı girer.</span><span class="sxs-lookup"><span data-stu-id="d80f2-222">A thread enters an application domain.</span></span>|  
  
 <span data-ttu-id="d80f2-223">Aşağıdaki tabloda olay verilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="d80f2-223">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="d80f2-224">Alan adı</span><span class="sxs-lookup"><span data-stu-id="d80f2-224">Field name</span></span>|<span data-ttu-id="d80f2-225">Veri türü</span><span class="sxs-lookup"><span data-stu-id="d80f2-225">Data type</span></span>|<span data-ttu-id="d80f2-226">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d80f2-226">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="d80f2-227">ThreadID</span><span class="sxs-lookup"><span data-stu-id="d80f2-227">ThreadID</span></span>|<span data-ttu-id="d80f2-228">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="d80f2-228">win:UInt64</span></span>|<span data-ttu-id="d80f2-229">İş parçacığı tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="d80f2-229">The thread identifier.</span></span>|  
|<span data-ttu-id="d80f2-230">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="d80f2-230">AppDomainID</span></span>|<span data-ttu-id="d80f2-231">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="d80f2-231">win:UInt64</span></span>|<span data-ttu-id="d80f2-232">Uygulama etki alanı tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="d80f2-232">The application domain identifier.</span></span>|  
|<span data-ttu-id="d80f2-233">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="d80f2-233">ClrInstanceID</span></span>|<span data-ttu-id="d80f2-234">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="d80f2-234">win:UInt16</span></span>|<span data-ttu-id="d80f2-235">CLR veya CoreCLR örneği için benzersiz kimlik.</span><span class="sxs-lookup"><span data-stu-id="d80f2-235">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="d80f2-236">Başa dön</span><span class="sxs-lookup"><span data-stu-id="d80f2-236">Back to top</span></span>](#top)  
  
<a name="threadterminated_event"></a>   
## <a name="threadterminated-event"></a><span data-ttu-id="d80f2-237">ThreadTerminated olayı</span><span class="sxs-lookup"><span data-stu-id="d80f2-237">ThreadTerminated Event</span></span>  
 <span data-ttu-id="d80f2-238">Aşağıdaki tablo düzeyi ve anahtar sözcüğü gösterir.</span><span class="sxs-lookup"><span data-stu-id="d80f2-238">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="d80f2-239">Olay oluşturma için anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="d80f2-239">Keyword for raising the event</span></span>|<span data-ttu-id="d80f2-240">Düzey</span><span class="sxs-lookup"><span data-stu-id="d80f2-240">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="d80f2-241">`AppDomainResourceManagementKeyword`(0x800)</span><span class="sxs-lookup"><span data-stu-id="d80f2-241">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="d80f2-242">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="d80f2-242">Informational(4)</span></span>|  
|<span data-ttu-id="d80f2-243">`ThreadingKeyword`(0x10000)</span><span class="sxs-lookup"><span data-stu-id="d80f2-243">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="d80f2-244">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="d80f2-244">Informational(4)</span></span>|  
  
 <span data-ttu-id="d80f2-245">Aşağıdaki tabloda olay bilgilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="d80f2-245">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="d80f2-246">Olay</span><span class="sxs-lookup"><span data-stu-id="d80f2-246">Event</span></span>|<span data-ttu-id="d80f2-247">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="d80f2-247">Event ID</span></span>|<span data-ttu-id="d80f2-248">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="d80f2-248">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ThreadTerminated`|<span data-ttu-id="d80f2-249">86</span><span class="sxs-lookup"><span data-stu-id="d80f2-249">86</span></span>|<span data-ttu-id="d80f2-250">Bir iş parçacığını sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="d80f2-250">A thread terminates.</span></span>|  
  
 <span data-ttu-id="d80f2-251">Aşağıdaki tabloda olay verilerini gösterir:</span><span class="sxs-lookup"><span data-stu-id="d80f2-251">The following table shows the event data:</span></span>  
  
|<span data-ttu-id="d80f2-252">Alan adı</span><span class="sxs-lookup"><span data-stu-id="d80f2-252">Field name</span></span>|<span data-ttu-id="d80f2-253">Veri türü</span><span class="sxs-lookup"><span data-stu-id="d80f2-253">Data type</span></span>|<span data-ttu-id="d80f2-254">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d80f2-254">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="d80f2-255">ThreadID</span><span class="sxs-lookup"><span data-stu-id="d80f2-255">ThreadID</span></span>|<span data-ttu-id="d80f2-256">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="d80f2-256">win:UInt64</span></span>|<span data-ttu-id="d80f2-257">İş parçacığı tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="d80f2-257">The thread identifier.</span></span>|  
|<span data-ttu-id="d80f2-258">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="d80f2-258">AppDomainID</span></span>|<span data-ttu-id="d80f2-259">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="d80f2-259">win:UInt64</span></span>|<span data-ttu-id="d80f2-260">Uygulama etki alanı tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="d80f2-260">The application domain identifier.</span></span>|  
|<span data-ttu-id="d80f2-261">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="d80f2-261">ClrInstanceID</span></span>|<span data-ttu-id="d80f2-262">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="d80f2-262">win:UInt16</span></span>|<span data-ttu-id="d80f2-263">CLR veya CoreCLR örneği için benzersiz kimlik.</span><span class="sxs-lookup"><span data-stu-id="d80f2-263">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d80f2-264">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d80f2-264">See Also</span></span>  
 [<span data-ttu-id="d80f2-265">CLR ETW Olayları</span><span class="sxs-lookup"><span data-stu-id="d80f2-265">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
