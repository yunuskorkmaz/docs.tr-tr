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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73138157"
---
# <a name="barrier"></a><span data-ttu-id="6e000-102">Engel</span><span class="sxs-lookup"><span data-stu-id="6e000-102">Barrier</span></span>

<span data-ttu-id="6e000-103">A, <xref:System.Threading.Barrier?displayProperty=nameWithType> birden çok iş parçacığının *(katılımcılar*olarak bilinir) aşamalar halinde bir algoritma üzerinde aynı anda çalışmasını sağlayan bir eşitleme ilkelidir.</span><span class="sxs-lookup"><span data-stu-id="6e000-103">A <xref:System.Threading.Barrier?displayProperty=nameWithType> is a synchronization primitive that enables multiple threads (known as *participants*) to work concurrently on an algorithm in phases.</span></span> <span data-ttu-id="6e000-104">Her katılımcı, koddaki bariyer noktasına ulaşana kadar yürütür.</span><span class="sxs-lookup"><span data-stu-id="6e000-104">Each participant executes until it reaches the barrier point in the code.</span></span> <span data-ttu-id="6e000-105">Bariyer, bir çalışma aşamasının sonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="6e000-105">The barrier represents the end of one phase of work.</span></span> <span data-ttu-id="6e000-106">Bir katılımcı bariyere ulaştığında, tüm katılımcılar aynı bariyere ulaşana kadar engeller.</span><span class="sxs-lookup"><span data-stu-id="6e000-106">When a participant reaches the barrier, it blocks until all participants have reached the same barrier.</span></span> <span data-ttu-id="6e000-107">Tüm katılımcılar bariyere ulaştıktan sonra, isteğe bağlı olarak aşamalı bir eylem başlatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6e000-107">After all participants have reached the barrier, you can optionally invoke a post-phase action.</span></span> <span data-ttu-id="6e000-108">Bu aşama sonrası eylem, diğer tüm iş parçacıkları hala engellenirken eylemleri tek bir iş parçacığı tarafından gerçekleştirmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="6e000-108">This post-phase action can be used to perform actions by a single thread while all other threads are still blocked.</span></span> <span data-ttu-id="6e000-109">Eylem yürütüldükten sonra katılımcıların tümü engeli kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="6e000-109">After the action has been executed, the participants are all unblocked.</span></span>  
  
 <span data-ttu-id="6e000-110">Aşağıdaki kod parçacığı temel bir engel deseni gösterir.</span><span class="sxs-lookup"><span data-stu-id="6e000-110">The following code snippet shows a basic barrier pattern.</span></span>  
  
 [!code-csharp[CDS_Barrier#02](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_barrier/cs/barrier.cs#02)]
 [!code-vb[CDS_Barrier#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_barrier/vb/barrier_vb.vb#02)]  
  
 <span data-ttu-id="6e000-111">Tam bir örnek için [bkz: Eşzamanlı işlemleri Bir Bariyerle eşitleme.](how-to-synchronize-concurrent-operations-with-a-barrier.md)</span><span class="sxs-lookup"><span data-stu-id="6e000-111">For a complete example, see [How to: synchronize concurrent operations with a Barrier](how-to-synchronize-concurrent-operations-with-a-barrier.md).</span></span>  
  
## <a name="adding-and-removing-participants"></a><span data-ttu-id="6e000-112">Katılımcıların eklenmesi ve kaldırılması</span><span class="sxs-lookup"><span data-stu-id="6e000-112">Adding and removing participants</span></span>

 <span data-ttu-id="6e000-113">Bir <xref:System.Threading.Barrier> örnek oluşturduğunuzda, katılımcı sayısını belirtin.</span><span class="sxs-lookup"><span data-stu-id="6e000-113">When you create a <xref:System.Threading.Barrier> instance, specify the number of participants.</span></span> <span data-ttu-id="6e000-114">Ayrıca, katılımcıları istediğiniz zaman dinamik olarak ekleyebilir veya kaldırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6e000-114">You can also add or remove participants dynamically at any time.</span></span> <span data-ttu-id="6e000-115">Örneğin, bir katılımcı sorunun kendi bölümünü çözerse, sonucu depolayabilir, yürütmeyi <xref:System.Threading.Barrier.RemoveParticipant%2A?displayProperty=nameWithType> bu iş parçacığıüzerinde durdurabilir ve engeldeki katılımcı sayısını azat etmeye çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6e000-115">For example, if one participant solves its part of the problem, you can store the result, stop execution on that thread, and call <xref:System.Threading.Barrier.RemoveParticipant%2A?displayProperty=nameWithType> to decrement the number of participants in the barrier.</span></span> <span data-ttu-id="6e000-116">Bir katılımcıyı arayarak <xref:System.Threading.Barrier.AddParticipant%2A?displayProperty=nameWithType>eklediğinizde, iade değeri geçerli faz numarasını belirtir ve bu da yeni katılımcının çalışmasını başlatmada yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="6e000-116">When you add a participant by calling <xref:System.Threading.Barrier.AddParticipant%2A?displayProperty=nameWithType>, the return value specifies the current phase number, which may be useful in order to initialize the work of the new participant.</span></span>  
  
## <a name="broken-barriers"></a><span data-ttu-id="6e000-117">Kırık bariyerler</span><span class="sxs-lookup"><span data-stu-id="6e000-117">Broken barriers</span></span>

 <span data-ttu-id="6e000-118">Bir katılımcı bariyere ulaşamazsa kilitlenmeler oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="6e000-118">Deadlocks can occur if one participant fails to reach the barrier.</span></span> <span data-ttu-id="6e000-119">Bu kilitlenmeleri önlemek için, bir <xref:System.Threading.Barrier.SignalAndWait%2A?displayProperty=nameWithType> zaman çıkış süresi ve iptal belirteci belirtmek için yöntemin aşırı yüklerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="6e000-119">To avoid these deadlocks, use the overloads of the <xref:System.Threading.Barrier.SignalAndWait%2A?displayProperty=nameWithType> method to specify a time-out period and a cancellation token.</span></span> <span data-ttu-id="6e000-120">Bu aşırı yüklemeler, her katılımcının bir sonraki aşamaya geçmeden önce kontrol edebileceği bir Boolean değerini döndürer.</span><span class="sxs-lookup"><span data-stu-id="6e000-120">These overloads return a Boolean value that every participant can check before it continues to the next phase.</span></span>  
  
## <a name="post-phase-exceptions"></a><span data-ttu-id="6e000-121">Aşama sonrası özel durumlar</span><span class="sxs-lookup"><span data-stu-id="6e000-121">Post-phase exceptions</span></span>

 <span data-ttu-id="6e000-122">Aşama sonrası temsilci bir özel durum atarsa, daha <xref:System.Threading.BarrierPostPhaseException> sonra tüm katılımcılara yayılan bir nesneye sarılır.</span><span class="sxs-lookup"><span data-stu-id="6e000-122">If the post-phase delegate throws an exception, it is wrapped in a <xref:System.Threading.BarrierPostPhaseException> object which is then propagated to all participants.</span></span>  
  
## <a name="barrier-versus-continuewhenall"></a><span data-ttu-id="6e000-123">Bariyer karşı ContinueWhenAll</span><span class="sxs-lookup"><span data-stu-id="6e000-123">Barrier versus ContinueWhenAll</span></span>

 <span data-ttu-id="6e000-124">İş parçacıkları döngüler halinde birden çok aşama gerçekleştirirken engeller özellikle yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="6e000-124">Barriers are especially useful when the threads are performing multiple phases in loops.</span></span> <span data-ttu-id="6e000-125">Kodunuz yalnızca bir veya iki çalışma aşaması gerektiriyorsa, nesnelerde örtük birleştirme ile birlikte kullanılıp kullanılmayacağınız <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> ı göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="6e000-125">If your code requires only one or two phases of work, consider whether to use <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> objects with any kind of implicit join, including:</span></span>  
  
- <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A?displayProperty=nameWithType>  
  
- <xref:System.Threading.Tasks.Parallel.Invoke%2A?displayProperty=nameWithType>  
  
- <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>  
  
- <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="6e000-126">Daha fazla bilgi için, [Devam Görevlerini Kullanarak Görevleri Zincirleme'ye](../parallel-programming/chaining-tasks-by-using-continuation-tasks.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="6e000-126">For more information, see [Chaining Tasks by Using Continuation Tasks](../parallel-programming/chaining-tasks-by-using-continuation-tasks.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e000-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6e000-127">See also</span></span>

- [<span data-ttu-id="6e000-128">İş parçacığı nesneleri ve özellikleri</span><span class="sxs-lookup"><span data-stu-id="6e000-128">Threading objects and features</span></span>](threading-objects-and-features.md)
- [<span data-ttu-id="6e000-129">Nasıl: bir Bariyer ile eşzamanlı işlemleri senkronize</span><span class="sxs-lookup"><span data-stu-id="6e000-129">How to: synchronize concurrent operations with a Barrier</span></span>](how-to-synchronize-concurrent-operations-with-a-barrier.md)
