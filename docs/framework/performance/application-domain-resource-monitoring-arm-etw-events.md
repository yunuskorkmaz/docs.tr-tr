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
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59133828"
---
# <a name="application-domain-resource-monitoring-arm-etw-events"></a><span data-ttu-id="c39fc-102">Uygulama Etki Alanı Kaynak İzleme (ARM) ETW Olayları</span><span class="sxs-lookup"><span data-stu-id="c39fc-102">Application Domain Resource Monitoring (ARM) ETW Events</span></span>
<a name="top"></a> <span data-ttu-id="c39fc-103">Bu olayları, uygulama etki alanı durumu hakkında ayrıntılı tanılama bilgileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="c39fc-103">These events provide detailed diagnostic information about the state of an application domain.</span></span> <span data-ttu-id="c39fc-104">Bu olayları kullanan ya da aynı bilgileri edinmek için uygulama etki alanı kaynak izleme (ARM) özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="c39fc-104">You can use these events or use the application domain resource monitoring (ARM) feature to obtain the same information.</span></span>  
  
 <span data-ttu-id="c39fc-105">Bu kategori aşağıdaki olaylar oluşur:</span><span class="sxs-lookup"><span data-stu-id="c39fc-105">This category consists of the following events:</span></span>  
  
-   [<span data-ttu-id="c39fc-106">ThreadCreated olay</span><span class="sxs-lookup"><span data-stu-id="c39fc-106">ThreadCreated Event</span></span>](#threadcreated_event)  
  
-   [<span data-ttu-id="c39fc-107">AppDomainMemAllocated olay</span><span class="sxs-lookup"><span data-stu-id="c39fc-107">AppDomainMemAllocated Event</span></span>](#appdomainmemallocated_event)  
  
-   [<span data-ttu-id="c39fc-108">AppDomainMemSurvived olay</span><span class="sxs-lookup"><span data-stu-id="c39fc-108">AppDomainMemSurvived Event</span></span>](#appdomainmemsurvived_event)  
  
-   [<span data-ttu-id="c39fc-109">ThreadAppDomainEnter olay</span><span class="sxs-lookup"><span data-stu-id="c39fc-109">ThreadAppDomainEnter Event</span></span>](#threadappdomainenter_event)  
  
-   [<span data-ttu-id="c39fc-110">ThreadTerminated olay</span><span class="sxs-lookup"><span data-stu-id="c39fc-110">ThreadTerminated Event</span></span>](#threadterminated_event)  
  
<a name="threadcreated_event"></a>   
## <a name="threadcreated-event"></a><span data-ttu-id="c39fc-111">ThreadCreated olay</span><span class="sxs-lookup"><span data-stu-id="c39fc-111">ThreadCreated Event</span></span>  
 <span data-ttu-id="c39fc-112">Bu olay Özet sağlayıcı altında oluşturulur `ThreadDC` (altında `AppDomainResourceManagementRundownKeyword` anahtar sözcüğü).</span><span class="sxs-lookup"><span data-stu-id="c39fc-112">This event is also raised  under the rundown provider as `ThreadDC` (under the `AppDomainResourceManagementRundownKeyword` keyword).</span></span> <span data-ttu-id="c39fc-113">Bu kategorideki Özet sağlayıcı altında oluşturulur yalnızca olay budur.</span><span class="sxs-lookup"><span data-stu-id="c39fc-113">This is the only event that is raised under the rundown provider in this category.</span></span>  
  
 <span data-ttu-id="c39fc-114">Aşağıdaki tabloda, düzeyi ve anahtar sözcüğü gösterir.</span><span class="sxs-lookup"><span data-stu-id="c39fc-114">The following table shows the keyword and level.</span></span> <span data-ttu-id="c39fc-115">(Daha fazla bilgi için [CLR ETW anahtar sözcükleri ve Düzeyler](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="c39fc-115">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="c39fc-116">Olayı için anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="c39fc-116">Keyword for raising the event</span></span>|<span data-ttu-id="c39fc-117">Düzey</span><span class="sxs-lookup"><span data-stu-id="c39fc-117">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="c39fc-118">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="c39fc-118">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="c39fc-119">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="c39fc-119">Informational(4)</span></span>|  
|<span data-ttu-id="c39fc-120">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="c39fc-120">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="c39fc-121">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="c39fc-121">Informational(4)</span></span>|  
  
 <span data-ttu-id="c39fc-122">Aşağıdaki tabloda, olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="c39fc-122">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="c39fc-123">Olay</span><span class="sxs-lookup"><span data-stu-id="c39fc-123">Event</span></span>|<span data-ttu-id="c39fc-124">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="c39fc-124">Event ID</span></span>|<span data-ttu-id="c39fc-125">Ne zaman gerçekleşti</span><span class="sxs-lookup"><span data-stu-id="c39fc-125">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ThreadCreated`|<span data-ttu-id="c39fc-126">85</span><span class="sxs-lookup"><span data-stu-id="c39fc-126">85</span></span>|<span data-ttu-id="c39fc-127">Uygulama etki alanı için bir iş parçacığı oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="c39fc-127">A thread was created for the application domain.</span></span>|  
  
 <span data-ttu-id="c39fc-128">Aşağıdaki tabloda, olay verilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="c39fc-128">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="c39fc-129">Alan adı</span><span class="sxs-lookup"><span data-stu-id="c39fc-129">Field name</span></span>|<span data-ttu-id="c39fc-130">Veri türü</span><span class="sxs-lookup"><span data-stu-id="c39fc-130">Data type</span></span>|<span data-ttu-id="c39fc-131">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c39fc-131">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="c39fc-132">ThreadID</span><span class="sxs-lookup"><span data-stu-id="c39fc-132">ThreadID</span></span>|<span data-ttu-id="c39fc-133">Kazanma: UInt64</span><span class="sxs-lookup"><span data-stu-id="c39fc-133">win:UInt64</span></span>|<span data-ttu-id="c39fc-134">Oluşturulan iş parçacığının kimliği.</span><span class="sxs-lookup"><span data-stu-id="c39fc-134">ID of the thread that was created.</span></span>|  
|<span data-ttu-id="c39fc-135">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="c39fc-135">AppDomainID</span></span>|<span data-ttu-id="c39fc-136">Kazanma: UInt64</span><span class="sxs-lookup"><span data-stu-id="c39fc-136">win:UInt64</span></span>|<span data-ttu-id="c39fc-137">Hangi iş parçacığı için etkinlik bildirilen uygulama etki alanı tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="c39fc-137">Identifier of the application domain for which thread activity is being reported.</span></span>|  
|<span data-ttu-id="c39fc-138">Bayraklar</span><span class="sxs-lookup"><span data-stu-id="c39fc-138">Flags</span></span>|<span data-ttu-id="c39fc-139">Kazanma: UInt32</span><span class="sxs-lookup"><span data-stu-id="c39fc-139">win:UInt32</span></span>|<span data-ttu-id="c39fc-140">İş parçacığı oluşturma bayrakları.</span><span class="sxs-lookup"><span data-stu-id="c39fc-140">Thread creation flags.</span></span>|  
|<span data-ttu-id="c39fc-141">ManagedThreadIndex</span><span class="sxs-lookup"><span data-stu-id="c39fc-141">ManagedThreadIndex</span></span>|<span data-ttu-id="c39fc-142">Kazanma: UInt32</span><span class="sxs-lookup"><span data-stu-id="c39fc-142">win:UInt32</span></span>|<span data-ttu-id="c39fc-143">Dizini oluşturulan iş parçacığının yönetilen.</span><span class="sxs-lookup"><span data-stu-id="c39fc-143">Managed index of the thread that was created.</span></span>|  
|<span data-ttu-id="c39fc-144">OSThreadId</span><span class="sxs-lookup"><span data-stu-id="c39fc-144">OSThreadID</span></span>|<span data-ttu-id="c39fc-145">Kazanma: UInt32</span><span class="sxs-lookup"><span data-stu-id="c39fc-145">win:UInt32</span></span>|<span data-ttu-id="c39fc-146">Oluşturulan iş parçacığının kimliği işletim sistemi.</span><span class="sxs-lookup"><span data-stu-id="c39fc-146">Operating system ID of the thread that was created.</span></span>|  
|<span data-ttu-id="c39fc-147">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="c39fc-147">ClrInstanceID</span></span>|<span data-ttu-id="c39fc-148">Kazanma: UInt16</span><span class="sxs-lookup"><span data-stu-id="c39fc-148">win:UInt16</span></span>|<span data-ttu-id="c39fc-149">CLR veya CoreCLR örneği için benzersiz kimlik.</span><span class="sxs-lookup"><span data-stu-id="c39fc-149">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="c39fc-150">Başa dön</span><span class="sxs-lookup"><span data-stu-id="c39fc-150">Back to top</span></span>](#top)  
  
<a name="appdomainmemallocated_event"></a>   
## <a name="appdomainmemallocated-event"></a><span data-ttu-id="c39fc-151">AppDomainMemAllocated olay</span><span class="sxs-lookup"><span data-stu-id="c39fc-151">AppDomainMemAllocated Event</span></span>  
 <span data-ttu-id="c39fc-152">Aşağıdaki tabloda, düzeyi ve anahtar sözcüğü gösterir.</span><span class="sxs-lookup"><span data-stu-id="c39fc-152">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="c39fc-153">Olayı için anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="c39fc-153">Keyword for raising the event</span></span>|<span data-ttu-id="c39fc-154">Düzey</span><span class="sxs-lookup"><span data-stu-id="c39fc-154">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="c39fc-155">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="c39fc-155">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="c39fc-156">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="c39fc-156">Informational(4)</span></span>|  
  
 <span data-ttu-id="c39fc-157">Aşağıdaki tabloda, olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="c39fc-157">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="c39fc-158">Olay</span><span class="sxs-lookup"><span data-stu-id="c39fc-158">Event</span></span>|<span data-ttu-id="c39fc-159">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="c39fc-159">Event ID</span></span>|<span data-ttu-id="c39fc-160">Ne zaman gerçekleşti</span><span class="sxs-lookup"><span data-stu-id="c39fc-160">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`AppDomainMemAllocated`|<span data-ttu-id="c39fc-161">83</span><span class="sxs-lookup"><span data-stu-id="c39fc-161">83</span></span>|<span data-ttu-id="c39fc-162">Her 4 MB bellek, uygulama etki alanında (yaklaşık) ayrılır.</span><span class="sxs-lookup"><span data-stu-id="c39fc-162">Every 4 MB of memory (approximately) is allocated in the application domain.</span></span>|  
  
 <span data-ttu-id="c39fc-163">Aşağıdaki tabloda, olay verilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="c39fc-163">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="c39fc-164">Alan adı</span><span class="sxs-lookup"><span data-stu-id="c39fc-164">Field name</span></span>|<span data-ttu-id="c39fc-165">Veri türü</span><span class="sxs-lookup"><span data-stu-id="c39fc-165">Data type</span></span>|<span data-ttu-id="c39fc-166">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c39fc-166">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="c39fc-167">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="c39fc-167">AppDomainID</span></span>|<span data-ttu-id="c39fc-168">Kazanma: UInt64</span><span class="sxs-lookup"><span data-stu-id="c39fc-168">win:UInt64</span></span>|<span data-ttu-id="c39fc-169">Kaynak kullanımı bildirilen uygulama etki alanı tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="c39fc-169">Identifier of the application domain for which resource usage is being reported.</span></span>|  
|<span data-ttu-id="c39fc-170">ayrılmış</span><span class="sxs-lookup"><span data-stu-id="c39fc-170">Allocated</span></span>|<span data-ttu-id="c39fc-171">Kazanma: UInt64</span><span class="sxs-lookup"><span data-stu-id="c39fc-171">win:UInt64</span></span>|<span data-ttu-id="c39fc-172">Uygulama etki alanı oluşturulduktan sonra bu uygulama etki alanında ayrılmış baytların toplam sayısı (boşaltılmış bellek miktarı değil çıkarılır).</span><span class="sxs-lookup"><span data-stu-id="c39fc-172">The total number of bytes allocated in this application domain since the application domain was created (the amount of freed memory is not subtracted).</span></span>|  
|<span data-ttu-id="c39fc-173">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="c39fc-173">ClrInstanceID</span></span>|<span data-ttu-id="c39fc-174">Kazanma: UInt16</span><span class="sxs-lookup"><span data-stu-id="c39fc-174">win:UInt16</span></span>|<span data-ttu-id="c39fc-175">CLR veya CoreCLR örneği için benzersiz kimlik.</span><span class="sxs-lookup"><span data-stu-id="c39fc-175">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="c39fc-176">Başa dön</span><span class="sxs-lookup"><span data-stu-id="c39fc-176">Back to top</span></span>](#top)  
  
<a name="appdomainmemsurvived_event"></a>   
## <a name="appdomainmemsurvived-event"></a><span data-ttu-id="c39fc-177">AppDomainMemSurvived olay</span><span class="sxs-lookup"><span data-stu-id="c39fc-177">AppDomainMemSurvived Event</span></span>  
 <span data-ttu-id="c39fc-178">Aşağıdaki tabloda, düzeyi ve anahtar sözcüğü gösterir.</span><span class="sxs-lookup"><span data-stu-id="c39fc-178">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="c39fc-179">Olayı için anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="c39fc-179">Keyword for raising the event</span></span>|<span data-ttu-id="c39fc-180">Düzey</span><span class="sxs-lookup"><span data-stu-id="c39fc-180">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="c39fc-181">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="c39fc-181">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="c39fc-182">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="c39fc-182">Informational(4)</span></span>|  
  
 <span data-ttu-id="c39fc-183">Aşağıdaki tabloda, olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="c39fc-183">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="c39fc-184">Olay</span><span class="sxs-lookup"><span data-stu-id="c39fc-184">Event</span></span>|<span data-ttu-id="c39fc-185">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="c39fc-185">Event ID</span></span>|<span data-ttu-id="c39fc-186">Ne zaman gerçekleşti</span><span class="sxs-lookup"><span data-stu-id="c39fc-186">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`AppDomainMemSurvived`|<span data-ttu-id="c39fc-187">84</span><span class="sxs-lookup"><span data-stu-id="c39fc-187">84</span></span>|<span data-ttu-id="c39fc-188">Her çöp toplama sona erdi.</span><span class="sxs-lookup"><span data-stu-id="c39fc-188">Each garbage collection has ended.</span></span>|  
  
 <span data-ttu-id="c39fc-189">Aşağıdaki tabloda, olay verilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="c39fc-189">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="c39fc-190">Alan adı</span><span class="sxs-lookup"><span data-stu-id="c39fc-190">Field name</span></span>|<span data-ttu-id="c39fc-191">Veri türü</span><span class="sxs-lookup"><span data-stu-id="c39fc-191">Data type</span></span>|<span data-ttu-id="c39fc-192">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c39fc-192">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="c39fc-193">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="c39fc-193">AppDomainID</span></span>|<span data-ttu-id="c39fc-194">Kazanma: UInt64</span><span class="sxs-lookup"><span data-stu-id="c39fc-194">win:UInt64</span></span>|<span data-ttu-id="c39fc-195">Kullanım raporlama için hangi kaynak etki alanı tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="c39fc-195">Identifier of the domain for which resource usage is being reported.</span></span>|  
|<span data-ttu-id="c39fc-196">Kurtulan</span><span class="sxs-lookup"><span data-stu-id="c39fc-196">Survived</span></span>|<span data-ttu-id="c39fc-197">Kazanma: UInt64</span><span class="sxs-lookup"><span data-stu-id="c39fc-197">win:UInt64</span></span>|<span data-ttu-id="c39fc-198">Sonra son toplamadan kurtulan ve bu uygulama etki alanına göre tutulması için bilinen bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="c39fc-198">The number of bytes that survived after the last collection and that are known to be held by this application domain.</span></span> <span data-ttu-id="c39fc-199">Bu sayı, sonra tam bir koleksiyon doğru ve eksiksiz olması, ancak kısa ömürlü bir toplamanın ardından tamamlanmamış olabilir.</span><span class="sxs-lookup"><span data-stu-id="c39fc-199">This number is accurate and complete after a full collection, but may be incomplete after an ephemeral collection.</span></span>|  
|<span data-ttu-id="c39fc-200">ProcessSurvived</span><span class="sxs-lookup"><span data-stu-id="c39fc-200">ProcessSurvived</span></span>|<span data-ttu-id="c39fc-201">Kazanma: UInt64</span><span class="sxs-lookup"><span data-stu-id="c39fc-201">win:UInt64</span></span>|<span data-ttu-id="c39fc-202">Son derlemeden kurtulan toplam bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="c39fc-202">The total bytes that survived from the last collection.</span></span> <span data-ttu-id="c39fc-203">Tam bir koleksiyon sonra bu numara temsil bayt sayısı, yönetilen yığınlar Canlı tutulmakta.</span><span class="sxs-lookup"><span data-stu-id="c39fc-203">After a full collection, this number represents the number of bytes being held live in managed heaps.</span></span> <span data-ttu-id="c39fc-204">Kısa ömürlü bir toplamanın ardından bu numara temsil bayt sayısı kısa ömürlü nesillerde Canlı tutulan.</span><span class="sxs-lookup"><span data-stu-id="c39fc-204">After an ephemeral collection, this number represents the number of bytes held live in ephemeral generations.</span></span>|  
|<span data-ttu-id="c39fc-205">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="c39fc-205">ClrInstanceID</span></span>|<span data-ttu-id="c39fc-206">Kazanma: UInt16</span><span class="sxs-lookup"><span data-stu-id="c39fc-206">win:UInt16</span></span>|<span data-ttu-id="c39fc-207">CLR veya CoreCLR örneği için benzersiz kimlik.</span><span class="sxs-lookup"><span data-stu-id="c39fc-207">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="c39fc-208">Başa dön</span><span class="sxs-lookup"><span data-stu-id="c39fc-208">Back to top</span></span>](#top)  
  
<a name="threadappdomainenter_event"></a>   
## <a name="threadappdomainenter-event"></a><span data-ttu-id="c39fc-209">ThreadAppDomainEnter olay</span><span class="sxs-lookup"><span data-stu-id="c39fc-209">ThreadAppDomainEnter Event</span></span>  
 <span data-ttu-id="c39fc-210">Aşağıdaki tabloda, düzeyi ve anahtar sözcüğü gösterir.</span><span class="sxs-lookup"><span data-stu-id="c39fc-210">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="c39fc-211">Olayı için anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="c39fc-211">Keyword for raising the event</span></span>|<span data-ttu-id="c39fc-212">Düzey</span><span class="sxs-lookup"><span data-stu-id="c39fc-212">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="c39fc-213">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="c39fc-213">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="c39fc-214">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="c39fc-214">Informational(4)</span></span>|  
|<span data-ttu-id="c39fc-215">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="c39fc-215">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="c39fc-216">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="c39fc-216">Informational(4)</span></span>|  
  
 <span data-ttu-id="c39fc-217">Aşağıdaki tabloda, olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="c39fc-217">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="c39fc-218">Olay</span><span class="sxs-lookup"><span data-stu-id="c39fc-218">Event</span></span>|<span data-ttu-id="c39fc-219">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="c39fc-219">Event ID</span></span>|<span data-ttu-id="c39fc-220">Ne zaman gerçekleşti</span><span class="sxs-lookup"><span data-stu-id="c39fc-220">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ThreadAppDomainEnter`|<span data-ttu-id="c39fc-221">87</span><span class="sxs-lookup"><span data-stu-id="c39fc-221">87</span></span>|<span data-ttu-id="c39fc-222">Bir iş parçacığı, bir uygulama etki alanı girer.</span><span class="sxs-lookup"><span data-stu-id="c39fc-222">A thread enters an application domain.</span></span>|  
  
 <span data-ttu-id="c39fc-223">Aşağıdaki tabloda, olay verilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="c39fc-223">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="c39fc-224">Alan adı</span><span class="sxs-lookup"><span data-stu-id="c39fc-224">Field name</span></span>|<span data-ttu-id="c39fc-225">Veri türü</span><span class="sxs-lookup"><span data-stu-id="c39fc-225">Data type</span></span>|<span data-ttu-id="c39fc-226">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c39fc-226">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="c39fc-227">ThreadID</span><span class="sxs-lookup"><span data-stu-id="c39fc-227">ThreadID</span></span>|<span data-ttu-id="c39fc-228">Kazanma: UInt64</span><span class="sxs-lookup"><span data-stu-id="c39fc-228">win:UInt64</span></span>|<span data-ttu-id="c39fc-229">İş parçacığı tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="c39fc-229">The thread identifier.</span></span>|  
|<span data-ttu-id="c39fc-230">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="c39fc-230">AppDomainID</span></span>|<span data-ttu-id="c39fc-231">Kazanma: UInt64</span><span class="sxs-lookup"><span data-stu-id="c39fc-231">win:UInt64</span></span>|<span data-ttu-id="c39fc-232">Uygulama etki alanı tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="c39fc-232">The application domain identifier.</span></span>|  
|<span data-ttu-id="c39fc-233">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="c39fc-233">ClrInstanceID</span></span>|<span data-ttu-id="c39fc-234">Kazanma: UInt16</span><span class="sxs-lookup"><span data-stu-id="c39fc-234">win:UInt16</span></span>|<span data-ttu-id="c39fc-235">CLR veya CoreCLR örneği için benzersiz kimlik.</span><span class="sxs-lookup"><span data-stu-id="c39fc-235">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="c39fc-236">Başa dön</span><span class="sxs-lookup"><span data-stu-id="c39fc-236">Back to top</span></span>](#top)  
  
<a name="threadterminated_event"></a>   
## <a name="threadterminated-event"></a><span data-ttu-id="c39fc-237">ThreadTerminated olay</span><span class="sxs-lookup"><span data-stu-id="c39fc-237">ThreadTerminated Event</span></span>  
 <span data-ttu-id="c39fc-238">Aşağıdaki tabloda, düzeyi ve anahtar sözcüğü gösterir.</span><span class="sxs-lookup"><span data-stu-id="c39fc-238">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="c39fc-239">Olayı için anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="c39fc-239">Keyword for raising the event</span></span>|<span data-ttu-id="c39fc-240">Düzey</span><span class="sxs-lookup"><span data-stu-id="c39fc-240">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="c39fc-241">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="c39fc-241">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="c39fc-242">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="c39fc-242">Informational(4)</span></span>|  
|<span data-ttu-id="c39fc-243">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="c39fc-243">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="c39fc-244">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="c39fc-244">Informational(4)</span></span>|  
  
 <span data-ttu-id="c39fc-245">Aşağıdaki tabloda, olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="c39fc-245">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="c39fc-246">Olay</span><span class="sxs-lookup"><span data-stu-id="c39fc-246">Event</span></span>|<span data-ttu-id="c39fc-247">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="c39fc-247">Event ID</span></span>|<span data-ttu-id="c39fc-248">Ne zaman gerçekleşti</span><span class="sxs-lookup"><span data-stu-id="c39fc-248">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ThreadTerminated`|<span data-ttu-id="c39fc-249">86</span><span class="sxs-lookup"><span data-stu-id="c39fc-249">86</span></span>|<span data-ttu-id="c39fc-250">Bir iş parçacığı sonlanır.</span><span class="sxs-lookup"><span data-stu-id="c39fc-250">A thread terminates.</span></span>|  
  
 <span data-ttu-id="c39fc-251">Aşağıdaki tabloda, olay verilerini gösterir:</span><span class="sxs-lookup"><span data-stu-id="c39fc-251">The following table shows the event data:</span></span>  
  
|<span data-ttu-id="c39fc-252">Alan adı</span><span class="sxs-lookup"><span data-stu-id="c39fc-252">Field name</span></span>|<span data-ttu-id="c39fc-253">Veri türü</span><span class="sxs-lookup"><span data-stu-id="c39fc-253">Data type</span></span>|<span data-ttu-id="c39fc-254">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c39fc-254">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="c39fc-255">ThreadID</span><span class="sxs-lookup"><span data-stu-id="c39fc-255">ThreadID</span></span>|<span data-ttu-id="c39fc-256">Kazanma: UInt64</span><span class="sxs-lookup"><span data-stu-id="c39fc-256">win:UInt64</span></span>|<span data-ttu-id="c39fc-257">İş parçacığı tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="c39fc-257">The thread identifier.</span></span>|  
|<span data-ttu-id="c39fc-258">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="c39fc-258">AppDomainID</span></span>|<span data-ttu-id="c39fc-259">Kazanma: UInt64</span><span class="sxs-lookup"><span data-stu-id="c39fc-259">win:UInt64</span></span>|<span data-ttu-id="c39fc-260">Uygulama etki alanı tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="c39fc-260">The application domain identifier.</span></span>|  
|<span data-ttu-id="c39fc-261">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="c39fc-261">ClrInstanceID</span></span>|<span data-ttu-id="c39fc-262">Kazanma: UInt16</span><span class="sxs-lookup"><span data-stu-id="c39fc-262">win:UInt16</span></span>|<span data-ttu-id="c39fc-263">CLR veya CoreCLR örneği için benzersiz kimlik.</span><span class="sxs-lookup"><span data-stu-id="c39fc-263">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c39fc-264">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c39fc-264">See also</span></span>

- [<span data-ttu-id="c39fc-265">CLR ETW Olayları</span><span class="sxs-lookup"><span data-stu-id="c39fc-265">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
