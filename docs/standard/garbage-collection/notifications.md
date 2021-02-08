---
description: 'Daha fazla bilgi edinin: çöp toplama bildirimleri'
title: Çöp Toplama Bildirimleri
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- garbage collection, notifications
ms.assetid: e12d8e74-31e3-4035-a87d-f3e66f0a9b89
ms.openlocfilehash: bbdb3cecde6a7e91b79992be9424ecffebfdaa15
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99782461"
---
# <a name="garbage-collection-notifications"></a><span data-ttu-id="8a4b9-103">Çöp Toplama Bildirimleri</span><span class="sxs-lookup"><span data-stu-id="8a4b9-103">Garbage Collection Notifications</span></span>

<span data-ttu-id="8a4b9-104">Ortak dil çalışma zamanı ile tam çöp toplamanın (yani 2. nesil bir koleksiyon) performansı olumsuz etkileyebileceği durumlar vardır.</span><span class="sxs-lookup"><span data-stu-id="8a4b9-104">There are situations in which a full garbage collection (that is, a generation 2 collection) by the common language runtime may adversely affect performance.</span></span> <span data-ttu-id="8a4b9-105">Bu, özellikle büyük hacimli istekleri işleyen sunucularla ilgili bir sorun olabilir; Bu durumda, uzun bir atık toplama bir istek zaman aşımına neden olabilir. Kritik bir süre boyunca tam bir koleksiyonun oluşmasını önlemek için, tam bir çöp toplamanın yaklaştığı ve iş yükünü başka bir sunucu örneğine yeniden yönlendirmek için işlem gerçekleştirilecek şekilde bir uyarı alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8a4b9-105">This can be an issue particularly with servers that process large volumes of requests; in this case, a long garbage collection can cause a request time-out. To prevent a full collection from occurring during a critical period, you can be notified that a full garbage collection is approaching and then take action to redirect the workload to another server instance.</span></span> <span data-ttu-id="8a4b9-106">Ayrıca, geçerli sunucu örneğinin istekleri işlemesini gerektirmeyen bir koleksiyonu kendiniz de yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8a4b9-106">You can also induce a collection yourself, provided that the current server instance does not need to process requests.</span></span>  
  
 <span data-ttu-id="8a4b9-107"><xref:System.GC.RegisterForFullGCNotification%2A>Yöntemi, çalışma zamanı tam çöp toplama işlemini yaklaştığında bir bildirimin bir bildirimine kaydolur.</span><span class="sxs-lookup"><span data-stu-id="8a4b9-107">The <xref:System.GC.RegisterForFullGCNotification%2A> method registers for a notification to be raised when the runtime senses that a full garbage collection is approaching.</span></span> <span data-ttu-id="8a4b9-108">Bu bildirimin iki bölümü vardır: tam çöp toplama yaklaşıyorsa ve tam çöp toplama tamamlandığında.</span><span class="sxs-lookup"><span data-stu-id="8a4b9-108">There are two parts to this notification: when the full garbage collection is approaching and when the full garbage collection has completed.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="8a4b9-109">Yalnızca atık koleksiyonları engelleme bildirimleri yükseltir.</span><span class="sxs-lookup"><span data-stu-id="8a4b9-109">Only blocking garbage collections raise notifications.</span></span> <span data-ttu-id="8a4b9-110">[\<gcConcurrent>](../../framework/configure-apps/file-schema/runtime/gcconcurrent-element.md)Yapılandırma öğesi etkinleştirildiğinde, arka plan atık koleksiyonları bildirim oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="8a4b9-110">When the [\<gcConcurrent>](../../framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) configuration element is enabled, background garbage collections will not raise notifications.</span></span>  
  
 <span data-ttu-id="8a4b9-111">Bir bildirimin ne zaman kabarık olduğunu anlamak için <xref:System.GC.WaitForFullGCApproach%2A> ve <xref:System.GC.WaitForFullGCComplete%2A> yöntemlerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="8a4b9-111">To determine when a notification has been raised, use the <xref:System.GC.WaitForFullGCApproach%2A> and <xref:System.GC.WaitForFullGCComplete%2A> methods.</span></span> <span data-ttu-id="8a4b9-112">Genellikle, `while` <xref:System.GCNotificationStatus> bildirim durumunu gösteren bir sabit listesi elde etmek için bu yöntemleri bir döngüde kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="8a4b9-112">Typically, you use these methods in a `while` loop to continually obtain a <xref:System.GCNotificationStatus> enumeration that shows the status of the notification.</span></span> <span data-ttu-id="8a4b9-113">Bu değer ise, şunları yapabilirsiniz <xref:System.GCNotificationStatus.Succeeded> :</span><span class="sxs-lookup"><span data-stu-id="8a4b9-113">If that value is <xref:System.GCNotificationStatus.Succeeded>, you can do the following:</span></span>  
  
