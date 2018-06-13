---
title: Uygulama Etki Alanı Kaynak İzleme (ARM) ETW Olayları
ms.date: 03/30/2017
helpviewer_keywords:
- ETW, application domain monitoring events
- application domain monitoring events [.NET Framework]
ms.assetid: d38ff268-a2ee-434e-b504-d570880e0289
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 47ab6e52278c77156e828869dd23575561879bff
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33398189"
---
# <a name="application-domain-resource-monitoring-arm-etw-events"></a><span data-ttu-id="e778f-102">Uygulama Etki Alanı Kaynak İzleme (ARM) ETW Olayları</span><span class="sxs-lookup"><span data-stu-id="e778f-102">Application Domain Resource Monitoring (ARM) ETW Events</span></span>
<a name="top"></a> <span data-ttu-id="e778f-103">Bu olaylar uygulama etki alanı durumu hakkında ayrıntılı tanılama bilgisi sağlayın.</span><span class="sxs-lookup"><span data-stu-id="e778f-103">These events provide detailed diagnostic information about the state of an application domain.</span></span> <span data-ttu-id="e778f-104">Bu olaylar kullanın ya da aynı bilgileri elde etmek için uygulama etki alanı kaynak izleme (ARM) özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="e778f-104">You can use these events or use the application domain resource monitoring (ARM) feature to obtain the same information.</span></span>  
  
 <span data-ttu-id="e778f-105">Bu kategori aşağıdaki olaylar oluşur:</span><span class="sxs-lookup"><span data-stu-id="e778f-105">This category consists of the following events:</span></span>  
  
