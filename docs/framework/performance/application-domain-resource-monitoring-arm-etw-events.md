---
title: Uygulama Etki Alanı Kaynak İzleme (ARM) ETW Olayları
ms.date: 03/30/2017
helpviewer_keywords:
- ETW, application domain monitoring events
- application domain monitoring events [.NET Framework]
ms.assetid: d38ff268-a2ee-434e-b504-d570880e0289
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2bb2b0dd95877fc6492f6d23a19c14688cd78f7c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59133828"
---
# <a name="application-domain-resource-monitoring-arm-etw-events"></a><span data-ttu-id="7df35-102">Uygulama Etki Alanı Kaynak İzleme (ARM) ETW Olayları</span><span class="sxs-lookup"><span data-stu-id="7df35-102">Application Domain Resource Monitoring (ARM) ETW Events</span></span>
<a name="top"></a> <span data-ttu-id="7df35-103">Bu olayları, uygulama etki alanı durumu hakkında ayrıntılı tanılama bilgileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="7df35-103">These events provide detailed diagnostic information about the state of an application domain.</span></span> <span data-ttu-id="7df35-104">Bu olayları kullanan ya da aynı bilgileri edinmek için uygulama etki alanı kaynak izleme (ARM) özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="7df35-104">You can use these events or use the application domain resource monitoring (ARM) feature to obtain the same information.</span></span>  
  
 <span data-ttu-id="7df35-105">Bu kategori aşağıdaki olaylar oluşur:</span><span class="sxs-lookup"><span data-stu-id="7df35-105">This category consists of the following events:</span></span>  
  
