---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: küçük döngü gövdelerini hızlandırma'
title: 'Nasıl yapılır: Küçük Döngü Gövdelerini Hızlandırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallel loops, how to speed up
ms.assetid: c7a66677-cb59-4cbf-969a-d2e8fc61a6ce
ms.openlocfilehash: 6505aae545959266e94fd866f7e4cd8643cffb65
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99629519"
---
# <a name="how-to-speed-up-small-loop-bodies"></a><span data-ttu-id="5dd59-103">Nasıl yapılır: Küçük Döngü Gövdelerini Hızlandırma</span><span class="sxs-lookup"><span data-stu-id="5dd59-103">How to: Speed Up Small Loop Bodies</span></span>

<span data-ttu-id="5dd59-104">Bir <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> döngünün küçük bir gövdesi olduğunda, C# ' deki [for](../../csharp/language-reference/keywords/for.md) döngüsü ve Visual Basic [for](/previous-versions/visualstudio/visual-studio-2008/44kykk21(v=vs.90)) döngüsü gibi eşdeğer sıralı döngüden daha yavaş çalışabilir.</span><span class="sxs-lookup"><span data-stu-id="5dd59-104">When a <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> loop has a small body, it might perform more slowly than the equivalent sequential loop, such as the [for](../../csharp/language-reference/keywords/for.md) loop in C# and the [For](/previous-versions/visualstudio/visual-studio-2008/44kykk21(v=vs.90)) loop in Visual Basic.</span></span> <span data-ttu-id="5dd59-105">Verilerin bölümlenmesi ve her döngü yinelemesinde bir temsilciyi çağırma maliyeti nedeniyle daha yavaş performans oluşur.</span><span class="sxs-lookup"><span data-stu-id="5dd59-105">Slower performance is caused by the overhead involved in partitioning the data and the cost of invoking a delegate on each loop iteration.</span></span> <span data-ttu-id="5dd59-106">Bu tür senaryolara yönelik olarak, <xref:System.Collections.Concurrent.Partitioner> sınıfı, temsilci <xref:System.Collections.Concurrent.Partitioner.Create%2A?displayProperty=nameWithType> gövdesi için sıralı bir döngü sağlamanıza olanak tanıyan yöntemini sağlar. böylece, temsilci her yineleme için bir kez değil, her bölüm için yalnızca bir kez çağırılır.</span><span class="sxs-lookup"><span data-stu-id="5dd59-106">To address such scenarios, the <xref:System.Collections.Concurrent.Partitioner> class provides the <xref:System.Collections.Concurrent.Partitioner.Create%2A?displayProperty=nameWithType> method, which enables you to provide a sequential loop for the delegate body, so that the delegate is invoked only once per partition, instead of once per iteration.</span></span> <span data-ttu-id="5dd59-107">Daha fazla bilgi için bkz. [PLıNQ ve TPL Için Özel Bölümleyiciler](custom-partitioners-for-plinq-and-tpl.md).</span><span class="sxs-lookup"><span data-stu-id="5dd59-107">For more information, see [Custom Partitioners for PLINQ and TPL](custom-partitioners-for-plinq-and-tpl.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5dd59-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="5dd59-108">Example</span></span>  

 [!code-csharp[TPL_Partitioners#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioner01.cs#01)]
 [!code-vb[TPL_Partitioners#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_partitioners/vb/partitionercreate01.vb#01)]  
  
 <span data-ttu-id="5dd59-109">Bu örnekte gösterilen yaklaşım, döngü en az miktarda iş gerçekleştirdiğinde kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="5dd59-109">The approach demonstrated in this example is useful when the loop performs a minimal amount of work.</span></span> <span data-ttu-id="5dd59-110">Çalışma daha pahalı hale geldiği için, <xref:System.Threading.Tasks.Parallel.For%2A> varsayılan bölümleyici ile veya döngüsünü kullanarak büyük olasılıkla aynı veya daha iyi bir performans alacaksınız <xref:System.Threading.Tasks.Parallel.ForEach%2A> .</span><span class="sxs-lookup"><span data-stu-id="5dd59-110">As the work becomes more computationally expensive, you will probably get the same or better performance by using a <xref:System.Threading.Tasks.Parallel.For%2A> or <xref:System.Threading.Tasks.Parallel.ForEach%2A> loop with the default partitioner.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5dd59-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5dd59-111">See also</span></span>

- [<span data-ttu-id="5dd59-112">Veri paralelliği</span><span class="sxs-lookup"><span data-stu-id="5dd59-112">Data Parallelism</span></span>](data-parallelism-task-parallel-library.md)
- [<span data-ttu-id="5dd59-113">PLıNQ ve TPL için Özel Bölümleyiciler</span><span class="sxs-lookup"><span data-stu-id="5dd59-113">Custom Partitioners for PLINQ and TPL</span></span>](custom-partitioners-for-plinq-and-tpl.md)
- [<span data-ttu-id="5dd59-114">Yineleyiciler (C#)</span><span class="sxs-lookup"><span data-stu-id="5dd59-114">Iterators (C#)</span></span>](../../csharp/programming-guide/concepts/iterators.md)
- [<span data-ttu-id="5dd59-115">Yineleyiciler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5dd59-115">Iterators (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/iterators.md)
- [<span data-ttu-id="5dd59-116">PLıNQ ve TPL 'deki lambda Ifadeleri</span><span class="sxs-lookup"><span data-stu-id="5dd59-116">Lambda Expressions in PLINQ and TPL</span></span>](lambda-expressions-in-plinq-and-tpl.md)