- <span data-ttu-id="8a4b9-114">Yöntemiyle elde edilen bir bildirime yanıt olarak <xref:System.GC.WaitForFullGCApproach%2A> , iş yükünü yeniden yönlendirebilir ve muhtemelen bir koleksiyonu kendiniz bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8a4b9-114">In response to a notification obtained with the <xref:System.GC.WaitForFullGCApproach%2A> method, you can redirect the workload and possibly induce a collection yourself.</span></span>  
  
- <span data-ttu-id="8a4b9-115">Yöntemiyle elde edilen bir bildirime yanıt olarak <xref:System.GC.WaitForFullGCComplete%2A> , geçerli sunucu örneğini istekleri yeniden işlemek için kullanılabilir hale getirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8a4b9-115">In response to a notification obtained with the <xref:System.GC.WaitForFullGCComplete%2A> method, you can make the current server instance available to process requests again.</span></span> <span data-ttu-id="8a4b9-116">Ayrıca, bilgi toplayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8a4b9-116">You can also gather information.</span></span> <span data-ttu-id="8a4b9-117">Örneğin, <xref:System.GC.CollectionCount%2A> koleksiyon sayısını kaydetmek için yöntemini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8a4b9-117">For example, you can use the <xref:System.GC.CollectionCount%2A> method to record the number of collections.</span></span>  
  
 <span data-ttu-id="8a4b9-118"><xref:System.GC.WaitForFullGCApproach%2A>Ve <xref:System.GC.WaitForFullGCComplete%2A> yöntemleri birlikte çalışmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="8a4b9-118">The <xref:System.GC.WaitForFullGCApproach%2A> and the <xref:System.GC.WaitForFullGCComplete%2A> methods are designed to work together.</span></span> <span data-ttu-id="8a4b9-119">Diğeri olmadan kullanmak, belirsiz sonuçlar doğurabilir.</span><span class="sxs-lookup"><span data-stu-id="8a4b9-119">Using one without the other can produce indeterminate results.</span></span>  
  
## <a name="full-garbage-collection"></a><span data-ttu-id="8a4b9-120">Tam çöp toplama</span><span class="sxs-lookup"><span data-stu-id="8a4b9-120">Full Garbage Collection</span></span>  

 <span data-ttu-id="8a4b9-121">Aşağıdaki senaryolardan herhangi biri doğru olduğunda, çalışma zamanı tam çöp toplamaya neden olur:</span><span class="sxs-lookup"><span data-stu-id="8a4b9-121">The runtime causes a full garbage collection when any of the following scenarios are true:</span></span>  
  
- <span data-ttu-id="8a4b9-122">Bir sonraki nesil 2 toplamaya neden olacak şekilde 2. nesil bir bellek yükseltildi.</span><span class="sxs-lookup"><span data-stu-id="8a4b9-122">Enough memory has been promoted into generation 2 to cause the next generation 2 collection.</span></span>  
  
