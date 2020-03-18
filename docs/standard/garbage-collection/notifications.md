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
ms.openlocfilehash: d5646c4969c95350ab4cd63b16f6f99ffba3a4ec
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73131541"
---
# <a name="garbage-collection-notifications"></a><span data-ttu-id="07c9b-102">Çöp Toplama Bildirimleri</span><span class="sxs-lookup"><span data-stu-id="07c9b-102">Garbage Collection Notifications</span></span>
<span data-ttu-id="07c9b-103">Ortak dil çalışma süresine göre tam bir çöp toplamanın (yani bir nesil 2 koleksiyonunun) performansı olumsuz etkileyebileceği durumlar vardır.</span><span class="sxs-lookup"><span data-stu-id="07c9b-103">There are situations in which a full garbage collection (that is, a generation 2 collection) by the common language runtime may adversely affect performance.</span></span> <span data-ttu-id="07c9b-104">Bu, özellikle büyük büyük sayıda isteği işleyen sunucularla ilgili bir sorun olabilir; bu durumda, uzun bir çöp toplama isteği zaman ayarı neden olabilir. Kritik bir dönemde tam bir koleksiyonun oluşmasını önlemek için, tam bir çöp toplamanın yaklaştığını bildirebilir ve ardından iş yükünü başka bir sunucu örneğine yönlendirmek için harekete geçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="07c9b-104">This can be an issue particularly with servers that process large volumes of requests; in this case, a long garbage collection can cause a request time-out. To prevent a full collection from occurring during a critical period, you can be notified that a full garbage collection is approaching and then take action to redirect the workload to another server instance.</span></span> <span data-ttu-id="07c9b-105">Geçerli sunucu örneğinin istekleri işlemesi gerekmediği sürece, bir koleksiyonu kendiniz de ikna edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="07c9b-105">You can also induce a collection yourself, provided that the current server instance does not need to process requests.</span></span>  
  
 <span data-ttu-id="07c9b-106">Yöntem, <xref:System.GC.RegisterForFullGCNotification%2A> çalışma zamanı tam bir çöp toplamanın yaklaştığını algıladığında yükseltilecek bir bildirim için kaydeder.</span><span class="sxs-lookup"><span data-stu-id="07c9b-106">The <xref:System.GC.RegisterForFullGCNotification%2A> method registers for a notification to be raised when the runtime senses that a full garbage collection is approaching.</span></span> <span data-ttu-id="07c9b-107">Bu bildirimin iki bölümü vardır: tam çöp toplama yaklaşırken ve tam çöp toplama tamamlandığında.</span><span class="sxs-lookup"><span data-stu-id="07c9b-107">There are two parts to this notification: when the full garbage collection is approaching and when the full garbage collection has completed.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="07c9b-108">Yalnızca çöp toplamaları engelleme bildirimleri yükseltmek.</span><span class="sxs-lookup"><span data-stu-id="07c9b-108">Only blocking garbage collections raise notifications.</span></span> <span data-ttu-id="07c9b-109">gcConcurrent>yapılandırma öğesi etkinleştirildiğinde, arka plan çöp koleksiyonları bildirimleri yükseltmez. [ \<](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md)</span><span class="sxs-lookup"><span data-stu-id="07c9b-109">When the [\<gcConcurrent>](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) configuration element is enabled, background garbage collections will not raise notifications.</span></span>  
  
 <span data-ttu-id="07c9b-110">Bildirimin ne zaman yükseltildiğini belirlemek <xref:System.GC.WaitForFullGCApproach%2A> <xref:System.GC.WaitForFullGCComplete%2A> için, bu bildirimi ve yöntemleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="07c9b-110">To determine when a notification has been raised, use the <xref:System.GC.WaitForFullGCApproach%2A> and <xref:System.GC.WaitForFullGCComplete%2A> methods.</span></span> <span data-ttu-id="07c9b-111">Genellikle, bildirimin durumunu gösteren `while` bir <xref:System.GCNotificationStatus> numaralandırma elde etmek için bu yöntemleri bir döngü içinde kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="07c9b-111">Typically, you use these methods in a `while` loop to continually obtain a <xref:System.GCNotificationStatus> enumeration that shows the status of the notification.</span></span> <span data-ttu-id="07c9b-112">Bu değer <xref:System.GCNotificationStatus.Succeeded>ise, aşağıdakileri yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="07c9b-112">If that value is <xref:System.GCNotificationStatus.Succeeded>, you can do the following:</span></span>  
  
