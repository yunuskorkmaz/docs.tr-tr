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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ebea62f33c5df252dd73a0708f31612cd2998728
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33580945"
---
# <a name="how-to-specify-the-execution-mode-in-plinq"></a><span data-ttu-id="d0e81-102">Nasıl yapılır: PLINQ'te Yürütme Modunu Belirtme</span><span class="sxs-lookup"><span data-stu-id="d0e81-102">How to: Specify the Execution Mode in PLINQ</span></span>
<span data-ttu-id="d0e81-103">Bu örnek varsayılan buluşsal atlamak için bir sorgu sorgu şekli bağımsız olarak paralel hale PLINQ zorlamak nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="d0e81-103">This example shows how to force PLINQ to bypass its default heuristics and parallelize a query regardless of the query's shape.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="d0e81-104">Bu örnek kullanım göstermeye yöneliktir ve eşdeğer sıralı LINQ daha hızlı nesneleri sorguya çalışmayabilir.</span><span class="sxs-lookup"><span data-stu-id="d0e81-104">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="d0e81-105">Speedup hakkında daha fazla bilgi için bkz: [Plınq'te hızlandırmayı anlama](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="d0e81-105">For more information about speedup, see [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d0e81-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="d0e81-106">Example</span></span>  
 [!code-csharp[PLINQ#22](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#22)]
 [!code-vb[PLINQ#22](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#22)]  
  
 <span data-ttu-id="d0e81-107">PLINQ paralelleştirme olanaklarını yararlanmak için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="d0e81-107">PLINQ is designed to exploit opportunities for parallelization.</span></span> <span data-ttu-id="d0e81-108">Ancak, tüm sorguları paralel yürütülmesini yararlanır.</span><span class="sxs-lookup"><span data-stu-id="d0e81-108">However, not all queries benefit from parallel execution.</span></span> <span data-ttu-id="d0e81-109">Sorguda çok az şey yapan bir tek kullanıcı temsilci içeriyorsa, örneğin, sorgu genellikle daha hızlı sırayla çalışır.</span><span class="sxs-lookup"><span data-stu-id="d0e81-109">For example, when a query contains a single user delegate that does very little work, the query will usually run faster sequentially.</span></span> <span data-ttu-id="d0e81-110">Parallelizing yürütme etkinleştirme söz konusu yükünü alınır speedup daha pahalı olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="d0e81-110">This is because the overhead involved in enabling parallelizing execution is more expensive than the speedup that is obtained.</span></span> <span data-ttu-id="d0e81-111">Bu nedenle, PLINQ otomatik olarak her sorguyu paralel hale değil.</span><span class="sxs-lookup"><span data-stu-id="d0e81-111">Therefore, PLINQ does not automatically parallelize every query.</span></span> <span data-ttu-id="d0e81-112">Önce sorgu ve onu oluşturan çeşitli işleçler şeklini inceler.</span><span class="sxs-lookup"><span data-stu-id="d0e81-112">It first examines the shape of the query and the various operators that comprise it.</span></span> <span data-ttu-id="d0e81-113">Bu analize dayalı olarak, varsayılan yürütme modu PLINQ'te bazılarını veya tümünü sorgu sırayla yürütmek karar verebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d0e81-113">Based on this analysis, PLINQ in the default execution mode may decide to execute some or all of the query sequentially.</span></span> <span data-ttu-id="d0e81-114">PLINQ kendi çözümlemesinden belirlemek mümkün olandan ancak, bazı durumlarda, daha sorgunuzu hakkında bilmeniz.</span><span class="sxs-lookup"><span data-stu-id="d0e81-114">However, in some cases you may know more about your query than PLINQ is able to determine from its analysis.</span></span> <span data-ttu-id="d0e81-115">Örneğin, bir temsilci çok pahalı olduğunu ve sorgu paralelleştirme kesinlikle faydalanırsınız biliyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="d0e81-115">For example, you may know that a delegate is very expensive, and that the query will definitely benefit from parallelization.</span></span> <span data-ttu-id="d0e81-116">Böyle durumlarda, kullandığınız <xref:System.Linq.ParallelEnumerable.WithExecutionMode%2A> yöntemi ve belirtin <xref:System.Linq.ParallelExecutionMode.ForceParallelism> değer her zaman sorguyu paralel çalıştırmak için PLINQ isteyin.</span><span class="sxs-lookup"><span data-stu-id="d0e81-116">In such cases, you can use the <xref:System.Linq.ParallelEnumerable.WithExecutionMode%2A> method and specify the <xref:System.Linq.ParallelExecutionMode.ForceParallelism> value to instruct PLINQ to always run the query as parallel.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d0e81-117">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="d0e81-117">Compiling the Code</span></span>  
 <span data-ttu-id="d0e81-118">Bu kodu kesip [PLINQ veri örneği](../../../docs/standard/parallel-programming/plinq-data-sample.md) ve yöntemi çağırın `Main`.</span><span class="sxs-lookup"><span data-stu-id="d0e81-118">Cut and paste this code into the [PLINQ Data Sample](../../../docs/standard/parallel-programming/plinq-data-sample.md) and call the method from `Main`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0e81-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d0e81-119">See Also</span></span>  
 <xref:System.Linq.ParallelEnumerable.AsSequential%2A>  
 [<span data-ttu-id="d0e81-120">Paralel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="d0e81-120">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
