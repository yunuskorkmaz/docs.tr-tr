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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73138117"
---
# <a name="countdownevent"></a><span data-ttu-id="571f2-102">CountdownEvent</span><span class="sxs-lookup"><span data-stu-id="571f2-102">CountdownEvent</span></span>
<span data-ttu-id="571f2-103"><xref:System.Threading.CountdownEvent?displayProperty=nameWithType>belirli bir sayıda sinyal verildikten sonra bekleyen iş parçacığı engellerini unengelbir senkronizasyon ilkel.</span><span class="sxs-lookup"><span data-stu-id="571f2-103"><xref:System.Threading.CountdownEvent?displayProperty=nameWithType> is a synchronization primitive that unblocks its waiting threads after it has been signaled a certain number of times.</span></span> <span data-ttu-id="571f2-104"><xref:System.Threading.CountdownEvent>aksi takdirde olay sinyalönce bir <xref:System.Threading.ManualResetEvent> veya el <xref:System.Threading.ManualResetEventSlim> ile bir değişken kullanmak zorunda kalacak senaryolar için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="571f2-104"><xref:System.Threading.CountdownEvent> is designed for scenarios in which you would otherwise have to use a <xref:System.Threading.ManualResetEvent> or <xref:System.Threading.ManualResetEventSlim> and manually decrement a variable before signaling the event.</span></span> <span data-ttu-id="571f2-105">Örneğin, bir çatal/birleştirme senaryosunda, yalnızca sinyal <xref:System.Threading.CountdownEvent> sayısı 5 olan bir tane oluşturabilir ve iş parçacığı havuzunda beş <xref:System.Threading.CountdownEvent.Signal%2A> iş öğesi başlatabilir ve tamamlandığında her iş öğesi aramasını sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="571f2-105">For example, in a fork/join scenario, you can just create a <xref:System.Threading.CountdownEvent> that has a signal count of 5, and then start five work items on the thread pool and have each work item call <xref:System.Threading.CountdownEvent.Signal%2A> when it completes.</span></span> <span data-ttu-id="571f2-106">Her çağrı <xref:System.Threading.CountdownEvent.Signal%2A> sinyal sayısını 1'e erdirer.</span><span class="sxs-lookup"><span data-stu-id="571f2-106">Each call to <xref:System.Threading.CountdownEvent.Signal%2A> decrements the signal count by 1.</span></span> <span data-ttu-id="571f2-107">Ana iş parçacığında, <xref:System.Threading.CountdownEvent.Wait%2A> sinyal sayısı sıfır olana kadar çağrı engellenir.</span><span class="sxs-lookup"><span data-stu-id="571f2-107">On the main thread, the call to <xref:System.Threading.CountdownEvent.Wait%2A> will block until the signal count is zero.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="571f2-108">Eski .NET Framework senkronizasyon API'leri ile etkileşime geçmesi <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> gerekmeyen <xref:System.Threading.Tasks.Parallel.Invoke%2A> kod için, çatal birleştirme paralelliğini ifade etmek için nesneleri veya yöntemi kullanmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="571f2-108">For code that does not have to interact with legacy .NET Framework synchronization APIs, consider using <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> objects or the <xref:System.Threading.Tasks.Parallel.Invoke%2A> method for an even easier approach to expressing fork-join parallelism.</span></span>  
  
 <span data-ttu-id="571f2-109"><xref:System.Threading.CountdownEvent>şu ek özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="571f2-109"><xref:System.Threading.CountdownEvent> has these additional features:</span></span>  
  
- <span data-ttu-id="571f2-110">Bekleme işlemi iptal belirteçleri kullanılarak iptal edilebilir.</span><span class="sxs-lookup"><span data-stu-id="571f2-110">The wait operation can be canceled by using cancellation tokens.</span></span>  
  
- <span data-ttu-id="571f2-111">Örnek oluşturulduktan sonra sinyal sayısı artımlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="571f2-111">Its signal count can be incremented after the instance is created.</span></span>  
  
- <span data-ttu-id="571f2-112">Örnekler, yöntemi arayarak <xref:System.Threading.CountdownEvent.Wait%2A> döndürüldikten sonra yeniden kullanılabilir. <xref:System.Threading.CountdownEvent.Reset%2A></span><span class="sxs-lookup"><span data-stu-id="571f2-112">Instances can be reused after <xref:System.Threading.CountdownEvent.Wait%2A> has returned by calling the <xref:System.Threading.CountdownEvent.Reset%2A> method.</span></span>  
  
