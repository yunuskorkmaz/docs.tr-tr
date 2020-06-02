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
ms.openlocfilehash: 4983cafb9d4a72262dc7a6a6c37fab23937b3274
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288088"
---
# <a name="how-to-speed-up-small-loop-bodies"></a><span data-ttu-id="9fb32-102">Nasıl yapılır: Küçük Döngü Gövdelerini Hızlandırma</span><span class="sxs-lookup"><span data-stu-id="9fb32-102">How to: Speed Up Small Loop Bodies</span></span>
<span data-ttu-id="9fb32-103">Bir <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> döngünün küçük bir gövdesi olduğunda, C# ' deki [for](../../csharp/language-reference/keywords/for.md) döngüsü ve Visual Basic [for](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/44kykk21(v=vs.90)) döngüsü gibi eşdeğer sıralı döngüden daha yavaş çalışabilir.</span><span class="sxs-lookup"><span data-stu-id="9fb32-103">When a <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> loop has a small body, it might perform more slowly than the equivalent sequential loop, such as the [for](../../csharp/language-reference/keywords/for.md) loop in C# and the [For](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/44kykk21(v=vs.90)) loop in Visual Basic.</span></span> <span data-ttu-id="9fb32-104">Verilerin bölümlenmesi ve her döngü yinelemesinde bir temsilciyi çağırma maliyeti nedeniyle daha yavaş performans oluşur.</span><span class="sxs-lookup"><span data-stu-id="9fb32-104">Slower performance is caused by the overhead involved in partitioning the data and the cost of invoking a delegate on each loop iteration.</span></span> <span data-ttu-id="9fb32-105">Bu tür senaryolara yönelik olarak, <xref:System.Collections.Concurrent.Partitioner> sınıfı, temsilci <xref:System.Collections.Concurrent.Partitioner.Create%2A?displayProperty=nameWithType> gövdesi için sıralı bir döngü sağlamanıza olanak tanıyan yöntemini sağlar. böylece, temsilci her yineleme için bir kez değil, her bölüm için yalnızca bir kez çağırılır.</span><span class="sxs-lookup"><span data-stu-id="9fb32-105">To address such scenarios, the <xref:System.Collections.Concurrent.Partitioner> class provides the <xref:System.Collections.Concurrent.Partitioner.Create%2A?displayProperty=nameWithType> method, which enables you to provide a sequential loop for the delegate body, so that the delegate is invoked only once per partition, instead of once per iteration.</span></span> <span data-ttu-id="9fb32-106">Daha fazla bilgi için bkz. [PLıNQ ve TPL Için Özel Bölümleyiciler](custom-partitioners-for-plinq-and-tpl.md).</span><span class="sxs-lookup"><span data-stu-id="9fb32-106">For more information, see [Custom Partitioners for PLINQ and TPL](custom-partitioners-for-plinq-and-tpl.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9fb32-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="9fb32-107">Example</span></span>  
 [!code-csharp[TPL_Partitioners#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioner01.cs#01)]
 [!code-vb[TPL_Partitioners#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_partitioners/vb/partitionercreate01.vb#01)]  
  
 <span data-ttu-id="9fb32-108">Bu örnekte gösterilen yaklaşım, döngü en az miktarda iş gerçekleştirdiğinde kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="9fb32-108">The approach demonstrated in this example is useful when the loop performs a minimal amount of work.</span></span> <span data-ttu-id="9fb32-109">Çalışma daha pahalı hale geldiği için, <xref:System.Threading.Tasks.Parallel.For%2A> varsayılan bölümleyici ile veya döngüsünü kullanarak büyük olasılıkla aynı veya daha iyi bir performans alacaksınız <xref:System.Threading.Tasks.Parallel.ForEach%2A> .</span><span class="sxs-lookup"><span data-stu-id="9fb32-109">As the work becomes more computationally expensive, you will probably get the same or better performance by using a <xref:System.Threading.Tasks.Parallel.For%2A> or <xref:System.Threading.Tasks.Parallel.ForEach%2A> loop with the default partitioner.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9fb32-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9fb32-110">See also</span></span>

- [<span data-ttu-id="9fb32-111">Veri paralelliği</span><span class="sxs-lookup"><span data-stu-id="9fb32-111">Data Parallelism</span></span>](data-parallelism-task-parallel-library.md)
- [<span data-ttu-id="9fb32-112">PLıNQ ve TPL için Özel Bölümleyiciler</span><span class="sxs-lookup"><span data-stu-id="9fb32-112">Custom Partitioners for PLINQ and TPL</span></span>](custom-partitioners-for-plinq-and-tpl.md)
- [<span data-ttu-id="9fb32-113">Yineleyiciler (C#)</span><span class="sxs-lookup"><span data-stu-id="9fb32-113">Iterators (C#)</span></span>](../../csharp/programming-guide/concepts/iterators.md)
- [<span data-ttu-id="9fb32-114">Yineleyiciler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9fb32-114">Iterators (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/iterators.md)
- [<span data-ttu-id="9fb32-115">PLıNQ ve TPL 'deki lambda Ifadeleri</span><span class="sxs-lookup"><span data-stu-id="9fb32-115">Lambda Expressions in PLINQ and TPL</span></span>](lambda-expressions-in-plinq-and-tpl.md)
