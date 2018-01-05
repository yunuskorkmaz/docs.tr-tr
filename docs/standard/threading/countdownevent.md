---
title: CountdownEvent
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: synchronization primitives, CountdownEvent
ms.assetid: eec3812a-e20f-4ecd-bfef-6921d508b708
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 144bcde6c4c8fb227773fe613da8445f100ce66d
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="countdownevent"></a><span data-ttu-id="0be03-102">CountdownEvent</span><span class="sxs-lookup"><span data-stu-id="0be03-102">CountdownEvent</span></span>
<span data-ttu-id="0be03-103"><xref:System.Threading.CountdownEvent?displayProperty=nameWithType>belirli bir kaç kez eşitleme ilkel edildikten sonra bekleyen parçacıklarını engelini kaldırır işaret olur.</span><span class="sxs-lookup"><span data-stu-id="0be03-103"><xref:System.Threading.CountdownEvent?displayProperty=nameWithType> is a synchronization primitive that unblocks its waiting threads after it has been signaled a certain number of times.</span></span> <span data-ttu-id="0be03-104"><xref:System.Threading.CountdownEvent>Aksi takdirde sahip olduğunuz kullanılacak senaryoları için tasarlanan bir <xref:System.Threading.ManualResetEvent> veya <xref:System.Threading.ManualResetEventSlim> ve olay sinyal önce el ile bir değişken azaltma.</span><span class="sxs-lookup"><span data-stu-id="0be03-104"><xref:System.Threading.CountdownEvent> is designed for scenarios in which you would otherwise have to use a <xref:System.Threading.ManualResetEvent> or <xref:System.Threading.ManualResetEventSlim> and manually decrement a variable before signaling the event.</span></span> <span data-ttu-id="0be03-105">Örneğin, bir çatalı/JOIN senaryosunda, yalnızca oluşturabileceğiniz bir <xref:System.Threading.CountdownEvent> 5 sinyal sayısını sahip ve ardından Başlat beş iş öğeleri iş parçacığı üzerinde havuz ve her iş öğesi çağrısı <xref:System.Threading.CountdownEvent.Signal%2A> tamamlandığında.</span><span class="sxs-lookup"><span data-stu-id="0be03-105">For example, in a fork/join scenario, you can just create a <xref:System.Threading.CountdownEvent> that has a signal count of 5, and then start five work items on the thread pool and have each work item call <xref:System.Threading.CountdownEvent.Signal%2A> when it completes.</span></span> <span data-ttu-id="0be03-106">Her çağrı <xref:System.Threading.CountdownEvent.Signal%2A> sinyal sayısı 1 ile azaltır.</span><span class="sxs-lookup"><span data-stu-id="0be03-106">Each call to <xref:System.Threading.CountdownEvent.Signal%2A> decrements the signal count by 1.</span></span> <span data-ttu-id="0be03-107">Çağrı ana iş parçacığı üzerinde <xref:System.Threading.CountdownEvent.Wait%2A> sinyal sayısı sıfır olana kadar engeller.</span><span class="sxs-lookup"><span data-stu-id="0be03-107">On the main thread, the call to <xref:System.Threading.CountdownEvent.Wait%2A> will block until the signal count is zero.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0be03-108">Eski .NET Framework eşitleme API'leri ile etkileşim kurmak zorunda değildir kodu kullanmayı <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> nesneleri veya <xref:System.Threading.Tasks.Parallel.Invoke%2A> çatalı birleştirme paralellik ifade etmek için daha kolay bir yaklaşım için yöntem.</span><span class="sxs-lookup"><span data-stu-id="0be03-108">For code that does not have to interact with legacy .NET Framework synchronization APIs, consider using <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> objects or the <xref:System.Threading.Tasks.Parallel.Invoke%2A> method for an even easier approach to expressing fork-join parallelism.</span></span>  
  
 <span data-ttu-id="0be03-109"><xref:System.Threading.CountdownEvent>Bu ek özellikler vardır:</span><span class="sxs-lookup"><span data-stu-id="0be03-109"><xref:System.Threading.CountdownEvent> has these additional features:</span></span>  
  
-   <span data-ttu-id="0be03-110">Bekleme işlemini iptal belirteçleri kullanarak iptal edilebilir.</span><span class="sxs-lookup"><span data-stu-id="0be03-110">The wait operation can be canceled by using cancellation tokens.</span></span>  
  
-   <span data-ttu-id="0be03-111">Örneği oluşturulduktan sonra onun sinyal sayısı artar.</span><span class="sxs-lookup"><span data-stu-id="0be03-111">Its signal count can be incremented after the instance is created.</span></span>  
  