-   [<span data-ttu-id="e778f-106">ThreadCreated olayı</span><span class="sxs-lookup"><span data-stu-id="e778f-106">ThreadCreated Event</span></span>](#threadcreated_event)  
  
-   [<span data-ttu-id="e778f-107">AppDomainMemAllocated olayı</span><span class="sxs-lookup"><span data-stu-id="e778f-107">AppDomainMemAllocated Event</span></span>](#appdomainmemallocated_event)  
  
-   [<span data-ttu-id="e778f-108">AppDomainMemSurvived olayı</span><span class="sxs-lookup"><span data-stu-id="e778f-108">AppDomainMemSurvived Event</span></span>](#appdomainmemsurvived_event)  
  
-   [<span data-ttu-id="e778f-109">ThreadAppDomainEnter olayı</span><span class="sxs-lookup"><span data-stu-id="e778f-109">ThreadAppDomainEnter Event</span></span>](#threadappdomainenter_event)  
  
-   [<span data-ttu-id="e778f-110">ThreadTerminated olayı</span><span class="sxs-lookup"><span data-stu-id="e778f-110">ThreadTerminated Event</span></span>](#threadterminated_event)  
  
<a name="threadcreated_event"></a>   
## <a name="threadcreated-event"></a><span data-ttu-id="e778f-111">ThreadCreated olayı</span><span class="sxs-lookup"><span data-stu-id="e778f-111">ThreadCreated Event</span></span>  
 <span data-ttu-id="e778f-112">Bu olay ayrıca özeti sağlayıcı altında oluşturulur `ThreadDC` (altında `AppDomainResourceManagementRundownKeyword` anahtar sözcüğü).</span><span class="sxs-lookup"><span data-stu-id="e778f-112">This event is also raised  under the rundown provider as `ThreadDC` (under the `AppDomainResourceManagementRundownKeyword` keyword).</span></span> <span data-ttu-id="e778f-113">Bu kategorideki özeti sağlayıcısı altında tetiklenir yalnızca olay budur.</span><span class="sxs-lookup"><span data-stu-id="e778f-113">This is the only event that is raised under the rundown provider in this category.</span></span>  
  
 <span data-ttu-id="e778f-114">Aşağıdaki tablo düzeyi ve anahtar sözcüğü gösterir.</span><span class="sxs-lookup"><span data-stu-id="e778f-114">The following table shows the keyword and level.</span></span> <span data-ttu-id="e778f-115">(Daha fazla bilgi için bkz: [CLR ETW anahtar sözcükleri ve Düzeyler](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="e778f-115">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="e778f-116">Olay oluşturma için anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="e778f-116">Keyword for raising the event</span></span>|<span data-ttu-id="e778f-117">Düzey</span><span class="sxs-lookup"><span data-stu-id="e778f-117">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="e778f-118">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="e778f-118">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="e778f-119">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="e778f-119">Informational(4)</span></span>|  
|<span data-ttu-id="e778f-120">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="e778f-120">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="e778f-121">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="e778f-121">Informational(4)</span></span>|  
  
 <span data-ttu-id="e778f-122">Aşağıdaki tabloda olay bilgilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="e778f-122">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="e778f-123">Olay</span><span class="sxs-lookup"><span data-stu-id="e778f-123">Event</span></span>|<span data-ttu-id="e778f-124">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="e778f-124">Event ID</span></span>|<span data-ttu-id="e778f-125">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="e778f-125">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ThreadCreated`|<span data-ttu-id="e778f-126">85</span><span class="sxs-lookup"><span data-stu-id="e778f-126">85</span></span>|<span data-ttu-id="e778f-127">Uygulama etki alanı için bir iş parçacığı oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="e778f-127">A thread was created for the application domain.</span></span>|  
  
 <span data-ttu-id="e778f-128">Aşağıdaki tabloda olay verilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="e778f-128">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="e778f-129">Alan adı</span><span class="sxs-lookup"><span data-stu-id="e778f-129">Field name</span></span>|<span data-ttu-id="e778f-130">Veri türü</span><span class="sxs-lookup"><span data-stu-id="e778f-130">Data type</span></span>|<span data-ttu-id="e778f-131">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e778f-131">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="e778f-132">ThreadID</span><span class="sxs-lookup"><span data-stu-id="e778f-132">ThreadID</span></span>|<span data-ttu-id="e778f-133">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="e778f-133">win:UInt64</span></span>|<span data-ttu-id="e778f-134">Oluşturulan iş parçacığı kimliği.</span><span class="sxs-lookup"><span data-stu-id="e778f-134">ID of the thread that was created.</span></span>|  
|<span data-ttu-id="e778f-135">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="e778f-135">AppDomainID</span></span>|<span data-ttu-id="e778f-136">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="e778f-136">win:UInt64</span></span>|<span data-ttu-id="e778f-137">Hangi iş parçacığı için etkinlik bildirilen uygulama etki alanı tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="e778f-137">Identifier of the application domain for which thread activity is being reported.</span></span>|  
|<span data-ttu-id="e778f-138">Bayraklar</span><span class="sxs-lookup"><span data-stu-id="e778f-138">Flags</span></span>|<span data-ttu-id="e778f-139">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="e778f-139">win:UInt32</span></span>|<span data-ttu-id="e778f-140">İş parçacığı oluşturma bayrakları.</span><span class="sxs-lookup"><span data-stu-id="e778f-140">Thread creation flags.</span></span>|  
|<span data-ttu-id="e778f-141">ManagedThreadIndex</span><span class="sxs-lookup"><span data-stu-id="e778f-141">ManagedThreadIndex</span></span>|<span data-ttu-id="e778f-142">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="e778f-142">win:UInt32</span></span>|<span data-ttu-id="e778f-143">Dizini oluşturulan iş parçacığının yönetilen.</span><span class="sxs-lookup"><span data-stu-id="e778f-143">Managed index of the thread that was created.</span></span>|  
|<span data-ttu-id="e778f-144">OSThreadId</span><span class="sxs-lookup"><span data-stu-id="e778f-144">OSThreadID</span></span>|<span data-ttu-id="e778f-145">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="e778f-145">win:UInt32</span></span>|<span data-ttu-id="e778f-146">Oluşturulan iş parçacığı kimliği işletim sistemi.</span><span class="sxs-lookup"><span data-stu-id="e778f-146">Operating system ID of the thread that was created.</span></span>|  
|<span data-ttu-id="e778f-147">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="e778f-147">ClrInstanceID</span></span>|<span data-ttu-id="e778f-148">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="e778f-148">win:UInt16</span></span>|<span data-ttu-id="e778f-149">CLR veya CoreCLR örneği için benzersiz kimlik.</span><span class="sxs-lookup"><span data-stu-id="e778f-149">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="e778f-150">Başa dön</span><span class="sxs-lookup"><span data-stu-id="e778f-150">Back to top</span></span>](#top)  
  
<a name="appdomainmemallocated_event"></a>   
## <a name="appdomainmemallocated-event"></a><span data-ttu-id="e778f-151">AppDomainMemAllocated olayı</span><span class="sxs-lookup"><span data-stu-id="e778f-151">AppDomainMemAllocated Event</span></span>  
 <span data-ttu-id="e778f-152">Aşağıdaki tablo düzeyi ve anahtar sözcüğü gösterir.</span><span class="sxs-lookup"><span data-stu-id="e778f-152">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="e778f-153">Olay oluşturma için anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="e778f-153">Keyword for raising the event</span></span>|<span data-ttu-id="e778f-154">Düzey</span><span class="sxs-lookup"><span data-stu-id="e778f-154">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="e778f-155">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="e778f-155">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="e778f-156">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="e778f-156">Informational(4)</span></span>|  
  
 <span data-ttu-id="e778f-157">Aşağıdaki tabloda olay bilgilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="e778f-157">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="e778f-158">Olay</span><span class="sxs-lookup"><span data-stu-id="e778f-158">Event</span></span>|<span data-ttu-id="e778f-159">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="e778f-159">Event ID</span></span>|<span data-ttu-id="e778f-160">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="e778f-160">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`AppDomainMemAllocated`|<span data-ttu-id="e778f-161">83</span><span class="sxs-lookup"><span data-stu-id="e778f-161">83</span></span>|<span data-ttu-id="e778f-162">Her 4 MB bellek (yaklaşık) uygulama etki alanında tahsis edilir.</span><span class="sxs-lookup"><span data-stu-id="e778f-162">Every 4 MB of memory (approximately) is allocated in the application domain.</span></span>|  
  
 <span data-ttu-id="e778f-163">Aşağıdaki tabloda olay verilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="e778f-163">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="e778f-164">Alan adı</span><span class="sxs-lookup"><span data-stu-id="e778f-164">Field name</span></span>|<span data-ttu-id="e778f-165">Veri türü</span><span class="sxs-lookup"><span data-stu-id="e778f-165">Data type</span></span>|<span data-ttu-id="e778f-166">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e778f-166">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="e778f-167">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="e778f-167">AppDomainID</span></span>|<span data-ttu-id="e778f-168">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="e778f-168">win:UInt64</span></span>|<span data-ttu-id="e778f-169">Kaynak kullanım bildirilen uygulama etki alanı tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="e778f-169">Identifier of the application domain for which resource usage is being reported.</span></span>|  
|<span data-ttu-id="e778f-170">Ayrılmış</span><span class="sxs-lookup"><span data-stu-id="e778f-170">Allocated</span></span>|<span data-ttu-id="e778f-171">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="e778f-171">win:UInt64</span></span>|<span data-ttu-id="e778f-172">Toplam uygulama etki alanı oluşturulduktan sonra bu uygulama etki alanında ayrılmış bayt sayısı (boşaltılmış bellek miktarını değil çıkarılır).</span><span class="sxs-lookup"><span data-stu-id="e778f-172">The total number of bytes allocated in this application domain since the application domain was created (the amount of freed memory is not subtracted).</span></span>|  
|<span data-ttu-id="e778f-173">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="e778f-173">ClrInstanceID</span></span>|<span data-ttu-id="e778f-174">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="e778f-174">win:UInt16</span></span>|<span data-ttu-id="e778f-175">CLR veya CoreCLR örneği için benzersiz kimlik.</span><span class="sxs-lookup"><span data-stu-id="e778f-175">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="e778f-176">Başa dön</span><span class="sxs-lookup"><span data-stu-id="e778f-176">Back to top</span></span>](#top)  
  
<a name="appdomainmemsurvived_event"></a>   
## <a name="appdomainmemsurvived-event"></a><span data-ttu-id="e778f-177">AppDomainMemSurvived olayı</span><span class="sxs-lookup"><span data-stu-id="e778f-177">AppDomainMemSurvived Event</span></span>  
 <span data-ttu-id="e778f-178">Aşağıdaki tablo düzeyi ve anahtar sözcüğü gösterir.</span><span class="sxs-lookup"><span data-stu-id="e778f-178">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="e778f-179">Olay oluşturma için anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="e778f-179">Keyword for raising the event</span></span>|<span data-ttu-id="e778f-180">Düzey</span><span class="sxs-lookup"><span data-stu-id="e778f-180">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="e778f-181">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="e778f-181">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="e778f-182">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="e778f-182">Informational(4)</span></span>|  
  
 <span data-ttu-id="e778f-183">Aşağıdaki tabloda olay bilgilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="e778f-183">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="e778f-184">Olay</span><span class="sxs-lookup"><span data-stu-id="e778f-184">Event</span></span>|<span data-ttu-id="e778f-185">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="e778f-185">Event ID</span></span>|<span data-ttu-id="e778f-186">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="e778f-186">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`AppDomainMemSurvived`|<span data-ttu-id="e778f-187">84</span><span class="sxs-lookup"><span data-stu-id="e778f-187">84</span></span>|<span data-ttu-id="e778f-188">Her çöp toplama sona erdi.</span><span class="sxs-lookup"><span data-stu-id="e778f-188">Each garbage collection has ended.</span></span>|  
  
 <span data-ttu-id="e778f-189">Aşağıdaki tabloda olay verilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="e778f-189">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="e778f-190">Alan adı</span><span class="sxs-lookup"><span data-stu-id="e778f-190">Field name</span></span>|<span data-ttu-id="e778f-191">Veri türü</span><span class="sxs-lookup"><span data-stu-id="e778f-191">Data type</span></span>|<span data-ttu-id="e778f-192">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e778f-192">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="e778f-193">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="e778f-193">AppDomainID</span></span>|<span data-ttu-id="e778f-194">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="e778f-194">win:UInt64</span></span>|<span data-ttu-id="e778f-195">Kaynak kullanım bildirilen etki alanı tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="e778f-195">Identifier of the domain for which resource usage is being reported.</span></span>|  
|<span data-ttu-id="e778f-196">Derdi bitti</span><span class="sxs-lookup"><span data-stu-id="e778f-196">Survived</span></span>|<span data-ttu-id="e778f-197">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="e778f-197">win:UInt64</span></span>|<span data-ttu-id="e778f-198">Sonra son koleksiyon derdi bitti ve bu uygulama etki alanı tarafından tutulması için bilinen bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="e778f-198">The number of bytes that survived after the last collection and that are known to be held by this application domain.</span></span> <span data-ttu-id="e778f-199">Bu sayı doğru ve eksiksiz sonra tam bir koleksiyon, ancak sonra kısa ömürlü bir koleksiyonu eksik olabilir.</span><span class="sxs-lookup"><span data-stu-id="e778f-199">This number is accurate and complete after a full collection, but may be incomplete after an ephemeral collection.</span></span>|  
|<span data-ttu-id="e778f-200">ProcessSurvived</span><span class="sxs-lookup"><span data-stu-id="e778f-200">ProcessSurvived</span></span>|<span data-ttu-id="e778f-201">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="e778f-201">win:UInt64</span></span>|<span data-ttu-id="e778f-202">Son koleksiyondan derdi bitti toplam bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="e778f-202">The total bytes that survived from the last collection.</span></span> <span data-ttu-id="e778f-203">Sonra tam bir koleksiyon, bu numara temsil bayt sayısı Yönetilen yığın Canlı tutuldu.</span><span class="sxs-lookup"><span data-stu-id="e778f-203">After a full collection, this number represents the number of bytes being held live in managed heaps.</span></span> <span data-ttu-id="e778f-204">Kısa ömürlü bir koleksiyon sonra bu sayı temsil bayt sayısı kısa ömürlü kuşakta Canlı tutulan.</span><span class="sxs-lookup"><span data-stu-id="e778f-204">After an ephemeral collection, this number represents the number of bytes held live in ephemeral generations.</span></span>|  
|<span data-ttu-id="e778f-205">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="e778f-205">ClrInstanceID</span></span>|<span data-ttu-id="e778f-206">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="e778f-206">win:UInt16</span></span>|<span data-ttu-id="e778f-207">CLR veya CoreCLR örneği için benzersiz kimlik.</span><span class="sxs-lookup"><span data-stu-id="e778f-207">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="e778f-208">Başa dön</span><span class="sxs-lookup"><span data-stu-id="e778f-208">Back to top</span></span>](#top)  
  
<a name="threadappdomainenter_event"></a>   
## <a name="threadappdomainenter-event"></a><span data-ttu-id="e778f-209">ThreadAppDomainEnter olayı</span><span class="sxs-lookup"><span data-stu-id="e778f-209">ThreadAppDomainEnter Event</span></span>  
 <span data-ttu-id="e778f-210">Aşağıdaki tablo düzeyi ve anahtar sözcüğü gösterir.</span><span class="sxs-lookup"><span data-stu-id="e778f-210">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="e778f-211">Olay oluşturma için anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="e778f-211">Keyword for raising the event</span></span>|<span data-ttu-id="e778f-212">Düzey</span><span class="sxs-lookup"><span data-stu-id="e778f-212">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="e778f-213">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="e778f-213">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="e778f-214">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="e778f-214">Informational(4)</span></span>|  
|<span data-ttu-id="e778f-215">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="e778f-215">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="e778f-216">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="e778f-216">Informational(4)</span></span>|  
  
 <span data-ttu-id="e778f-217">Aşağıdaki tabloda olay bilgilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="e778f-217">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="e778f-218">Olay</span><span class="sxs-lookup"><span data-stu-id="e778f-218">Event</span></span>|<span data-ttu-id="e778f-219">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="e778f-219">Event ID</span></span>|<span data-ttu-id="e778f-220">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="e778f-220">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ThreadAppDomainEnter`|<span data-ttu-id="e778f-221">87</span><span class="sxs-lookup"><span data-stu-id="e778f-221">87</span></span>|<span data-ttu-id="e778f-222">Bir iş parçacığı uygulama etki alanı girer.</span><span class="sxs-lookup"><span data-stu-id="e778f-222">A thread enters an application domain.</span></span>|  
  
 <span data-ttu-id="e778f-223">Aşağıdaki tabloda olay verilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="e778f-223">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="e778f-224">Alan adı</span><span class="sxs-lookup"><span data-stu-id="e778f-224">Field name</span></span>|<span data-ttu-id="e778f-225">Veri türü</span><span class="sxs-lookup"><span data-stu-id="e778f-225">Data type</span></span>|<span data-ttu-id="e778f-226">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e778f-226">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="e778f-227">ThreadID</span><span class="sxs-lookup"><span data-stu-id="e778f-227">ThreadID</span></span>|<span data-ttu-id="e778f-228">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="e778f-228">win:UInt64</span></span>|<span data-ttu-id="e778f-229">İş parçacığı tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="e778f-229">The thread identifier.</span></span>|  
|<span data-ttu-id="e778f-230">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="e778f-230">AppDomainID</span></span>|<span data-ttu-id="e778f-231">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="e778f-231">win:UInt64</span></span>|<span data-ttu-id="e778f-232">Uygulama etki alanı tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="e778f-232">The application domain identifier.</span></span>|  
|<span data-ttu-id="e778f-233">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="e778f-233">ClrInstanceID</span></span>|<span data-ttu-id="e778f-234">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="e778f-234">win:UInt16</span></span>|<span data-ttu-id="e778f-235">CLR veya CoreCLR örneği için benzersiz kimlik.</span><span class="sxs-lookup"><span data-stu-id="e778f-235">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="e778f-236">Başa dön</span><span class="sxs-lookup"><span data-stu-id="e778f-236">Back to top</span></span>](#top)  
  
<a name="threadterminated_event"></a>   
## <a name="threadterminated-event"></a><span data-ttu-id="e778f-237">ThreadTerminated olayı</span><span class="sxs-lookup"><span data-stu-id="e778f-237">ThreadTerminated Event</span></span>  
 <span data-ttu-id="e778f-238">Aşağıdaki tablo düzeyi ve anahtar sözcüğü gösterir.</span><span class="sxs-lookup"><span data-stu-id="e778f-238">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="e778f-239">Olay oluşturma için anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="e778f-239">Keyword for raising the event</span></span>|<span data-ttu-id="e778f-240">Düzey</span><span class="sxs-lookup"><span data-stu-id="e778f-240">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="e778f-241">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="e778f-241">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="e778f-242">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="e778f-242">Informational(4)</span></span>|  
|<span data-ttu-id="e778f-243">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="e778f-243">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="e778f-244">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="e778f-244">Informational(4)</span></span>|  
  
 <span data-ttu-id="e778f-245">Aşağıdaki tabloda olay bilgilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="e778f-245">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="e778f-246">Olay</span><span class="sxs-lookup"><span data-stu-id="e778f-246">Event</span></span>|<span data-ttu-id="e778f-247">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="e778f-247">Event ID</span></span>|<span data-ttu-id="e778f-248">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="e778f-248">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ThreadTerminated`|<span data-ttu-id="e778f-249">86</span><span class="sxs-lookup"><span data-stu-id="e778f-249">86</span></span>|<span data-ttu-id="e778f-250">Bir iş parçacığını sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="e778f-250">A thread terminates.</span></span>|  
  
 <span data-ttu-id="e778f-251">Aşağıdaki tabloda olay verilerini gösterir:</span><span class="sxs-lookup"><span data-stu-id="e778f-251">The following table shows the event data:</span></span>  
  
|<span data-ttu-id="e778f-252">Alan adı</span><span class="sxs-lookup"><span data-stu-id="e778f-252">Field name</span></span>|<span data-ttu-id="e778f-253">Veri türü</span><span class="sxs-lookup"><span data-stu-id="e778f-253">Data type</span></span>|<span data-ttu-id="e778f-254">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e778f-254">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="e778f-255">ThreadID</span><span class="sxs-lookup"><span data-stu-id="e778f-255">ThreadID</span></span>|<span data-ttu-id="e778f-256">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="e778f-256">win:UInt64</span></span>|<span data-ttu-id="e778f-257">İş parçacığı tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="e778f-257">The thread identifier.</span></span>|  
|<span data-ttu-id="e778f-258">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="e778f-258">AppDomainID</span></span>|<span data-ttu-id="e778f-259">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="e778f-259">win:UInt64</span></span>|<span data-ttu-id="e778f-260">Uygulama etki alanı tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="e778f-260">The application domain identifier.</span></span>|  
|<span data-ttu-id="e778f-261">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="e778f-261">ClrInstanceID</span></span>|<span data-ttu-id="e778f-262">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="e778f-262">win:UInt16</span></span>|<span data-ttu-id="e778f-263">CLR veya CoreCLR örneği için benzersiz kimlik.</span><span class="sxs-lookup"><span data-stu-id="e778f-263">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e778f-264">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e778f-264">See Also</span></span>  
 [<span data-ttu-id="e778f-265">CLR ETW Olayları</span><span class="sxs-lookup"><span data-stu-id="e778f-265">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
