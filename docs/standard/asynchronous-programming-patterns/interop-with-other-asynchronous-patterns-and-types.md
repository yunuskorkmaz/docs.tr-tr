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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c92725a43e43877488ff9ba93007530c794dd290
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33571104"
---
# <a name="interop-with-other-asynchronous-patterns-and-types"></a><span data-ttu-id="305f3-102">Diğer Zaman Uyumsuz Desen ve Türlerle Birlikte Çalışma</span><span class="sxs-lookup"><span data-stu-id="305f3-102">Interop with Other Asynchronous Patterns and Types</span></span>
<span data-ttu-id="305f3-103">.NET Framework 1.0 sunulan <xref:System.IAsyncResult> düzeni, aksi takdirde olarak bilinen [zaman uyumsuz programlama modeli (APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md), veya `Begin/End` düzeni.</span><span class="sxs-lookup"><span data-stu-id="305f3-103">The .NET Framework 1.0 introduced the <xref:System.IAsyncResult> pattern, otherwise known as the [Asynchronous Programming Model (APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md), or the `Begin/End` pattern.</span></span>  <span data-ttu-id="305f3-104">.NET Framework 2.0 eklenen [olay tabanlı zaman uyumsuz desen (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md).</span><span class="sxs-lookup"><span data-stu-id="305f3-104">The .NET Framework 2.0 added the [Event-based Asynchronous Pattern (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md).</span></span>  <span data-ttu-id="305f3-105">.NET Framework 4'ile başlayan [görev tabanlı zaman uyumsuz desen (TAP)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) APM ve EAP yerini alır, ancak kolayca geçiş yordamları önceki model oluşturma yeteneği sağlar.</span><span class="sxs-lookup"><span data-stu-id="305f3-105">Starting with the .NET Framework 4, the [Task-based Asynchronous Pattern (TAP)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) supersedes both APM and EAP, but provides the ability to easily build migration routines from the earlier patterns.</span></span>  
  
 <span data-ttu-id="305f3-106">Bu konuda:</span><span class="sxs-lookup"><span data-stu-id="305f3-106">In this topic:</span></span>  
  
-   <span data-ttu-id="305f3-107">[Görevler ve APM](#APM) ([DOKUNUN APM gelen](#ApmToTap) veya [APM DOKUNUN gelen](#TapToApm))</span><span class="sxs-lookup"><span data-stu-id="305f3-107">[Tasks and APM](#APM) ([from APM to TAP](#ApmToTap) or [from TAP to APM](#TapToApm))</span></span>  
  
-   [<span data-ttu-id="305f3-108">Görevleri ve EAP</span><span class="sxs-lookup"><span data-stu-id="305f3-108">Tasks and EAP</span></span>](#EAP)  
  
-   <span data-ttu-id="305f3-109">[Görevler ve bekleme tanıtıcıları](#WaitHandles) ([DOKUNUN bekleme tanıtıcıları gelen](#WHToTap) veya [bekleme tanıtıcıları için DOKUNUN gelen](#TapToWH))</span><span class="sxs-lookup"><span data-stu-id="305f3-109">[Tasks and wait handles](#WaitHandles) ([from wait handles to TAP](#WHToTap) or [from TAP to wait handles](#TapToWH))</span></span>  
  
<a name="APM"></a>   
## <a name="tasks-and-the-asynchronous-programming-model-apm"></a><span data-ttu-id="305f3-110">Görevler ve zaman uyumsuz programlama modeli (APM)</span><span class="sxs-lookup"><span data-stu-id="305f3-110">Tasks and the Asynchronous Programming Model (APM)</span></span>  
  
<a name="ApmToTap"></a>   
### <a name="from-apm-to-tap"></a><span data-ttu-id="305f3-111">APM için DOKUNUN</span><span class="sxs-lookup"><span data-stu-id="305f3-111">From APM to TAP</span></span>  
 <span data-ttu-id="305f3-112">Çünkü [zaman uyumsuz programlama modeli (APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md) düzeni çok yapılandırılmış, APM uygulaması DOKUNUN uygulaması olarak kullanıma sunmak için bir kapsayıcı oluşturmak oldukça kolaydır.</span><span class="sxs-lookup"><span data-stu-id="305f3-112">Because the [Asynchronous Programming Model (APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md) pattern is very structured, it is quite easy to build a wrapper to expose an APM implementation as a TAP implementation.</span></span> <span data-ttu-id="305f3-113">Aslında .NET Framework ile başlayarak, [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], biçiminde Yardımcısı yordamları içerir <xref:System.Threading.Tasks.TaskFactory.FromAsync%2A> yöntemi aşırı bu çeviri sağlamak için.</span><span class="sxs-lookup"><span data-stu-id="305f3-113">In fact, the .NET Framework, starting with [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], includes helper routines in the form of <xref:System.Threading.Tasks.TaskFactory.FromAsync%2A> method overloads to provide this translation.</span></span>  
  
 <span data-ttu-id="305f3-114">Göz önünde bulundurun <xref:System.IO.Stream> sınıfı ve onun <xref:System.IO.Stream.BeginRead%2A> ve <xref:System.IO.Stream.EndRead%2A> APM karşılık gelen göstermek için zaman uyumlu yöntemleri <xref:System.IO.Stream.Read%2A> yöntemi:</span><span class="sxs-lookup"><span data-stu-id="305f3-114">Consider the <xref:System.IO.Stream> class and its <xref:System.IO.Stream.BeginRead%2A> and <xref:System.IO.Stream.EndRead%2A> methods, which represent the APM counterpart to the synchronous <xref:System.IO.Stream.Read%2A> method:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Stream1.cs#1)]
 [!code-vb[Conceptual.AsyncInterop#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/stream1.vb#1)]  
[!code-csharp[Conceptual.AsyncInterop#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Stream1.cs#2)]
[!code-vb[Conceptual.AsyncInterop#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/stream1.vb#2)]  
[!code-csharp[Conceptual.AsyncInterop#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Stream1.cs#3)]
[!code-vb[Conceptual.AsyncInterop#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/stream1.vb#3)]  
  
 <span data-ttu-id="305f3-115">Kullanabileceğiniz <xref:System.Threading.Tasks.TaskFactory%601.FromAsync%2A?displayProperty=nameWithType> yöntemi bu işlem için DOKUNUN sarmalayıcı aşağıdaki gibi gerçekleştirin:</span><span class="sxs-lookup"><span data-stu-id="305f3-115">You can use the <xref:System.Threading.Tasks.TaskFactory%601.FromAsync%2A?displayProperty=nameWithType> method to implement a TAP wrapper for this operation as follows:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wrap1.cs#4)]
 [!code-vb[Conceptual.AsyncInterop#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wrap1.vb#4)]  
  
 <span data-ttu-id="305f3-116">Bu uygulama aşağıdakine benzer:</span><span class="sxs-lookup"><span data-stu-id="305f3-116">This implementation is similar to the following:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wrap2.cs#5)]
 [!code-vb[Conceptual.AsyncInterop#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wrap2.vb#5)]  
  
<a name="TapToApm"></a>   
### <a name="from-tap-to-apm"></a><span data-ttu-id="305f3-117">APM için DOKUNUN</span><span class="sxs-lookup"><span data-stu-id="305f3-117">From TAP to APM</span></span>  
 <span data-ttu-id="305f3-118">Mevcut altyapınızı APM düzeni görüyorsa de DOKUNUN uygulama alabilir ve APM uygulaması beklenirken kullanmak istersiniz.</span><span class="sxs-lookup"><span data-stu-id="305f3-118">If your existing infrastructure expects the APM pattern, you'll also want to take a TAP implementation and use it where an APM implementation is expected.</span></span>  <span data-ttu-id="305f3-119">Görevler oluşturulabildikleri için ve <xref:System.Threading.Tasks.Task> sınıfı <xref:System.IAsyncResult> arabirimini uyguladığı için, bunu yapmak amacıyla daha basit bir yardımcı işlev kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="305f3-119">Because tasks can be composed and  the <xref:System.Threading.Tasks.Task> class implements <xref:System.IAsyncResult>, you can use a straightforward helper function to do this.</span></span> <span data-ttu-id="305f3-120">Aşağıdaki kod uzantısı kullanır <xref:System.Threading.Tasks.Task%601> sınıfı, ancak kullanabileceğiniz neredeyse aynı işlevi için genel olmayan görevleri.</span><span class="sxs-lookup"><span data-stu-id="305f3-120">The following code uses an extension of the <xref:System.Threading.Tasks.Task%601> class, but you can use an almost identical function for non-generic tasks.</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#6](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM1.cs#6)]
 [!code-vb[Conceptual.AsyncInterop#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM1.vb#6)]  
  
 <span data-ttu-id="305f3-121">Şimdi, aşağıdaki DOKUNUN uygulamaya sahip olduğu bir durum düşünün:</span><span class="sxs-lookup"><span data-stu-id="305f3-121">Now, consider a case where you have the following TAP implementation:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM2.cs#7)]
 [!code-vb[Conceptual.AsyncInterop#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM2.vb#7)]  
  
 <span data-ttu-id="305f3-122">ve bu APM uygulamasını sağlamak istiyorsanız:</span><span class="sxs-lookup"><span data-stu-id="305f3-122">and you want to provide this APM implementation:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#8](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM2.cs#8)]
 [!code-vb[Conceptual.AsyncInterop#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM2.vb#8)]  
[!code-csharp[Conceptual.AsyncInterop#9](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM2.cs#9)]
[!code-vb[Conceptual.AsyncInterop#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM2.vb#9)]  
  
 <span data-ttu-id="305f3-123">Aşağıdaki örnek, bir geçiş APM gösterir:</span><span class="sxs-lookup"><span data-stu-id="305f3-123">The following example demonstrates one migration to APM:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#10](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM2.cs#10)]
 [!code-vb[Conceptual.AsyncInterop#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM2.vb#10)]  
  
<a name="EAP"></a>   
## <a name="tasks-and-the-event-based-asynchronous-pattern-eap"></a><span data-ttu-id="305f3-124">Görevleri ve olay tabanlı zaman uyumsuz desen (EAP)</span><span class="sxs-lookup"><span data-stu-id="305f3-124">Tasks and the Event-based Asynchronous Pattern (EAP)</span></span>  
 <span data-ttu-id="305f3-125">Kaydırma bir [olay tabanlı zaman uyumsuz desen (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md) uygulamasıdır bir APM desen kaydırma değerinden daha karmaşık olduğu EAP düzeni daha fazla değişim ve APM düzeni daha az yapısı.</span><span class="sxs-lookup"><span data-stu-id="305f3-125">Wrapping an [Event-based Asynchronous Pattern (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md) implementation is more involved than wrapping an APM pattern, because the EAP pattern has more variation and less structure than the APM pattern.</span></span>  <span data-ttu-id="305f3-126">Göstermek için aşağıdaki kodu sarmalar `DownloadStringAsync` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="305f3-126">To demonstrate, the following code wraps the `DownloadStringAsync` method.</span></span>  <span data-ttu-id="305f3-127">`DownloadStringAsync` bir URI kabul eder, başlatır `DownloadProgressChanged` ilerleme ve başlatır birden çok istatistikleri rapor için indirilirken olay `DownloadStringCompleted` doldurduktan olay.</span><span class="sxs-lookup"><span data-stu-id="305f3-127">`DownloadStringAsync` accepts a URI, raises the `DownloadProgressChanged` event while downloading in order to report multiple statistics on progress, and raises the `DownloadStringCompleted` event when it's done.</span></span>  <span data-ttu-id="305f3-128">Nihai sonucu belirtilen URI sayfanın içeriğini içeren bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="305f3-128">The final result is a string that contains the contents of the page at the specified URI.</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#11](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/EAP1.cs#11)]
 [!code-vb[Conceptual.AsyncInterop#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/EAP1.vb#11)]  
  
<a name="WaitHandles"></a>   
## <a name="tasks-and-wait-handles"></a><span data-ttu-id="305f3-129">Görevleri ve bekleme tanıtıcıları</span><span class="sxs-lookup"><span data-stu-id="305f3-129">Tasks and Wait Handles</span></span>  
  
<a name="WHToTap"></a>   
### <a name="from-wait-handles-to-tap"></a><span data-ttu-id="305f3-130">Bekleme işleyicilerine DOKUNUN</span><span class="sxs-lookup"><span data-stu-id="305f3-130">From Wait Handles to TAP</span></span>  
 <span data-ttu-id="305f3-131">Bekleme tanıtıcıları bir zaman uyumsuz desen uygulamayan rağmen Gelişmiş geliştiriciler kullanabilir <xref:System.Threading.WaitHandle> sınıfı ve <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A?displayProperty=nameWithType> bekleme tanıtıcısı ayarlandığında zaman uyumsuz bildirimleri için yöntem.</span><span class="sxs-lookup"><span data-stu-id="305f3-131">Although wait handles don't implement an asynchronous pattern, advanced developers may use the <xref:System.Threading.WaitHandle> class and the <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A?displayProperty=nameWithType> method for asynchronous notifications when a wait handle is set.</span></span>  <span data-ttu-id="305f3-132">Kayabilir <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A> yöntemi zaman uyumlu herhangi bir bekleme tanıtıcısı bekleme görev tabanlı bir alternatifi etkinleştirmek için:</span><span class="sxs-lookup"><span data-stu-id="305f3-132">You can wrap the <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A> method to enable a task-based alternative to any synchronous wait on a wait handle:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#12](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wait1.cs#12)]
 [!code-vb[Conceptual.AsyncInterop#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wait1.vb#12)]  
  
 <span data-ttu-id="305f3-133">Bu yöntemle varolan kullanabileceğiniz <xref:System.Threading.WaitHandle> zaman uyumsuz yöntemleri uygulamalarında.</span><span class="sxs-lookup"><span data-stu-id="305f3-133">With this method, you can use existing <xref:System.Threading.WaitHandle> implementations in asynchronous methods.</span></span>  <span data-ttu-id="305f3-134">Örneğin, belirli bir zamanda yürütme zaman uyumsuz işlemleri sayısını azaltma istiyorsanız, bir semafor kullanabilirler (bir <xref:System.Threading.SemaphoreSlim?displayProperty=nameWithType> nesnesi).</span><span class="sxs-lookup"><span data-stu-id="305f3-134">For example, if you want to throttle the number of asynchronous operations that are executing at any particular time, you can utilize a semaphore (a <xref:System.Threading.SemaphoreSlim?displayProperty=nameWithType> object).</span></span>  <span data-ttu-id="305f3-135">İçin daraltabilir *N* eşzamanlı olarak çalışan işlem sayısı için semafor 's sayısı başlatma tarafından *N*semafor üzerinde bir işlemi gerçekleştirmek için istediğiniz zaman bekleyen ve serbest bırakma bir işlem bittiğinde semafor:</span><span class="sxs-lookup"><span data-stu-id="305f3-135">You can throttle to *N* the number of operations that run concurrently by initializing the semaphore’s count to *N*, waiting on the semaphore any time you want to perform an operation, and releasing the semaphore when you’re done with an operation:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#13](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Semaphore1.cs#13)]
 [!code-vb[Conceptual.AsyncInterop#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Semaphore1.vb#13)]  
  
 <span data-ttu-id="305f3-136">Bekleme tanıtıcıları bağlı değildir ve bunun yerine görevlerle tam çalışır bir zaman uyumsuz semafor de oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="305f3-136">You can also build an asynchronous semaphore that does not rely on wait handles and instead works completely with tasks.</span></span> <span data-ttu-id="305f3-137">Bunu yapmak için bu bölümünde açıklandığı gibi teknikler kullanabilirsiniz [görev tabanlı zaman uyumsuz desen kullanma](../../../docs/standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md) üstünde veri yapılarını oluşturmak için <xref:System.Threading.Tasks.Task>.</span><span class="sxs-lookup"><span data-stu-id="305f3-137">To do this, you can use techniques such as those discussed in [Consuming the Task-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md) for building data structures on top of <xref:System.Threading.Tasks.Task>.</span></span>  
  
<a name="TapToWH"></a>   
### <a name="from-tap-to-wait-handles"></a><span data-ttu-id="305f3-138">Bekleme tanıtıcıları için DOKUNUN</span><span class="sxs-lookup"><span data-stu-id="305f3-138">From TAP to Wait Handles</span></span>  
 <span data-ttu-id="305f3-139">Daha önce belirtildiği gibi <xref:System.Threading.Tasks.Task> sınıfını uygular <xref:System.IAsyncResult>, ve o uygulama sunan bir <xref:System.Threading.Tasks.Task.System%23IAsyncResult%23AsyncWaitHandle%2A> ne zaman ayarlanacak bir bekleme tanıtıcısı döndüren özelliği <xref:System.Threading.Tasks.Task> tamamlar.</span><span class="sxs-lookup"><span data-stu-id="305f3-139">As previously mentioned, the <xref:System.Threading.Tasks.Task> class implements <xref:System.IAsyncResult>, and that implementation exposes an <xref:System.Threading.Tasks.Task.System%23IAsyncResult%23AsyncWaitHandle%2A> property that returns a wait handle that will be set when the <xref:System.Threading.Tasks.Task> completes.</span></span>  <span data-ttu-id="305f3-140">Alabileceğiniz bir <xref:System.Threading.WaitHandle> için bir <xref:System.Threading.Tasks.Task> gibi:</span><span class="sxs-lookup"><span data-stu-id="305f3-140">You can get a <xref:System.Threading.WaitHandle> for a <xref:System.Threading.Tasks.Task> as follows:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#14](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wait1.cs#14)]
 [!code-vb[Conceptual.AsyncInterop#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wait1.vb#14)]  
  
## <a name="see-also"></a><span data-ttu-id="305f3-141">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="305f3-141">See Also</span></span>  
 [<span data-ttu-id="305f3-142">Görev Tabanlı Zaman Uyumsuz Desen (TAP)</span><span class="sxs-lookup"><span data-stu-id="305f3-142">Task-based Asynchronous Pattern (TAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)  
 [<span data-ttu-id="305f3-143">Görev Tabanlı Zaman Uyumsuz Deseni Uygulama</span><span class="sxs-lookup"><span data-stu-id="305f3-143">Implementing the Task-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/implementing-the-task-based-asynchronous-pattern.md)  
 [<span data-ttu-id="305f3-144">Görev Tabanlı Zaman Uyumsuz Desen Kullanma</span><span class="sxs-lookup"><span data-stu-id="305f3-144">Consuming the Task-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md)
