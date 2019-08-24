---
title: Çöp Toplama Bildirimleri
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- garbage collection, notifications
ms.assetid: e12d8e74-31e3-4035-a87d-f3e66f0a9b89
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: edf519621c2113843b89d96948243e9c095d2a57
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/23/2019
ms.locfileid: "69988867"
---
# <a name="garbage-collection-notifications"></a><span data-ttu-id="bc065-102">Çöp Toplama Bildirimleri</span><span class="sxs-lookup"><span data-stu-id="bc065-102">Garbage Collection Notifications</span></span>
<span data-ttu-id="bc065-103">Ortak dil çalışma zamanı ile tam çöp toplamanın (yani 2. nesil bir koleksiyon) performansı olumsuz etkileyebileceği durumlar vardır.</span><span class="sxs-lookup"><span data-stu-id="bc065-103">There are situations in which a full garbage collection (that is, a generation 2 collection) by the common language runtime may adversely affect performance.</span></span> <span data-ttu-id="bc065-104">Bu, özellikle büyük hacimli istekleri işleyen sunucularla ilgili bir sorun olabilir; Bu durumda, uzun bir atık toplama bir istek zaman aşımına neden olabilir. Kritik bir süre boyunca tam bir koleksiyonun oluşmasını önlemek için, tam bir çöp toplamanın yaklaştığı ve iş yükünü başka bir sunucu örneğine yeniden yönlendirmek için işlem gerçekleştirilecek şekilde bir uyarı alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bc065-104">This can be an issue particularly with servers that process large volumes of requests; in this case, a long garbage collection can cause a request time-out. To prevent a full collection from occurring during a critical period, you can be notified that a full garbage collection is approaching and then take action to redirect the workload to another server instance.</span></span> <span data-ttu-id="bc065-105">Ayrıca, geçerli sunucu örneğinin istekleri işlemesini gerektirmeyen bir koleksiyonu kendiniz de yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bc065-105">You can also induce a collection yourself, provided that the current server instance does not need to process requests.</span></span>  
  
 <span data-ttu-id="bc065-106"><xref:System.GC.RegisterForFullGCNotification%2A> Yöntemi, çalışma zamanı tam çöp toplama işlemini yaklaştığında bir bildirimin bir bildirimine kaydolur.</span><span class="sxs-lookup"><span data-stu-id="bc065-106">The <xref:System.GC.RegisterForFullGCNotification%2A> method registers for a notification to be raised when the runtime senses that a full garbage collection is approaching.</span></span> <span data-ttu-id="bc065-107">Bu bildirimin iki bölümü vardır: tam çöp toplama yaklaşıyorsa ve tam çöp toplama tamamlandığında.</span><span class="sxs-lookup"><span data-stu-id="bc065-107">There are two parts to this notification: when the full garbage collection is approaching and when the full garbage collection has completed.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="bc065-108">Yalnızca atık koleksiyonları engelleme bildirimleri yükseltir.</span><span class="sxs-lookup"><span data-stu-id="bc065-108">Only blocking garbage collections raise notifications.</span></span> <span data-ttu-id="bc065-109">GcConcurrent > yapılandırma öğesi etkinleştirildiğinde, arka plan atık koleksiyonları bildirim oluşturmaz. [ \<](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md)</span><span class="sxs-lookup"><span data-stu-id="bc065-109">When the [\<gcConcurrent>](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) configuration element is enabled, background garbage collections will not raise notifications.</span></span>  
  
 <span data-ttu-id="bc065-110">Bir bildirimin ne zaman kabarık olduğunu anlamak için <xref:System.GC.WaitForFullGCApproach%2A> ve <xref:System.GC.WaitForFullGCComplete%2A> yöntemlerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="bc065-110">To determine when a notification has been raised, use the <xref:System.GC.WaitForFullGCApproach%2A> and <xref:System.GC.WaitForFullGCComplete%2A> methods.</span></span> <span data-ttu-id="bc065-111">Genellikle, bildirim durumunu gösteren bir `while` <xref:System.GCNotificationStatus> sabit listesi elde etmek için bu yöntemleri bir döngüde kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="bc065-111">Typically, you use these methods in a `while` loop to continually obtain a <xref:System.GCNotificationStatus> enumeration that shows the status of the notification.</span></span> <span data-ttu-id="bc065-112">Bu değer ise <xref:System.GCNotificationStatus.Succeeded>, şunları yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="bc065-112">If that value is <xref:System.GCNotificationStatus.Succeeded>, you can do the following:</span></span>  
  
