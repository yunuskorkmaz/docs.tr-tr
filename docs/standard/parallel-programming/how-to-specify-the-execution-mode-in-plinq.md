---
title: "Nasıl yapılır: PLINQ'te Yürütme Modunu Belirtme"
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to use execution mode
ms.assetid: e52ff26c-c5d3-4fab-9fec-c937fb387963
ms.openlocfilehash: 6ef813937b731b417be31e189d89b81cccc75280
ms.sourcegitcommit: 961ec21c22d2f1d55c9cc8a7edf2ade1d1fd92e3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2020
ms.locfileid: "80588546"
---
# <a name="how-to-specify-the-execution-mode-in-plinq"></a><span data-ttu-id="86e5d-102">Nasıl yapılır: PLINQ'te Yürütme Modunu Belirtme</span><span class="sxs-lookup"><span data-stu-id="86e5d-102">How to: Specify the Execution Mode in PLINQ</span></span>
<span data-ttu-id="86e5d-103">Bu örnek, PLINQ'yi varsayılan sezgisel'ini atlayarak nasıl zorlayacağını ve sorgunun şekline bakılmaksızın sorguyu paralelleştirmeyi gösterir.</span><span class="sxs-lookup"><span data-stu-id="86e5d-103">This example shows how to force PLINQ to bypass its default heuristics and parallelize a query regardless of the query's shape.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="86e5d-104">Bu örnek, kullanımı göstermek için tasarlanmıştır ve Nesneler sorgusuna eşdeğer ardışık LINQ'dan daha hızlı çalışmayabilir.</span><span class="sxs-lookup"><span data-stu-id="86e5d-104">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="86e5d-105">Hız hakkında daha fazla bilgi için [PLINQ'da Hızları Anlama'ya](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="86e5d-105">For more information about speedup, see [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="86e5d-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="86e5d-106">Example</span></span>  
 [!code-csharp[PLINQ#22](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#22)]
 [!code-vb[PLINQ#22](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#22)]  
  
 <span data-ttu-id="86e5d-107">PLINQ, paralelleştirme fırsatlarından yararlanmak için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="86e5d-107">PLINQ is designed to exploit opportunities for parallelization.</span></span> <span data-ttu-id="86e5d-108">Ancak, tüm sorgular paralel yürütme yarar.</span><span class="sxs-lookup"><span data-stu-id="86e5d-108">However, not all queries benefit from parallel execution.</span></span> <span data-ttu-id="86e5d-109">Örneğin, bir sorgu çok az iş yapan tek bir kullanıcı temsilcisi içeriyorsa, sorgu genellikle sırayla daha hızlı çalışır.</span><span class="sxs-lookup"><span data-stu-id="86e5d-109">For example, when a query contains a single user delegate that does very little work, the query will usually run faster sequentially.</span></span> <span data-ttu-id="86e5d-110">Bunun nedeni, paralelyürütmeyi etkinleştirmede yer alan yükün elde edilen hızdan daha pahalı olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="86e5d-110">This is because the overhead involved in enabling parallelizing execution is more expensive than the speedup that is obtained.</span></span> <span data-ttu-id="86e5d-111">Bu nedenle, PLINQ otomatik olarak her sorgu paraleldeğildir.</span><span class="sxs-lookup"><span data-stu-id="86e5d-111">Therefore, PLINQ does not automatically parallelize every query.</span></span> <span data-ttu-id="86e5d-112">Önce sorgunun şeklini ve onu oluşturan çeşitli işleçleri inceler.</span><span class="sxs-lookup"><span data-stu-id="86e5d-112">It first examines the shape of the query and the various operators that comprise it.</span></span> <span data-ttu-id="86e5d-113">Bu çözümlemedayanarak, varsayılan yürütme modundaPLINQ, sorgunun bir kısmını veya tamamını sırayla yürütmeye karar verebilir.</span><span class="sxs-lookup"><span data-stu-id="86e5d-113">Based on this analysis, PLINQ in the default execution mode may decide to execute some or all of the query sequentially.</span></span> <span data-ttu-id="86e5d-114">Ancak, bazı durumlarda, PLINQ onun analizinden belirlemek mümkün daha sorgu hakkında daha fazla bilgi edinebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="86e5d-114">However, in some cases you may know more about your query than PLINQ is able to determine from its analysis.</span></span> <span data-ttu-id="86e5d-115">Örneğin, bir temsilcinin çok pahalı olduğunu ve sorgunun kesinlikle paralelleştirmeden yararlanacağını biliyor olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="86e5d-115">For example, you may know that a delegate is very expensive, and that the query will definitely benefit from parallelization.</span></span> <span data-ttu-id="86e5d-116">Bu gibi durumlarda, <xref:System.Linq.ParallelEnumerable.WithExecutionMode%2A> yöntemi kullanabilir ve <xref:System.Linq.ParallelExecutionMode.ForceParallelism> PLINQ'a sorguyu her zaman paralel olarak çalıştırmasını söylemek için değeri belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="86e5d-116">In such cases, you can use the <xref:System.Linq.ParallelEnumerable.WithExecutionMode%2A> method and specify the <xref:System.Linq.ParallelExecutionMode.ForceParallelism> value to instruct PLINQ to always run the query as parallel.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="86e5d-117">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="86e5d-117">Compiling the Code</span></span>  
 <span data-ttu-id="86e5d-118">Bu kodu [PLINQ Veri Örneği'ne](../../../docs/standard/parallel-programming/plinq-data-sample.md) kesip yapıştırın ve yöntemi .'den `Main`çağırın.</span><span class="sxs-lookup"><span data-stu-id="86e5d-118">Cut and paste this code into the [PLINQ Data Sample](../../../docs/standard/parallel-programming/plinq-data-sample.md) and call the method from `Main`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86e5d-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="86e5d-119">See also</span></span>

- <xref:System.Linq.ParallelEnumerable.AsSequential%2A>
- [<span data-ttu-id="86e5d-120">Paralel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="86e5d-120">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/introduction-to-plinq.md)
