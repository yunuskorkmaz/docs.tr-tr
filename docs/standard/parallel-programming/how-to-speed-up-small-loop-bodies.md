---
title: 'Nasıl yapılır: Küçük Döngü Gövdelerini Hızlandırma'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallel loops, how to speed up
ms.assetid: c7a66677-cb59-4cbf-969a-d2e8fc61a6ce
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c5cb872acbe496f1f27ee9065dd3b276bbed349b
ms.sourcegitcommit: 67de6cb5dd66a19f2180ba7e4d7aecc697f8a963
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44341662"
---
# <a name="how-to-speed-up-small-loop-bodies"></a><span data-ttu-id="e5b67-102">Nasıl yapılır: Küçük Döngü Gövdelerini Hızlandırma</span><span class="sxs-lookup"><span data-stu-id="e5b67-102">How to: Speed Up Small Loop Bodies</span></span>
<span data-ttu-id="e5b67-103">Olduğunda bir <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> döngüye sahip küçük bir gövde, eşdeğer sıralı döngü daha yavaş, gibi gerçekleştirebileceğiniz [için](~/docs/csharp/language-reference/keywords/for.md) döngüde C# ve [için](https://msdn.microsoft.com/library/c470a263-9b49-4308-8fd6-8592b84a7980) Visual Basic'te döngü.</span><span class="sxs-lookup"><span data-stu-id="e5b67-103">When a <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> loop has a small body, it might perform more slowly than the equivalent sequential loop, such as the [for](~/docs/csharp/language-reference/keywords/for.md) loop in C# and the [For](https://msdn.microsoft.com/library/c470a263-9b49-4308-8fd6-8592b84a7980) loop in Visual Basic.</span></span> <span data-ttu-id="e5b67-104">Yavaş performans verileri ve her döngü yinelemesinin bir Temsilcide çağırma maliyeti Bölümlemede yükü nedeniyle oluşur.</span><span class="sxs-lookup"><span data-stu-id="e5b67-104">Slower performance is caused by the overhead involved in partitioning the data and the cost of invoking a delegate on each loop iteration.</span></span> <span data-ttu-id="e5b67-105">Bu tür senaryolara <xref:System.Collections.Concurrent.Partitioner> sağlar sınıfını <xref:System.Collections.Concurrent.Partitioner.Create%2A?displayProperty=nameWithType> yöntemi temsilci gövdesi için sıralı döngü girmenize olanak tanır ve böylece temsilci yineleme başına bir kez yerine bir bölüm başına yalnızca bir kez çağrılır.</span><span class="sxs-lookup"><span data-stu-id="e5b67-105">To address such scenarios, the <xref:System.Collections.Concurrent.Partitioner> class provides the <xref:System.Collections.Concurrent.Partitioner.Create%2A?displayProperty=nameWithType> method, which enables you to provide a sequential loop for the delegate body, so that the delegate is invoked only once per partition, instead of once per iteration.</span></span> <span data-ttu-id="e5b67-106">Daha fazla bilgi için [PLINQ ve TPL için özel Bölümleyiciler](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md).</span><span class="sxs-lookup"><span data-stu-id="e5b67-106">For more information, see [Custom Partitioners for PLINQ and TPL](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e5b67-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="e5b67-107">Example</span></span>  
 [!code-csharp[TPL_Partitioners#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioner01.cs#01)]
 [!code-vb[TPL_Partitioners#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_partitioners/vb/partitionercreate01.vb#01)]  
  
 <span data-ttu-id="e5b67-108">Bu örnekte gösterilen yaklaşım, döngünün en az miktarda iş gerçekleştirdiğinde kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="e5b67-108">The approach demonstrated in this example is useful when the loop performs a minimal amount of work.</span></span> <span data-ttu-id="e5b67-109">İş daha hesaplama açısından pahalı hale geldiğinde, büyük olasılıkla aynı veya daha iyi performans kullanarak erişmenizi sağlayacak bir <xref:System.Threading.Tasks.Parallel.For%2A> veya <xref:System.Threading.Tasks.Parallel.ForEach%2A> varsayılan bölümleyici ile döngüsü.</span><span class="sxs-lookup"><span data-stu-id="e5b67-109">As the work becomes more computationally expensive, you will probably get the same or better performance by using a <xref:System.Threading.Tasks.Parallel.For%2A> or <xref:System.Threading.Tasks.Parallel.ForEach%2A> loop with the default partitioner.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5b67-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e5b67-110">See also</span></span>

- [<span data-ttu-id="e5b67-111">Veri Paralelliği</span><span class="sxs-lookup"><span data-stu-id="e5b67-111">Data Parallelism</span></span>](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)  
- [<span data-ttu-id="e5b67-112">PLINQ ve TPL için Özel Bölümleyiciler</span><span class="sxs-lookup"><span data-stu-id="e5b67-112">Custom Partitioners for PLINQ and TPL</span></span>](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md)  
- [<span data-ttu-id="e5b67-113">Yineleyiciler</span><span class="sxs-lookup"><span data-stu-id="e5b67-113">Iterators</span></span>](https://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7)  
- [<span data-ttu-id="e5b67-114">PLINQ ve TPL'deki Lambda İfadeleri</span><span class="sxs-lookup"><span data-stu-id="e5b67-114">Lambda Expressions in PLINQ and TPL</span></span>](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