- <span data-ttu-id="8a4b9-123">Bir sonraki nesil 2 toplamaya neden olmak için büyük nesne yığınına yeterli bellek yükseltildi.</span><span class="sxs-lookup"><span data-stu-id="8a4b9-123">Enough memory has been promoted into the large object heap to cause the next generation 2 collection.</span></span>  
  
- <span data-ttu-id="8a4b9-124">1. nesil bir koleksiyon, diğer faktörler nedeniyle 2. nesil bir toplamaya ilerletildi.</span><span class="sxs-lookup"><span data-stu-id="8a4b9-124">A collection of generation 1 is escalated to a collection of generation 2 due to other factors.</span></span>  
  
 <span data-ttu-id="8a4b9-125">Yönteminde belirttiğiniz eşikler <xref:System.GC.RegisterForFullGCNotification%2A> ilk iki senaryo için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="8a4b9-125">The thresholds you specify in the <xref:System.GC.RegisterForFullGCNotification%2A> method apply to the first two scenarios.</span></span> <span data-ttu-id="8a4b9-126">Ancak, ilk senaryoda bildirimi her zaman, iki nedenden dolayı belirttiğiniz eşik değerleriyle orantılı şekilde almazsınız:</span><span class="sxs-lookup"><span data-stu-id="8a4b9-126">However, in the first scenario you will not always receive the notification at the time proportional to the threshold values you specify for two reasons:</span></span>  
  
- <span data-ttu-id="8a4b9-127">Çalışma zamanı her küçük nesne ayırmayı denetlemez (performans nedenleriyle).</span><span class="sxs-lookup"><span data-stu-id="8a4b9-127">The runtime does not check each small object allocation (for performance reasons).</span></span>  
  
- <span data-ttu-id="8a4b9-128">Yalnızca 1. nesil koleksiyonlar belleği 2. nesil olarak yükseltir.</span><span class="sxs-lookup"><span data-stu-id="8a4b9-128">Only generation 1 collections promote memory into generation 2.</span></span>  
  
 <span data-ttu-id="8a4b9-129">Ayrıca üçüncü senaryo, bildirimi alacağınız zaman açıklanmayacak şekilde katkıda bulunur.</span><span class="sxs-lookup"><span data-stu-id="8a4b9-129">The third scenario also contributes to the uncertainty of when you will receive the notification.</span></span> <span data-ttu-id="8a4b9-130">Bu bir garanti olmamasına karşın, bu süre boyunca istekleri yeniden yönlendirerek veya daha iyi bir hale gelebileceği zaman koleksiyonu kendiniz gerçekleştirerek, inopportune tam çöp toplamanın etkilerini azaltmak için faydalı bir yol olduğunu kanıtlamaz.</span><span class="sxs-lookup"><span data-stu-id="8a4b9-130">Although this is not a guarantee, it does prove to be a useful way to mitigate the effects of an inopportune full garbage collection by redirecting the requests during this time or inducing the collection yourself when it can be better accommodated.</span></span>  
  
## <a name="notification-threshold-parameters"></a><span data-ttu-id="8a4b9-131">Bildirim eşiği parametreleri</span><span class="sxs-lookup"><span data-stu-id="8a4b9-131">Notification Threshold Parameters</span></span>  

 <span data-ttu-id="8a4b9-132"><xref:System.GC.RegisterForFullGCNotification%2A>Yöntemi 2. nesil nesnelerin eşik değerlerini ve büyük nesne yığınını belirtmek için iki parametreye sahiptir.</span><span class="sxs-lookup"><span data-stu-id="8a4b9-132">The <xref:System.GC.RegisterForFullGCNotification%2A> method has two parameters to specify the threshold values of the generation 2 objects and the large object heap.</span></span> <span data-ttu-id="8a4b9-133">Bu değerler karşılandığında bir çöp toplama bildirimi oluşturulmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8a4b9-133">When those values are met, a garbage collection notification should be raised.</span></span> <span data-ttu-id="8a4b9-134">Aşağıdaki tabloda bu parametreler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8a4b9-134">The following table describes these parameters.</span></span>  
  
