---
title: Diğer Zaman Uyumsuz Desen ve Türlerle Birlikte Çalışma
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- .NET Framework, and TAP
- asynchronous design patterns, .NET Framework
- TAP, .NET Framework support for
- Task-based Asynchronous Pattern, .NET Framework support for
- .NET Framework, asynchronous design patterns
ms.assetid: f120a5d9-933b-4d1d-acb6-f034a57c3749
ms.openlocfilehash: 981c13c68eaf1eb0c19f95eb1b097935ea02a16d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78159760"
---
# <a name="interop-with-other-asynchronous-patterns-and-types"></a><span data-ttu-id="9b27d-102">Diğer Zaman Uyumsuz Desen ve Türlerle Birlikte Çalışma</span><span class="sxs-lookup"><span data-stu-id="9b27d-102">Interop with Other Asynchronous Patterns and Types</span></span>
<span data-ttu-id="9b27d-103">.NET Framework 1.0, <xref:System.IAsyncResult> aksi takdirde [Asynchronous Programming Model (APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md)veya `Begin/End` desen olarak bilinen desen tanıttı.</span><span class="sxs-lookup"><span data-stu-id="9b27d-103">The .NET Framework 1.0 introduced the <xref:System.IAsyncResult> pattern, otherwise known as the [Asynchronous Programming Model (APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md), or the `Begin/End` pattern.</span></span>  <span data-ttu-id="9b27d-104">.NET Framework 2.0 [Olay tabanlı Eşzamanlı Desen (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)eklendi.</span><span class="sxs-lookup"><span data-stu-id="9b27d-104">The .NET Framework 2.0 added the [Event-based Asynchronous Pattern (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md).</span></span>  <span data-ttu-id="9b27d-105">.NET Framework 4'ten başlayarak, [Görev tabanlı Eşzamanlı Desen (TAP)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) hem APM hem de EAP'nin yerini alır, ancak önceki desenlerden geçiş yordamları oluşturma olanağı sağlar.</span><span class="sxs-lookup"><span data-stu-id="9b27d-105">Starting with the .NET Framework 4, the [Task-based Asynchronous Pattern (TAP)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) supersedes both APM and EAP, but provides the ability to easily build migration routines from the earlier patterns.</span></span>  
  
 <span data-ttu-id="9b27d-106">Bu konuda:</span><span class="sxs-lookup"><span data-stu-id="9b27d-106">In this topic:</span></span>  
  
- <span data-ttu-id="9b27d-107">[Görevler ve APM](#APM) [(APM'den TAP'a](#ApmToTap) veya [TAP'ten APM'ye](#TapToApm))</span><span class="sxs-lookup"><span data-stu-id="9b27d-107">[Tasks and APM](#APM) ([from APM to TAP](#ApmToTap) or [from TAP to APM](#TapToApm))</span></span>  
  
- [<span data-ttu-id="9b27d-108">Görevler ve EAP</span><span class="sxs-lookup"><span data-stu-id="9b27d-108">Tasks and EAP</span></span>](#EAP)  
  
- <span data-ttu-id="9b27d-109">[Görevler ve bekleme tutamaçları](#WaitHandles) [(bekleme tutamaçlarından TAP'a](#WHToTap) veya [TAP'tan bekleme tutamaçlarına](#TapToWH)kadar)</span><span class="sxs-lookup"><span data-stu-id="9b27d-109">[Tasks and wait handles](#WaitHandles) ([from wait handles to TAP](#WHToTap) or [from TAP to wait handles](#TapToWH))</span></span>  
  
<a name="APM"></a>
## <a name="tasks-and-the-asynchronous-programming-model-apm"></a><span data-ttu-id="9b27d-110">Görevler ve Eşzamanlı Programlama Modeli (APM)</span><span class="sxs-lookup"><span data-stu-id="9b27d-110">Tasks and the Asynchronous Programming Model (APM)</span></span>  
  
<a name="ApmToTap"></a>
### <a name="from-apm-to-tap"></a><span data-ttu-id="9b27d-111">APM'den TAP'a</span><span class="sxs-lookup"><span data-stu-id="9b27d-111">From APM to TAP</span></span>  
 <span data-ttu-id="9b27d-112">[Asynchronous Programming Model (APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md) deseni çok yapılandırılmış olduğundan, bir Tap uygulaması olarak bir APM uygulamasını ortaya çıkarmak için bir sarmalayıcı oluşturmak oldukça kolaydır.</span><span class="sxs-lookup"><span data-stu-id="9b27d-112">Because the [Asynchronous Programming Model (APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md) pattern is very structured, it is quite easy to build a wrapper to expose an APM implementation as a TAP implementation.</span></span> <span data-ttu-id="9b27d-113">Aslında,.NET Framework 4 ile başlayan .NET Framework, bu çeviriyi <xref:System.Threading.Tasks.TaskFactory.FromAsync%2A> sağlamak için aşırı yükleme yöntemi biçiminde yardımcı yordamlar içerir.</span><span class="sxs-lookup"><span data-stu-id="9b27d-113">In fact, the .NET Framework, starting with .NET Framework 4, includes helper routines in the form of <xref:System.Threading.Tasks.TaskFactory.FromAsync%2A> method overloads to provide this translation.</span></span>  
  
 <span data-ttu-id="9b27d-114">Senkron <xref:System.IO.Stream> <xref:System.IO.Stream.Read%2A> yönteme <xref:System.IO.Stream.BeginRead%2A> <xref:System.IO.Stream.EndRead%2A> APM karşıtlığını temsil eden sınıfı ve yöntemlerini göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="9b27d-114">Consider the <xref:System.IO.Stream> class and its <xref:System.IO.Stream.BeginRead%2A> and <xref:System.IO.Stream.EndRead%2A> methods, which represent the APM counterpart to the synchronous <xref:System.IO.Stream.Read%2A> method:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Stream1.cs#1)]
 [!code-vb[Conceptual.AsyncInterop#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/stream1.vb#1)]  
[!code-csharp[Conceptual.AsyncInterop#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Stream1.cs#2)]
[!code-vb[Conceptual.AsyncInterop#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/stream1.vb#2)]  
[!code-csharp[Conceptual.AsyncInterop#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Stream1.cs#3)]
[!code-vb[Conceptual.AsyncInterop#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/stream1.vb#3)]  
  
 <span data-ttu-id="9b27d-115">Bu işlem <xref:System.Threading.Tasks.TaskFactory%601.FromAsync%2A?displayProperty=nameWithType> için tap sarıcıyı uygulamak için yöntemi aşağıdaki gibi kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="9b27d-115">You can use the <xref:System.Threading.Tasks.TaskFactory%601.FromAsync%2A?displayProperty=nameWithType> method to implement a TAP wrapper for this operation as follows:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wrap1.cs#4)]
 [!code-vb[Conceptual.AsyncInterop#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wrap1.vb#4)]  
  
 <span data-ttu-id="9b27d-116">Bu uygulama aşağıdakilere benzer:</span><span class="sxs-lookup"><span data-stu-id="9b27d-116">This implementation is similar to the following:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wrap2.cs#5)]
 [!code-vb[Conceptual.AsyncInterop#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wrap2.vb#5)]  
  
<a name="TapToApm"></a>
### <a name="from-tap-to-apm"></a><span data-ttu-id="9b27d-117">TAP'tan APM'ye</span><span class="sxs-lookup"><span data-stu-id="9b27d-117">From TAP to APM</span></span>  
 <span data-ttu-id="9b27d-118">Varolan altyapınız APM deseni bekliyorsa, bir TAP uygulamasını alıp APM uygulamasının beklendiği yerde kullanmak da istersiniz.</span><span class="sxs-lookup"><span data-stu-id="9b27d-118">If your existing infrastructure expects the APM pattern, you'll also want to take a TAP implementation and use it where an APM implementation is expected.</span></span>  <span data-ttu-id="9b27d-119">Görevler oluşturulabildikleri için ve <xref:System.Threading.Tasks.Task> sınıfı <xref:System.IAsyncResult> arabirimini uyguladığı için, bunu yapmak amacıyla daha basit bir yardımcı işlev kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9b27d-119">Because tasks can be composed and  the <xref:System.Threading.Tasks.Task> class implements <xref:System.IAsyncResult>, you can use a straightforward helper function to do this.</span></span> <span data-ttu-id="9b27d-120">Aşağıdaki kod sınıfın bir <xref:System.Threading.Tasks.Task%601> uzantısı kullanır, ancak genel olmayan görevler için hemen hemen aynı işlevi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9b27d-120">The following code uses an extension of the <xref:System.Threading.Tasks.Task%601> class, but you can use an almost identical function for non-generic tasks.</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#6](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM1.cs#6)]
 [!code-vb[Conceptual.AsyncInterop#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM1.vb#6)]  
  
 <span data-ttu-id="9b27d-121">Şimdi, aşağıdaki TAP uygulamasına sahip olduğunuz bir durumu düşünün:</span><span class="sxs-lookup"><span data-stu-id="9b27d-121">Now, consider a case where you have the following TAP implementation:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM2.cs#7)]
 [!code-vb[Conceptual.AsyncInterop#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM2.vb#7)]  
  
 <span data-ttu-id="9b27d-122">ve bu APM uygulamasını sağlamak istiyorsunuz:</span><span class="sxs-lookup"><span data-stu-id="9b27d-122">and you want to provide this APM implementation:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#8](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM2.cs#8)]
 [!code-vb[Conceptual.AsyncInterop#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM2.vb#8)]  
[!code-csharp[Conceptual.AsyncInterop#9](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM2.cs#9)]
[!code-vb[Conceptual.AsyncInterop#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM2.vb#9)]  
  
 <span data-ttu-id="9b27d-123">Aşağıdaki örnek, APM'ye bir geçişi gösterir:</span><span class="sxs-lookup"><span data-stu-id="9b27d-123">The following example demonstrates one migration to APM:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#10](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM2.cs#10)]
 [!code-vb[Conceptual.AsyncInterop#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM2.vb#10)]  
  
<a name="EAP"></a>
## <a name="tasks-and-the-event-based-asynchronous-pattern-eap"></a><span data-ttu-id="9b27d-124">Görevler ve Olay Tabanlı Eşzamanlı Desen (EAP)</span><span class="sxs-lookup"><span data-stu-id="9b27d-124">Tasks and the Event-based Asynchronous Pattern (EAP)</span></span>  
 <span data-ttu-id="9b27d-125">Olay [tabanlı Bir Eşzamanlı Desen (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md) uygulamasını sarma, APM deseni sarmaktan daha fazla ilgilidir, çünkü EAP deseni APM deseninden daha fazla varyasyona ve daha az yapıya sahiptir.</span><span class="sxs-lookup"><span data-stu-id="9b27d-125">Wrapping an [Event-based Asynchronous Pattern (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md) implementation is more involved than wrapping an APM pattern, because the EAP pattern has more variation and less structure than the APM pattern.</span></span>  <span data-ttu-id="9b27d-126">Göstermek için, aşağıdaki kod `DownloadStringAsync` yöntemi sarar.</span><span class="sxs-lookup"><span data-stu-id="9b27d-126">To demonstrate, the following code wraps the `DownloadStringAsync` method.</span></span>  <span data-ttu-id="9b27d-127">`DownloadStringAsync`bir URI kabul eder, ilerleme yle `DownloadProgressChanged` ilgili birden çok istatistik bildirmek `DownloadStringCompleted` için indirirken olayı yükseltir ve bittiğinde olayı yükseltir.</span><span class="sxs-lookup"><span data-stu-id="9b27d-127">`DownloadStringAsync` accepts a URI, raises the `DownloadProgressChanged` event while downloading in order to report multiple statistics on progress, and raises the `DownloadStringCompleted` event when it's done.</span></span>  <span data-ttu-id="9b27d-128">Nihai sonuç, belirtilen URI'deki sayfanın içeriğini içeren bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="9b27d-128">The final result is a string that contains the contents of the page at the specified URI.</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#11](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/EAP1.cs#11)]
 [!code-vb[Conceptual.AsyncInterop#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/EAP1.vb#11)]  
  
<a name="WaitHandles"></a>
## <a name="tasks-and-wait-handles"></a><span data-ttu-id="9b27d-129">Görevler ve Bekleme Tutamaçları</span><span class="sxs-lookup"><span data-stu-id="9b27d-129">Tasks and Wait Handles</span></span>  
  
<a name="WHToTap"></a>
### <a name="from-wait-handles-to-tap"></a><span data-ttu-id="9b27d-130">Bekleme Tutamaçları'ndan TAP'a</span><span class="sxs-lookup"><span data-stu-id="9b27d-130">From Wait Handles to TAP</span></span>  
 <span data-ttu-id="9b27d-131">Bekleme tutamaçları eşzamanlı bir desen uygulamasa da, gelişmiş <xref:System.Threading.WaitHandle> geliştiriciler bekleme <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A?displayProperty=nameWithType> tutamacı ayarlandığında sınıfı ve eşzamanlı bildirimler yöntemini kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="9b27d-131">Although wait handles don't implement an asynchronous pattern, advanced developers may use the <xref:System.Threading.WaitHandle> class and the <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A?displayProperty=nameWithType> method for asynchronous notifications when a wait handle is set.</span></span>  <span data-ttu-id="9b27d-132">Bekleme tutamacında <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A> herhangi bir eşzamanlı bekleme ye yönelik görev tabanlı bir alternatifi etkinleştirmek için yöntemi kaydırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="9b27d-132">You can wrap the <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A> method to enable a task-based alternative to any synchronous wait on a wait handle:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#12](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wait1.cs#12)]
 [!code-vb[Conceptual.AsyncInterop#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wait1.vb#12)]  
  
 <span data-ttu-id="9b27d-133">Bu yöntemle, varolan <xref:System.Threading.WaitHandle> uygulamaları eşzamanlı yöntemlerde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9b27d-133">With this method, you can use existing <xref:System.Threading.WaitHandle> implementations in asynchronous methods.</span></span>  <span data-ttu-id="9b27d-134">Örneğin, belirli bir zamanda yürütülen eşzamanlı işlem sayısını daraltmak istiyorsanız, bir semafor (nesne) <xref:System.Threading.SemaphoreSlim?displayProperty=nameWithType> kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9b27d-134">For example, if you want to throttle the number of asynchronous operations that are executing at any particular time, you can utilize a semaphore (a <xref:System.Threading.SemaphoreSlim?displayProperty=nameWithType> object).</span></span>  <span data-ttu-id="9b27d-135">Semafor sayısını *N'ye*başlayarak aynı anda çalışan işlem sayısını *N'ye* daraltabilir, bir işlemi gerçekleştirmek istediğinizde semaforu bekleyebilir ve bir işlemle bitirdiğinizde semaforu serbest bırakabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="9b27d-135">You can throttle to *N* the number of operations that run concurrently by initializing the semaphore’s count to *N*, waiting on the semaphore any time you want to perform an operation, and releasing the semaphore when you’re done with an operation:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#13](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Semaphore1.cs#13)]
 [!code-vb[Conceptual.AsyncInterop#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Semaphore1.vb#13)]  
  
 <span data-ttu-id="9b27d-136">Ayrıca bekleme kolları güvenmez ve bunun yerine görevleri tamamen çalışır bir eşzamanlı semafor oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9b27d-136">You can also build an asynchronous semaphore that does not rely on wait handles and instead works completely with tasks.</span></span> <span data-ttu-id="9b27d-137">Bunu yapmak için, 'nin üstüne veri yapıları oluşturmak için [Görev Tabanlı Asynchronous Deseni'ni Tüketme'de](../../../docs/standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md) tartışılanlar gibi teknikler <xref:System.Threading.Tasks.Task>kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9b27d-137">To do this, you can use techniques such as those discussed in [Consuming the Task-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md) for building data structures on top of <xref:System.Threading.Tasks.Task>.</span></span>  
  
<a name="TapToWH"></a>
### <a name="from-tap-to-wait-handles"></a><span data-ttu-id="9b27d-138">TAP'tan Bekleme Tutamaçlarına</span><span class="sxs-lookup"><span data-stu-id="9b27d-138">From TAP to Wait Handles</span></span>  
 <span data-ttu-id="9b27d-139">Daha önce de belirtildiği <xref:System.Threading.Tasks.Task> gibi, <xref:System.IAsyncResult>sınıf uygular ve <xref:System.Threading.Tasks.Task.System%23IAsyncResult%23AsyncWaitHandle%2A> bu uygulama <xref:System.Threading.Tasks.Task> tamamlandığında ayarlanacak bir bekleme tutamacı döndüren bir özellik ortaya çıkarır.</span><span class="sxs-lookup"><span data-stu-id="9b27d-139">As previously mentioned, the <xref:System.Threading.Tasks.Task> class implements <xref:System.IAsyncResult>, and that implementation exposes an <xref:System.Threading.Tasks.Task.System%23IAsyncResult%23AsyncWaitHandle%2A> property that returns a wait handle that will be set when the <xref:System.Threading.Tasks.Task> completes.</span></span>  <span data-ttu-id="9b27d-140">Aşağıdaki gibi <xref:System.Threading.WaitHandle> bir <xref:System.Threading.Tasks.Task> a alabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="9b27d-140">You can get a <xref:System.Threading.WaitHandle> for a <xref:System.Threading.Tasks.Task> as follows:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#14](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wait1.cs#14)]
 [!code-vb[Conceptual.AsyncInterop#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wait1.vb#14)]  
  
## <a name="see-also"></a><span data-ttu-id="9b27d-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9b27d-141">See also</span></span>

- [<span data-ttu-id="9b27d-142">Görev Tabanlı Zaman Uyumsuz Desen (TAP)</span><span class="sxs-lookup"><span data-stu-id="9b27d-142">Task-based Asynchronous Pattern (TAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)
- [<span data-ttu-id="9b27d-143">Görev Tabanlı Zaman Uyumsuz Deseni Uygulama</span><span class="sxs-lookup"><span data-stu-id="9b27d-143">Implementing the Task-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/implementing-the-task-based-asynchronous-pattern.md)
- [<span data-ttu-id="9b27d-144">Görev Tabanlı Zaman Uyumsuz Desen Kullanma</span><span class="sxs-lookup"><span data-stu-id="9b27d-144">Consuming the Task-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md)