- <span data-ttu-id="07c9b-113"><xref:System.GC.WaitForFullGCApproach%2A> Yöntemle elde edilen bir bildirime yanıt olarak, iş yükünü yeniden yönlendirebilir ve büyük olasılıkla bir koleksiyonu kendiniz ikna edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="07c9b-113">In response to a notification obtained with the <xref:System.GC.WaitForFullGCApproach%2A> method, you can redirect the workload and possibly induce a collection yourself.</span></span>  
  
- <span data-ttu-id="07c9b-114"><xref:System.GC.WaitForFullGCComplete%2A> Yöntemle elde edilen bir bildirime yanıt olarak, geçerli sunucu örneğini istekleri yeniden işlemek için kullanılabilir hale getirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="07c9b-114">In response to a notification obtained with the <xref:System.GC.WaitForFullGCComplete%2A> method, you can make the current server instance available to process requests again.</span></span> <span data-ttu-id="07c9b-115">Ayrıca bilgi toplayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="07c9b-115">You can also gather information.</span></span> <span data-ttu-id="07c9b-116">Örneğin, koleksiyon sayısını <xref:System.GC.CollectionCount%2A> kaydetmek için yöntemi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="07c9b-116">For example, you can use the <xref:System.GC.CollectionCount%2A> method to record the number of collections.</span></span>  
  
 <span data-ttu-id="07c9b-117">Ve <xref:System.GC.WaitForFullGCApproach%2A> <xref:System.GC.WaitForFullGCComplete%2A> yöntemler birlikte çalışacak şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="07c9b-117">The <xref:System.GC.WaitForFullGCApproach%2A> and the <xref:System.GC.WaitForFullGCComplete%2A> methods are designed to work together.</span></span> <span data-ttu-id="07c9b-118">Birini diğeri olmadan kullanmak belirsiz sonuçlar üretebilir.</span><span class="sxs-lookup"><span data-stu-id="07c9b-118">Using one without the other can produce indeterminate results.</span></span>  
  
## <a name="full-garbage-collection"></a><span data-ttu-id="07c9b-119">Tam Çöp Toplama</span><span class="sxs-lookup"><span data-stu-id="07c9b-119">Full Garbage Collection</span></span>  
 <span data-ttu-id="07c9b-120">Çalışma zamanı, aşağıdaki senaryolardan herhangi biri doğru olduğunda tam bir çöp toplama neden olur:</span><span class="sxs-lookup"><span data-stu-id="07c9b-120">The runtime causes a full garbage collection when any of the following scenarios are true:</span></span>  
  
- <span data-ttu-id="07c9b-121">Yeterli bellek nesil 2 sonraki nesil 2 koleksiyonu neden yükseltildi.</span><span class="sxs-lookup"><span data-stu-id="07c9b-121">Enough memory has been promoted into generation 2 to cause the next generation 2 collection.</span></span>  
  
- <span data-ttu-id="07c9b-122">Yeterli bellek sonraki nesil 2 toplama neden büyük nesne yığını na yükseltildi.</span><span class="sxs-lookup"><span data-stu-id="07c9b-122">Enough memory has been promoted into the large object heap to cause the next generation 2 collection.</span></span>  
  
- <span data-ttu-id="07c9b-123">Nesil 1 koleksiyonu, diğer faktörler nedeniyle nesil 2 koleksiyonuna yükseltilir.</span><span class="sxs-lookup"><span data-stu-id="07c9b-123">A collection of generation 1 is escalated to a collection of generation 2 due to other factors.</span></span>  
  
 <span data-ttu-id="07c9b-124"><xref:System.GC.RegisterForFullGCNotification%2A> Yöntemde belirttiğiniz eşikler ilk iki senaryoya uygulanır.</span><span class="sxs-lookup"><span data-stu-id="07c9b-124">The thresholds you specify in the <xref:System.GC.RegisterForFullGCNotification%2A> method apply to the first two scenarios.</span></span> <span data-ttu-id="07c9b-125">Ancak, ilk senaryoda her zaman iki nedenden dolayı belirttiğiniz eşik değerleri ile orantılı zamanda bildirim almazsınız:</span><span class="sxs-lookup"><span data-stu-id="07c9b-125">However, in the first scenario you will not always receive the notification at the time proportional to the threshold values you specify for two reasons:</span></span>  
  
- <span data-ttu-id="07c9b-126">Çalışma süresi her küçük nesne ayırmayı denetlemez (performans nedenleriyle).</span><span class="sxs-lookup"><span data-stu-id="07c9b-126">The runtime does not check each small object allocation (for performance reasons).</span></span>  
  
