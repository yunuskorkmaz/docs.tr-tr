---
description: "Şu konuda daha fazla bilgi edinin: nasıl yapılır: PLıNQ 'te yürütme modunu belirtme"
title: "Nasıl yapılır: PLINQ'te Yürütme Modunu Belirtme"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to use execution mode
ms.assetid: e52ff26c-c5d3-4fab-9fec-c937fb387963
ms.openlocfilehash: f897a7a2f60da1747b4cec253a98fd5608eb0f61
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99641583"
---
# <a name="how-to-specify-the-execution-mode-in-plinq"></a><span data-ttu-id="1f6e4-103">Nasıl yapılır: PLINQ'te Yürütme Modunu Belirtme</span><span class="sxs-lookup"><span data-stu-id="1f6e4-103">How to: Specify the Execution Mode in PLINQ</span></span>

<span data-ttu-id="1f6e4-104">Bu örnekte, PLıNQ 'ın varsayılan buluşsal yöntemlerini atlaması ve sorgu şeklinin ne olursa olsun bir sorgu paralel hale getirmek nasıl zorlanacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1f6e4-104">This example shows how to force PLINQ to bypass its default heuristics and parallelize a query regardless of the query's shape.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1f6e4-105">Bu örnek, kullanımı göstermeye yöneliktir ve eşdeğer sıralı LINQ to Objects sorgusundan daha hızlı çalışmayabilir.</span><span class="sxs-lookup"><span data-stu-id="1f6e4-105">This example is intended to demonstrate usage and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="1f6e4-106">Hızlı yedekleme hakkında daha fazla bilgi için bkz. [PLıNQ 'Te hızlı hızlandırı anlama](understanding-speedup-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="1f6e4-106">For more information about speedup, see [Understanding Speedup in PLINQ](understanding-speedup-in-plinq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1f6e4-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="1f6e4-107">Example</span></span>  

 [!code-csharp[PLINQ#22](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#22)]
 [!code-vb[PLINQ#22](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#22)]  
  
 <span data-ttu-id="1f6e4-108">PLıNQ, paralelleştirme için fırsatlardan yararlanmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="1f6e4-108">PLINQ is designed to exploit opportunities for parallelization.</span></span> <span data-ttu-id="1f6e4-109">Ancak, tüm sorgular paralel yürütmeden faydalanır.</span><span class="sxs-lookup"><span data-stu-id="1f6e4-109">However, not all queries benefit from parallel execution.</span></span> <span data-ttu-id="1f6e4-110">Örneğin, bir sorgu çok az iş yapan tek bir kullanıcı temsilcisi içerdiğinde, sorgu genellikle sırayla daha hızlı çalışır.</span><span class="sxs-lookup"><span data-stu-id="1f6e4-110">For example, when a query contains a single user delegate that does little work, the query will usually run faster sequentially.</span></span> <span data-ttu-id="1f6e4-111">Paralel yürütme daha hızlıdır, çünkü paralelleştirme yürütmesinin etkinleştirilmesindeki ek yük, elde edilen hızlı hale getirme özelliğinden daha pahalıdır.</span><span class="sxs-lookup"><span data-stu-id="1f6e4-111">Sequential execution is faster because the overhead involved in enabling parallelizing execution is more expensive than the speedup that's obtained.</span></span> <span data-ttu-id="1f6e4-112">Bu nedenle, PLıNQ her sorguyu otomatik olarak paralel hale getirmek.</span><span class="sxs-lookup"><span data-stu-id="1f6e4-112">Therefore, PLINQ does not automatically parallelize every query.</span></span> <span data-ttu-id="1f6e4-113">Önce sorgunun şeklini ve onu oluşturan çeşitli işleçleri inceler.</span><span class="sxs-lookup"><span data-stu-id="1f6e4-113">It first examines the shape of the query and the various operators that comprise it.</span></span> <span data-ttu-id="1f6e4-114">Bu analize dayalı olarak, varsayılan yürütme modundaki PLıNQ sorgunun bir kısmını veya tümünü ardışık olarak yürütmeye karar verebilir.</span><span class="sxs-lookup"><span data-stu-id="1f6e4-114">Based on this analysis, PLINQ in the default execution mode may decide to execute some or all of the query sequentially.</span></span> <span data-ttu-id="1f6e4-115">Ancak bazı durumlarda, sorgunuz hakkında PLıNQ ' den daha fazla bilgi sahibi olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1f6e4-115">However, in some cases you may know more about your query than PLINQ is able to determine from its analysis.</span></span> <span data-ttu-id="1f6e4-116">Örneğin, bir temsilcinin pahalı olduğunu ve sorgunun paralelleştirmeyi kesinlikle yararlı olacağını bilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1f6e4-116">For example, you may know that a delegate is expensive and that the query will definitely benefit from parallelization.</span></span> <span data-ttu-id="1f6e4-117">Bu gibi durumlarda <xref:System.Linq.ParallelEnumerable.WithExecutionMode%2A> yöntemini kullanabilir ve <xref:System.Linq.ParallelExecutionMode.ForceParallelism> PLINQ 'ın sorguyu her zaman paralel olarak çalıştırmasını istemek için değeri belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1f6e4-117">In such cases, you can use the <xref:System.Linq.ParallelEnumerable.WithExecutionMode%2A> method and specify the <xref:System.Linq.ParallelExecutionMode.ForceParallelism> value to instruct PLINQ to always run the query as parallel.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="1f6e4-118">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="1f6e4-118">Compiling the Code</span></span>  

 <span data-ttu-id="1f6e4-119">Bu kodu kesip [PLINQ veri örneğine](plinq-data-sample.md) yapıştırın ve öğesinden yöntemi çağırın `Main` .</span><span class="sxs-lookup"><span data-stu-id="1f6e4-119">Cut and paste this code into the [PLINQ Data Sample](plinq-data-sample.md) and call the method from `Main`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f6e4-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1f6e4-120">See also</span></span>

- <xref:System.Linq.ParallelEnumerable.AsSequential%2A>
- [<span data-ttu-id="1f6e4-121">Paralel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="1f6e4-121">Parallel LINQ (PLINQ)</span></span>](introduction-to-plinq.md)
