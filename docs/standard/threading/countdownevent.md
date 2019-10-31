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
ms.openlocfilehash: 628d6a96606117d447c61d01595d13dd4a957ce4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138117"
---
# <a name="countdownevent"></a><span data-ttu-id="eda9b-102">CountdownEvent</span><span class="sxs-lookup"><span data-stu-id="eda9b-102">CountdownEvent</span></span>
<span data-ttu-id="eda9b-103"><xref:System.Threading.CountdownEvent?displayProperty=nameWithType>, bekleyen iş parçacıklarını belirli sayıda sinyalden sonra engelleyen bir eşitleme temel sayısıdır.</span><span class="sxs-lookup"><span data-stu-id="eda9b-103"><xref:System.Threading.CountdownEvent?displayProperty=nameWithType> is a synchronization primitive that unblocks its waiting threads after it has been signaled a certain number of times.</span></span> <span data-ttu-id="eda9b-104"><xref:System.Threading.CountdownEvent>, başka bir <xref:System.Threading.ManualResetEvent> veya <xref:System.Threading.ManualResetEventSlim> kullanmak zorunda olduğunuz ve olayı sinyalden önce bir değişkeni el ile azaltabileceği senaryolar için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="eda9b-104"><xref:System.Threading.CountdownEvent> is designed for scenarios in which you would otherwise have to use a <xref:System.Threading.ManualResetEvent> or <xref:System.Threading.ManualResetEventSlim> and manually decrement a variable before signaling the event.</span></span> <span data-ttu-id="eda9b-105">Örneğin, bir çatal/JOIN senaryosunda, yalnızca 5 numaralı sinyal sayısına sahip bir <xref:System.Threading.CountdownEvent> oluşturup iş parçacığı havuzunda beş iş öğesi başlatabilir ve her bir iş öğesi çağrısını tamamlandığında <xref:System.Threading.CountdownEvent.Signal%2A> sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="eda9b-105">For example, in a fork/join scenario, you can just create a <xref:System.Threading.CountdownEvent> that has a signal count of 5, and then start five work items on the thread pool and have each work item call <xref:System.Threading.CountdownEvent.Signal%2A> when it completes.</span></span> <span data-ttu-id="eda9b-106"><xref:System.Threading.CountdownEvent.Signal%2A> yapılan her bir çağrı, sinyal sayısını 1 azaltır.</span><span class="sxs-lookup"><span data-stu-id="eda9b-106">Each call to <xref:System.Threading.CountdownEvent.Signal%2A> decrements the signal count by 1.</span></span> <span data-ttu-id="eda9b-107">Ana iş parçacığında, <xref:System.Threading.CountdownEvent.Wait%2A> çağrısı, sinyal sayısı sıfır olana kadar engeller.</span><span class="sxs-lookup"><span data-stu-id="eda9b-107">On the main thread, the call to <xref:System.Threading.CountdownEvent.Wait%2A> will block until the signal count is zero.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="eda9b-108">Eski .NET Framework eşitleme API 'Leri ile etkileşim kurmak zorunda olmayan kod için, çatal birleştiren paralellik belirtme konusunda daha kolay bir yaklaşım için <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> nesneleri veya <xref:System.Threading.Tasks.Parallel.Invoke%2A> metodunu kullanmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="eda9b-108">For code that does not have to interact with legacy .NET Framework synchronization APIs, consider using <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> objects or the <xref:System.Threading.Tasks.Parallel.Invoke%2A> method for an even easier approach to expressing fork-join parallelism.</span></span>  
  
 <span data-ttu-id="eda9b-109"><xref:System.Threading.CountdownEvent> şu ek özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="eda9b-109"><xref:System.Threading.CountdownEvent> has these additional features:</span></span>  
  
- <span data-ttu-id="eda9b-110">Bekleme işlemi, iptal belirteçleri kullanılarak iptal edilebilir.</span><span class="sxs-lookup"><span data-stu-id="eda9b-110">The wait operation can be canceled by using cancellation tokens.</span></span>  
  
- <span data-ttu-id="eda9b-111">Örnek oluşturulduktan sonra sinyal sayısı arttırılabilirler.</span><span class="sxs-lookup"><span data-stu-id="eda9b-111">Its signal count can be incremented after the instance is created.</span></span>  
  