- <span data-ttu-id="07c9b-127">Yalnızca nesil 1 koleksiyonları belleği nesil 2'ye dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="07c9b-127">Only generation 1 collections promote memory into generation 2.</span></span>  
  
 <span data-ttu-id="07c9b-128">Üçüncü senaryo, bildirimi ne zaman alacağınız konusundaki belirsizliğe de katkıda bulunur.</span><span class="sxs-lookup"><span data-stu-id="07c9b-128">The third scenario also contributes to the uncertainty of when you will receive the notification.</span></span> <span data-ttu-id="07c9b-129">Bu bir garanti olmasa da, bu süre içinde istekleri yeniden yönlendirerek veya daha iyi barındırılabilir zaman toplama kendiniz indükleyerek bir uygunsuz tam çöp toplama etkilerini azaltmak için yararlı bir yol olduğunu kanıtlıyor.</span><span class="sxs-lookup"><span data-stu-id="07c9b-129">Although this is not a guarantee, it does prove to be a useful way to mitigate the effects of an inopportune full garbage collection by redirecting the requests during this time or inducing the collection yourself when it can be better accommodated.</span></span>  
  
## <a name="notification-threshold-parameters"></a><span data-ttu-id="07c9b-130">Bildirim Eşik Parametreleri</span><span class="sxs-lookup"><span data-stu-id="07c9b-130">Notification Threshold Parameters</span></span>  
 <span data-ttu-id="07c9b-131">Yöntem, <xref:System.GC.RegisterForFullGCNotification%2A> nesil 2 nesnelerin eşik değerlerini ve büyük nesne yığınını belirtmek için iki parametreye sahiptir.</span><span class="sxs-lookup"><span data-stu-id="07c9b-131">The <xref:System.GC.RegisterForFullGCNotification%2A> method has two parameters to specify the threshold values of the generation 2 objects and the large object heap.</span></span> <span data-ttu-id="07c9b-132">Bu değerler karşılandığında, bir çöp toplama bildirimi yükseltilmelidir.</span><span class="sxs-lookup"><span data-stu-id="07c9b-132">When those values are met, a garbage collection notification should be raised.</span></span> <span data-ttu-id="07c9b-133">Aşağıdaki tabloda bu parametreler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="07c9b-133">The following table describes these parameters.</span></span>  
  
|<span data-ttu-id="07c9b-134">Parametre</span><span class="sxs-lookup"><span data-stu-id="07c9b-134">Parameter</span></span>|<span data-ttu-id="07c9b-135">Açıklama</span><span class="sxs-lookup"><span data-stu-id="07c9b-135">Description</span></span>|  
|---------------|-----------------|  
|`maxGenerationThreshold`|<span data-ttu-id="07c9b-136">Bildirimin nesil 2'de tanıtılan nesnelere göre ne zaman yükseltilmesi gerektiğini belirten 1 ile 99 arasındaki bir sayı.</span><span class="sxs-lookup"><span data-stu-id="07c9b-136">A number between 1 and 99 that specifies when the notification should be raised based on the objects promoted in generation 2.</span></span>|  
|`largeObjectHeapThreshold`|<span data-ttu-id="07c9b-137">Bildirimin büyük nesne yığınına ayrılan nesnelere göre ne zaman yükseltilmesi gerektiğini belirten 1 ile 99 arasındaki bir sayı.</span><span class="sxs-lookup"><span data-stu-id="07c9b-137">A number between 1 and 99 that specifies when the notification should be raised based on the objects that are allocated in the large object heap.</span></span>|  
  
 <span data-ttu-id="07c9b-138">Çok yüksek bir değer belirtirseniz, bildirim alma olasılığınız yüksektir, ancak çalışma süresinin koleksiyona neden olmasını beklemek çok uzun olabilir.</span><span class="sxs-lookup"><span data-stu-id="07c9b-138">If you specify a value that is too high, there is a high probability that you will receive a notification, but it could be too long a period to wait before the runtime causes a collection.</span></span> <span data-ttu-id="07c9b-139">Bir koleksiyona kendiniz neden olursanız, çalışma zamanı koleksiyona neden olursa geri alınacaktan daha fazla nesne geri alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="07c9b-139">If you induce a collection yourself, you may reclaim more objects than would be reclaimed if the runtime causes the collection.</span></span>  
  
 <span data-ttu-id="07c9b-140">Çok düşük bir değer belirtirseniz, bildirimalmak için yeterli zamana sahip olmadan önce çalışma süresi koleksiyona neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="07c9b-140">If you specify a value that is too low, the runtime may cause the collection before you have had sufficient time to be notified.</span></span>  
  
