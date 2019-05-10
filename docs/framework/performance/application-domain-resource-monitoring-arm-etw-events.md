---
title: Uygulama Etki Alanı Kaynak İzleme (ARM) ETW Olayları
ms.date: 03/30/2017
helpviewer_keywords:
- ETW, application domain monitoring events
- application domain monitoring events [.NET Framework]
ms.assetid: d38ff268-a2ee-434e-b504-d570880e0289
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ac396e1a5b83f33068266553024c37ef436c150d
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64616629"
---
# <a name="application-domain-resource-monitoring-arm-etw-events"></a><span data-ttu-id="89f05-102">Uygulama Etki Alanı Kaynak İzleme (ARM) ETW Olayları</span><span class="sxs-lookup"><span data-stu-id="89f05-102">Application Domain Resource Monitoring (ARM) ETW Events</span></span>
<a name="top"></a> <span data-ttu-id="89f05-103">Bu olayları, uygulama etki alanı durumu hakkında ayrıntılı tanılama bilgileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="89f05-103">These events provide detailed diagnostic information about the state of an application domain.</span></span> <span data-ttu-id="89f05-104">Bu olayları kullanan ya da aynı bilgileri edinmek için uygulama etki alanı kaynak izleme (ARM) özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="89f05-104">You can use these events or use the application domain resource monitoring (ARM) feature to obtain the same information.</span></span>  
  
 <span data-ttu-id="89f05-105">Bu kategori aşağıdaki olaylar oluşur:</span><span class="sxs-lookup"><span data-stu-id="89f05-105">This category consists of the following events:</span></span>  
  
