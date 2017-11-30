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
ms.openlocfilehash: a93e8cc1ab0b7488f920b556d2073d2813c3b7a9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="application-domain-resource-monitoring-arm-etw-events"></a><span data-ttu-id="a39e5-102">Uygulama Etki Alanı Kaynak İzleme (ARM) ETW Olayları</span><span class="sxs-lookup"><span data-stu-id="a39e5-102">Application Domain Resource Monitoring (ARM) ETW Events</span></span>
<span data-ttu-id="a39e5-103"><a name="top"></a>Bu olaylar uygulama etki alanı durumu hakkında ayrıntılı tanılama bilgisi sağlayın.</span><span class="sxs-lookup"><span data-stu-id="a39e5-103"><a name="top"></a> These events provide detailed diagnostic information about the state of an application domain.</span></span> <span data-ttu-id="a39e5-104">Bu olaylar kullanın ya da aynı bilgileri elde etmek için uygulama etki alanı kaynak izleme (ARM) özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="a39e5-104">You can use these events or use the application domain resource monitoring (ARM) feature to obtain the same information.</span></span>  
  
 <span data-ttu-id="a39e5-105">Bu kategori aşağıdaki olaylar oluşur:</span><span class="sxs-lookup"><span data-stu-id="a39e5-105">This category consists of the following events:</span></span>  
  
