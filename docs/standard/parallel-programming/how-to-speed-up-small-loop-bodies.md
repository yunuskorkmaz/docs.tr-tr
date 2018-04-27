---
title: 'Nasıl yapılır: Küçük Döngü Gövdelerini Hızlandırma'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallel loops, how to speed up
ms.assetid: c7a66677-cb59-4cbf-969a-d2e8fc61a6ce
caps.latest.revision: 18
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 856c2a60150cb7a376afb291e6806d7fc91f3d2b
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2018
---
# <a name="how-to-speed-up-small-loop-bodies"></a><span data-ttu-id="95399-102">Nasıl yapılır: Küçük Döngü Gövdelerini Hızlandırma</span><span class="sxs-lookup"><span data-stu-id="95399-102">How to: Speed Up Small Loop Bodies</span></span>
<span data-ttu-id="95399-103">Zaman bir <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> döngü sahip küçük bir gövde, eşdeğer sıralı döngü daha yavaş onu gibi gerçekleştirebileceğiniz [için](~/docs/csharp/language-reference/keywords/for.md) döngü C# ve [için](http://msdn.microsoft.com/library/c470a263-9b49-4308-8fd6-8592b84a7980) Visual Basic'te döngü.</span><span class="sxs-lookup"><span data-stu-id="95399-103">When a <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> loop has a small body, it might perform more slowly than the equivalent sequential loop, such as the [for](~/docs/csharp/language-reference/keywords/for.md) loop in C# and the [For](http://msdn.microsoft.com/library/c470a263-9b49-4308-8fd6-8592b84a7980) loop in Visual Basic.</span></span> <span data-ttu-id="95399-104">Performans verileri ve temsilci her döngü tekrarında üzerinde çağırma maliyet bölümlendirme söz konusu yükünü kaynaklanır.</span><span class="sxs-lookup"><span data-stu-id="95399-104">Slower performance is caused by the overhead involved in partitioning the data and the cost of invoking a delegate on each loop iteration.</span></span> <span data-ttu-id="95399-105">Bu tür senaryosu için <xref:System.Collections.Concurrent.Partitioner> sınıfı sağlar <xref:System.Collections.Concurrent.Partitioner.Create%2A?displayProperty=nameWithType> temsilci gövdesi için sıralı döngü vermenizi sağlar ve böylece temsilci yineleme başına bir kez yerine bölüm başına yalnızca bir kez çağrılır yöntemi.</span><span class="sxs-lookup"><span data-stu-id="95399-105">To address such scenarios, the <xref:System.Collections.Concurrent.Partitioner> class provides the <xref:System.Collections.Concurrent.Partitioner.Create%2A?displayProperty=nameWithType> method, which enables you to provide a sequential loop for the delegate body, so that the delegate is invoked only once per partition, instead of once per iteration.</span></span> <span data-ttu-id="95399-106">Daha fazla bilgi için bkz: [PLINQ ve TPL için özel Bölümleyiciler](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md).</span><span class="sxs-lookup"><span data-stu-id="95399-106">For more information, see [Custom Partitioners for PLINQ and TPL](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="95399-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="95399-107">Example</span></span>  
 [!code-csharp[TPL_Partitioners#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioner01.cs#01)]
 [!code-vb[TPL_Partitioners#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_partitioners/vb/partitionercreate01.vb#01)]  
  
 <span data-ttu-id="95399-108">Bu örnekte gösterilen yaklaşım, döngü iş en az miktarda gerçekleştirdiğinde kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="95399-108">The approach demonstrated in this example is useful when the loop performs a minimal amount of work.</span></span> <span data-ttu-id="95399-109">İş pkı'ya daha pahalı hale geldiğinde, büyük olasılıkla aynı veya daha iyi performans kullanarak karşılaşırsınız bir <xref:System.Threading.Tasks.Parallel.For%2A> veya <xref:System.Threading.Tasks.Parallel.ForEach%2A> döngü varsayılan bölümleyici ile.</span><span class="sxs-lookup"><span data-stu-id="95399-109">As the work becomes more computationally expensive, you will probably get the same or better performance by using a <xref:System.Threading.Tasks.Parallel.For%2A> or <xref:System.Threading.Tasks.Parallel.ForEach%2A> loop with the default partitioner.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95399-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="95399-110">See Also</span></span>  
 [<span data-ttu-id="95399-111">Veri Paralelliği</span><span class="sxs-lookup"><span data-stu-id="95399-111">Data Parallelism</span></span>](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)  
 [<span data-ttu-id="95399-112">PLINQ ve TPL için Özel Bölümleyiciler</span><span class="sxs-lookup"><span data-stu-id="95399-112">Custom Partitioners for PLINQ and TPL</span></span>](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md)  
 [<span data-ttu-id="95399-113">Yineleyiciler</span><span class="sxs-lookup"><span data-stu-id="95399-113">Iterators</span></span>](https://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7)  
 [<span data-ttu-id="95399-114">PLINQ ve TPL'deki Lambda İfadeleri</span><span class="sxs-lookup"><span data-stu-id="95399-114">Lambda Expressions in PLINQ and TPL</span></span>](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
