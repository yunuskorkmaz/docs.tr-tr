---
title: Engel (.NET Framework)
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
helpviewer_keywords: synchronization primitives, Barrier
ms.assetid: 613a8bc7-6a28-4795-bd6c-1abd9050478f
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 392e975f6bf566c2ba36290940eb0daee03f004f
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="barrier-net-framework"></a><span data-ttu-id="532cf-102">Engel (.NET Framework)</span><span class="sxs-lookup"><span data-stu-id="532cf-102">Barrier (.NET Framework)</span></span>
<span data-ttu-id="532cf-103">A *engel* birden çok iş parçacığı sağlayan bir kullanıcı tarafından tanımlanan eşitleme ilkel (olarak bilinen *katılımcıları*) aynı anda üzerinde bir algoritma aşamada çalışması için.</span><span class="sxs-lookup"><span data-stu-id="532cf-103">A *barrier* is a user-defined synchronization primitive that enables multiple threads (known as *participants*) to work concurrently on an algorithm in phases.</span></span> <span data-ttu-id="532cf-104">Kodda engel noktası ulaşana kadar her katılımcı yürütür.</span><span class="sxs-lookup"><span data-stu-id="532cf-104">Each participant executes until it reaches the barrier point in the code.</span></span> <span data-ttu-id="532cf-105">Engeli iş bir aşamada sonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="532cf-105">The barrier represents the end of one phase of work.</span></span> <span data-ttu-id="532cf-106">Katılımcı engel ulaşırsa, tüm katılımcılar aynı engel ulaştınız kadar engeller.</span><span class="sxs-lookup"><span data-stu-id="532cf-106">When a participant reaches the barrier, it blocks until all participants have reached the same barrier.</span></span> <span data-ttu-id="532cf-107">Tüm katılımcılar engel ulaştınız sonra sonrası aşaması eylem isteğe bağlı olarak çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="532cf-107">After all participants have reached the barrier, you can optionally invoke a post-phase action.</span></span> <span data-ttu-id="532cf-108">Diğer tüm iş parçacıklarının hala engellenirken sonrası Bu aşama eylemi eylemleri gerçekleştirmek için tek bir iş parçacığı tarafından kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="532cf-108">This post-phase action can be used to perform actions by a single thread while all other threads are still blocked.</span></span> <span data-ttu-id="532cf-109">Eylem yürütüldükten sonra katılımcıları tüm engellenmemiş.</span><span class="sxs-lookup"><span data-stu-id="532cf-109">After the action has been executed, the participants are all unblocked.</span></span>  
  
 <span data-ttu-id="532cf-110">Aşağıdaki kod parçacığını bir temel engel deseni gösterir.</span><span class="sxs-lookup"><span data-stu-id="532cf-110">The following code snippet shows a basic barrier pattern.</span></span>  
  
 [!code-csharp[CDS_Barrier#02](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_barrier/cs/barrier.cs#02)]
 [!code-vb[CDS_Barrier#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_barrier/vb/barrier_vb.vb#02)]  
  
 <span data-ttu-id="532cf-111">Tam bir örnek için bkz: [nasıl yapılır: eşitleme eş zamanlı görevleri bir engelle ile](../../../docs/standard/threading/how-to-synchronize-concurrent-operations-with-a-barrier.md).</span><span class="sxs-lookup"><span data-stu-id="532cf-111">For a complete example, see [How to: Synchronize Concurrent Operations with a Barrier](../../../docs/standard/threading/how-to-synchronize-concurrent-operations-with-a-barrier.md).</span></span>  
  
## <a name="adding-and-removing-participants"></a><span data-ttu-id="532cf-112">Ekleme ve katılımcıları kaldırma</span><span class="sxs-lookup"><span data-stu-id="532cf-112">Adding and Removing Participants</span></span>  
 <span data-ttu-id="532cf-113">Oluştururken bir <xref:System.Threading.Barrier>, katılımcılar sayısını belirtin.</span><span class="sxs-lookup"><span data-stu-id="532cf-113">When you create a <xref:System.Threading.Barrier>, specify the number of participants.</span></span> <span data-ttu-id="532cf-114">Ayrıca ekleyebilir veya katılımcıları dinamik olarak dilediğiniz zaman kaldırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="532cf-114">You can also add or remove participants dynamically at any time.</span></span> <span data-ttu-id="532cf-115">Örneğin, bir katılımcı sorunun onun parçası çözer, iş parçacığı ve arama sonucu, Dur yürütülmesine depolayabilirsiniz <xref:System.Threading.Barrier.RemoveParticipant%2A> engel katılımcıları sayısını düşürmek için.</span><span class="sxs-lookup"><span data-stu-id="532cf-115">For example, if one participant solves its part of the problem, you can store the result, stop execution on that thread, and call <xref:System.Threading.Barrier.RemoveParticipant%2A> to decrement the number of participants in the barrier.</span></span> <span data-ttu-id="532cf-116">Çağırarak katılımcı eklediğinizde <xref:System.Threading.Barrier.AddParticipant%2A>, dönüş değeri yeni katılımcı iş başlatmak için yararlı olabilecek geçerli aşama numarasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="532cf-116">When you add a participant by calling <xref:System.Threading.Barrier.AddParticipant%2A>, the return value specifies the current phase number, which may be useful in order to initialize the work of the new participant.</span></span>  
  
## <a name="broken-barriers"></a><span data-ttu-id="532cf-117">Bozuk engelleri</span><span class="sxs-lookup"><span data-stu-id="532cf-117">Broken Barriers</span></span>  
 <span data-ttu-id="532cf-118">Kilitlenmeler bir katılımcı engel erişemeyen ortaya çıkabilir.</span><span class="sxs-lookup"><span data-stu-id="532cf-118">Deadlocks can occur if one participant fails to reach the barrier.</span></span> <span data-ttu-id="532cf-119">Bu kilitlenmeler önlemek için aşırı kullanın <xref:System.Threading.Barrier.SignalAndWait%2A> yöntemi bir zaman aşımı süresi ve bir iptal belirteci belirtin.</span><span class="sxs-lookup"><span data-stu-id="532cf-119">To avoid these deadlocks, use the overloads of the <xref:System.Threading.Barrier.SignalAndWait%2A> method to specify a time-out period and a cancellation token.</span></span> <span data-ttu-id="532cf-120">Bu aşırı dönüş her katılımcı önce kontrol edebilirsiniz bir Boole değeri sonraki aşamasına devam eder.</span><span class="sxs-lookup"><span data-stu-id="532cf-120">These overloads return a Boolean value that every participant can check before it continues to the next phase.</span></span>  
  
## <a name="post-phase-exceptions"></a><span data-ttu-id="532cf-121">Özel durumlar sonrası aşaması</span><span class="sxs-lookup"><span data-stu-id="532cf-121">Post-Phase Exceptions</span></span>  
 <span data-ttu-id="532cf-122">Sonrası aşaması temsilci bir özel durum oluşturursa, paketlenir bir <xref:System.Threading.BarrierPostPhaseException> sonra tüm katılımcılar yayıldığı nesnesidir.</span><span class="sxs-lookup"><span data-stu-id="532cf-122">If the post-phase delegate throws an exception, it is wrapped in a <xref:System.Threading.BarrierPostPhaseException> object which is then propagated to all participants.</span></span>  
  
## <a name="barrier-versus-continuewhenall"></a><span data-ttu-id="532cf-123">Engel ContinueWhenAll karşılaştırması</span><span class="sxs-lookup"><span data-stu-id="532cf-123">Barrier Versus ContinueWhenAll</span></span>  
 <span data-ttu-id="532cf-124">İş parçacığı Döngülerde birden çok aşamaları gerçekleştirirken engelleri özellikle yararlı olur.</span><span class="sxs-lookup"><span data-stu-id="532cf-124">Barriers are especially useful when the threads are performing multiple phases in loops.</span></span> <span data-ttu-id="532cf-125">Kodunuzu iş yalnızca bir veya iki aşamaları gerektiriyorsa, kullanıp kullanmayacağınızı düşünün <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> örtük birleştirme, her türlü nesneleriyle dahil olmak üzere:</span><span class="sxs-lookup"><span data-stu-id="532cf-125">If your code requires only one or two phases of work, consider whether to use <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> objects with any kind of implicit join, including:</span></span>  
  
-   <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A>  
  
-   <xref:System.Threading.Tasks.Parallel.Invoke%2A>  
  
-   <xref:System.Threading.Tasks.Parallel.ForEach%2A>  
  
-   <xref:System.Threading.Tasks.Parallel.For%2A>  
  
 <span data-ttu-id="532cf-126">Daha fazla bilgi için bkz: [zincirleme görevleri devamlılık görevlerini kullanarak tarafından](../../../docs/standard/parallel-programming/chaining-tasks-by-using-continuation-tasks.md).</span><span class="sxs-lookup"><span data-stu-id="532cf-126">For more information, see [Chaining Tasks by Using Continuation Tasks](../../../docs/standard/parallel-programming/chaining-tasks-by-using-continuation-tasks.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="532cf-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="532cf-127">See Also</span></span>  
 [<span data-ttu-id="532cf-128">İş Parçacığı Nesneleri ve Özellikleri</span><span class="sxs-lookup"><span data-stu-id="532cf-128">Threading Objects and Features</span></span>](../../../docs/standard/threading/threading-objects-and-features.md)  
 [<span data-ttu-id="532cf-129">Nasıl yapılır: Eş Zamanlı Görevleri bir Engelle Eşitleme</span><span class="sxs-lookup"><span data-stu-id="532cf-129">How to: Synchronize Concurrent Operations with a Barrier</span></span>](../../../docs/standard/threading/how-to-synchronize-concurrent-operations-with-a-barrier.md)