- <span data-ttu-id="bc065-113"><xref:System.GC.WaitForFullGCApproach%2A> Yöntemiyle elde edilen bir bildirime yanıt olarak, iş yükünü yeniden yönlendirebilir ve muhtemelen bir koleksiyonu kendiniz bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bc065-113">In response to a notification obtained with the <xref:System.GC.WaitForFullGCApproach%2A> method, you can redirect the workload and possibly induce a collection yourself.</span></span>  
  
- <span data-ttu-id="bc065-114"><xref:System.GC.WaitForFullGCComplete%2A> Yöntemiyle elde edilen bir bildirime yanıt olarak, geçerli sunucu örneğini istekleri yeniden işlemek için kullanılabilir hale getirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bc065-114">In response to a notification obtained with the <xref:System.GC.WaitForFullGCComplete%2A> method, you can make the current server instance available to process requests again.</span></span> <span data-ttu-id="bc065-115">Ayrıca, bilgi toplayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bc065-115">You can also gather information.</span></span> <span data-ttu-id="bc065-116">Örneğin, koleksiyon sayısını kaydetmek için <xref:System.GC.CollectionCount%2A> yöntemini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bc065-116">For example, you can use the <xref:System.GC.CollectionCount%2A> method to record the number of collections.</span></span>  
  
 <span data-ttu-id="bc065-117"><xref:System.GC.WaitForFullGCApproach%2A> Veyöntemleri<xref:System.GC.WaitForFullGCComplete%2A> birlikte çalışmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="bc065-117">The <xref:System.GC.WaitForFullGCApproach%2A> and the <xref:System.GC.WaitForFullGCComplete%2A> methods are designed to work together.</span></span> <span data-ttu-id="bc065-118">Diğeri olmadan kullanmak, belirsiz sonuçlar doğurabilir.</span><span class="sxs-lookup"><span data-stu-id="bc065-118">Using one without the other can produce indeterminate results.</span></span>  
  
## <a name="full-garbage-collection"></a><span data-ttu-id="bc065-119">Tam çöp toplama</span><span class="sxs-lookup"><span data-stu-id="bc065-119">Full Garbage Collection</span></span>  
 <span data-ttu-id="bc065-120">Aşağıdaki senaryolardan herhangi biri doğru olduğunda, çalışma zamanı tam çöp toplamaya neden olur:</span><span class="sxs-lookup"><span data-stu-id="bc065-120">The runtime causes a full garbage collection when any of the following scenarios are true:</span></span>  
  
- <span data-ttu-id="bc065-121">Bir sonraki nesil 2 toplamaya neden olacak şekilde 2. nesil bir bellek yükseltildi.</span><span class="sxs-lookup"><span data-stu-id="bc065-121">Enough memory has been promoted into generation 2 to cause the next generation 2 collection.</span></span>  
  
- <span data-ttu-id="bc065-122">Bir sonraki nesil 2 toplamaya neden olmak için büyük nesne yığınına yeterli bellek yükseltildi.</span><span class="sxs-lookup"><span data-stu-id="bc065-122">Enough memory has been promoted into the large object heap to cause the next generation 2 collection.</span></span>  
  
- <span data-ttu-id="bc065-123">1\. nesil bir koleksiyon, diğer faktörler nedeniyle 2. nesil bir toplamaya ilerletildi.</span><span class="sxs-lookup"><span data-stu-id="bc065-123">A collection of generation 1 is escalated to a collection of generation 2 due to other factors.</span></span>  
  
 <span data-ttu-id="bc065-124"><xref:System.GC.RegisterForFullGCNotification%2A> Yönteminde belirttiğiniz eşikler ilk iki senaryo için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="bc065-124">The thresholds you specify in the <xref:System.GC.RegisterForFullGCNotification%2A> method apply to the first two scenarios.</span></span> <span data-ttu-id="bc065-125">Ancak, ilk senaryoda bildirimi her zaman, iki nedenden dolayı belirttiğiniz eşik değerleriyle orantılı şekilde almazsınız:</span><span class="sxs-lookup"><span data-stu-id="bc065-125">However, in the first scenario you will not always receive the notification at the time proportional to the threshold values you specify for two reasons:</span></span>  
  
- <span data-ttu-id="bc065-126">Çalışma zamanı her küçük nesne ayırmayı denetlemez (performans nedenleriyle).</span><span class="sxs-lookup"><span data-stu-id="bc065-126">The runtime does not check each small object allocation (for performance reasons).</span></span>  
  
