---
title: CountdownEvent
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- synchronization primitives, CountdownEvent
ms.assetid: eec3812a-e20f-4ecd-bfef-6921d508b708
ms.openlocfilehash: 8ed1414ad377015400d9e126d924bf426fbc753d
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84277862"
---
# <a name="countdownevent"></a><span data-ttu-id="00469-102">CountdownEvent</span><span class="sxs-lookup"><span data-stu-id="00469-102">CountdownEvent</span></span>
<span data-ttu-id="00469-103"><xref:System.Threading.CountdownEvent?displayProperty=nameWithType>, bekleyen iş parçacıklarını belirli sayıda sinyalden sonra engelleyen bir eşitleme temel larıdır.</span><span class="sxs-lookup"><span data-stu-id="00469-103"><xref:System.Threading.CountdownEvent?displayProperty=nameWithType> is a synchronization primitive that unblocks its waiting threads after it has been signaled a certain number of times.</span></span> <span data-ttu-id="00469-104"><xref:System.Threading.CountdownEvent>, aksi takdirde bir veya kullanmanız gereken senaryolar için tasarlanmıştır <xref:System.Threading.ManualResetEvent> <xref:System.Threading.ManualResetEventSlim> ve olayı sinyalden önce bir değişkeni el ile azaltır.</span><span class="sxs-lookup"><span data-stu-id="00469-104"><xref:System.Threading.CountdownEvent> is designed for scenarios in which you would otherwise have to use a <xref:System.Threading.ManualResetEvent> or <xref:System.Threading.ManualResetEventSlim> and manually decrement a variable before signaling the event.</span></span> <span data-ttu-id="00469-105">Örneğin, bir çatal/JOIN senaryosunda, yalnızca <xref:System.Threading.CountdownEvent> 5 numaralı sinyal sayısına sahip bir tane oluşturabilir ve sonra iş parçacığı havuzunda beş iş öğesi başlatabilir ve tamamlandığında her iş öğesi çağrısını yapabilirsiniz <xref:System.Threading.CountdownEvent.Signal%2A> .</span><span class="sxs-lookup"><span data-stu-id="00469-105">For example, in a fork/join scenario, you can just create a <xref:System.Threading.CountdownEvent> that has a signal count of 5, and then start five work items on the thread pool and have each work item call <xref:System.Threading.CountdownEvent.Signal%2A> when it completes.</span></span> <span data-ttu-id="00469-106">Her çağrı <xref:System.Threading.CountdownEvent.Signal%2A> , sinyal sayısını 1 ' i azaltır.</span><span class="sxs-lookup"><span data-stu-id="00469-106">Each call to <xref:System.Threading.CountdownEvent.Signal%2A> decrements the signal count by 1.</span></span> <span data-ttu-id="00469-107">Ana iş parçacığında, çağrısı, <xref:System.Threading.CountdownEvent.Wait%2A> sinyal sayısı sıfır olana kadar engeller.</span><span class="sxs-lookup"><span data-stu-id="00469-107">On the main thread, the call to <xref:System.Threading.CountdownEvent.Wait%2A> will block until the signal count is zero.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="00469-108">Eski .NET Framework eşitleme API 'Leri ile etkileşim kurmak zorunda olmayan kod için, <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> <xref:System.Threading.Tasks.Parallel.Invoke%2A> çatalı birleştiren paralellik ifade etmek için nesneleri veya yöntemi kullanmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="00469-108">For code that does not have to interact with legacy .NET Framework synchronization APIs, consider using <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> objects or the <xref:System.Threading.Tasks.Parallel.Invoke%2A> method for an even easier approach to expressing fork-join parallelism.</span></span>  
  
 <span data-ttu-id="00469-109"><xref:System.Threading.CountdownEvent>Şu ek özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="00469-109"><xref:System.Threading.CountdownEvent> has these additional features:</span></span>  
  
- <span data-ttu-id="00469-110">Bekleme işlemi, iptal belirteçleri kullanılarak iptal edilebilir.</span><span class="sxs-lookup"><span data-stu-id="00469-110">The wait operation can be canceled by using cancellation tokens.</span></span>  
  
- <span data-ttu-id="00469-111">Örnek oluşturulduktan sonra sinyal sayısı arttırılabilirler.</span><span class="sxs-lookup"><span data-stu-id="00469-111">Its signal count can be incremented after the instance is created.</span></span>  
  