## <a name="example"></a><span data-ttu-id="07c9b-141">Örnek</span><span class="sxs-lookup"><span data-stu-id="07c9b-141">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="07c9b-142">Açıklama</span><span class="sxs-lookup"><span data-stu-id="07c9b-142">Description</span></span>  
 <span data-ttu-id="07c9b-143">Aşağıdaki örnekte, bir sunucu grubu gelen Web isteklerini karşılar.</span><span class="sxs-lookup"><span data-stu-id="07c9b-143">In the following example, a group of servers service incoming Web requests.</span></span> <span data-ttu-id="07c9b-144">İşlem isteklerinin iş yükünü simüle etmek için, <xref:System.Collections.Generic.List%601> bir koleksiyona bayt dizileri eklenir.</span><span class="sxs-lookup"><span data-stu-id="07c9b-144">To simulate the workload of processing requests, byte arrays are added to a <xref:System.Collections.Generic.List%601> collection.</span></span> <span data-ttu-id="07c9b-145">Her sunucu bir çöp toplama bildirimi için kaydeder `WaitForFullGCProc` ve sonra sürekli ve <xref:System.GCNotificationStatus> <xref:System.GC.WaitForFullGCApproach%2A> <xref:System.GC.WaitForFullGCComplete%2A> yöntemleri tarafından döndürülen numaralandırma izlemek için kullanıcı yöntemi üzerinde bir iş parçacığı başlar.</span><span class="sxs-lookup"><span data-stu-id="07c9b-145">Each server registers for a garbage collection notification and then starts a thread on the `WaitForFullGCProc` user method to continuously monitor the <xref:System.GCNotificationStatus> enumeration that is returned by the <xref:System.GC.WaitForFullGCApproach%2A> and the <xref:System.GC.WaitForFullGCComplete%2A> methods.</span></span>  
  
 <span data-ttu-id="07c9b-146">Ve <xref:System.GC.WaitForFullGCApproach%2A> <xref:System.GC.WaitForFullGCComplete%2A> yöntemler, bir bildirim yükseltildiğinde kendi olay işleme kullanıcı yöntemlerini çağırır:</span><span class="sxs-lookup"><span data-stu-id="07c9b-146">The <xref:System.GC.WaitForFullGCApproach%2A> and the <xref:System.GC.WaitForFullGCComplete%2A> methods call their respective event-handling user methods when a notification is raised:</span></span>  
  
- `OnFullGCApproachNotify`  
  
     <span data-ttu-id="07c9b-147">Bu yöntem, `RedirectRequests` istek sıraya sunucusunucuya istekleri göndermeyi askıya almak için talimat kullanıcı yöntemi çağırır.</span><span class="sxs-lookup"><span data-stu-id="07c9b-147">This method calls the `RedirectRequests` user method, which instructs the request queuing server to suspend sending requests to the server.</span></span> <span data-ttu-id="07c9b-148">Bu, sınıf düzeyi değişkenini `bAllocate` daha `false` fazla nesne nin ayrılmaması için ayarlayarak simüle edilir.</span><span class="sxs-lookup"><span data-stu-id="07c9b-148">This is simulated by setting the class-level variable `bAllocate` to `false` so that no more objects are allocated.</span></span>  
  
     <span data-ttu-id="07c9b-149">Ardından, `FinishExistingRequests` bekleyen sunucu isteklerini işlemeyi bitirmek için kullanıcı yöntemi çağrılır.</span><span class="sxs-lookup"><span data-stu-id="07c9b-149">Next, the `FinishExistingRequests` user method is called to finish processing the pending server requests.</span></span> <span data-ttu-id="07c9b-150">Bu, koleksiyonun temizlenmesiyle <xref:System.Collections.Generic.List%601> simüle edilir.</span><span class="sxs-lookup"><span data-stu-id="07c9b-150">This is simulated by clearing the <xref:System.Collections.Generic.List%601> collection.</span></span>  
  
     <span data-ttu-id="07c9b-151">Son olarak, iş yükü hafif olduğundan bir çöp toplama neden oldu.</span><span class="sxs-lookup"><span data-stu-id="07c9b-151">Finally, a garbage collection is induced because the workload is light.</span></span>  
  