|<span data-ttu-id="8a4b9-135">Parametre</span><span class="sxs-lookup"><span data-stu-id="8a4b9-135">Parameter</span></span>|<span data-ttu-id="8a4b9-136">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8a4b9-136">Description</span></span>|  
|---------------|-----------------|  
|`maxGenerationThreshold`|<span data-ttu-id="8a4b9-137">2. nesil üzerinde yükseltilen nesneler temelinde bildirimin ne zaman oluşturulması gerektiğini belirten, 1 ile 99 arasında bir sayı.</span><span class="sxs-lookup"><span data-stu-id="8a4b9-137">A number between 1 and 99 that specifies when the notification should be raised based on the objects promoted in generation 2.</span></span>|  
|`largeObjectHeapThreshold`|<span data-ttu-id="8a4b9-138">Büyük nesne yığınında ayrılan nesneler temelinde bildirimin ne zaman oluşturulması gerektiğini belirten, 1 ile 99 arasında bir sayı.</span><span class="sxs-lookup"><span data-stu-id="8a4b9-138">A number between 1 and 99 that specifies when the notification should be raised based on the objects that are allocated in the large object heap.</span></span>|  
  
 <span data-ttu-id="8a4b9-139">Çok yüksek bir değer belirtirseniz, bir bildirim almanız, ancak çalışma zamanı bir koleksiyona neden olması için çok uzun bir süre olabilir.</span><span class="sxs-lookup"><span data-stu-id="8a4b9-139">If you specify a value that is too high, there is a high probability that you will receive a notification, but it could be too long a period to wait before the runtime causes a collection.</span></span> <span data-ttu-id="8a4b9-140">Bir koleksiyonu kendiniz kullandıysanız, çalışma zamanı koleksiyona neden olursa daha fazla nesne geri kazanırsınız.</span><span class="sxs-lookup"><span data-stu-id="8a4b9-140">If you induce a collection yourself, you may reclaim more objects than would be reclaimed if the runtime causes the collection.</span></span>  
  
 <span data-ttu-id="8a4b9-141">Çok düşük bir değer belirtirseniz çalışma zamanı, bildirim almak için yeterli zamana girmeden önce koleksiyona neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="8a4b9-141">If you specify a value that is too low, the runtime may cause the collection before you have had sufficient time to be notified.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8a4b9-142">Örnek</span><span class="sxs-lookup"><span data-stu-id="8a4b9-142">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="8a4b9-143">Description</span><span class="sxs-lookup"><span data-stu-id="8a4b9-143">Description</span></span>  

 <span data-ttu-id="8a4b9-144">Aşağıdaki örnekte, bir sunucu grubu gelen Web istekleri hizmetidir.</span><span class="sxs-lookup"><span data-stu-id="8a4b9-144">In the following example, a group of servers service incoming Web requests.</span></span> <span data-ttu-id="8a4b9-145">İstekleri işleme iş yükünün benzetimini yapmak için, bir koleksiyona bayt dizileri eklenir <xref:System.Collections.Generic.List%601> .</span><span class="sxs-lookup"><span data-stu-id="8a4b9-145">To simulate the workload of processing requests, byte arrays are added to a <xref:System.Collections.Generic.List%601> collection.</span></span> <span data-ttu-id="8a4b9-146">Her sunucu bir çöp toplama bildirimine kaydolduktan sonra `WaitForFullGCProc` <xref:System.GCNotificationStatus> , ve yöntemleri tarafından döndürülen numaralandırmayı sürekli olarak izlemek için Kullanıcı yönteminde bir iş parçacığı başlatır <xref:System.GC.WaitForFullGCApproach%2A> <xref:System.GC.WaitForFullGCComplete%2A> .</span><span class="sxs-lookup"><span data-stu-id="8a4b9-146">Each server registers for a garbage collection notification and then starts a thread on the `WaitForFullGCProc` user method to continuously monitor the <xref:System.GCNotificationStatus> enumeration that is returned by the <xref:System.GC.WaitForFullGCApproach%2A> and the <xref:System.GC.WaitForFullGCComplete%2A> methods.</span></span>  
  
 <span data-ttu-id="8a4b9-147"><xref:System.GC.WaitForFullGCApproach%2A>Ve yöntemleri, <xref:System.GC.WaitForFullGCComplete%2A> bir bildirim oluşturulduğunda ilgili olay işleme Kullanıcı yöntemlerini çağırır:</span><span class="sxs-lookup"><span data-stu-id="8a4b9-147">The <xref:System.GC.WaitForFullGCApproach%2A> and the <xref:System.GC.WaitForFullGCComplete%2A> methods call their respective event-handling user methods when a notification is raised:</span></span>  
  