- <span data-ttu-id="00469-112">Örnekler <xref:System.Threading.CountdownEvent.Wait%2A> , yöntemi çağırarak döndürülmeden sonra yeniden kullanılabilir <xref:System.Threading.CountdownEvent.Reset%2A> .</span><span class="sxs-lookup"><span data-stu-id="00469-112">Instances can be reused after <xref:System.Threading.CountdownEvent.Wait%2A> has returned by calling the <xref:System.Threading.CountdownEvent.Reset%2A> method.</span></span>  
  
- <span data-ttu-id="00469-113">Örnekler, gibi <xref:System.Threading.WaitHandle> diğer .NET Framework eşitleme API 'leri ile tümleştirme için sunar <xref:System.Threading.WaitHandle.WaitAll%2A> .</span><span class="sxs-lookup"><span data-stu-id="00469-113">Instances expose a <xref:System.Threading.WaitHandle> for integration with other .NET Framework synchronization APIs such as <xref:System.Threading.WaitHandle.WaitAll%2A>.</span></span>  
  
## <a name="basic-usage"></a><span data-ttu-id="00469-114">Temel kullanım</span><span class="sxs-lookup"><span data-stu-id="00469-114">Basic Usage</span></span>  
 <span data-ttu-id="00469-115">Aşağıdaki örnek, <xref:System.Threading.CountdownEvent> ile iş öğelerinin nasıl kullanılacağını göstermektedir <xref:System.Threading.ThreadPool> .</span><span class="sxs-lookup"><span data-stu-id="00469-115">The following example demonstrates how to use a <xref:System.Threading.CountdownEvent> with <xref:System.Threading.ThreadPool> work items.</span></span>  
  
 [!code-csharp[CDS_CountdownEvent#01](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_countdownevent/cs/countdownevent.cs#01)]
 [!code-vb[CDS_CountdownEvent#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_countdownevent/vb/module1.vb#01)]  
  
## <a name="countdownevent-with-cancellation"></a><span data-ttu-id="00469-116">Iptal Ile CountdownEvent</span><span class="sxs-lookup"><span data-stu-id="00469-116">CountdownEvent With Cancellation</span></span>  
 <span data-ttu-id="00469-117">Aşağıdaki örnek, <xref:System.Threading.CountdownEvent> bir iptal belirteci kullanılarak üzerinde bekleme işleminin nasıl iptal edildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="00469-117">The following example shows how to cancel the wait operation on <xref:System.Threading.CountdownEvent> by using a cancellation token.</span></span> <span data-ttu-id="00469-118">Temel model, .NET Framework 4 ' te tanıtılan Birleşik iptal için modeli izler.</span><span class="sxs-lookup"><span data-stu-id="00469-118">The basic pattern follows the model for unified cancellation, which is introduced in .NET Framework 4.</span></span> <span data-ttu-id="00469-119">Daha fazla bilgi için bkz. [yönetilen Iş parçacıklarında iptal](cancellation-in-managed-threads.md).</span><span class="sxs-lookup"><span data-stu-id="00469-119">For more information, see [Cancellation in Managed Threads](cancellation-in-managed-threads.md).</span></span>  
  
 [!code-csharp[CDS_CountdownEvent#02](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_countdownevent/cs/countdownevent.cs#02)]
 [!code-vb[CDS_CountdownEvent#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_countdownevent/vb/canceleventwait.vb#02)]  
  
 <span data-ttu-id="00469-120">Bekleme işleminin sinyal veren iş parçacıklarını iptal etmediğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="00469-120">Note that the wait operation does not cancel the threads that are signaling it.</span></span> <span data-ttu-id="00469-121">Genellikle, iptal, mantıksal bir işleme uygulanır ve bu, olayın ve bekleyen tüm iş öğelerinin de tamamlanmasını içerebilir.</span><span class="sxs-lookup"><span data-stu-id="00469-121">Typically, cancellation is applied to a logical operation, and that can include waiting on the event as well as all the work items that the wait is synchronizing.</span></span> <span data-ttu-id="00469-122">Bu örnekte, her iş öğesi, iptal isteğine yanıt verebilmesi için aynı iptal belirtecinin bir kopyasını geçti.</span><span class="sxs-lookup"><span data-stu-id="00469-122">In this example, each work item is passed a copy of the same cancellation token so that it can respond to the cancellation request.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00469-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="00469-123">See also</span></span>

- <xref:System.Threading.Semaphore?displayProperty=nameWithType>