-   [<span data-ttu-id="a39e5-106">ThreadCreated olayı</span><span class="sxs-lookup"><span data-stu-id="a39e5-106">ThreadCreated Event</span></span>](#threadcreated_event)  
  
-   [<span data-ttu-id="a39e5-107">AppDomainMemAllocated olayı</span><span class="sxs-lookup"><span data-stu-id="a39e5-107">AppDomainMemAllocated Event</span></span>](#appdomainmemallocated_event)  
  
-   [<span data-ttu-id="a39e5-108">AppDomainMemSurvived olayı</span><span class="sxs-lookup"><span data-stu-id="a39e5-108">AppDomainMemSurvived Event</span></span>](#appdomainmemsurvived_event)  
  
-   [<span data-ttu-id="a39e5-109">ThreadAppDomainEnter olayı</span><span class="sxs-lookup"><span data-stu-id="a39e5-109">ThreadAppDomainEnter Event</span></span>](#threadappdomainenter_event)  
  
-   [<span data-ttu-id="a39e5-110">ThreadTerminated olayı</span><span class="sxs-lookup"><span data-stu-id="a39e5-110">ThreadTerminated Event</span></span>](#threadterminated_event)  
  
<a name="threadcreated_event"></a>   
## <a name="threadcreated-event"></a><span data-ttu-id="a39e5-111">ThreadCreated olayı</span><span class="sxs-lookup"><span data-stu-id="a39e5-111">ThreadCreated Event</span></span>  
 <span data-ttu-id="a39e5-112">Bu olay ayrıca özeti sağlayıcı altında oluşturulur `ThreadDC` (altında `AppDomainResourceManagementRundownKeyword` anahtar sözcüğü).</span><span class="sxs-lookup"><span data-stu-id="a39e5-112">This event is also raised  under the rundown provider as `ThreadDC` (under the `AppDomainResourceManagementRundownKeyword` keyword).</span></span> <span data-ttu-id="a39e5-113">Bu kategorideki özeti sağlayıcısı altında tetiklenir yalnızca olay budur.</span><span class="sxs-lookup"><span data-stu-id="a39e5-113">This is the only event that is raised under the rundown provider in this category.</span></span>  
  
 <span data-ttu-id="a39e5-114">Aşağıdaki tablo düzeyi ve anahtar sözcüğü gösterir.</span><span class="sxs-lookup"><span data-stu-id="a39e5-114">The following table shows the keyword and level.</span></span> <span data-ttu-id="a39e5-115">(Daha fazla bilgi için bkz: [CLR ETW anahtar sözcükleri ve Düzeyler](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="a39e5-115">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="a39e5-116">Olay oluşturma için anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="a39e5-116">Keyword for raising the event</span></span>|<span data-ttu-id="a39e5-117">Düzey</span><span class="sxs-lookup"><span data-stu-id="a39e5-117">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="a39e5-118">`AppDomainResourceManagementKeyword`(0x800)</span><span class="sxs-lookup"><span data-stu-id="a39e5-118">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="a39e5-119">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="a39e5-119">Informational(4)</span></span>|  
|<span data-ttu-id="a39e5-120">`ThreadingKeyword`(0x10000)</span><span class="sxs-lookup"><span data-stu-id="a39e5-120">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="a39e5-121">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="a39e5-121">Informational(4)</span></span>|  
  
 <span data-ttu-id="a39e5-122">Aşağıdaki tabloda olay bilgilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="a39e5-122">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="a39e5-123">Olay</span><span class="sxs-lookup"><span data-stu-id="a39e5-123">Event</span></span>|<span data-ttu-id="a39e5-124">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="a39e5-124">Event ID</span></span>|<span data-ttu-id="a39e5-125">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="a39e5-125">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ThreadCreated`|<span data-ttu-id="a39e5-126">85</span><span class="sxs-lookup"><span data-stu-id="a39e5-126">85</span></span>|<span data-ttu-id="a39e5-127">Uygulama etki alanı için bir iş parçacığı oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="a39e5-127">A thread was created for the application domain.</span></span>|  
  
 <span data-ttu-id="a39e5-128">Aşağıdaki tabloda olay verilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="a39e5-128">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="a39e5-129">Alan adı</span><span class="sxs-lookup"><span data-stu-id="a39e5-129">Field name</span></span>|<span data-ttu-id="a39e5-130">Veri türü</span><span class="sxs-lookup"><span data-stu-id="a39e5-130">Data type</span></span>|<span data-ttu-id="a39e5-131">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a39e5-131">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="a39e5-132">ThreadID</span><span class="sxs-lookup"><span data-stu-id="a39e5-132">ThreadID</span></span>|<span data-ttu-id="a39e5-133">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="a39e5-133">win:UInt64</span></span>|<span data-ttu-id="a39e5-134">Oluşturulan iş parçacığı kimliği.</span><span class="sxs-lookup"><span data-stu-id="a39e5-134">ID of the thread that was created.</span></span>|  
|<span data-ttu-id="a39e5-135">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="a39e5-135">AppDomainID</span></span>|<span data-ttu-id="a39e5-136">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="a39e5-136">win:UInt64</span></span>|<span data-ttu-id="a39e5-137">Hangi iş parçacığı için etkinlik bildirilen uygulama etki alanı tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="a39e5-137">Identifier of the application domain for which thread activity is being reported.</span></span>|  
|<span data-ttu-id="a39e5-138">Bayraklar</span><span class="sxs-lookup"><span data-stu-id="a39e5-138">Flags</span></span>|<span data-ttu-id="a39e5-139">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="a39e5-139">win:UInt32</span></span>|<span data-ttu-id="a39e5-140">İş parçacığı oluşturma bayrakları.</span><span class="sxs-lookup"><span data-stu-id="a39e5-140">Thread creation flags.</span></span>|  
|<span data-ttu-id="a39e5-141">ManagedThreadIndex</span><span class="sxs-lookup"><span data-stu-id="a39e5-141">ManagedThreadIndex</span></span>|<span data-ttu-id="a39e5-142">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="a39e5-142">win:UInt32</span></span>|<span data-ttu-id="a39e5-143">Dizini oluşturulan iş parçacığının yönetilen.</span><span class="sxs-lookup"><span data-stu-id="a39e5-143">Managed index of the thread that was created.</span></span>|  
|<span data-ttu-id="a39e5-144">OSThreadId</span><span class="sxs-lookup"><span data-stu-id="a39e5-144">OSThreadID</span></span>|<span data-ttu-id="a39e5-145">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="a39e5-145">win:UInt32</span></span>|<span data-ttu-id="a39e5-146">Oluşturulan iş parçacığı kimliği işletim sistemi.</span><span class="sxs-lookup"><span data-stu-id="a39e5-146">Operating system ID of the thread that was created.</span></span>|  
|<span data-ttu-id="a39e5-147">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="a39e5-147">ClrInstanceID</span></span>|<span data-ttu-id="a39e5-148">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="a39e5-148">win:UInt16</span></span>|<span data-ttu-id="a39e5-149">CLR veya CoreCLR örneği için benzersiz kimlik.</span><span class="sxs-lookup"><span data-stu-id="a39e5-149">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="a39e5-150">Başa dön</span><span class="sxs-lookup"><span data-stu-id="a39e5-150">Back to top</span></span>](#top)  
  
<a name="appdomainmemallocated_event"></a>   
## <a name="appdomainmemallocated-event"></a><span data-ttu-id="a39e5-151">AppDomainMemAllocated olayı</span><span class="sxs-lookup"><span data-stu-id="a39e5-151">AppDomainMemAllocated Event</span></span>  
 <span data-ttu-id="a39e5-152">Aşağıdaki tablo düzeyi ve anahtar sözcüğü gösterir.</span><span class="sxs-lookup"><span data-stu-id="a39e5-152">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="a39e5-153">Olay oluşturma için anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="a39e5-153">Keyword for raising the event</span></span>|<span data-ttu-id="a39e5-154">Düzey</span><span class="sxs-lookup"><span data-stu-id="a39e5-154">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="a39e5-155">`AppDomainResourceManagementKeyword`(0x800)</span><span class="sxs-lookup"><span data-stu-id="a39e5-155">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="a39e5-156">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="a39e5-156">Informational(4)</span></span>|  
  
 <span data-ttu-id="a39e5-157">Aşağıdaki tabloda olay bilgilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="a39e5-157">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="a39e5-158">Olay</span><span class="sxs-lookup"><span data-stu-id="a39e5-158">Event</span></span>|<span data-ttu-id="a39e5-159">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="a39e5-159">Event ID</span></span>|<span data-ttu-id="a39e5-160">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="a39e5-160">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`AppDomainMemAllocated`|<span data-ttu-id="a39e5-161">83</span><span class="sxs-lookup"><span data-stu-id="a39e5-161">83</span></span>|<span data-ttu-id="a39e5-162">Her 4 MB bellek (yaklaşık) uygulama etki alanında tahsis edilir.</span><span class="sxs-lookup"><span data-stu-id="a39e5-162">Every 4 MB of memory (approximately) is allocated in the application domain.</span></span>|  
  
 <span data-ttu-id="a39e5-163">Aşağıdaki tabloda olay verilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="a39e5-163">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="a39e5-164">Alan adı</span><span class="sxs-lookup"><span data-stu-id="a39e5-164">Field name</span></span>|<span data-ttu-id="a39e5-165">Veri türü</span><span class="sxs-lookup"><span data-stu-id="a39e5-165">Data type</span></span>|<span data-ttu-id="a39e5-166">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a39e5-166">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="a39e5-167">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="a39e5-167">AppDomainID</span></span>|<span data-ttu-id="a39e5-168">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="a39e5-168">win:UInt64</span></span>|<span data-ttu-id="a39e5-169">Kaynak kullanım bildirilen uygulama etki alanı tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="a39e5-169">Identifier of the application domain for which resource usage is being reported.</span></span>|  
|<span data-ttu-id="a39e5-170">Ayrılmış</span><span class="sxs-lookup"><span data-stu-id="a39e5-170">Allocated</span></span>|<span data-ttu-id="a39e5-171">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="a39e5-171">win:UInt64</span></span>|<span data-ttu-id="a39e5-172">Toplam uygulama etki alanı oluşturulduktan sonra bu uygulama etki alanında ayrılmış bayt sayısı (boşaltılmış bellek miktarını değil çıkarılır).</span><span class="sxs-lookup"><span data-stu-id="a39e5-172">The total number of bytes allocated in this application domain since the application domain was created (the amount of freed memory is not subtracted).</span></span>|  
|<span data-ttu-id="a39e5-173">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="a39e5-173">ClrInstanceID</span></span>|<span data-ttu-id="a39e5-174">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="a39e5-174">win:UInt16</span></span>|<span data-ttu-id="a39e5-175">CLR veya CoreCLR örneği için benzersiz kimlik.</span><span class="sxs-lookup"><span data-stu-id="a39e5-175">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="a39e5-176">Başa dön</span><span class="sxs-lookup"><span data-stu-id="a39e5-176">Back to top</span></span>](#top)  
  
<a name="appdomainmemsurvived_event"></a>   
## <a name="appdomainmemsurvived-event"></a><span data-ttu-id="a39e5-177">AppDomainMemSurvived olayı</span><span class="sxs-lookup"><span data-stu-id="a39e5-177">AppDomainMemSurvived Event</span></span>  
 <span data-ttu-id="a39e5-178">Aşağıdaki tablo düzeyi ve anahtar sözcüğü gösterir.</span><span class="sxs-lookup"><span data-stu-id="a39e5-178">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="a39e5-179">Olay oluşturma için anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="a39e5-179">Keyword for raising the event</span></span>|<span data-ttu-id="a39e5-180">Düzey</span><span class="sxs-lookup"><span data-stu-id="a39e5-180">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="a39e5-181">`AppDomainResourceManagementKeyword`(0x800)</span><span class="sxs-lookup"><span data-stu-id="a39e5-181">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="a39e5-182">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="a39e5-182">Informational(4)</span></span>|  
  
 <span data-ttu-id="a39e5-183">Aşağıdaki tabloda olay bilgilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="a39e5-183">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="a39e5-184">Olay</span><span class="sxs-lookup"><span data-stu-id="a39e5-184">Event</span></span>|<span data-ttu-id="a39e5-185">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="a39e5-185">Event ID</span></span>|<span data-ttu-id="a39e5-186">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="a39e5-186">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`AppDomainMemSurvived`|<span data-ttu-id="a39e5-187">84</span><span class="sxs-lookup"><span data-stu-id="a39e5-187">84</span></span>|<span data-ttu-id="a39e5-188">Her çöp toplama sona erdi.</span><span class="sxs-lookup"><span data-stu-id="a39e5-188">Each garbage collection has ended.</span></span>|  
  
 <span data-ttu-id="a39e5-189">Aşağıdaki tabloda olay verilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="a39e5-189">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="a39e5-190">Alan adı</span><span class="sxs-lookup"><span data-stu-id="a39e5-190">Field name</span></span>|<span data-ttu-id="a39e5-191">Veri türü</span><span class="sxs-lookup"><span data-stu-id="a39e5-191">Data type</span></span>|<span data-ttu-id="a39e5-192">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a39e5-192">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="a39e5-193">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="a39e5-193">AppDomainID</span></span>|<span data-ttu-id="a39e5-194">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="a39e5-194">win:UInt64</span></span>|<span data-ttu-id="a39e5-195">Kaynak kullanım bildirilen etki alanı tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="a39e5-195">Identifier of the domain for which resource usage is being reported.</span></span>|  
|<span data-ttu-id="a39e5-196">Derdi bitti</span><span class="sxs-lookup"><span data-stu-id="a39e5-196">Survived</span></span>|<span data-ttu-id="a39e5-197">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="a39e5-197">win:UInt64</span></span>|<span data-ttu-id="a39e5-198">Sonra son koleksiyon derdi bitti ve bu uygulama etki alanı tarafından tutulması için bilinen bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="a39e5-198">The number of bytes that survived after the last collection and that are known to be held by this application domain.</span></span> <span data-ttu-id="a39e5-199">Bu sayı doğru ve eksiksiz sonra tam bir koleksiyon, ancak sonra kısa ömürlü bir koleksiyonu eksik olabilir.</span><span class="sxs-lookup"><span data-stu-id="a39e5-199">This number is accurate and complete after a full collection, but may be incomplete after an ephemeral collection.</span></span>|  
|<span data-ttu-id="a39e5-200">ProcessSurvived</span><span class="sxs-lookup"><span data-stu-id="a39e5-200">ProcessSurvived</span></span>|<span data-ttu-id="a39e5-201">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="a39e5-201">win:UInt64</span></span>|<span data-ttu-id="a39e5-202">Son koleksiyondan derdi bitti toplam bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="a39e5-202">The total bytes that survived from the last collection.</span></span> <span data-ttu-id="a39e5-203">Sonra tam bir koleksiyon, bu numara temsil bayt sayısı Yönetilen yığın Canlı tutuldu.</span><span class="sxs-lookup"><span data-stu-id="a39e5-203">After a full collection, this number represents the number of bytes being held live in managed heaps.</span></span> <span data-ttu-id="a39e5-204">Kısa ömürlü bir koleksiyon sonra bu sayı temsil bayt sayısı kısa ömürlü kuşakta Canlı tutulan.</span><span class="sxs-lookup"><span data-stu-id="a39e5-204">After an ephemeral collection, this number represents the number of bytes held live in ephemeral generations.</span></span>|  
|<span data-ttu-id="a39e5-205">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="a39e5-205">ClrInstanceID</span></span>|<span data-ttu-id="a39e5-206">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="a39e5-206">win:UInt16</span></span>|<span data-ttu-id="a39e5-207">CLR veya CoreCLR örneği için benzersiz kimlik.</span><span class="sxs-lookup"><span data-stu-id="a39e5-207">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="a39e5-208">Başa dön</span><span class="sxs-lookup"><span data-stu-id="a39e5-208">Back to top</span></span>](#top)  
  
<a name="threadappdomainenter_event"></a>   
## <a name="threadappdomainenter-event"></a><span data-ttu-id="a39e5-209">ThreadAppDomainEnter olayı</span><span class="sxs-lookup"><span data-stu-id="a39e5-209">ThreadAppDomainEnter Event</span></span>  
 <span data-ttu-id="a39e5-210">Aşağıdaki tablo düzeyi ve anahtar sözcüğü gösterir.</span><span class="sxs-lookup"><span data-stu-id="a39e5-210">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="a39e5-211">Olay oluşturma için anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="a39e5-211">Keyword for raising the event</span></span>|<span data-ttu-id="a39e5-212">Düzey</span><span class="sxs-lookup"><span data-stu-id="a39e5-212">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="a39e5-213">`AppDomainResourceManagementKeyword`(0x800)</span><span class="sxs-lookup"><span data-stu-id="a39e5-213">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="a39e5-214">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="a39e5-214">Informational(4)</span></span>|  
|<span data-ttu-id="a39e5-215">`ThreadingKeyword`(0x10000)</span><span class="sxs-lookup"><span data-stu-id="a39e5-215">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="a39e5-216">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="a39e5-216">Informational(4)</span></span>|  
  
 <span data-ttu-id="a39e5-217">Aşağıdaki tabloda olay bilgilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="a39e5-217">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="a39e5-218">Olay</span><span class="sxs-lookup"><span data-stu-id="a39e5-218">Event</span></span>|<span data-ttu-id="a39e5-219">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="a39e5-219">Event ID</span></span>|<span data-ttu-id="a39e5-220">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="a39e5-220">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ThreadAppDomainEnter`|<span data-ttu-id="a39e5-221">87</span><span class="sxs-lookup"><span data-stu-id="a39e5-221">87</span></span>|<span data-ttu-id="a39e5-222">Bir iş parçacığı uygulama etki alanı girer.</span><span class="sxs-lookup"><span data-stu-id="a39e5-222">A thread enters an application domain.</span></span>|  
  
 <span data-ttu-id="a39e5-223">Aşağıdaki tabloda olay verilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="a39e5-223">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="a39e5-224">Alan adı</span><span class="sxs-lookup"><span data-stu-id="a39e5-224">Field name</span></span>|<span data-ttu-id="a39e5-225">Veri türü</span><span class="sxs-lookup"><span data-stu-id="a39e5-225">Data type</span></span>|<span data-ttu-id="a39e5-226">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a39e5-226">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="a39e5-227">ThreadID</span><span class="sxs-lookup"><span data-stu-id="a39e5-227">ThreadID</span></span>|<span data-ttu-id="a39e5-228">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="a39e5-228">win:UInt64</span></span>|<span data-ttu-id="a39e5-229">İş parçacığı tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="a39e5-229">The thread identifier.</span></span>|  
|<span data-ttu-id="a39e5-230">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="a39e5-230">AppDomainID</span></span>|<span data-ttu-id="a39e5-231">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="a39e5-231">win:UInt64</span></span>|<span data-ttu-id="a39e5-232">Uygulama etki alanı tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="a39e5-232">The application domain identifier.</span></span>|  
|<span data-ttu-id="a39e5-233">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="a39e5-233">ClrInstanceID</span></span>|<span data-ttu-id="a39e5-234">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="a39e5-234">win:UInt16</span></span>|<span data-ttu-id="a39e5-235">CLR veya CoreCLR örneği için benzersiz kimlik.</span><span class="sxs-lookup"><span data-stu-id="a39e5-235">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="a39e5-236">Başa dön</span><span class="sxs-lookup"><span data-stu-id="a39e5-236">Back to top</span></span>](#top)  
  
<a name="threadterminated_event"></a>   
## <a name="threadterminated-event"></a><span data-ttu-id="a39e5-237">ThreadTerminated olayı</span><span class="sxs-lookup"><span data-stu-id="a39e5-237">ThreadTerminated Event</span></span>  
 <span data-ttu-id="a39e5-238">Aşağıdaki tablo düzeyi ve anahtar sözcüğü gösterir.</span><span class="sxs-lookup"><span data-stu-id="a39e5-238">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="a39e5-239">Olay oluşturma için anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="a39e5-239">Keyword for raising the event</span></span>|<span data-ttu-id="a39e5-240">Düzey</span><span class="sxs-lookup"><span data-stu-id="a39e5-240">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="a39e5-241">`AppDomainResourceManagementKeyword`(0x800)</span><span class="sxs-lookup"><span data-stu-id="a39e5-241">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="a39e5-242">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="a39e5-242">Informational(4)</span></span>|  
|<span data-ttu-id="a39e5-243">`ThreadingKeyword`(0x10000)</span><span class="sxs-lookup"><span data-stu-id="a39e5-243">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="a39e5-244">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="a39e5-244">Informational(4)</span></span>|  
  
 <span data-ttu-id="a39e5-245">Aşağıdaki tabloda olay bilgilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="a39e5-245">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="a39e5-246">Olay</span><span class="sxs-lookup"><span data-stu-id="a39e5-246">Event</span></span>|<span data-ttu-id="a39e5-247">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="a39e5-247">Event ID</span></span>|<span data-ttu-id="a39e5-248">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="a39e5-248">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ThreadTerminated`|<span data-ttu-id="a39e5-249">86</span><span class="sxs-lookup"><span data-stu-id="a39e5-249">86</span></span>|<span data-ttu-id="a39e5-250">Bir iş parçacığını sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="a39e5-250">A thread terminates.</span></span>|  
  
 <span data-ttu-id="a39e5-251">Aşağıdaki tabloda olay verilerini gösterir:</span><span class="sxs-lookup"><span data-stu-id="a39e5-251">The following table shows the event data:</span></span>  
  
|<span data-ttu-id="a39e5-252">Alan adı</span><span class="sxs-lookup"><span data-stu-id="a39e5-252">Field name</span></span>|<span data-ttu-id="a39e5-253">Veri türü</span><span class="sxs-lookup"><span data-stu-id="a39e5-253">Data type</span></span>|<span data-ttu-id="a39e5-254">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a39e5-254">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="a39e5-255">ThreadID</span><span class="sxs-lookup"><span data-stu-id="a39e5-255">ThreadID</span></span>|<span data-ttu-id="a39e5-256">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="a39e5-256">win:UInt64</span></span>|<span data-ttu-id="a39e5-257">İş parçacığı tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="a39e5-257">The thread identifier.</span></span>|  
|<span data-ttu-id="a39e5-258">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="a39e5-258">AppDomainID</span></span>|<span data-ttu-id="a39e5-259">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="a39e5-259">win:UInt64</span></span>|<span data-ttu-id="a39e5-260">Uygulama etki alanı tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="a39e5-260">The application domain identifier.</span></span>|  
|<span data-ttu-id="a39e5-261">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="a39e5-261">ClrInstanceID</span></span>|<span data-ttu-id="a39e5-262">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="a39e5-262">win:UInt16</span></span>|<span data-ttu-id="a39e5-263">CLR veya CoreCLR örneği için benzersiz kimlik.</span><span class="sxs-lookup"><span data-stu-id="a39e5-263">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a39e5-264">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a39e5-264">See Also</span></span>  
 [<span data-ttu-id="a39e5-265">CLR ETW olayları</span><span class="sxs-lookup"><span data-stu-id="a39e5-265">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