-   <span data-ttu-id="0be03-112">Örneği yeniden kullanılabilir sonra <xref:System.Threading.CountdownEvent.Wait%2A> çağırarak döndürdü <xref:System.Threading.CountdownEvent.Reset%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="0be03-112">Instances can be reused after <xref:System.Threading.CountdownEvent.Wait%2A> has returned by calling the <xref:System.Threading.CountdownEvent.Reset%2A> method.</span></span>  
  
-   <span data-ttu-id="0be03-113">Örnekleri kullanıma bir <xref:System.Threading.WaitHandle> diğer .NET Framework eşitleme API'leri ile tümleştirme gibi <xref:System.Threading.WaitHandle.WaitAll%2A>.</span><span class="sxs-lookup"><span data-stu-id="0be03-113">Instances expose a <xref:System.Threading.WaitHandle> for integration with other .NET Framework synchronization APIs such as <xref:System.Threading.WaitHandle.WaitAll%2A>.</span></span>  
  
## <a name="basic-usage"></a><span data-ttu-id="0be03-114">Temel kullanım</span><span class="sxs-lookup"><span data-stu-id="0be03-114">Basic Usage</span></span>  
 <span data-ttu-id="0be03-115">Aşağıdaki örnekte nasıl kullanılacağını gösteren bir <xref:System.Threading.CountdownEvent> ile <xref:System.Threading.ThreadPool> iş öğeleri.</span><span class="sxs-lookup"><span data-stu-id="0be03-115">The following example demonstrates how to use a <xref:System.Threading.CountdownEvent> with <xref:System.Threading.ThreadPool> work items.</span></span>  
  
 [!code-csharp[CDS_CountdownEvent#01](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_countdownevent/cs/countdownevent.cs#01)]
 [!code-vb[CDS_CountdownEvent#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_countdownevent/vb/module1.vb#01)]  
  
## <a name="countdownevent-with-cancellation"></a><span data-ttu-id="0be03-116">İptal etme ile CountdownEvent</span><span class="sxs-lookup"><span data-stu-id="0be03-116">CountdownEvent With Cancellation</span></span>  
 <span data-ttu-id="0be03-117">Aşağıdaki örnek, üzerinde bekleme işlemini iptal etmek gösterilmiştir <xref:System.Threading.CountdownEvent> kullanarak bir iptal belirteci.</span><span class="sxs-lookup"><span data-stu-id="0be03-117">The following example shows how to cancel the wait operation on <xref:System.Threading.CountdownEvent> by using a cancellation token.</span></span> <span data-ttu-id="0be03-118">Model sunulan birleşik iptali için temel deseni izler [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0be03-118">The basic pattern follows the model for unified cancellation, which is introduced in [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)].</span></span> <span data-ttu-id="0be03-119">Daha fazla bilgi için bkz: [yönetilen iş parçacıklarında iptal](../../../docs/standard/threading/cancellation-in-managed-threads.md).</span><span class="sxs-lookup"><span data-stu-id="0be03-119">For more information, see [Cancellation in Managed Threads](../../../docs/standard/threading/cancellation-in-managed-threads.md).</span></span>  
  
 [!code-csharp[CDS_CountdownEvent#02](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_countdownevent/cs/countdownevent.cs#02)]
 [!code-vb[CDS_CountdownEvent#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_countdownevent/vb/canceleventwait.vb#02)]  
  
 <span data-ttu-id="0be03-120">Bekleme işlem sinyal iş parçacıkları iptal etmez unutmayın.</span><span class="sxs-lookup"><span data-stu-id="0be03-120">Note that the wait operation does not cancel the threads that are signaling it.</span></span> <span data-ttu-id="0be03-121">Genellikle, mantıksal bir işlemi iptal uygulanır ve beklemeyi eşitleme tüm iş öğeleri yanı sıra olay üzerinde bekleyen içerebilir.</span><span class="sxs-lookup"><span data-stu-id="0be03-121">Typically, cancellation is applied to a logical operation, and that can include waiting on the event as well as all the work items that the wait is synchronizing.</span></span> <span data-ttu-id="0be03-122">İptal isteğine yanıt vermesi Bu örnekte, aynı iptal belirtecini bir kopyasını her iş öğesi geçirilir.</span><span class="sxs-lookup"><span data-stu-id="0be03-122">In this example, each work item is passed a copy of the same cancellation token so that it can respond to the cancellation request.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0be03-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0be03-123">See Also</span></span>  
 [<span data-ttu-id="0be03-124">EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent</span><span class="sxs-lookup"><span data-stu-id="0be03-124">EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent</span></span>](../../../docs/standard/threading/eventwaithandle-autoresetevent-countdownevent-manualresetevent.md)
