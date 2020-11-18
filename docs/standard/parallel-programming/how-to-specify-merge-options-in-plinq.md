---
title: "Nasıl yapılır: PLINQ'te Birleştirme Seçeneklerini Belirtme"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to use merge options
ms.assetid: 0f33b527-e91a-4550-a39a-e63e396fd831
ms.openlocfilehash: 91c5ac91538942368b66399bf0bc0132a15bf667
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94825604"
---
# <a name="how-to-specify-merge-options-in-plinq"></a><span data-ttu-id="bceac-102">Nasıl yapılır: PLINQ'te Birleştirme Seçeneklerini Belirtme</span><span class="sxs-lookup"><span data-stu-id="bceac-102">How to: Specify Merge Options in PLINQ</span></span>
<span data-ttu-id="bceac-103">Bu örnekte, bir PLıNQ sorgusunda sonraki tüm işleçlere uygulanacak birleştirme seçeneklerinin nasıl ayarlanacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="bceac-103">This example shows how to specify the merge options that will apply to all subsequent operators in a PLINQ query.</span></span> <span data-ttu-id="bceac-104">Birleştirme seçeneklerini açıkça ayarlamanız gerekmez, ancak bunu yapmak performansı iyileştirebilir.</span><span class="sxs-lookup"><span data-stu-id="bceac-104">You do not have to set merge options explicitly, but doing so may improve performance.</span></span> <span data-ttu-id="bceac-105">Birleştirme seçenekleri hakkında daha fazla bilgi için bkz. [PLıNQ Içindeki birleştirme seçenekleri](merge-options-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="bceac-105">For more information about merge options, see [Merge Options in PLINQ](merge-options-in-plinq.md).</span></span>  
  
> [!WARNING]
> <span data-ttu-id="bceac-106">Bu örnek, kullanımı göstermeye yöneliktir ve eşdeğer sıralı LINQ to Objects sorgusundan daha hızlı çalışmayabilir.</span><span class="sxs-lookup"><span data-stu-id="bceac-106">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="bceac-107">Hızlı yedekleme hakkında daha fazla bilgi için bkz. [PLıNQ 'Te hızlı hızlandırı anlama](understanding-speedup-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="bceac-107">For more information about speedup, see [Understanding Speedup in PLINQ](understanding-speedup-in-plinq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="bceac-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="bceac-108">Example</span></span>  
 <span data-ttu-id="bceac-109">Aşağıdaki örnek, sıralanmamış bir kaynağı olan temel bir senaryoda birleştirme seçeneklerinin davranışını gösterir ve her öğeye pahalı bir işlev uygular.</span><span class="sxs-lookup"><span data-stu-id="bceac-109">The following example demonstrates the behavior of merge options in a basic scenario that has an unordered source and applies an expensive function to every element.</span></span>  
  
 [!code-csharp[PLINQ#23](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#23)]
 [!code-vb[PLINQ#23](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#23)]  
  
 <span data-ttu-id="bceac-110"><xref:System.Linq.ParallelMergeOptions.AutoBuffered>Seçeneğin ilk öğeden önce istenmeyen bir gecikme olduğu durumlarda, <xref:System.Linq.ParallelMergeOptions.NotBuffered> sonuç öğelerini daha hızlı ve daha sorunsuz bir şekilde sunun seçeneğini deneyin.</span><span class="sxs-lookup"><span data-stu-id="bceac-110">In cases where the <xref:System.Linq.ParallelMergeOptions.AutoBuffered> option incurs an undesirable latency before the first element is yielded, try the <xref:System.Linq.ParallelMergeOptions.NotBuffered> option to yield result elements faster and more smoothly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bceac-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bceac-111">See also</span></span>

- <xref:System.Linq.ParallelMergeOptions>
- [<span data-ttu-id="bceac-112">Paralel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="bceac-112">Parallel LINQ (PLINQ)</span></span>](introduction-to-plinq.md)
