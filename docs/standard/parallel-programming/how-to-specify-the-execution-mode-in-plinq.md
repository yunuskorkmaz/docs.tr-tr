---
title: "Nasıl yapılır: PLINQ'te yürütme modunu belirtme"
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to use execution mode
ms.assetid: e52ff26c-c5d3-4fab-9fec-c937fb387963
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c67b23da6742af3cb65da6da49dbab982a0248bb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54694626"
---
# <a name="how-to-specify-the-execution-mode-in-plinq"></a><span data-ttu-id="11a47-102">Nasıl yapılır: PLINQ'te yürütme modunu belirtme</span><span class="sxs-lookup"><span data-stu-id="11a47-102">How to: Specify the Execution Mode in PLINQ</span></span>
<span data-ttu-id="11a47-103">Bu örnekte, varsayılan buluşsal atlamak ve sorgunun şekli bağımsız olarak bir sorgu paralel hale getirmek için PLINQ zorlamak gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="11a47-103">This example shows how to force PLINQ to bypass its default heuristics and parallelize a query regardless of the query's shape.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="11a47-104">Bu örnek, kullanımını göstermek için tasarlanmıştır ve nesneleri sorgu için eşdeğer sıralı LINQ daha hızlı çalışmayabilir.</span><span class="sxs-lookup"><span data-stu-id="11a47-104">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="11a47-105">Hızlandırmayı hakkında daha fazla bilgi için bkz: [plınq'te hızlandırmayı anlama](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="11a47-105">For more information about speedup, see [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="11a47-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="11a47-106">Example</span></span>  
 [!code-csharp[PLINQ#22](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#22)]
 [!code-vb[PLINQ#22](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#22)]  
  
 <span data-ttu-id="11a47-107">PLINQ, paralelleştirme için fırsatlar yararlanmak için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="11a47-107">PLINQ is designed to exploit opportunities for parallelization.</span></span> <span data-ttu-id="11a47-108">Ancak, tüm sorguları paralel yürütmeyi yararlanır.</span><span class="sxs-lookup"><span data-stu-id="11a47-108">However, not all queries benefit from parallel execution.</span></span> <span data-ttu-id="11a47-109">Çok az çalışır bir tek kullanıcı temsilcisi bir sorgu içeriyor, örneğin, sorgu genellikle daha hızlı bir şekilde sırayla çalışır.</span><span class="sxs-lookup"><span data-stu-id="11a47-109">For example, when a query contains a single user delegate that does very little work, the query will usually run faster sequentially.</span></span> <span data-ttu-id="11a47-110">Paralel yürütme etkinleştirirken yükü elde edilen hızlandırmayı daha ucuz olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="11a47-110">This is because the overhead involved in enabling parallelizing execution is more expensive than the speedup that is obtained.</span></span> <span data-ttu-id="11a47-111">Bu nedenle, PLINQ otomatik olarak her bir sorguyu paralelleştirmesi değil.</span><span class="sxs-lookup"><span data-stu-id="11a47-111">Therefore, PLINQ does not automatically parallelize every query.</span></span> <span data-ttu-id="11a47-112">Öncelikle, sorgu ve onu oluşturan çeşitli işleçler şeklini inceler.</span><span class="sxs-lookup"><span data-stu-id="11a47-112">It first examines the shape of the query and the various operators that comprise it.</span></span> <span data-ttu-id="11a47-113">Bu analizi temel alarak, PLINQ varsayılan yürütme modunda bazılarını veya tümünü sorgu ardışık olarak yürütmek karar verebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="11a47-113">Based on this analysis, PLINQ in the default execution mode may decide to execute some or all of the query sequentially.</span></span> <span data-ttu-id="11a47-114">PLINQ, analiz belirlemek mümkün olandan ancak bazı durumlarda daha sorgunuzu hakkında haberdar olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="11a47-114">However, in some cases you may know more about your query than PLINQ is able to determine from its analysis.</span></span> <span data-ttu-id="11a47-115">Örneğin, bir temsilci çok pahalı olduğundan ve sorgunun paralelleştirme kesinlikle faydalanır haberdar olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="11a47-115">For example, you may know that a delegate is very expensive, and that the query will definitely benefit from parallelization.</span></span> <span data-ttu-id="11a47-116">Bu gibi durumlarda, kullandığınız <xref:System.Linq.ParallelEnumerable.WithExecutionMode%2A> yöntemi belirtin <xref:System.Linq.ParallelExecutionMode.ForceParallelism> değeri her zaman sorguyu paralel çalıştırmak için PLINQ bildirin.</span><span class="sxs-lookup"><span data-stu-id="11a47-116">In such cases, you can use the <xref:System.Linq.ParallelEnumerable.WithExecutionMode%2A> method and specify the <xref:System.Linq.ParallelExecutionMode.ForceParallelism> value to instruct PLINQ to always run the query as parallel.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="11a47-117">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="11a47-117">Compiling the Code</span></span>  
 <span data-ttu-id="11a47-118">Bu kodu kesip [PLINQ veri örneği](../../../docs/standard/parallel-programming/plinq-data-sample.md) ve içinden yöntemi çağırın `Main`.</span><span class="sxs-lookup"><span data-stu-id="11a47-118">Cut and paste this code into the [PLINQ Data Sample](../../../docs/standard/parallel-programming/plinq-data-sample.md) and call the method from `Main`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11a47-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="11a47-119">See also</span></span>

- <xref:System.Linq.ParallelEnumerable.AsSequential%2A>
- [<span data-ttu-id="11a47-120">Paralel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="11a47-120">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
