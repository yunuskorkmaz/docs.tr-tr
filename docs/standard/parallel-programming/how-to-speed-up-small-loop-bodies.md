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
ms.openlocfilehash: c91aecee226b52d9045f3bd95a05c234abac8c96
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90548318"
---
# <a name="how-to-speed-up-small-loop-bodies"></a><span data-ttu-id="bf8f7-102">Nasıl yapılır: Küçük Döngü Gövdelerini Hızlandırma</span><span class="sxs-lookup"><span data-stu-id="bf8f7-102">How to: Speed Up Small Loop Bodies</span></span>
<span data-ttu-id="bf8f7-103">Bir <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> döngünün küçük bir gövdesi olduğunda, C# ' deki [for](../../csharp/language-reference/keywords/for.md) döngüsü ve Visual Basic [for](/previous-versions/visualstudio/visual-studio-2008/44kykk21(v=vs.90)) döngüsü gibi eşdeğer sıralı döngüden daha yavaş çalışabilir.</span><span class="sxs-lookup"><span data-stu-id="bf8f7-103">When a <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> loop has a small body, it might perform more slowly than the equivalent sequential loop, such as the [for](../../csharp/language-reference/keywords/for.md) loop in C# and the [For](/previous-versions/visualstudio/visual-studio-2008/44kykk21(v=vs.90)) loop in Visual Basic.</span></span> <span data-ttu-id="bf8f7-104">Verilerin bölümlenmesi ve her döngü yinelemesinde bir temsilciyi çağırma maliyeti nedeniyle daha yavaş performans oluşur.</span><span class="sxs-lookup"><span data-stu-id="bf8f7-104">Slower performance is caused by the overhead involved in partitioning the data and the cost of invoking a delegate on each loop iteration.</span></span> <span data-ttu-id="bf8f7-105">Bu tür senaryolara yönelik olarak, <xref:System.Collections.Concurrent.Partitioner> sınıfı, temsilci <xref:System.Collections.Concurrent.Partitioner.Create%2A?displayProperty=nameWithType> gövdesi için sıralı bir döngü sağlamanıza olanak tanıyan yöntemini sağlar. böylece, temsilci her yineleme için bir kez değil, her bölüm için yalnızca bir kez çağırılır.</span><span class="sxs-lookup"><span data-stu-id="bf8f7-105">To address such scenarios, the <xref:System.Collections.Concurrent.Partitioner> class provides the <xref:System.Collections.Concurrent.Partitioner.Create%2A?displayProperty=nameWithType> method, which enables you to provide a sequential loop for the delegate body, so that the delegate is invoked only once per partition, instead of once per iteration.</span></span> <span data-ttu-id="bf8f7-106">Daha fazla bilgi için bkz. [PLıNQ ve TPL Için Özel Bölümleyiciler](custom-partitioners-for-plinq-and-tpl.md).</span><span class="sxs-lookup"><span data-stu-id="bf8f7-106">For more information, see [Custom Partitioners for PLINQ and TPL](custom-partitioners-for-plinq-and-tpl.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="bf8f7-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="bf8f7-107">Example</span></span>  
 [!code-csharp[TPL_Partitioners#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioner01.cs#01)]
 [!code-vb[TPL_Partitioners#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_partitioners/vb/partitionercreate01.vb#01)]  
  
 <span data-ttu-id="bf8f7-108">Bu örnekte gösterilen yaklaşım, döngü en az miktarda iş gerçekleştirdiğinde kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="bf8f7-108">The approach demonstrated in this example is useful when the loop performs a minimal amount of work.</span></span> <span data-ttu-id="bf8f7-109">Çalışma daha pahalı hale geldiği için, <xref:System.Threading.Tasks.Parallel.For%2A> varsayılan bölümleyici ile veya döngüsünü kullanarak büyük olasılıkla aynı veya daha iyi bir performans alacaksınız <xref:System.Threading.Tasks.Parallel.ForEach%2A> .</span><span class="sxs-lookup"><span data-stu-id="bf8f7-109">As the work becomes more computationally expensive, you will probably get the same or better performance by using a <xref:System.Threading.Tasks.Parallel.For%2A> or <xref:System.Threading.Tasks.Parallel.ForEach%2A> loop with the default partitioner.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf8f7-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bf8f7-110">See also</span></span>

- [<span data-ttu-id="bf8f7-111">Veri paralelliği</span><span class="sxs-lookup"><span data-stu-id="bf8f7-111">Data Parallelism</span></span>](data-parallelism-task-parallel-library.md)
- [<span data-ttu-id="bf8f7-112">PLıNQ ve TPL için Özel Bölümleyiciler</span><span class="sxs-lookup"><span data-stu-id="bf8f7-112">Custom Partitioners for PLINQ and TPL</span></span>](custom-partitioners-for-plinq-and-tpl.md)
- [<span data-ttu-id="bf8f7-113">Yineleyiciler (C#)</span><span class="sxs-lookup"><span data-stu-id="bf8f7-113">Iterators (C#)</span></span>](../../csharp/programming-guide/concepts/iterators.md)
- [<span data-ttu-id="bf8f7-114">Yineleyiciler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bf8f7-114">Iterators (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/iterators.md)
- [<span data-ttu-id="bf8f7-115">PLıNQ ve TPL 'deki lambda Ifadeleri</span><span class="sxs-lookup"><span data-stu-id="bf8f7-115">Lambda Expressions in PLINQ and TPL</span></span>](lambda-expressions-in-plinq-and-tpl.md)
