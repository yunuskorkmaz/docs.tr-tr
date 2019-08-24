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
ms.openlocfilehash: 705b6bc364e2ecf00c3629814228157c90017a8b
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/23/2019
ms.locfileid: "69988453"
---
# <a name="how-to-specify-the-execution-mode-in-plinq"></a><span data-ttu-id="e74fc-102">Nasıl yapılır: PLINQ'te Yürütme Modunu Belirtme</span><span class="sxs-lookup"><span data-stu-id="e74fc-102">How to: Specify the Execution Mode in PLINQ</span></span>
<span data-ttu-id="e74fc-103">Bu örnekte, PLıNQ 'ın varsayılan buluşsal yöntemlerini atlaması ve sorgu şeklinin ne olursa olsun bir sorgu paralel hale getirmek nasıl zorlanacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="e74fc-103">This example shows how to force PLINQ to bypass its default heuristics and parallelize a query regardless of the query's shape.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="e74fc-104">Bu örnek, kullanımı göstermeye yöneliktir ve eşdeğer sıralı LINQ to Objects sorgusundan daha hızlı çalışmayabilir.</span><span class="sxs-lookup"><span data-stu-id="e74fc-104">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="e74fc-105">Hızlı yedekleme hakkında daha fazla bilgi için bkz. [PLıNQ 'Te hızlı hızlandırı anlama](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="e74fc-105">For more information about speedup, see [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e74fc-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="e74fc-106">Example</span></span>  
 [!code-csharp[PLINQ#22](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#22)]
 [!code-vb[PLINQ#22](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#22)]  
  
 <span data-ttu-id="e74fc-107">PLıNQ, paralelleştirme için fırsatlardan yararlanmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="e74fc-107">PLINQ is designed to exploit opportunities for parallelization.</span></span> <span data-ttu-id="e74fc-108">Ancak, tüm sorgular paralel yürütmeden faydalanır.</span><span class="sxs-lookup"><span data-stu-id="e74fc-108">However, not all queries benefit from parallel execution.</span></span> <span data-ttu-id="e74fc-109">Örneğin, bir sorgu çok az iş yapan tek bir kullanıcı temsilcisi içerdiğinde, sorgu genellikle sırayla daha hızlı çalışır.</span><span class="sxs-lookup"><span data-stu-id="e74fc-109">For example, when a query contains a single user delegate that does very little work, the query will usually run faster sequentially.</span></span> <span data-ttu-id="e74fc-110">Bunun nedeni, paralelleştirme yürütmesinin etkinleştirilmesi ile ilgili ek yükün elde edilen hızlı hale getirme sürecinden daha pahalıdır.</span><span class="sxs-lookup"><span data-stu-id="e74fc-110">This is because the overhead involved in enabling parallelizing execution is more expensive than the speedup that is obtained.</span></span> <span data-ttu-id="e74fc-111">Bu nedenle, PLıNQ her sorguyu otomatik olarak paralel hale getirmek.</span><span class="sxs-lookup"><span data-stu-id="e74fc-111">Therefore, PLINQ does not automatically parallelize every query.</span></span> <span data-ttu-id="e74fc-112">Önce sorgunun şeklini ve onu oluşturan çeşitli işleçleri inceler.</span><span class="sxs-lookup"><span data-stu-id="e74fc-112">It first examines the shape of the query and the various operators that comprise it.</span></span> <span data-ttu-id="e74fc-113">Bu analize dayalı olarak, varsayılan yürütme modundaki PLıNQ sorgunun bir kısmını veya tümünü ardışık olarak yürütmeye karar verebilir.</span><span class="sxs-lookup"><span data-stu-id="e74fc-113">Based on this analysis, PLINQ in the default execution mode may decide to execute some or all of the query sequentially.</span></span> <span data-ttu-id="e74fc-114">Ancak bazı durumlarda, sorgunuz hakkında PLıNQ ' den daha fazla bilgi sahibi olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e74fc-114">However, in some cases you may know more about your query than PLINQ is able to determine from its analysis.</span></span> <span data-ttu-id="e74fc-115">Örneğin, bir temsilcinin çok pahalı olduğunu ve sorgunun paralelleştirmeyi kesinlikle yararlı olacağını bilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e74fc-115">For example, you may know that a delegate is very expensive, and that the query will definitely benefit from parallelization.</span></span> <span data-ttu-id="e74fc-116">Bu gibi durumlarda <xref:System.Linq.ParallelEnumerable.WithExecutionMode%2A> yöntemini kullanabilir ve PLINQ 'ın sorguyu her zaman <xref:System.Linq.ParallelExecutionMode.ForceParallelism> paralel olarak çalıştırmasını istemek için değeri belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e74fc-116">In such cases, you can use the <xref:System.Linq.ParallelEnumerable.WithExecutionMode%2A> method and specify the <xref:System.Linq.ParallelExecutionMode.ForceParallelism> value to instruct PLINQ to always run the query as parallel.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e74fc-117">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="e74fc-117">Compiling the Code</span></span>  
 <span data-ttu-id="e74fc-118">Bu kodu kesip [PLINQ veri örneğine](../../../docs/standard/parallel-programming/plinq-data-sample.md) yapıştırın ve öğesinden `Main`yöntemi çağırın.</span><span class="sxs-lookup"><span data-stu-id="e74fc-118">Cut and paste this code into the [PLINQ Data Sample](../../../docs/standard/parallel-programming/plinq-data-sample.md) and call the method from `Main`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e74fc-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e74fc-119">See also</span></span>

- <xref:System.Linq.ParallelEnumerable.AsSequential%2A>
- [<span data-ttu-id="e74fc-120">Paralel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="e74fc-120">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
