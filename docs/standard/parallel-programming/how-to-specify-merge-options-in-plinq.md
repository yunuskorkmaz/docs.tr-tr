---
title: "Nasıl yapılır: PLINQ'te Birleştirme Seçeneklerini Belirtme"
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to use merge options
ms.assetid: 0f33b527-e91a-4550-a39a-e63e396fd831
ms.openlocfilehash: e98ede3664a8815c60a490239a789c69fa557895
ms.sourcegitcommit: 961ec21c22d2f1d55c9cc8a7edf2ade1d1fd92e3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2020
ms.locfileid: "80588553"
---
# <a name="how-to-specify-merge-options-in-plinq"></a><span data-ttu-id="16f2d-102">Nasıl yapılır: PLINQ'te Birleştirme Seçeneklerini Belirtme</span><span class="sxs-lookup"><span data-stu-id="16f2d-102">How to: Specify Merge Options in PLINQ</span></span>
<span data-ttu-id="16f2d-103">Bu örnek, plinq sorgusunda sonraki tüm işleçler için geçerli olacak birleştirme seçeneklerini nasıl belirteceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="16f2d-103">This example shows how to specify the merge options that will apply to all subsequent operators in a PLINQ query.</span></span> <span data-ttu-id="16f2d-104">Birleştirme seçeneklerini açıkça ayarlamanız gerekmez, ancak bunu yapmak performansı artırabilir.</span><span class="sxs-lookup"><span data-stu-id="16f2d-104">You do not have to set merge options explicitly, but doing so may improve performance.</span></span> <span data-ttu-id="16f2d-105">Birleştirme seçenekleri hakkında daha fazla bilgi için [PLINQ'da Birleştirme Seçenekleri'ne](../../../docs/standard/parallel-programming/merge-options-in-plinq.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="16f2d-105">For more information about merge options, see [Merge Options in PLINQ](../../../docs/standard/parallel-programming/merge-options-in-plinq.md).</span></span>  
  
> [!WARNING]
> <span data-ttu-id="16f2d-106">Bu örnek, kullanımı göstermek için tasarlanmıştır ve Nesneler sorgusuna eşdeğer ardışık LINQ'dan daha hızlı çalışmayabilir.</span><span class="sxs-lookup"><span data-stu-id="16f2d-106">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="16f2d-107">Hız hakkında daha fazla bilgi için [PLINQ'da Hızları Anlama'ya](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="16f2d-107">For more information about speedup, see [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="16f2d-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="16f2d-108">Example</span></span>  
 <span data-ttu-id="16f2d-109">Aşağıdaki örnek, sıralanmamış bir kaynağa sahip ve her öğeiçin pahalı bir işlev uygulayan temel bir senaryoda birleştirme seçeneklerinin davranışını gösterir.</span><span class="sxs-lookup"><span data-stu-id="16f2d-109">The following example demonstrates the behavior of merge options in a basic scenario that has an unordered source and applies an expensive function to every element.</span></span>  
  
 [!code-csharp[PLINQ#23](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#23)]
 [!code-vb[PLINQ#23](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#23)]  
  
 <span data-ttu-id="16f2d-110">Seçeneğin <xref:System.Linq.ParallelMergeOptions.AutoBuffered> ilk öğe verilmeden önce istenmeyen bir gecikmeye neden olduğu durumlarda, sonuç öğelerini <xref:System.Linq.ParallelMergeOptions.NotBuffered> daha hızlı ve daha sorunsuz bir şekilde verim verme seçeneğini deneyin.</span><span class="sxs-lookup"><span data-stu-id="16f2d-110">In cases where the <xref:System.Linq.ParallelMergeOptions.AutoBuffered> option incurs an undesirable latency before the first element is yielded, try the <xref:System.Linq.ParallelMergeOptions.NotBuffered> option to yield result elements faster and more smoothly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16f2d-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="16f2d-111">See also</span></span>

- <xref:System.Linq.ParallelMergeOptions>
- [<span data-ttu-id="16f2d-112">Paralel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="16f2d-112">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/introduction-to-plinq.md)