-   [<span data-ttu-id="7df35-106">ThreadCreated olay</span><span class="sxs-lookup"><span data-stu-id="7df35-106">ThreadCreated Event</span></span>](#threadcreated_event)  
  
-   [<span data-ttu-id="7df35-107">AppDomainMemAllocated olay</span><span class="sxs-lookup"><span data-stu-id="7df35-107">AppDomainMemAllocated Event</span></span>](#appdomainmemallocated_event)  
  
-   [<span data-ttu-id="7df35-108">AppDomainMemSurvived olay</span><span class="sxs-lookup"><span data-stu-id="7df35-108">AppDomainMemSurvived Event</span></span>](#appdomainmemsurvived_event)  
  
-   [<span data-ttu-id="7df35-109">ThreadAppDomainEnter olay</span><span class="sxs-lookup"><span data-stu-id="7df35-109">ThreadAppDomainEnter Event</span></span>](#threadappdomainenter_event)  
  
-   [<span data-ttu-id="7df35-110">ThreadTerminated olay</span><span class="sxs-lookup"><span data-stu-id="7df35-110">ThreadTerminated Event</span></span>](#threadterminated_event)  
  
<a name="threadcreated_event"></a>   
## <a name="threadcreated-event"></a><span data-ttu-id="7df35-111">ThreadCreated olay</span><span class="sxs-lookup"><span data-stu-id="7df35-111">ThreadCreated Event</span></span>  
 <span data-ttu-id="7df35-112">Bu olay Özet sağlayıcı altında oluşturulur `ThreadDC` (altında `AppDomainResourceManagementRundownKeyword` anahtar sözcüğü).</span><span class="sxs-lookup"><span data-stu-id="7df35-112">This event is also raised  under the rundown provider as `ThreadDC` (under the `AppDomainResourceManagementRundownKeyword` keyword).</span></span> <span data-ttu-id="7df35-113">Bu kategorideki Özet sağlayıcı altında oluşturulur yalnızca olay budur.</span><span class="sxs-lookup"><span data-stu-id="7df35-113">This is the only event that is raised under the rundown provider in this category.</span></span>  
  
 <span data-ttu-id="7df35-114">Aşağıdaki tabloda, düzeyi ve anahtar sözcüğü gösterir.</span><span class="sxs-lookup"><span data-stu-id="7df35-114">The following table shows the keyword and level.</span></span> <span data-ttu-id="7df35-115">(Daha fazla bilgi için [CLR ETW anahtar sözcükleri ve Düzeyler](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="7df35-115">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="7df35-116">Olayı için anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="7df35-116">Keyword for raising the event</span></span>|<span data-ttu-id="7df35-117">Düzey</span><span class="sxs-lookup"><span data-stu-id="7df35-117">Level</span></span>|  
|-----------------------------------|-----------|  
|`AppDomainResourceManagementKeyword` <span data-ttu-id="7df35-118">(0x800)</span><span class="sxs-lookup"><span data-stu-id="7df35-118">(0x800)</span></span>|<span data-ttu-id="7df35-119">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="7df35-119">Informational(4)</span></span>|  
|`ThreadingKeyword` <span data-ttu-id="7df35-120">(0x10000)</span><span class="sxs-lookup"><span data-stu-id="7df35-120">(0x10000)</span></span>|<span data-ttu-id="7df35-121">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="7df35-121">Informational(4)</span></span>|  
  
 <span data-ttu-id="7df35-122">Aşağıdaki tabloda, olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="7df35-122">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="7df35-123">Olay</span><span class="sxs-lookup"><span data-stu-id="7df35-123">Event</span></span>|<span data-ttu-id="7df35-124">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="7df35-124">Event ID</span></span>|<span data-ttu-id="7df35-125">Ne zaman gerçekleşti</span><span class="sxs-lookup"><span data-stu-id="7df35-125">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ThreadCreated`|<span data-ttu-id="7df35-126">85</span><span class="sxs-lookup"><span data-stu-id="7df35-126">85</span></span>|<span data-ttu-id="7df35-127">Uygulama etki alanı için bir iş parçacığı oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="7df35-127">A thread was created for the application domain.</span></span>|  
  
 <span data-ttu-id="7df35-128">Aşağıdaki tabloda, olay verilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="7df35-128">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="7df35-129">Alan adı</span><span class="sxs-lookup"><span data-stu-id="7df35-129">Field name</span></span>|<span data-ttu-id="7df35-130">Veri türü</span><span class="sxs-lookup"><span data-stu-id="7df35-130">Data type</span></span>|<span data-ttu-id="7df35-131">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7df35-131">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="7df35-132">ThreadID</span><span class="sxs-lookup"><span data-stu-id="7df35-132">ThreadID</span></span>|<span data-ttu-id="7df35-133">Kazanma: UInt64</span><span class="sxs-lookup"><span data-stu-id="7df35-133">win:UInt64</span></span>|<span data-ttu-id="7df35-134">Oluşturulan iş parçacığının kimliği.</span><span class="sxs-lookup"><span data-stu-id="7df35-134">ID of the thread that was created.</span></span>|  
|<span data-ttu-id="7df35-135">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="7df35-135">AppDomainID</span></span>|<span data-ttu-id="7df35-136">Kazanma: UInt64</span><span class="sxs-lookup"><span data-stu-id="7df35-136">win:UInt64</span></span>|<span data-ttu-id="7df35-137">Hangi iş parçacığı için etkinlik bildirilen uygulama etki alanı tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="7df35-137">Identifier of the application domain for which thread activity is being reported.</span></span>|  
|<span data-ttu-id="7df35-138">Bayraklar</span><span class="sxs-lookup"><span data-stu-id="7df35-138">Flags</span></span>|<span data-ttu-id="7df35-139">Kazanma: UInt32</span><span class="sxs-lookup"><span data-stu-id="7df35-139">win:UInt32</span></span>|<span data-ttu-id="7df35-140">İş parçacığı oluşturma bayrakları.</span><span class="sxs-lookup"><span data-stu-id="7df35-140">Thread creation flags.</span></span>|  
|<span data-ttu-id="7df35-141">ManagedThreadIndex</span><span class="sxs-lookup"><span data-stu-id="7df35-141">ManagedThreadIndex</span></span>|<span data-ttu-id="7df35-142">Kazanma: UInt32</span><span class="sxs-lookup"><span data-stu-id="7df35-142">win:UInt32</span></span>|<span data-ttu-id="7df35-143">Dizini oluşturulan iş parçacığının yönetilen.</span><span class="sxs-lookup"><span data-stu-id="7df35-143">Managed index of the thread that was created.</span></span>|  
|<span data-ttu-id="7df35-144">OSThreadId</span><span class="sxs-lookup"><span data-stu-id="7df35-144">OSThreadID</span></span>|<span data-ttu-id="7df35-145">Kazanma: UInt32</span><span class="sxs-lookup"><span data-stu-id="7df35-145">win:UInt32</span></span>|<span data-ttu-id="7df35-146">Oluşturulan iş parçacığının kimliği işletim sistemi.</span><span class="sxs-lookup"><span data-stu-id="7df35-146">Operating system ID of the thread that was created.</span></span>|  
|<span data-ttu-id="7df35-147">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="7df35-147">ClrInstanceID</span></span>|<span data-ttu-id="7df35-148">Kazanma: UInt16</span><span class="sxs-lookup"><span data-stu-id="7df35-148">win:UInt16</span></span>|<span data-ttu-id="7df35-149">CLR veya CoreCLR örneği için benzersiz kimlik.</span><span class="sxs-lookup"><span data-stu-id="7df35-149">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="7df35-150">Başa dön</span><span class="sxs-lookup"><span data-stu-id="7df35-150">Back to top</span></span>](#top)  
  
<a name="appdomainmemallocated_event"></a>   
## <a name="appdomainmemallocated-event"></a><span data-ttu-id="7df35-151">AppDomainMemAllocated olay</span><span class="sxs-lookup"><span data-stu-id="7df35-151">AppDomainMemAllocated Event</span></span>  
 <span data-ttu-id="7df35-152">Aşağıdaki tabloda, düzeyi ve anahtar sözcüğü gösterir.</span><span class="sxs-lookup"><span data-stu-id="7df35-152">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="7df35-153">Olayı için anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="7df35-153">Keyword for raising the event</span></span>|<span data-ttu-id="7df35-154">Düzey</span><span class="sxs-lookup"><span data-stu-id="7df35-154">Level</span></span>|  
|-----------------------------------|-----------|  
|`AppDomainResourceManagementKeyword` <span data-ttu-id="7df35-155">(0x800)</span><span class="sxs-lookup"><span data-stu-id="7df35-155">(0x800)</span></span>|<span data-ttu-id="7df35-156">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="7df35-156">Informational(4)</span></span>|  
  
 <span data-ttu-id="7df35-157">Aşağıdaki tabloda, olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="7df35-157">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="7df35-158">Olay</span><span class="sxs-lookup"><span data-stu-id="7df35-158">Event</span></span>|<span data-ttu-id="7df35-159">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="7df35-159">Event ID</span></span>|<span data-ttu-id="7df35-160">Ne zaman gerçekleşti</span><span class="sxs-lookup"><span data-stu-id="7df35-160">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`AppDomainMemAllocated`|<span data-ttu-id="7df35-161">83</span><span class="sxs-lookup"><span data-stu-id="7df35-161">83</span></span>|<span data-ttu-id="7df35-162">Her 4 MB bellek, uygulama etki alanında (yaklaşık) ayrılır.</span><span class="sxs-lookup"><span data-stu-id="7df35-162">Every 4 MB of memory (approximately) is allocated in the application domain.</span></span>|  
  
 <span data-ttu-id="7df35-163">Aşağıdaki tabloda, olay verilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="7df35-163">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="7df35-164">Alan adı</span><span class="sxs-lookup"><span data-stu-id="7df35-164">Field name</span></span>|<span data-ttu-id="7df35-165">Veri türü</span><span class="sxs-lookup"><span data-stu-id="7df35-165">Data type</span></span>|<span data-ttu-id="7df35-166">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7df35-166">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="7df35-167">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="7df35-167">AppDomainID</span></span>|<span data-ttu-id="7df35-168">Kazanma: UInt64</span><span class="sxs-lookup"><span data-stu-id="7df35-168">win:UInt64</span></span>|<span data-ttu-id="7df35-169">Kaynak kullanımı bildirilen uygulama etki alanı tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="7df35-169">Identifier of the application domain for which resource usage is being reported.</span></span>|  
|<span data-ttu-id="7df35-170">ayrılmış</span><span class="sxs-lookup"><span data-stu-id="7df35-170">Allocated</span></span>|<span data-ttu-id="7df35-171">Kazanma: UInt64</span><span class="sxs-lookup"><span data-stu-id="7df35-171">win:UInt64</span></span>|<span data-ttu-id="7df35-172">Uygulama etki alanı oluşturulduktan sonra bu uygulama etki alanında ayrılmış baytların toplam sayısı (boşaltılmış bellek miktarı değil çıkarılır).</span><span class="sxs-lookup"><span data-stu-id="7df35-172">The total number of bytes allocated in this application domain since the application domain was created (the amount of freed memory is not subtracted).</span></span>|  
|<span data-ttu-id="7df35-173">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="7df35-173">ClrInstanceID</span></span>|<span data-ttu-id="7df35-174">Kazanma: UInt16</span><span class="sxs-lookup"><span data-stu-id="7df35-174">win:UInt16</span></span>|<span data-ttu-id="7df35-175">CLR veya CoreCLR örneği için benzersiz kimlik.</span><span class="sxs-lookup"><span data-stu-id="7df35-175">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="7df35-176">Başa dön</span><span class="sxs-lookup"><span data-stu-id="7df35-176">Back to top</span></span>](#top)  
  
<a name="appdomainmemsurvived_event"></a>   
## <a name="appdomainmemsurvived-event"></a><span data-ttu-id="7df35-177">AppDomainMemSurvived olay</span><span class="sxs-lookup"><span data-stu-id="7df35-177">AppDomainMemSurvived Event</span></span>  
 <span data-ttu-id="7df35-178">Aşağıdaki tabloda, düzeyi ve anahtar sözcüğü gösterir.</span><span class="sxs-lookup"><span data-stu-id="7df35-178">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="7df35-179">Olayı için anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="7df35-179">Keyword for raising the event</span></span>|<span data-ttu-id="7df35-180">Düzey</span><span class="sxs-lookup"><span data-stu-id="7df35-180">Level</span></span>|  
|-----------------------------------|-----------|  
|`AppDomainResourceManagementKeyword` <span data-ttu-id="7df35-181">(0x800)</span><span class="sxs-lookup"><span data-stu-id="7df35-181">(0x800)</span></span>|<span data-ttu-id="7df35-182">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="7df35-182">Informational(4)</span></span>|  
  
 <span data-ttu-id="7df35-183">Aşağıdaki tabloda, olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="7df35-183">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="7df35-184">Olay</span><span class="sxs-lookup"><span data-stu-id="7df35-184">Event</span></span>|<span data-ttu-id="7df35-185">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="7df35-185">Event ID</span></span>|<span data-ttu-id="7df35-186">Ne zaman gerçekleşti</span><span class="sxs-lookup"><span data-stu-id="7df35-186">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`AppDomainMemSurvived`|<span data-ttu-id="7df35-187">84</span><span class="sxs-lookup"><span data-stu-id="7df35-187">84</span></span>|<span data-ttu-id="7df35-188">Her çöp toplama sona erdi.</span><span class="sxs-lookup"><span data-stu-id="7df35-188">Each garbage collection has ended.</span></span>|  
  
 <span data-ttu-id="7df35-189">Aşağıdaki tabloda, olay verilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="7df35-189">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="7df35-190">Alan adı</span><span class="sxs-lookup"><span data-stu-id="7df35-190">Field name</span></span>|<span data-ttu-id="7df35-191">Veri türü</span><span class="sxs-lookup"><span data-stu-id="7df35-191">Data type</span></span>|<span data-ttu-id="7df35-192">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7df35-192">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="7df35-193">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="7df35-193">AppDomainID</span></span>|<span data-ttu-id="7df35-194">Kazanma: UInt64</span><span class="sxs-lookup"><span data-stu-id="7df35-194">win:UInt64</span></span>|<span data-ttu-id="7df35-195">Kullanım raporlama için hangi kaynak etki alanı tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="7df35-195">Identifier of the domain for which resource usage is being reported.</span></span>|  
|<span data-ttu-id="7df35-196">Kurtulan</span><span class="sxs-lookup"><span data-stu-id="7df35-196">Survived</span></span>|<span data-ttu-id="7df35-197">Kazanma: UInt64</span><span class="sxs-lookup"><span data-stu-id="7df35-197">win:UInt64</span></span>|<span data-ttu-id="7df35-198">Sonra son toplamadan kurtulan ve bu uygulama etki alanına göre tutulması için bilinen bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="7df35-198">The number of bytes that survived after the last collection and that are known to be held by this application domain.</span></span> <span data-ttu-id="7df35-199">Bu sayı, sonra tam bir koleksiyon doğru ve eksiksiz olması, ancak kısa ömürlü bir toplamanın ardından tamamlanmamış olabilir.</span><span class="sxs-lookup"><span data-stu-id="7df35-199">This number is accurate and complete after a full collection, but may be incomplete after an ephemeral collection.</span></span>|  
|<span data-ttu-id="7df35-200">ProcessSurvived</span><span class="sxs-lookup"><span data-stu-id="7df35-200">ProcessSurvived</span></span>|<span data-ttu-id="7df35-201">Kazanma: UInt64</span><span class="sxs-lookup"><span data-stu-id="7df35-201">win:UInt64</span></span>|<span data-ttu-id="7df35-202">Son derlemeden kurtulan toplam bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="7df35-202">The total bytes that survived from the last collection.</span></span> <span data-ttu-id="7df35-203">Tam bir koleksiyon sonra bu numara temsil bayt sayısı, yönetilen yığınlar Canlı tutulmakta.</span><span class="sxs-lookup"><span data-stu-id="7df35-203">After a full collection, this number represents the number of bytes being held live in managed heaps.</span></span> <span data-ttu-id="7df35-204">Kısa ömürlü bir toplamanın ardından bu numara temsil bayt sayısı kısa ömürlü nesillerde Canlı tutulan.</span><span class="sxs-lookup"><span data-stu-id="7df35-204">After an ephemeral collection, this number represents the number of bytes held live in ephemeral generations.</span></span>|  
|<span data-ttu-id="7df35-205">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="7df35-205">ClrInstanceID</span></span>|<span data-ttu-id="7df35-206">Kazanma: UInt16</span><span class="sxs-lookup"><span data-stu-id="7df35-206">win:UInt16</span></span>|<span data-ttu-id="7df35-207">CLR veya CoreCLR örneği için benzersiz kimlik.</span><span class="sxs-lookup"><span data-stu-id="7df35-207">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="7df35-208">Başa dön</span><span class="sxs-lookup"><span data-stu-id="7df35-208">Back to top</span></span>](#top)  
  
<a name="threadappdomainenter_event"></a>   
## <a name="threadappdomainenter-event"></a><span data-ttu-id="7df35-209">ThreadAppDomainEnter olay</span><span class="sxs-lookup"><span data-stu-id="7df35-209">ThreadAppDomainEnter Event</span></span>  
 <span data-ttu-id="7df35-210">Aşağıdaki tabloda, düzeyi ve anahtar sözcüğü gösterir.</span><span class="sxs-lookup"><span data-stu-id="7df35-210">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="7df35-211">Olayı için anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="7df35-211">Keyword for raising the event</span></span>|<span data-ttu-id="7df35-212">Düzey</span><span class="sxs-lookup"><span data-stu-id="7df35-212">Level</span></span>|  
|-----------------------------------|-----------|  
|`AppDomainResourceManagementKeyword` <span data-ttu-id="7df35-213">(0x800)</span><span class="sxs-lookup"><span data-stu-id="7df35-213">(0x800)</span></span>|<span data-ttu-id="7df35-214">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="7df35-214">Informational(4)</span></span>|  
|`ThreadingKeyword` <span data-ttu-id="7df35-215">(0x10000)</span><span class="sxs-lookup"><span data-stu-id="7df35-215">(0x10000)</span></span>|<span data-ttu-id="7df35-216">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="7df35-216">Informational(4)</span></span>|  
  
 <span data-ttu-id="7df35-217">Aşağıdaki tabloda, olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="7df35-217">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="7df35-218">Olay</span><span class="sxs-lookup"><span data-stu-id="7df35-218">Event</span></span>|<span data-ttu-id="7df35-219">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="7df35-219">Event ID</span></span>|<span data-ttu-id="7df35-220">Ne zaman gerçekleşti</span><span class="sxs-lookup"><span data-stu-id="7df35-220">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ThreadAppDomainEnter`|<span data-ttu-id="7df35-221">87</span><span class="sxs-lookup"><span data-stu-id="7df35-221">87</span></span>|<span data-ttu-id="7df35-222">Bir iş parçacığı, bir uygulama etki alanı girer.</span><span class="sxs-lookup"><span data-stu-id="7df35-222">A thread enters an application domain.</span></span>|  
  
 <span data-ttu-id="7df35-223">Aşağıdaki tabloda, olay verilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="7df35-223">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="7df35-224">Alan adı</span><span class="sxs-lookup"><span data-stu-id="7df35-224">Field name</span></span>|<span data-ttu-id="7df35-225">Veri türü</span><span class="sxs-lookup"><span data-stu-id="7df35-225">Data type</span></span>|<span data-ttu-id="7df35-226">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7df35-226">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="7df35-227">ThreadID</span><span class="sxs-lookup"><span data-stu-id="7df35-227">ThreadID</span></span>|<span data-ttu-id="7df35-228">Kazanma: UInt64</span><span class="sxs-lookup"><span data-stu-id="7df35-228">win:UInt64</span></span>|<span data-ttu-id="7df35-229">İş parçacığı tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="7df35-229">The thread identifier.</span></span>|  
|<span data-ttu-id="7df35-230">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="7df35-230">AppDomainID</span></span>|<span data-ttu-id="7df35-231">Kazanma: UInt64</span><span class="sxs-lookup"><span data-stu-id="7df35-231">win:UInt64</span></span>|<span data-ttu-id="7df35-232">Uygulama etki alanı tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="7df35-232">The application domain identifier.</span></span>|  
|<span data-ttu-id="7df35-233">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="7df35-233">ClrInstanceID</span></span>|<span data-ttu-id="7df35-234">Kazanma: UInt16</span><span class="sxs-lookup"><span data-stu-id="7df35-234">win:UInt16</span></span>|<span data-ttu-id="7df35-235">CLR veya CoreCLR örneği için benzersiz kimlik.</span><span class="sxs-lookup"><span data-stu-id="7df35-235">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="7df35-236">Başa dön</span><span class="sxs-lookup"><span data-stu-id="7df35-236">Back to top</span></span>](#top)  
  
<a name="threadterminated_event"></a>   
## <a name="threadterminated-event"></a><span data-ttu-id="7df35-237">ThreadTerminated olay</span><span class="sxs-lookup"><span data-stu-id="7df35-237">ThreadTerminated Event</span></span>  
 <span data-ttu-id="7df35-238">Aşağıdaki tabloda, düzeyi ve anahtar sözcüğü gösterir.</span><span class="sxs-lookup"><span data-stu-id="7df35-238">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="7df35-239">Olayı için anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="7df35-239">Keyword for raising the event</span></span>|<span data-ttu-id="7df35-240">Düzey</span><span class="sxs-lookup"><span data-stu-id="7df35-240">Level</span></span>|  
|-----------------------------------|-----------|  
|`AppDomainResourceManagementKeyword` <span data-ttu-id="7df35-241">(0x800)</span><span class="sxs-lookup"><span data-stu-id="7df35-241">(0x800)</span></span>|<span data-ttu-id="7df35-242">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="7df35-242">Informational(4)</span></span>|  
|`ThreadingKeyword` <span data-ttu-id="7df35-243">(0x10000)</span><span class="sxs-lookup"><span data-stu-id="7df35-243">(0x10000)</span></span>|<span data-ttu-id="7df35-244">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="7df35-244">Informational(4)</span></span>|  
  
 <span data-ttu-id="7df35-245">Aşağıdaki tabloda, olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="7df35-245">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="7df35-246">Olay</span><span class="sxs-lookup"><span data-stu-id="7df35-246">Event</span></span>|<span data-ttu-id="7df35-247">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="7df35-247">Event ID</span></span>|<span data-ttu-id="7df35-248">Ne zaman gerçekleşti</span><span class="sxs-lookup"><span data-stu-id="7df35-248">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ThreadTerminated`|<span data-ttu-id="7df35-249">86</span><span class="sxs-lookup"><span data-stu-id="7df35-249">86</span></span>|<span data-ttu-id="7df35-250">Bir iş parçacığı sonlanır.</span><span class="sxs-lookup"><span data-stu-id="7df35-250">A thread terminates.</span></span>|  
  
 <span data-ttu-id="7df35-251">Aşağıdaki tabloda, olay verilerini gösterir:</span><span class="sxs-lookup"><span data-stu-id="7df35-251">The following table shows the event data:</span></span>  
  
|<span data-ttu-id="7df35-252">Alan adı</span><span class="sxs-lookup"><span data-stu-id="7df35-252">Field name</span></span>|<span data-ttu-id="7df35-253">Veri türü</span><span class="sxs-lookup"><span data-stu-id="7df35-253">Data type</span></span>|<span data-ttu-id="7df35-254">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7df35-254">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="7df35-255">ThreadID</span><span class="sxs-lookup"><span data-stu-id="7df35-255">ThreadID</span></span>|<span data-ttu-id="7df35-256">Kazanma: UInt64</span><span class="sxs-lookup"><span data-stu-id="7df35-256">win:UInt64</span></span>|<span data-ttu-id="7df35-257">İş parçacığı tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="7df35-257">The thread identifier.</span></span>|  
|<span data-ttu-id="7df35-258">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="7df35-258">AppDomainID</span></span>|<span data-ttu-id="7df35-259">Kazanma: UInt64</span><span class="sxs-lookup"><span data-stu-id="7df35-259">win:UInt64</span></span>|<span data-ttu-id="7df35-260">Uygulama etki alanı tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="7df35-260">The application domain identifier.</span></span>|  
|<span data-ttu-id="7df35-261">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="7df35-261">ClrInstanceID</span></span>|<span data-ttu-id="7df35-262">Kazanma: UInt16</span><span class="sxs-lookup"><span data-stu-id="7df35-262">win:UInt16</span></span>|<span data-ttu-id="7df35-263">CLR veya CoreCLR örneği için benzersiz kimlik.</span><span class="sxs-lookup"><span data-stu-id="7df35-263">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7df35-264">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7df35-264">See also</span></span>

- [<span data-ttu-id="7df35-265">CLR ETW Olayları</span><span class="sxs-lookup"><span data-stu-id="7df35-265">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