- <span data-ttu-id="bc065-127">Yalnızca 1. nesil koleksiyonlar belleği 2. nesil olarak yükseltir.</span><span class="sxs-lookup"><span data-stu-id="bc065-127">Only generation 1 collections promote memory into generation 2.</span></span>  
  
 <span data-ttu-id="bc065-128">Ayrıca üçüncü senaryo, bildirimi alacağınız zaman açıklanmayacak şekilde katkıda bulunur.</span><span class="sxs-lookup"><span data-stu-id="bc065-128">The third scenario also contributes to the uncertainty of when you will receive the notification.</span></span> <span data-ttu-id="bc065-129">Bu bir garanti olmamasına karşın, bu süre boyunca istekleri yeniden yönlendirerek veya daha iyi bir hale gelebileceği zaman koleksiyonu kendiniz gerçekleştirerek, inopportune tam çöp toplamanın etkilerini azaltmak için faydalı bir yol olduğunu kanıtlamaz.</span><span class="sxs-lookup"><span data-stu-id="bc065-129">Although this is not a guarantee, it does prove to be a useful way to mitigate the effects of an inopportune full garbage collection by redirecting the requests during this time or inducing the collection yourself when it can be better accommodated.</span></span>  
  
## <a name="notification-threshold-parameters"></a><span data-ttu-id="bc065-130">Bildirim eşiği parametreleri</span><span class="sxs-lookup"><span data-stu-id="bc065-130">Notification Threshold Parameters</span></span>  
 <span data-ttu-id="bc065-131"><xref:System.GC.RegisterForFullGCNotification%2A> Yöntemi 2. nesil nesnelerin eşik değerlerini ve büyük nesne yığınını belirtmek için iki parametreye sahiptir.</span><span class="sxs-lookup"><span data-stu-id="bc065-131">The <xref:System.GC.RegisterForFullGCNotification%2A> method has two parameters to specify the threshold values of the generation 2 objects and the large object heap.</span></span> <span data-ttu-id="bc065-132">Bu değerler karşılandığında bir çöp toplama bildirimi oluşturulmalıdır.</span><span class="sxs-lookup"><span data-stu-id="bc065-132">When those values are met, a garbage collection notification should be raised.</span></span> <span data-ttu-id="bc065-133">Aşağıdaki tabloda bu parametreler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="bc065-133">The following table describes these parameters.</span></span>  
  