- [<span data-ttu-id="89f05-106">ThreadCreated olay</span><span class="sxs-lookup"><span data-stu-id="89f05-106">ThreadCreated Event</span></span>](#threadcreated_event)  
  
- [<span data-ttu-id="89f05-107">AppDomainMemAllocated olay</span><span class="sxs-lookup"><span data-stu-id="89f05-107">AppDomainMemAllocated Event</span></span>](#appdomainmemallocated_event)  
  
- [<span data-ttu-id="89f05-108">AppDomainMemSurvived olay</span><span class="sxs-lookup"><span data-stu-id="89f05-108">AppDomainMemSurvived Event</span></span>](#appdomainmemsurvived_event)  
  
- [<span data-ttu-id="89f05-109">ThreadAppDomainEnter olay</span><span class="sxs-lookup"><span data-stu-id="89f05-109">ThreadAppDomainEnter Event</span></span>](#threadappdomainenter_event)  
  
- [<span data-ttu-id="89f05-110">ThreadTerminated olay</span><span class="sxs-lookup"><span data-stu-id="89f05-110">ThreadTerminated Event</span></span>](#threadterminated_event)  
  
<a name="threadcreated_event"></a>   
## <a name="threadcreated-event"></a><span data-ttu-id="89f05-111">ThreadCreated olay</span><span class="sxs-lookup"><span data-stu-id="89f05-111">ThreadCreated Event</span></span>  
 <span data-ttu-id="89f05-112">Bu olay Özet sağlayıcı altında oluşturulur `ThreadDC` (altında `AppDomainResourceManagementRundownKeyword` anahtar sözcüğü).</span><span class="sxs-lookup"><span data-stu-id="89f05-112">This event is also raised  under the rundown provider as `ThreadDC` (under the `AppDomainResourceManagementRundownKeyword` keyword).</span></span> <span data-ttu-id="89f05-113">Bu kategorideki Özet sağlayıcı altında oluşturulur yalnızca olay budur.</span><span class="sxs-lookup"><span data-stu-id="89f05-113">This is the only event that is raised under the rundown provider in this category.</span></span>  
  
 <span data-ttu-id="89f05-114">Aşağıdaki tabloda, düzeyi ve anahtar sözcüğü gösterir.</span><span class="sxs-lookup"><span data-stu-id="89f05-114">The following table shows the keyword and level.</span></span> <span data-ttu-id="89f05-115">(Daha fazla bilgi için [CLR ETW anahtar sözcükleri ve Düzeyler](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="89f05-115">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="89f05-116">Olayı için anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="89f05-116">Keyword for raising the event</span></span>|<span data-ttu-id="89f05-117">Düzey</span><span class="sxs-lookup"><span data-stu-id="89f05-117">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="89f05-118">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="89f05-118">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="89f05-119">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="89f05-119">Informational(4)</span></span>|  
|<span data-ttu-id="89f05-120">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="89f05-120">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="89f05-121">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="89f05-121">Informational(4)</span></span>|  
  
 <span data-ttu-id="89f05-122">Aşağıdaki tabloda, olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="89f05-122">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="89f05-123">Olay</span><span class="sxs-lookup"><span data-stu-id="89f05-123">Event</span></span>|<span data-ttu-id="89f05-124">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="89f05-124">Event ID</span></span>|<span data-ttu-id="89f05-125">Ne zaman gerçekleşti</span><span class="sxs-lookup"><span data-stu-id="89f05-125">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ThreadCreated`|<span data-ttu-id="89f05-126">85</span><span class="sxs-lookup"><span data-stu-id="89f05-126">85</span></span>|<span data-ttu-id="89f05-127">Uygulama etki alanı için bir iş parçacığı oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="89f05-127">A thread was created for the application domain.</span></span>|  
  
 <span data-ttu-id="89f05-128">Aşağıdaki tabloda, olay verilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="89f05-128">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="89f05-129">Alan adı</span><span class="sxs-lookup"><span data-stu-id="89f05-129">Field name</span></span>|<span data-ttu-id="89f05-130">Veri türü</span><span class="sxs-lookup"><span data-stu-id="89f05-130">Data type</span></span>|<span data-ttu-id="89f05-131">Açıklama</span><span class="sxs-lookup"><span data-stu-id="89f05-131">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="89f05-132">ThreadID</span><span class="sxs-lookup"><span data-stu-id="89f05-132">ThreadID</span></span>|<span data-ttu-id="89f05-133">Kazanma: UInt64</span><span class="sxs-lookup"><span data-stu-id="89f05-133">win:UInt64</span></span>|<span data-ttu-id="89f05-134">Oluşturulan iş parçacığının kimliği.</span><span class="sxs-lookup"><span data-stu-id="89f05-134">ID of the thread that was created.</span></span>|  
|<span data-ttu-id="89f05-135">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="89f05-135">AppDomainID</span></span>|<span data-ttu-id="89f05-136">Kazanma: UInt64</span><span class="sxs-lookup"><span data-stu-id="89f05-136">win:UInt64</span></span>|<span data-ttu-id="89f05-137">Hangi iş parçacığı için etkinlik bildirilen uygulama etki alanı tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="89f05-137">Identifier of the application domain for which thread activity is being reported.</span></span>|  
|<span data-ttu-id="89f05-138">Bayraklar</span><span class="sxs-lookup"><span data-stu-id="89f05-138">Flags</span></span>|<span data-ttu-id="89f05-139">Kazanma: UInt32</span><span class="sxs-lookup"><span data-stu-id="89f05-139">win:UInt32</span></span>|<span data-ttu-id="89f05-140">İş parçacığı oluşturma bayrakları.</span><span class="sxs-lookup"><span data-stu-id="89f05-140">Thread creation flags.</span></span>|  
|<span data-ttu-id="89f05-141">ManagedThreadIndex</span><span class="sxs-lookup"><span data-stu-id="89f05-141">ManagedThreadIndex</span></span>|<span data-ttu-id="89f05-142">Kazanma: UInt32</span><span class="sxs-lookup"><span data-stu-id="89f05-142">win:UInt32</span></span>|<span data-ttu-id="89f05-143">Dizini oluşturulan iş parçacığının yönetilen.</span><span class="sxs-lookup"><span data-stu-id="89f05-143">Managed index of the thread that was created.</span></span>|  
|<span data-ttu-id="89f05-144">OSThreadId</span><span class="sxs-lookup"><span data-stu-id="89f05-144">OSThreadID</span></span>|<span data-ttu-id="89f05-145">Kazanma: UInt32</span><span class="sxs-lookup"><span data-stu-id="89f05-145">win:UInt32</span></span>|<span data-ttu-id="89f05-146">Oluşturulan iş parçacığının kimliği işletim sistemi.</span><span class="sxs-lookup"><span data-stu-id="89f05-146">Operating system ID of the thread that was created.</span></span>|  
|<span data-ttu-id="89f05-147">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="89f05-147">ClrInstanceID</span></span>|<span data-ttu-id="89f05-148">Kazanma: UInt16</span><span class="sxs-lookup"><span data-stu-id="89f05-148">win:UInt16</span></span>|<span data-ttu-id="89f05-149">CLR veya CoreCLR örneği için benzersiz kimlik.</span><span class="sxs-lookup"><span data-stu-id="89f05-149">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="89f05-150">Başa dön</span><span class="sxs-lookup"><span data-stu-id="89f05-150">Back to top</span></span>](#top)  
  
<a name="appdomainmemallocated_event"></a>   
## <a name="appdomainmemallocated-event"></a><span data-ttu-id="89f05-151">AppDomainMemAllocated olay</span><span class="sxs-lookup"><span data-stu-id="89f05-151">AppDomainMemAllocated Event</span></span>  
 <span data-ttu-id="89f05-152">Aşağıdaki tabloda, düzeyi ve anahtar sözcüğü gösterir.</span><span class="sxs-lookup"><span data-stu-id="89f05-152">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="89f05-153">Olayı için anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="89f05-153">Keyword for raising the event</span></span>|<span data-ttu-id="89f05-154">Düzey</span><span class="sxs-lookup"><span data-stu-id="89f05-154">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="89f05-155">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="89f05-155">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="89f05-156">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="89f05-156">Informational(4)</span></span>|  
  
 <span data-ttu-id="89f05-157">Aşağıdaki tabloda, olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="89f05-157">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="89f05-158">Olay</span><span class="sxs-lookup"><span data-stu-id="89f05-158">Event</span></span>|<span data-ttu-id="89f05-159">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="89f05-159">Event ID</span></span>|<span data-ttu-id="89f05-160">Ne zaman gerçekleşti</span><span class="sxs-lookup"><span data-stu-id="89f05-160">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`AppDomainMemAllocated`|<span data-ttu-id="89f05-161">83</span><span class="sxs-lookup"><span data-stu-id="89f05-161">83</span></span>|<span data-ttu-id="89f05-162">Her 4 MB bellek, uygulama etki alanında (yaklaşık) ayrılır.</span><span class="sxs-lookup"><span data-stu-id="89f05-162">Every 4 MB of memory (approximately) is allocated in the application domain.</span></span>|  
  
 <span data-ttu-id="89f05-163">Aşağıdaki tabloda, olay verilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="89f05-163">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="89f05-164">Alan adı</span><span class="sxs-lookup"><span data-stu-id="89f05-164">Field name</span></span>|<span data-ttu-id="89f05-165">Veri türü</span><span class="sxs-lookup"><span data-stu-id="89f05-165">Data type</span></span>|<span data-ttu-id="89f05-166">Açıklama</span><span class="sxs-lookup"><span data-stu-id="89f05-166">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="89f05-167">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="89f05-167">AppDomainID</span></span>|<span data-ttu-id="89f05-168">Kazanma: UInt64</span><span class="sxs-lookup"><span data-stu-id="89f05-168">win:UInt64</span></span>|<span data-ttu-id="89f05-169">Kaynak kullanımı bildirilen uygulama etki alanı tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="89f05-169">Identifier of the application domain for which resource usage is being reported.</span></span>|  
|<span data-ttu-id="89f05-170">ayrılmış</span><span class="sxs-lookup"><span data-stu-id="89f05-170">Allocated</span></span>|<span data-ttu-id="89f05-171">Kazanma: UInt64</span><span class="sxs-lookup"><span data-stu-id="89f05-171">win:UInt64</span></span>|<span data-ttu-id="89f05-172">Uygulama etki alanı oluşturulduktan sonra bu uygulama etki alanında ayrılmış baytların toplam sayısı (boşaltılmış bellek miktarı değil çıkarılır).</span><span class="sxs-lookup"><span data-stu-id="89f05-172">The total number of bytes allocated in this application domain since the application domain was created (the amount of freed memory is not subtracted).</span></span>|  
|<span data-ttu-id="89f05-173">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="89f05-173">ClrInstanceID</span></span>|<span data-ttu-id="89f05-174">Kazanma: UInt16</span><span class="sxs-lookup"><span data-stu-id="89f05-174">win:UInt16</span></span>|<span data-ttu-id="89f05-175">CLR veya CoreCLR örneği için benzersiz kimlik.</span><span class="sxs-lookup"><span data-stu-id="89f05-175">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="89f05-176">Başa dön</span><span class="sxs-lookup"><span data-stu-id="89f05-176">Back to top</span></span>](#top)  
  
<a name="appdomainmemsurvived_event"></a>   
## <a name="appdomainmemsurvived-event"></a><span data-ttu-id="89f05-177">AppDomainMemSurvived olay</span><span class="sxs-lookup"><span data-stu-id="89f05-177">AppDomainMemSurvived Event</span></span>  
 <span data-ttu-id="89f05-178">Aşağıdaki tabloda, düzeyi ve anahtar sözcüğü gösterir.</span><span class="sxs-lookup"><span data-stu-id="89f05-178">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="89f05-179">Olayı için anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="89f05-179">Keyword for raising the event</span></span>|<span data-ttu-id="89f05-180">Düzey</span><span class="sxs-lookup"><span data-stu-id="89f05-180">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="89f05-181">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="89f05-181">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="89f05-182">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="89f05-182">Informational(4)</span></span>|  
  
 <span data-ttu-id="89f05-183">Aşağıdaki tabloda, olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="89f05-183">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="89f05-184">Olay</span><span class="sxs-lookup"><span data-stu-id="89f05-184">Event</span></span>|<span data-ttu-id="89f05-185">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="89f05-185">Event ID</span></span>|<span data-ttu-id="89f05-186">Ne zaman gerçekleşti</span><span class="sxs-lookup"><span data-stu-id="89f05-186">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`AppDomainMemSurvived`|<span data-ttu-id="89f05-187">84</span><span class="sxs-lookup"><span data-stu-id="89f05-187">84</span></span>|<span data-ttu-id="89f05-188">Her çöp toplama sona erdi.</span><span class="sxs-lookup"><span data-stu-id="89f05-188">Each garbage collection has ended.</span></span>|  
  
 <span data-ttu-id="89f05-189">Aşağıdaki tabloda, olay verilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="89f05-189">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="89f05-190">Alan adı</span><span class="sxs-lookup"><span data-stu-id="89f05-190">Field name</span></span>|<span data-ttu-id="89f05-191">Veri türü</span><span class="sxs-lookup"><span data-stu-id="89f05-191">Data type</span></span>|<span data-ttu-id="89f05-192">Açıklama</span><span class="sxs-lookup"><span data-stu-id="89f05-192">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="89f05-193">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="89f05-193">AppDomainID</span></span>|<span data-ttu-id="89f05-194">Kazanma: UInt64</span><span class="sxs-lookup"><span data-stu-id="89f05-194">win:UInt64</span></span>|<span data-ttu-id="89f05-195">Kullanım raporlama için hangi kaynak etki alanı tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="89f05-195">Identifier of the domain for which resource usage is being reported.</span></span>|  
|<span data-ttu-id="89f05-196">Kurtulan</span><span class="sxs-lookup"><span data-stu-id="89f05-196">Survived</span></span>|<span data-ttu-id="89f05-197">Kazanma: UInt64</span><span class="sxs-lookup"><span data-stu-id="89f05-197">win:UInt64</span></span>|<span data-ttu-id="89f05-198">Sonra son toplamadan kurtulan ve bu uygulama etki alanına göre tutulması için bilinen bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="89f05-198">The number of bytes that survived after the last collection and that are known to be held by this application domain.</span></span> <span data-ttu-id="89f05-199">Bu sayı, sonra tam bir koleksiyon doğru ve eksiksiz olması, ancak kısa ömürlü bir toplamanın ardından tamamlanmamış olabilir.</span><span class="sxs-lookup"><span data-stu-id="89f05-199">This number is accurate and complete after a full collection, but may be incomplete after an ephemeral collection.</span></span>|  
|<span data-ttu-id="89f05-200">ProcessSurvived</span><span class="sxs-lookup"><span data-stu-id="89f05-200">ProcessSurvived</span></span>|<span data-ttu-id="89f05-201">Kazanma: UInt64</span><span class="sxs-lookup"><span data-stu-id="89f05-201">win:UInt64</span></span>|<span data-ttu-id="89f05-202">Son derlemeden kurtulan toplam bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="89f05-202">The total bytes that survived from the last collection.</span></span> <span data-ttu-id="89f05-203">Tam bir koleksiyon sonra bu numara temsil bayt sayısı, yönetilen yığınlar Canlı tutulmakta.</span><span class="sxs-lookup"><span data-stu-id="89f05-203">After a full collection, this number represents the number of bytes being held live in managed heaps.</span></span> <span data-ttu-id="89f05-204">Kısa ömürlü bir toplamanın ardından bu numara temsil bayt sayısı kısa ömürlü nesillerde Canlı tutulan.</span><span class="sxs-lookup"><span data-stu-id="89f05-204">After an ephemeral collection, this number represents the number of bytes held live in ephemeral generations.</span></span>|  
|<span data-ttu-id="89f05-205">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="89f05-205">ClrInstanceID</span></span>|<span data-ttu-id="89f05-206">Kazanma: UInt16</span><span class="sxs-lookup"><span data-stu-id="89f05-206">win:UInt16</span></span>|<span data-ttu-id="89f05-207">CLR veya CoreCLR örneği için benzersiz kimlik.</span><span class="sxs-lookup"><span data-stu-id="89f05-207">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="89f05-208">Başa dön</span><span class="sxs-lookup"><span data-stu-id="89f05-208">Back to top</span></span>](#top)  
  
<a name="threadappdomainenter_event"></a>   
## <a name="threadappdomainenter-event"></a><span data-ttu-id="89f05-209">ThreadAppDomainEnter olay</span><span class="sxs-lookup"><span data-stu-id="89f05-209">ThreadAppDomainEnter Event</span></span>  
 <span data-ttu-id="89f05-210">Aşağıdaki tabloda, düzeyi ve anahtar sözcüğü gösterir.</span><span class="sxs-lookup"><span data-stu-id="89f05-210">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="89f05-211">Olayı için anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="89f05-211">Keyword for raising the event</span></span>|<span data-ttu-id="89f05-212">Düzey</span><span class="sxs-lookup"><span data-stu-id="89f05-212">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="89f05-213">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="89f05-213">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="89f05-214">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="89f05-214">Informational(4)</span></span>|  
|<span data-ttu-id="89f05-215">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="89f05-215">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="89f05-216">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="89f05-216">Informational(4)</span></span>|  
  
 <span data-ttu-id="89f05-217">Aşağıdaki tabloda, olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="89f05-217">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="89f05-218">Olay</span><span class="sxs-lookup"><span data-stu-id="89f05-218">Event</span></span>|<span data-ttu-id="89f05-219">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="89f05-219">Event ID</span></span>|<span data-ttu-id="89f05-220">Ne zaman gerçekleşti</span><span class="sxs-lookup"><span data-stu-id="89f05-220">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ThreadAppDomainEnter`|<span data-ttu-id="89f05-221">87</span><span class="sxs-lookup"><span data-stu-id="89f05-221">87</span></span>|<span data-ttu-id="89f05-222">Bir iş parçacığı, bir uygulama etki alanı girer.</span><span class="sxs-lookup"><span data-stu-id="89f05-222">A thread enters an application domain.</span></span>|  
  
 <span data-ttu-id="89f05-223">Aşağıdaki tabloda, olay verilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="89f05-223">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="89f05-224">Alan adı</span><span class="sxs-lookup"><span data-stu-id="89f05-224">Field name</span></span>|<span data-ttu-id="89f05-225">Veri türü</span><span class="sxs-lookup"><span data-stu-id="89f05-225">Data type</span></span>|<span data-ttu-id="89f05-226">Açıklama</span><span class="sxs-lookup"><span data-stu-id="89f05-226">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="89f05-227">ThreadID</span><span class="sxs-lookup"><span data-stu-id="89f05-227">ThreadID</span></span>|<span data-ttu-id="89f05-228">Kazanma: UInt64</span><span class="sxs-lookup"><span data-stu-id="89f05-228">win:UInt64</span></span>|<span data-ttu-id="89f05-229">İş parçacığı tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="89f05-229">The thread identifier.</span></span>|  
|<span data-ttu-id="89f05-230">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="89f05-230">AppDomainID</span></span>|<span data-ttu-id="89f05-231">Kazanma: UInt64</span><span class="sxs-lookup"><span data-stu-id="89f05-231">win:UInt64</span></span>|<span data-ttu-id="89f05-232">Uygulama etki alanı tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="89f05-232">The application domain identifier.</span></span>|  
|<span data-ttu-id="89f05-233">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="89f05-233">ClrInstanceID</span></span>|<span data-ttu-id="89f05-234">Kazanma: UInt16</span><span class="sxs-lookup"><span data-stu-id="89f05-234">win:UInt16</span></span>|<span data-ttu-id="89f05-235">CLR veya CoreCLR örneği için benzersiz kimlik.</span><span class="sxs-lookup"><span data-stu-id="89f05-235">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="89f05-236">Başa dön</span><span class="sxs-lookup"><span data-stu-id="89f05-236">Back to top</span></span>](#top)  
  
<a name="threadterminated_event"></a>   
## <a name="threadterminated-event"></a><span data-ttu-id="89f05-237">ThreadTerminated olay</span><span class="sxs-lookup"><span data-stu-id="89f05-237">ThreadTerminated Event</span></span>  
 <span data-ttu-id="89f05-238">Aşağıdaki tabloda, düzeyi ve anahtar sözcüğü gösterir.</span><span class="sxs-lookup"><span data-stu-id="89f05-238">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="89f05-239">Olayı için anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="89f05-239">Keyword for raising the event</span></span>|<span data-ttu-id="89f05-240">Düzey</span><span class="sxs-lookup"><span data-stu-id="89f05-240">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="89f05-241">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="89f05-241">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="89f05-242">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="89f05-242">Informational(4)</span></span>|  
|<span data-ttu-id="89f05-243">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="89f05-243">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="89f05-244">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="89f05-244">Informational(4)</span></span>|  
  
 <span data-ttu-id="89f05-245">Aşağıdaki tabloda, olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="89f05-245">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="89f05-246">Olay</span><span class="sxs-lookup"><span data-stu-id="89f05-246">Event</span></span>|<span data-ttu-id="89f05-247">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="89f05-247">Event ID</span></span>|<span data-ttu-id="89f05-248">Ne zaman gerçekleşti</span><span class="sxs-lookup"><span data-stu-id="89f05-248">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ThreadTerminated`|<span data-ttu-id="89f05-249">86</span><span class="sxs-lookup"><span data-stu-id="89f05-249">86</span></span>|<span data-ttu-id="89f05-250">Bir iş parçacığı sonlanır.</span><span class="sxs-lookup"><span data-stu-id="89f05-250">A thread terminates.</span></span>|  
  
 <span data-ttu-id="89f05-251">Aşağıdaki tabloda, olay verilerini gösterir:</span><span class="sxs-lookup"><span data-stu-id="89f05-251">The following table shows the event data:</span></span>  
  
|<span data-ttu-id="89f05-252">Alan adı</span><span class="sxs-lookup"><span data-stu-id="89f05-252">Field name</span></span>|<span data-ttu-id="89f05-253">Veri türü</span><span class="sxs-lookup"><span data-stu-id="89f05-253">Data type</span></span>|<span data-ttu-id="89f05-254">Açıklama</span><span class="sxs-lookup"><span data-stu-id="89f05-254">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="89f05-255">ThreadID</span><span class="sxs-lookup"><span data-stu-id="89f05-255">ThreadID</span></span>|<span data-ttu-id="89f05-256">Kazanma: UInt64</span><span class="sxs-lookup"><span data-stu-id="89f05-256">win:UInt64</span></span>|<span data-ttu-id="89f05-257">İş parçacığı tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="89f05-257">The thread identifier.</span></span>|  
|<span data-ttu-id="89f05-258">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="89f05-258">AppDomainID</span></span>|<span data-ttu-id="89f05-259">Kazanma: UInt64</span><span class="sxs-lookup"><span data-stu-id="89f05-259">win:UInt64</span></span>|<span data-ttu-id="89f05-260">Uygulama etki alanı tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="89f05-260">The application domain identifier.</span></span>|  
|<span data-ttu-id="89f05-261">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="89f05-261">ClrInstanceID</span></span>|<span data-ttu-id="89f05-262">Kazanma: UInt16</span><span class="sxs-lookup"><span data-stu-id="89f05-262">win:UInt16</span></span>|<span data-ttu-id="89f05-263">CLR veya CoreCLR örneği için benzersiz kimlik.</span><span class="sxs-lookup"><span data-stu-id="89f05-263">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="89f05-264">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="89f05-264">See also</span></span>

- [<span data-ttu-id="89f05-265">CLR ETW Olayları</span><span class="sxs-lookup"><span data-stu-id="89f05-265">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
