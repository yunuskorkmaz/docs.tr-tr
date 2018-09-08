---
title: Engel (.NET Framework)
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- synchronization primitives, Barrier
ms.assetid: 613a8bc7-6a28-4795-bd6c-1abd9050478f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 385e370f205851630f809b285a93c2609220efeb
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44137115"
---
# <a name="barrier-net-framework"></a><span data-ttu-id="05835-102">Engel (.NET Framework)</span><span class="sxs-lookup"><span data-stu-id="05835-102">Barrier (.NET Framework)</span></span>
<span data-ttu-id="05835-103">A *engel* birden çok iş parçacığı sağlayan bir kullanıcı tanımlı eşitleme ilkel (olarak bilinen *katılımcıları*) üzerinde bir algoritma aşamalarında eşzamanlı olarak çalışacak şekilde.</span><span class="sxs-lookup"><span data-stu-id="05835-103">A *barrier* is a user-defined synchronization primitive that enables multiple threads (known as *participants*) to work concurrently on an algorithm in phases.</span></span> <span data-ttu-id="05835-104">Kodda engel noktası ulaşana kadar her katılımcı yürütür.</span><span class="sxs-lookup"><span data-stu-id="05835-104">Each participant executes until it reaches the barrier point in the code.</span></span> <span data-ttu-id="05835-105">Engel çalışmanın bir aşama sonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="05835-105">The barrier represents the end of one phase of work.</span></span> <span data-ttu-id="05835-106">Katılımcı engel ulaştığında, tüm katılımcılar aynı engele kadar engeller.</span><span class="sxs-lookup"><span data-stu-id="05835-106">When a participant reaches the barrier, it blocks until all participants have reached the same barrier.</span></span> <span data-ttu-id="05835-107">Tüm katılımcıları engele sonra isteğe bağlı olarak bir aşama sonrası eylemi çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="05835-107">After all participants have reached the barrier, you can optionally invoke a post-phase action.</span></span> <span data-ttu-id="05835-108">Diğer tüm iş parçacıklarının hala engellenirken sonrası Bu aşama eylem eylemleri gerçekleştirmek için tek bir iş parçacığı tarafından kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="05835-108">This post-phase action can be used to perform actions by a single thread while all other threads are still blocked.</span></span> <span data-ttu-id="05835-109">Katılımcılar, tüm Eylem yürütüldükten sonra engellenmemektedir.</span><span class="sxs-lookup"><span data-stu-id="05835-109">After the action has been executed, the participants are all unblocked.</span></span>  
  
 <span data-ttu-id="05835-110">Aşağıdaki kod parçacığı bir engel temel deseni gösterir.</span><span class="sxs-lookup"><span data-stu-id="05835-110">The following code snippet shows a basic barrier pattern.</span></span>  
  
 [!code-csharp[CDS_Barrier#02](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_barrier/cs/barrier.cs#02)]
 [!code-vb[CDS_Barrier#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_barrier/vb/barrier_vb.vb#02)]  
  
 <span data-ttu-id="05835-111">Tam bir örnek için bkz. [nasıl yapılır: eş zamanlı görevleri bir engel ile eşitleme](../../../docs/standard/threading/how-to-synchronize-concurrent-operations-with-a-barrier.md).</span><span class="sxs-lookup"><span data-stu-id="05835-111">For a complete example, see [How to: Synchronize Concurrent Operations with a Barrier](../../../docs/standard/threading/how-to-synchronize-concurrent-operations-with-a-barrier.md).</span></span>  
  
## <a name="adding-and-removing-participants"></a><span data-ttu-id="05835-112">Ekleme ve kaldırma katılımcıları</span><span class="sxs-lookup"><span data-stu-id="05835-112">Adding and Removing Participants</span></span>  
 <span data-ttu-id="05835-113">Oluştururken bir <xref:System.Threading.Barrier>, katılımcılar sayısını belirtin.</span><span class="sxs-lookup"><span data-stu-id="05835-113">When you create a <xref:System.Threading.Barrier>, specify the number of participants.</span></span> <span data-ttu-id="05835-114">Ayrıca, ekleyebilir veya katılımcıları dinamik olarak dilediğiniz zaman kaldırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="05835-114">You can also add or remove participants dynamically at any time.</span></span> <span data-ttu-id="05835-115">Örneğin, bir katılımcı kendi parçası sorunu çözer, iş parçacığı ve arama sonucu, Dur yürütülmesine depolayabilirsiniz <xref:System.Threading.Barrier.RemoveParticipant%2A> engel katılımcılarının sayısını azaltmak için.</span><span class="sxs-lookup"><span data-stu-id="05835-115">For example, if one participant solves its part of the problem, you can store the result, stop execution on that thread, and call <xref:System.Threading.Barrier.RemoveParticipant%2A> to decrement the number of participants in the barrier.</span></span> <span data-ttu-id="05835-116">Eklediğinizde, bir katılımcı çağırarak <xref:System.Threading.Barrier.AddParticipant%2A>, dönüş değeri yeni katılımcı çalışmasını başlatmak için yararlı olabilecek geçerli aşama numarasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="05835-116">When you add a participant by calling <xref:System.Threading.Barrier.AddParticipant%2A>, the return value specifies the current phase number, which may be useful in order to initialize the work of the new participant.</span></span>  
  
## <a name="broken-barriers"></a><span data-ttu-id="05835-117">Bozuk engelleri</span><span class="sxs-lookup"><span data-stu-id="05835-117">Broken Barriers</span></span>  
 <span data-ttu-id="05835-118">Engel ulaşmak bir katılımcı başarısız olursa, kilitlenmeleri ortaya çıkabilir.</span><span class="sxs-lookup"><span data-stu-id="05835-118">Deadlocks can occur if one participant fails to reach the barrier.</span></span> <span data-ttu-id="05835-119">Bu kilitlenmeleri önlemek için aşırı yüklemeleri kullanın. <xref:System.Threading.Barrier.SignalAndWait%2A> bir zaman aşımı süresi ve bir iptal belirteci belirtmek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="05835-119">To avoid these deadlocks, use the overloads of the <xref:System.Threading.Barrier.SignalAndWait%2A> method to specify a time-out period and a cancellation token.</span></span> <span data-ttu-id="05835-120">Bu aşırı yüklemeler dönüş her katılımcı önce denetleyebilen bir Boole değeri sonraki aşamaya devam eder.</span><span class="sxs-lookup"><span data-stu-id="05835-120">These overloads return a Boolean value that every participant can check before it continues to the next phase.</span></span>  
  
## <a name="post-phase-exceptions"></a><span data-ttu-id="05835-121">Son aşama özel durumları</span><span class="sxs-lookup"><span data-stu-id="05835-121">Post-Phase Exceptions</span></span>  
 <span data-ttu-id="05835-122">Sonrası aşaması temsilci bir özel durum oluşturursa, sarmalandıktan bir <xref:System.Threading.BarrierPostPhaseException> için tüm katılımcıları sonra yayılır nesnesidir.</span><span class="sxs-lookup"><span data-stu-id="05835-122">If the post-phase delegate throws an exception, it is wrapped in a <xref:System.Threading.BarrierPostPhaseException> object which is then propagated to all participants.</span></span>  
  
## <a name="barrier-versus-continuewhenall"></a><span data-ttu-id="05835-123">Engel ContinueWhenAll karşılaştırması</span><span class="sxs-lookup"><span data-stu-id="05835-123">Barrier Versus ContinueWhenAll</span></span>  
 <span data-ttu-id="05835-124">İş parçacıklarını birden çok aşama Döngülerde gerçekleştirirken engelleri özellikle yararlı olur.</span><span class="sxs-lookup"><span data-stu-id="05835-124">Barriers are especially useful when the threads are performing multiple phases in loops.</span></span> <span data-ttu-id="05835-125">Kodunuzu iş yalnızca bir veya iki aşamaya gerektiriyorsa, kullanıp kullanmayacağınızı düşünün <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> örtük birleşim, herhangi bir türden nesneler de dahil olmak üzere:</span><span class="sxs-lookup"><span data-stu-id="05835-125">If your code requires only one or two phases of work, consider whether to use <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> objects with any kind of implicit join, including:</span></span>  
  
-   <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A>  
  
-   <xref:System.Threading.Tasks.Parallel.Invoke%2A>  
  
-   <xref:System.Threading.Tasks.Parallel.ForEach%2A>  
  
-   <xref:System.Threading.Tasks.Parallel.For%2A>  
  
 <span data-ttu-id="05835-126">Daha fazla bilgi için [kullanarak devamlılık görevleri zinciri görevleriyle](../../../docs/standard/parallel-programming/chaining-tasks-by-using-continuation-tasks.md).</span><span class="sxs-lookup"><span data-stu-id="05835-126">For more information, see [Chaining Tasks by Using Continuation Tasks](../../../docs/standard/parallel-programming/chaining-tasks-by-using-continuation-tasks.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05835-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="05835-127">See also</span></span>

- [<span data-ttu-id="05835-128">İş Parçacığı Nesneleri ve Özellikleri</span><span class="sxs-lookup"><span data-stu-id="05835-128">Threading Objects and Features</span></span>](../../../docs/standard/threading/threading-objects-and-features.md)  
- [<span data-ttu-id="05835-129">Nasıl yapılır: Eş Zamanlı Görevleri bir Engelle Eşitleme</span><span class="sxs-lookup"><span data-stu-id="05835-129">How to: Synchronize Concurrent Operations with a Barrier</span></span>](../../../docs/standard/threading/how-to-synchronize-concurrent-operations-with-a-barrier.md)