|<span data-ttu-id="bc065-134">Parametre</span><span class="sxs-lookup"><span data-stu-id="bc065-134">Parameter</span></span>|<span data-ttu-id="bc065-135">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bc065-135">Description</span></span>|  
|---------------|-----------------|  
|`maxGenerationThreshold`|<span data-ttu-id="bc065-136">2\. nesil üzerinde yükseltilen nesneler temelinde bildirimin ne zaman oluşturulması gerektiğini belirten, 1 ile 99 arasında bir sayı.</span><span class="sxs-lookup"><span data-stu-id="bc065-136">A number between 1 and 99 that specifies when the notification should be raised based on the objects promoted in generation 2.</span></span>|  
|`largeObjectHeapThreshold`|<span data-ttu-id="bc065-137">Büyük nesne yığınında ayrılan nesneler temelinde bildirimin ne zaman oluşturulması gerektiğini belirten, 1 ile 99 arasında bir sayı.</span><span class="sxs-lookup"><span data-stu-id="bc065-137">A number between 1 and 99 that specifies when the notification should be raised based on the objects that are allocated in the large object heap.</span></span>|  
  
 <span data-ttu-id="bc065-138">Çok yüksek bir değer belirtirseniz, bir bildirim almanız, ancak çalışma zamanı bir koleksiyona neden olması için çok uzun bir süre olabilir.</span><span class="sxs-lookup"><span data-stu-id="bc065-138">If you specify a value that is too high, there is a high probability that you will receive a notification, but it could be too long a period to wait before the runtime causes a collection.</span></span> <span data-ttu-id="bc065-139">Bir koleksiyonu kendiniz kullandıysanız, çalışma zamanı koleksiyona neden olursa daha fazla nesne geri kazanırsınız.</span><span class="sxs-lookup"><span data-stu-id="bc065-139">If you induce a collection yourself, you may reclaim more objects than would be reclaimed if the runtime causes the collection.</span></span>  
  
 <span data-ttu-id="bc065-140">Çok düşük bir değer belirtirseniz çalışma zamanı, bildirim almak için yeterli zamana girmeden önce koleksiyona neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="bc065-140">If you specify a value that is too low, the runtime may cause the collection before you have had sufficient time to be notified.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bc065-141">Örnek</span><span class="sxs-lookup"><span data-stu-id="bc065-141">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="bc065-142">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bc065-142">Description</span></span>  
 <span data-ttu-id="bc065-143">Aşağıdaki örnekte, bir sunucu grubu gelen Web istekleri hizmetidir.</span><span class="sxs-lookup"><span data-stu-id="bc065-143">In the following example, a group of servers service incoming Web requests.</span></span> <span data-ttu-id="bc065-144">İstekleri işleme iş yükünün benzetimini yapmak için, bir <xref:System.Collections.Generic.List%601> koleksiyona bayt dizileri eklenir.</span><span class="sxs-lookup"><span data-stu-id="bc065-144">To simulate the workload of processing requests, byte arrays are added to a <xref:System.Collections.Generic.List%601> collection.</span></span> <span data-ttu-id="bc065-145">Her sunucu bir `WaitForFullGCProc` çöp toplama bildirimine kaydolduktan sonra, <xref:System.GC.WaitForFullGCApproach%2A> ve <xref:System.GC.WaitForFullGCComplete%2A> yöntemleri tarafından döndürülen <xref:System.GCNotificationStatus> numaralandırmayı sürekli olarak izlemek için Kullanıcı yönteminde bir iş parçacığı başlatır.</span><span class="sxs-lookup"><span data-stu-id="bc065-145">Each server registers for a garbage collection notification and then starts a thread on the `WaitForFullGCProc` user method to continuously monitor the <xref:System.GCNotificationStatus> enumeration that is returned by the <xref:System.GC.WaitForFullGCApproach%2A> and the <xref:System.GC.WaitForFullGCComplete%2A> methods.</span></span>  
  
 <span data-ttu-id="bc065-146">Ve yöntemleri, <xref:System.GC.WaitForFullGCApproach%2A>birbildirim oluşturulduğundailgiliolayişlemeKullanıcıyöntemleriniçağırır:<xref:System.GC.WaitForFullGCComplete%2A></span><span class="sxs-lookup"><span data-stu-id="bc065-146">The <xref:System.GC.WaitForFullGCApproach%2A> and the <xref:System.GC.WaitForFullGCComplete%2A> methods call their respective event-handling user methods when a notification is raised:</span></span>  
  
- `OnFullGCApproachNotify`  
  
     <span data-ttu-id="bc065-147">Bu yöntem, istek `RedirectRequests` Kuyruklama sunucusuna istekleri sunucuya göndermeyi askıya almaya yönlendiren Kullanıcı yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="bc065-147">This method calls the `RedirectRequests` user method, which instructs the request queuing server to suspend sending requests to the server.</span></span> <span data-ttu-id="bc065-148">Bu, sınıf düzeyi değişkeni `bAllocate` , daha fazla nesne ayrılmaması için olarak `false` ayarlanarak benzetilir.</span><span class="sxs-lookup"><span data-stu-id="bc065-148">This is simulated by setting the class-level variable `bAllocate` to `false` so that no more objects are allocated.</span></span>  
  
     <span data-ttu-id="bc065-149">Ardından, `FinishExistingRequests` bekleyen sunucu isteklerini işlemeyi tamamlayacak Kullanıcı yöntemi çağırılır.</span><span class="sxs-lookup"><span data-stu-id="bc065-149">Next, the `FinishExistingRequests` user method is called to finish processing the pending server requests.</span></span> <span data-ttu-id="bc065-150">Bu, <xref:System.Collections.Generic.List%601> koleksiyonu temizleyerek benzetilir.</span><span class="sxs-lookup"><span data-stu-id="bc065-150">This is simulated by clearing the <xref:System.Collections.Generic.List%601> collection.</span></span>  
  
     <span data-ttu-id="bc065-151">Son olarak, iş yükü hafif olduğundan bir çöp toplama işlemi yapılır.</span><span class="sxs-lookup"><span data-stu-id="bc065-151">Finally, a garbage collection is induced because the workload is light.</span></span>  
  