- <span data-ttu-id="eda9b-112">Örnekler, <xref:System.Threading.CountdownEvent.Wait%2A> <xref:System.Threading.CountdownEvent.Reset%2A> yöntemi çağırarak geri alındıktan sonra yeniden kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="eda9b-112">Instances can be reused after <xref:System.Threading.CountdownEvent.Wait%2A> has returned by calling the <xref:System.Threading.CountdownEvent.Reset%2A> method.</span></span>  
  
- <span data-ttu-id="eda9b-113">Örnekler, <xref:System.Threading.WaitHandle.WaitAll%2A>gibi diğer .NET Framework eşitleme API 'Leriyle tümleştirme için <xref:System.Threading.WaitHandle> sunar.</span><span class="sxs-lookup"><span data-stu-id="eda9b-113">Instances expose a <xref:System.Threading.WaitHandle> for integration with other .NET Framework synchronization APIs such as <xref:System.Threading.WaitHandle.WaitAll%2A>.</span></span>  
  
## <a name="basic-usage"></a><span data-ttu-id="eda9b-114">Temel kullanım</span><span class="sxs-lookup"><span data-stu-id="eda9b-114">Basic Usage</span></span>  
 <span data-ttu-id="eda9b-115">Aşağıdaki örnek, <xref:System.Threading.ThreadPool> iş öğeleriyle <xref:System.Threading.CountdownEvent> nasıl kullanacağınızı gösterir.</span><span class="sxs-lookup"><span data-stu-id="eda9b-115">The following example demonstrates how to use a <xref:System.Threading.CountdownEvent> with <xref:System.Threading.ThreadPool> work items.</span></span>  
  
 [!code-csharp[CDS_CountdownEvent#01](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_countdownevent/cs/countdownevent.cs#01)]
 [!code-vb[CDS_CountdownEvent#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_countdownevent/vb/module1.vb#01)]  
  
## <a name="countdownevent-with-cancellation"></a><span data-ttu-id="eda9b-116">Iptal Ile CountdownEvent</span><span class="sxs-lookup"><span data-stu-id="eda9b-116">CountdownEvent With Cancellation</span></span>  
 <span data-ttu-id="eda9b-117">Aşağıdaki örnek, bir iptal belirteci kullanarak <xref:System.Threading.CountdownEvent> bekleme işleminin nasıl iptal edildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="eda9b-117">The following example shows how to cancel the wait operation on <xref:System.Threading.CountdownEvent> by using a cancellation token.</span></span> <span data-ttu-id="eda9b-118">Temel model, .NET Framework 4 ' te tanıtılan Birleşik iptal için modeli izler.</span><span class="sxs-lookup"><span data-stu-id="eda9b-118">The basic pattern follows the model for unified cancellation, which is introduced in .NET Framework 4.</span></span> <span data-ttu-id="eda9b-119">Daha fazla bilgi için bkz. [yönetilen Iş parçacıklarında iptal](../../../docs/standard/threading/cancellation-in-managed-threads.md).</span><span class="sxs-lookup"><span data-stu-id="eda9b-119">For more information, see [Cancellation in Managed Threads](../../../docs/standard/threading/cancellation-in-managed-threads.md).</span></span>  
  
 [!code-csharp[CDS_CountdownEvent#02](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_countdownevent/cs/countdownevent.cs#02)]
 [!code-vb[CDS_CountdownEvent#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_countdownevent/vb/canceleventwait.vb#02)]  
  
 <span data-ttu-id="eda9b-120">Bekleme işleminin sinyal veren iş parçacıklarını iptal etmediğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="eda9b-120">Note that the wait operation does not cancel the threads that are signaling it.</span></span> <span data-ttu-id="eda9b-121">Genellikle, iptal, mantıksal bir işleme uygulanır ve bu, olayın ve bekleyen tüm iş öğelerinin de tamamlanmasını içerebilir.</span><span class="sxs-lookup"><span data-stu-id="eda9b-121">Typically, cancellation is applied to a logical operation, and that can include waiting on the event as well as all the work items that the wait is synchronizing.</span></span> <span data-ttu-id="eda9b-122">Bu örnekte, her iş öğesi, iptal isteğine yanıt verebilmesi için aynı iptal belirtecinin bir kopyasını geçti.</span><span class="sxs-lookup"><span data-stu-id="eda9b-122">In this example, each work item is passed a copy of the same cancellation token so that it can respond to the cancellation request.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eda9b-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="eda9b-123">See also</span></span>

- <xref:System.Threading.Semaphore?displayProperty=nameWithType>