- <span data-ttu-id="571f2-113">Örnekler gibi <xref:System.Threading.WaitHandle.WaitAll%2A> <xref:System.Threading.WaitHandle> diğer .NET Framework senkronizasyon API'leri ile entegrasyon için ortaya .</span><span class="sxs-lookup"><span data-stu-id="571f2-113">Instances expose a <xref:System.Threading.WaitHandle> for integration with other .NET Framework synchronization APIs such as <xref:System.Threading.WaitHandle.WaitAll%2A>.</span></span>  
  
## <a name="basic-usage"></a><span data-ttu-id="571f2-114">Temel Kullanım</span><span class="sxs-lookup"><span data-stu-id="571f2-114">Basic Usage</span></span>  
 <span data-ttu-id="571f2-115">Aşağıdaki örnek, bir <xref:System.Threading.CountdownEvent> iş öğesinin nasıl kullanılacağını <xref:System.Threading.ThreadPool> gösterir.</span><span class="sxs-lookup"><span data-stu-id="571f2-115">The following example demonstrates how to use a <xref:System.Threading.CountdownEvent> with <xref:System.Threading.ThreadPool> work items.</span></span>  
  
 [!code-csharp[CDS_CountdownEvent#01](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_countdownevent/cs/countdownevent.cs#01)]
 [!code-vb[CDS_CountdownEvent#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_countdownevent/vb/module1.vb#01)]  
  
## <a name="countdownevent-with-cancellation"></a><span data-ttu-id="571f2-116">İptal Ile CountdownOlay</span><span class="sxs-lookup"><span data-stu-id="571f2-116">CountdownEvent With Cancellation</span></span>  
 <span data-ttu-id="571f2-117">Aşağıdaki örnek, bir iptal belirteci kullanarak bekleme işleminin <xref:System.Threading.CountdownEvent> nasıl iptal edilebildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="571f2-117">The following example shows how to cancel the wait operation on <xref:System.Threading.CountdownEvent> by using a cancellation token.</span></span> <span data-ttu-id="571f2-118">Temel desen, .NET Framework 4'te tanıtılan birleşik iptal modelini izler.</span><span class="sxs-lookup"><span data-stu-id="571f2-118">The basic pattern follows the model for unified cancellation, which is introduced in .NET Framework 4.</span></span> <span data-ttu-id="571f2-119">Daha fazla bilgi için Yönetilen [İş Parçacıklarında İptal'e](../../../docs/standard/threading/cancellation-in-managed-threads.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="571f2-119">For more information, see [Cancellation in Managed Threads](../../../docs/standard/threading/cancellation-in-managed-threads.md).</span></span>  
  
 [!code-csharp[CDS_CountdownEvent#02](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_countdownevent/cs/countdownevent.cs#02)]
 [!code-vb[CDS_CountdownEvent#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_countdownevent/vb/canceleventwait.vb#02)]  
  
 <span data-ttu-id="571f2-120">Bekleme işleminin sinyal veren iş parçacıklarını iptal etmediğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="571f2-120">Note that the wait operation does not cancel the threads that are signaling it.</span></span> <span data-ttu-id="571f2-121">Genellikle, iptal mantıksal bir işlem uygulanır ve bu olay yanı sıra bekleme eşitleme olduğu tüm iş öğeleri bekleme içerebilir.</span><span class="sxs-lookup"><span data-stu-id="571f2-121">Typically, cancellation is applied to a logical operation, and that can include waiting on the event as well as all the work items that the wait is synchronizing.</span></span> <span data-ttu-id="571f2-122">Bu örnekte, her iş öğesi, iptal isteğine yanıt verebilmek için aynı iptal belirteci nin bir kopyasına geçirilir.</span><span class="sxs-lookup"><span data-stu-id="571f2-122">In this example, each work item is passed a copy of the same cancellation token so that it can respond to the cancellation request.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="571f2-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="571f2-123">See also</span></span>

- <xref:System.Threading.Semaphore?displayProperty=nameWithType>