- `OnFullGCCompleteNotify`  
  
     <span data-ttu-id="07c9b-152">Bu yöntem, sunucu `AcceptRequests` artık tam bir çöp toplama duyarlı olmadığından istekleri kabul devam etmek için kullanıcı yöntemi çağırır.</span><span class="sxs-lookup"><span data-stu-id="07c9b-152">This method calls the user method `AcceptRequests` to resume accepting requests because the server is no longer susceptible to a full garbage collection.</span></span> <span data-ttu-id="07c9b-153">Bu eylem, nesnelerin `bAllocate` `true` <xref:System.Collections.Generic.List%601> koleksiyona eklenmeye devam edilebilmeleri için değişkeni ayarlayarak simüle edilir.</span><span class="sxs-lookup"><span data-stu-id="07c9b-153">This action is simulated by setting the `bAllocate` variable to `true` so that objects can resume being added to the <xref:System.Collections.Generic.List%601> collection.</span></span>  
  
 <span data-ttu-id="07c9b-154">Aşağıdaki kod, `Main` örneğin yöntemini içerir.</span><span class="sxs-lookup"><span data-stu-id="07c9b-154">The following code contains the `Main` method of the example.</span></span>  
  
 [!code-cpp[GCNotification#2](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#2)]
 [!code-csharp[GCNotification#2](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#2)]
 [!code-vb[GCNotification#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#2)]  
  
 <span data-ttu-id="07c9b-155">Aşağıdaki kod, `WaitForFullGCProc` çöp toplama bildirimlerini denetlemek için sürekli bir süre döngüsü içeren kullanıcı yöntemini içerir.</span><span class="sxs-lookup"><span data-stu-id="07c9b-155">The following code contains the `WaitForFullGCProc` user method, that contains a continuous while loop to check for garbage collection notifications.</span></span>  
  
 [!code-cpp[GCNotification#8](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#8)]
 [!code-csharp[GCNotification#8](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#8)]
 [!code-vb[GCNotification#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#8)]  
  
 <span data-ttu-id="07c9b-156">Aşağıdaki kod, `OnFullGCApproachNotify`</span><span class="sxs-lookup"><span data-stu-id="07c9b-156">The following code contains the `OnFullGCApproachNotify` method as called from the</span></span>  
  
 <span data-ttu-id="07c9b-157">`WaitForFullGCProc`Yöntem.</span><span class="sxs-lookup"><span data-stu-id="07c9b-157">`WaitForFullGCProc` method.</span></span>  
  
 [!code-cpp[GCNotification#5](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#5)]
 [!code-csharp[GCNotification#5](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#5)]
 [!code-vb[GCNotification#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#5)]  
  
 <span data-ttu-id="07c9b-158">Aşağıdaki kod, `OnFullGCApproachComplete`</span><span class="sxs-lookup"><span data-stu-id="07c9b-158">The following code contains the `OnFullGCApproachComplete` method as called from the</span></span>  
  
 <span data-ttu-id="07c9b-159">`WaitForFullGCProc`Yöntem.</span><span class="sxs-lookup"><span data-stu-id="07c9b-159">`WaitForFullGCProc` method.</span></span>  
  
 [!code-cpp[GCNotification#6](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#6)]
 [!code-csharp[GCNotification#6](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#6)]
 [!code-vb[GCNotification#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#6)]  
  
 <span data-ttu-id="07c9b-160">Aşağıdaki kod, yöntem ve `OnFullGCApproachNotify` `OnFullGCCompleteNotify` yöntemden çağrılan kullanıcı yöntemlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="07c9b-160">The following code contains the user methods that are called from the `OnFullGCApproachNotify` and `OnFullGCCompleteNotify` methods.</span></span> <span data-ttu-id="07c9b-161">Kullanıcı yöntemleri istekleri yeniden yönlendirir, varolan istekleri ni tamamlar ve tam bir çöp toplama oluştuktan sonra istekleri devam ettirin.</span><span class="sxs-lookup"><span data-stu-id="07c9b-161">The user methods redirect requests, finish existing requests, and then resume requests after a full garbage collection has occurred.</span></span>  
  
 [!code-cpp[GCNotification#9](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#9)]
 [!code-csharp[GCNotification#9](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#9)]
 [!code-vb[GCNotification#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#9)]  
  
 <span data-ttu-id="07c9b-162">Kod örneğinin tamamı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="07c9b-162">The entire code sample is as follows:</span></span>  
  
 [!code-cpp[GCNotification#1](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#1)]
 [!code-csharp[GCNotification#1](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#1)]
 [!code-vb[GCNotification#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="07c9b-163">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="07c9b-163">See also</span></span>

- [<span data-ttu-id="07c9b-164">Çöp Toplama</span><span class="sxs-lookup"><span data-stu-id="07c9b-164">Garbage Collection</span></span>](../../../docs/standard/garbage-collection/index.md)