- `OnFullGCApproachNotify`  
  
     <span data-ttu-id="8a4b9-148">Bu yöntem, `RedirectRequests` istek Kuyruklama sunucusuna istekleri sunucuya göndermeyi askıya almaya yönlendiren Kullanıcı yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="8a4b9-148">This method calls the `RedirectRequests` user method, which instructs the request queuing server to suspend sending requests to the server.</span></span> <span data-ttu-id="8a4b9-149">Bu, sınıf düzeyi değişkeni, `bAllocate` `false` daha fazla nesne ayrılmaması için olarak ayarlanarak benzetilir.</span><span class="sxs-lookup"><span data-stu-id="8a4b9-149">This is simulated by setting the class-level variable `bAllocate` to `false` so that no more objects are allocated.</span></span>  
  
     <span data-ttu-id="8a4b9-150">Ardından, `FinishExistingRequests` bekleyen sunucu isteklerini işlemeyi tamamlayacak Kullanıcı yöntemi çağırılır.</span><span class="sxs-lookup"><span data-stu-id="8a4b9-150">Next, the `FinishExistingRequests` user method is called to finish processing the pending server requests.</span></span> <span data-ttu-id="8a4b9-151">Bu, koleksiyonu temizleyerek benzetilir <xref:System.Collections.Generic.List%601> .</span><span class="sxs-lookup"><span data-stu-id="8a4b9-151">This is simulated by clearing the <xref:System.Collections.Generic.List%601> collection.</span></span>  
  
     <span data-ttu-id="8a4b9-152">Son olarak, iş yükü hafif olduğundan bir çöp toplama işlemi yapılır.</span><span class="sxs-lookup"><span data-stu-id="8a4b9-152">Finally, a garbage collection is induced because the workload is light.</span></span>  
  