- `OnFullGCCompleteNotify`  
  
     <span data-ttu-id="bc065-152">Bu yöntem, sunucu artık tam `AcceptRequests` bir atık toplama için savunmasız olmadığından istekleri kabul etmek için Kullanıcı yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="bc065-152">This method calls the user method `AcceptRequests` to resume accepting requests because the server is no longer susceptible to a full garbage collection.</span></span> <span data-ttu-id="bc065-153">Bu eylem, `bAllocate` nesnenin <xref:System.Collections.Generic.List%601> koleksiyona eklenmeyi sürdürmesini sağlamak `true` için değişkeni olarak ayarlanarak benzetilir.</span><span class="sxs-lookup"><span data-stu-id="bc065-153">This action is simulated by setting the `bAllocate` variable to `true` so that objects can resume being added to the <xref:System.Collections.Generic.List%601> collection.</span></span>  
  
 <span data-ttu-id="bc065-154">Aşağıdaki kod, örneğin `Main` yöntemini içerir.</span><span class="sxs-lookup"><span data-stu-id="bc065-154">The following code contains the `Main` method of the example.</span></span>  
  
 [!code-cpp[GCNotification#2](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#2)]
 [!code-csharp[GCNotification#2](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#2)]
 [!code-vb[GCNotification#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#2)]  
  
 <span data-ttu-id="bc065-155">Aşağıdaki kod, atık toplama `WaitForFullGCProc` bildirimlerini denetlemek için sürekli while döngüsünü içeren Kullanıcı yöntemini içerir.</span><span class="sxs-lookup"><span data-stu-id="bc065-155">The following code contains the `WaitForFullGCProc` user method, that contains a continuous while loop to check for garbage collection notifications.</span></span>  
  
 [!code-cpp[GCNotification#8](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#8)]
 [!code-csharp[GCNotification#8](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#8)]
 [!code-vb[GCNotification#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#8)]  
  
 <span data-ttu-id="bc065-156">Aşağıdaki kod `OnFullGCApproachNotify` ,</span><span class="sxs-lookup"><span data-stu-id="bc065-156">The following code contains the `OnFullGCApproachNotify` method as called from the</span></span>  
  
 <span data-ttu-id="bc065-157">`WaitForFullGCProc`yöntemidir.</span><span class="sxs-lookup"><span data-stu-id="bc065-157">`WaitForFullGCProc` method.</span></span>  
  
 [!code-cpp[GCNotification#5](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#5)]
 [!code-csharp[GCNotification#5](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#5)]
 [!code-vb[GCNotification#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#5)]  
  
 <span data-ttu-id="bc065-158">Aşağıdaki kod `OnFullGCApproachComplete` ,</span><span class="sxs-lookup"><span data-stu-id="bc065-158">The following code contains the `OnFullGCApproachComplete` method as called from the</span></span>  
  
 <span data-ttu-id="bc065-159">`WaitForFullGCProc`yöntemidir.</span><span class="sxs-lookup"><span data-stu-id="bc065-159">`WaitForFullGCProc` method.</span></span>  
  
 [!code-cpp[GCNotification#6](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#6)]
 [!code-csharp[GCNotification#6](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#6)]
 [!code-vb[GCNotification#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#6)]  
  
 <span data-ttu-id="bc065-160">Aşağıdaki kod, `OnFullGCApproachNotify` ve `OnFullGCCompleteNotify` yöntemlerinden çağrılan Kullanıcı yöntemlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="bc065-160">The following code contains the user methods that are called from the `OnFullGCApproachNotify` and `OnFullGCCompleteNotify` methods.</span></span> <span data-ttu-id="bc065-161">Kullanıcı yöntemleri istekleri yeniden yönlendirir, mevcut istekleri bitirir ve sonra tam çöp toplama gerçekleştirildikten sonra istekleri sürdürür.</span><span class="sxs-lookup"><span data-stu-id="bc065-161">The user methods redirect requests, finish existing requests, and then resume requests after a full garbage collection has occurred.</span></span>  
  
 [!code-cpp[GCNotification#9](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#9)]
 [!code-csharp[GCNotification#9](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#9)]
 [!code-vb[GCNotification#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#9)]  
  
 <span data-ttu-id="bc065-162">Tüm kod örneği aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="bc065-162">The entire code sample is as follows:</span></span>  
  
 [!code-cpp[GCNotification#1](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#1)]
 [!code-csharp[GCNotification#1](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#1)]
 [!code-vb[GCNotification#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="bc065-163">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bc065-163">See also</span></span>

- [<span data-ttu-id="bc065-164">Atık Toplama</span><span class="sxs-lookup"><span data-stu-id="bc065-164">Garbage Collection</span></span>](../../../docs/standard/garbage-collection/index.md)
