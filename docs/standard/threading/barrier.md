---
title: Engel
ms.date: 09/14/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- synchronization primitives, Barrier
ms.assetid: 613a8bc7-6a28-4795-bd6c-1abd9050478f
ms.openlocfilehash: 5aa34f7f39f4b9b626bea29372cf984f3cefb361
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138157"
---
# <a name="barrier"></a><span data-ttu-id="f7735-102">Engel</span><span class="sxs-lookup"><span data-stu-id="f7735-102">Barrier</span></span>

<span data-ttu-id="f7735-103"><xref:System.Threading.Barrier?displayProperty=nameWithType>, birden çok iş parçacığının ( *katılımcılar*olarak bilinir) aşamalar halinde bir algoritmada eşzamanlı olarak çalışmasını sağlayan bir eşitleme temel masıdır.</span><span class="sxs-lookup"><span data-stu-id="f7735-103">A <xref:System.Threading.Barrier?displayProperty=nameWithType> is a synchronization primitive that enables multiple threads (known as *participants*) to work concurrently on an algorithm in phases.</span></span> <span data-ttu-id="f7735-104">Her katılımcı, koddaki engel noktasına ulaşıncaya kadar yürütülür.</span><span class="sxs-lookup"><span data-stu-id="f7735-104">Each participant executes until it reaches the barrier point in the code.</span></span> <span data-ttu-id="f7735-105">Engel, bir iş aşamasının sonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f7735-105">The barrier represents the end of one phase of work.</span></span> <span data-ttu-id="f7735-106">Bir katılımcı blobuna ulaştığında, tüm katılımcılar aynı engelye ulaşana kadar engeller.</span><span class="sxs-lookup"><span data-stu-id="f7735-106">When a participant reaches the barrier, it blocks until all participants have reached the same barrier.</span></span> <span data-ttu-id="f7735-107">Tüm katılımcılar engelye ulaştıktan sonra, isteğe bağlı olarak bir aşama sonrası eylemi çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f7735-107">After all participants have reached the barrier, you can optionally invoke a post-phase action.</span></span> <span data-ttu-id="f7735-108">Bu son aşama eylemi, diğer tüm iş parçacıkları hala engellenirken eylemleri tek bir iş parçacığı tarafından gerçekleştirmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f7735-108">This post-phase action can be used to perform actions by a single thread while all other threads are still blocked.</span></span> <span data-ttu-id="f7735-109">Eylem yürütüldükten sonra katılımcıların engeli kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="f7735-109">After the action has been executed, the participants are all unblocked.</span></span>  
  
 <span data-ttu-id="f7735-110">Aşağıdaki kod parçacığında temel bir engel gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="f7735-110">The following code snippet shows a basic barrier pattern.</span></span>  
  
 [!code-csharp[CDS_Barrier#02](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_barrier/cs/barrier.cs#02)]
 [!code-vb[CDS_Barrier#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_barrier/vb/barrier_vb.vb#02)]  
  
 <span data-ttu-id="f7735-111">Tüm bir örnek için bkz. [nasıl yapılır: eş zamanlı işlemleri bir engel ile senkronize etme](how-to-synchronize-concurrent-operations-with-a-barrier.md).</span><span class="sxs-lookup"><span data-stu-id="f7735-111">For a complete example, see [How to: synchronize concurrent operations with a Barrier](how-to-synchronize-concurrent-operations-with-a-barrier.md).</span></span>  
  
## <a name="adding-and-removing-participants"></a><span data-ttu-id="f7735-112">Katılımcıları ekleme ve kaldırma</span><span class="sxs-lookup"><span data-stu-id="f7735-112">Adding and removing participants</span></span>

 <span data-ttu-id="f7735-113">Bir <xref:System.Threading.Barrier> örneği oluşturduğunuzda, katılımcı sayısını belirtin.</span><span class="sxs-lookup"><span data-stu-id="f7735-113">When you create a <xref:System.Threading.Barrier> instance, specify the number of participants.</span></span> <span data-ttu-id="f7735-114">Ayrıca, istediğiniz zaman dinamik olarak katılımcı ekleyebilir veya kaldırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f7735-114">You can also add or remove participants dynamically at any time.</span></span> <span data-ttu-id="f7735-115">Örneğin, bir katılımcı sorunun parçasını çözerse, sonucu saklayabilir, bu iş parçacığında yürütmeyi durdurabilir ve engelteki katılımcı sayısını azaltmak için <xref:System.Threading.Barrier.RemoveParticipant%2A?displayProperty=nameWithType> çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f7735-115">For example, if one participant solves its part of the problem, you can store the result, stop execution on that thread, and call <xref:System.Threading.Barrier.RemoveParticipant%2A?displayProperty=nameWithType> to decrement the number of participants in the barrier.</span></span> <span data-ttu-id="f7735-116"><xref:System.Threading.Barrier.AddParticipant%2A?displayProperty=nameWithType>çağırarak bir katılımcı eklediğinizde, dönüş değeri, yeni katılımcının işini başlatmak için yararlı olabilecek geçerli aşama numarasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="f7735-116">When you add a participant by calling <xref:System.Threading.Barrier.AddParticipant%2A?displayProperty=nameWithType>, the return value specifies the current phase number, which may be useful in order to initialize the work of the new participant.</span></span>  
  
## <a name="broken-barriers"></a><span data-ttu-id="f7735-117">Bozuk engelleri</span><span class="sxs-lookup"><span data-stu-id="f7735-117">Broken barriers</span></span>

 <span data-ttu-id="f7735-118">Bir katılımcının engeli geçemediğinde kilitlenmeler meydana gelebilir.</span><span class="sxs-lookup"><span data-stu-id="f7735-118">Deadlocks can occur if one participant fails to reach the barrier.</span></span> <span data-ttu-id="f7735-119">Bu kilitlenmeleri önlemek için <xref:System.Threading.Barrier.SignalAndWait%2A?displayProperty=nameWithType> yönteminin aşırı yüklerini kullanarak bir zaman aşımı süresi ve bir iptal belirteci belirtin.</span><span class="sxs-lookup"><span data-stu-id="f7735-119">To avoid these deadlocks, use the overloads of the <xref:System.Threading.Barrier.SignalAndWait%2A?displayProperty=nameWithType> method to specify a time-out period and a cancellation token.</span></span> <span data-ttu-id="f7735-120">Bu aşırı yüklemeler, her katılımcının bir sonraki aşamaya devam etmeden önce denetlemesindeki bir Boole değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="f7735-120">These overloads return a Boolean value that every participant can check before it continues to the next phase.</span></span>  
  
## <a name="post-phase-exceptions"></a><span data-ttu-id="f7735-121">Son aşama özel durumları</span><span class="sxs-lookup"><span data-stu-id="f7735-121">Post-phase exceptions</span></span>

 <span data-ttu-id="f7735-122">Aşama sonrası temsilci bir özel durum oluşturursa, daha sonra tüm katılımcılara yayılan bir <xref:System.Threading.BarrierPostPhaseException> nesnesine sarmalanır.</span><span class="sxs-lookup"><span data-stu-id="f7735-122">If the post-phase delegate throws an exception, it is wrapped in a <xref:System.Threading.BarrierPostPhaseException> object which is then propagated to all participants.</span></span>  
  
## <a name="barrier-versus-continuewhenall"></a><span data-ttu-id="f7735-123">Engel ve devam eden</span><span class="sxs-lookup"><span data-stu-id="f7735-123">Barrier versus ContinueWhenAll</span></span>

 <span data-ttu-id="f7735-124">Engelleri, özellikle iş parçacıkları Döngülerde birden çok aşama gerçekleştirirken yararlı olur.</span><span class="sxs-lookup"><span data-stu-id="f7735-124">Barriers are especially useful when the threads are performing multiple phases in loops.</span></span> <span data-ttu-id="f7735-125">Kodunuz yalnızca bir veya iki iş aşaması gerektiriyorsa, <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> nesneleri her türlü örtük birleşimde kullanıp kullanmayacağınızı göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="f7735-125">If your code requires only one or two phases of work, consider whether to use <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> objects with any kind of implicit join, including:</span></span>  
  
- <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A?displayProperty=nameWithType>  
  
- <xref:System.Threading.Tasks.Parallel.Invoke%2A?displayProperty=nameWithType>  
  
- <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>  
  
- <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="f7735-126">Daha fazla bilgi için bkz. [devamlılık görevlerini kullanarak görevleri zincirleme](../parallel-programming/chaining-tasks-by-using-continuation-tasks.md).</span><span class="sxs-lookup"><span data-stu-id="f7735-126">For more information, see [Chaining Tasks by Using Continuation Tasks](../parallel-programming/chaining-tasks-by-using-continuation-tasks.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7735-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f7735-127">See also</span></span>

- [<span data-ttu-id="f7735-128">İş parçacığı nesneleri ve özellikleri</span><span class="sxs-lookup"><span data-stu-id="f7735-128">Threading objects and features</span></span>](threading-objects-and-features.md)
- [<span data-ttu-id="f7735-129">Nasıl yapılır: eş zamanlı işlemleri bir engel ile senkronize etme</span><span class="sxs-lookup"><span data-stu-id="f7735-129">How to: synchronize concurrent operations with a Barrier</span></span>](how-to-synchronize-concurrent-operations-with-a-barrier.md)