- `OnFullGCCompleteNotify`  
  
     <span data-ttu-id="8a4b9-153">Bu yöntem, `AcceptRequests` sunucu artık tam bir atık toplama için savunmasız olmadığından istekleri kabul etmek için Kullanıcı yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="8a4b9-153">This method calls the user method `AcceptRequests` to resume accepting requests because the server is no longer susceptible to a full garbage collection.</span></span> <span data-ttu-id="8a4b9-154">Bu eylem, `bAllocate` `true` nesnenin koleksiyona eklenmeyi sürdürmesini sağlamak için değişkeni olarak ayarlanarak benzetilir <xref:System.Collections.Generic.List%601> .</span><span class="sxs-lookup"><span data-stu-id="8a4b9-154">This action is simulated by setting the `bAllocate` variable to `true` so that objects can resume being added to the <xref:System.Collections.Generic.List%601> collection.</span></span>  
  
 <span data-ttu-id="8a4b9-155">Aşağıdaki kod, `Main` Örneğin yöntemini içerir.</span><span class="sxs-lookup"><span data-stu-id="8a4b9-155">The following code contains the `Main` method of the example.</span></span>  
  
 [!code-cpp[GCNotification#2](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#2)]
 [!code-csharp[GCNotification#2](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#2)]
 [!code-vb[GCNotification#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#2)]  
  
 <span data-ttu-id="8a4b9-156">Aşağıdaki kod `WaitForFullGCProc` , atık toplama bildirimlerini denetlemek için sürekli while döngüsünü içeren Kullanıcı yöntemini içerir.</span><span class="sxs-lookup"><span data-stu-id="8a4b9-156">The following code contains the `WaitForFullGCProc` user method, that contains a continuous while loop to check for garbage collection notifications.</span></span>  
  
 [!code-cpp[GCNotification#8](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#8)]
 [!code-csharp[GCNotification#8](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#8)]
 [!code-vb[GCNotification#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#8)]  
  
 <span data-ttu-id="8a4b9-157">Aşağıdaki kod `OnFullGCApproachNotify` ,</span><span class="sxs-lookup"><span data-stu-id="8a4b9-157">The following code contains the `OnFullGCApproachNotify` method as called from the</span></span>  
  
 <span data-ttu-id="8a4b9-158">`WaitForFullGCProc` yöntemidir.</span><span class="sxs-lookup"><span data-stu-id="8a4b9-158">`WaitForFullGCProc` method.</span></span>  
  
 [!code-cpp[GCNotification#5](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#5)]
 [!code-csharp[GCNotification#5](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#5)]
 [!code-vb[GCNotification#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#5)]  
  
 <span data-ttu-id="8a4b9-159">Aşağıdaki kod `OnFullGCApproachComplete` ,</span><span class="sxs-lookup"><span data-stu-id="8a4b9-159">The following code contains the `OnFullGCApproachComplete` method as called from the</span></span>  
  
 <span data-ttu-id="8a4b9-160">`WaitForFullGCProc` yöntemidir.</span><span class="sxs-lookup"><span data-stu-id="8a4b9-160">`WaitForFullGCProc` method.</span></span>  
  
 [!code-cpp[GCNotification#6](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#6)]
 [!code-csharp[GCNotification#6](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#6)]
 [!code-vb[GCNotification#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#6)]  
  
 <span data-ttu-id="8a4b9-161">Aşağıdaki kod, ve yöntemlerinden çağrılan Kullanıcı yöntemlerini içerir `OnFullGCApproachNotify` `OnFullGCCompleteNotify` .</span><span class="sxs-lookup"><span data-stu-id="8a4b9-161">The following code contains the user methods that are called from the `OnFullGCApproachNotify` and `OnFullGCCompleteNotify` methods.</span></span> <span data-ttu-id="8a4b9-162">Kullanıcı yöntemleri istekleri yeniden yönlendirir, mevcut istekleri bitirir ve sonra tam çöp toplama gerçekleştirildikten sonra istekleri sürdürür.</span><span class="sxs-lookup"><span data-stu-id="8a4b9-162">The user methods redirect requests, finish existing requests, and then resume requests after a full garbage collection has occurred.</span></span>  
  
 [!code-cpp[GCNotification#9](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#9)]
 [!code-csharp[GCNotification#9](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#9)]
 [!code-vb[GCNotification#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#9)]  
  
 <span data-ttu-id="8a4b9-163">Tüm kod örneği aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="8a4b9-163">The entire code sample is as follows:</span></span>  
  
 [!code-cpp[GCNotification#1](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#1)]
 [!code-csharp[GCNotification#1](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#1)]
 [!code-vb[GCNotification#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="8a4b9-164">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8a4b9-164">See also</span></span>

- [<span data-ttu-id="8a4b9-165">Çöp toplama</span><span class="sxs-lookup"><span data-stu-id="8a4b9-165">Garbage Collection</span></span>](index.md)
