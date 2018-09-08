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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8914d3c443971f73e6f3fa366c26567bae60dbe1
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44135061"
---
# <a name="how-to-specify-merge-options-in-plinq"></a><span data-ttu-id="cf32a-102">Nasıl yapılır: PLINQ'te Birleştirme Seçeneklerini Belirtme</span><span class="sxs-lookup"><span data-stu-id="cf32a-102">How to: Specify Merge Options in PLINQ</span></span>
<span data-ttu-id="cf32a-103">Bu örnekte, izleyen tüm işleçler sırayla bir PLINQ sorgusu uygulanacağı birleştirme seçeneklerini belirtme gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="cf32a-103">This example shows how to specify the merge options that will apply to all subsequent operators in a PLINQ query.</span></span> <span data-ttu-id="cf32a-104">Birleştirme seçeneklerini açıkça ayarlamak zorunda değildir, ancak bunun yapılması, bu nedenle performansını artırabilir.</span><span class="sxs-lookup"><span data-stu-id="cf32a-104">You do not have to set merge options explicitly, but doing so may improve performance.</span></span> <span data-ttu-id="cf32a-105">Birleştirme seçenekleri hakkında daha fazla bilgi için bkz. [plınq'te birleştirme seçeneklerini](../../../docs/standard/parallel-programming/merge-options-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="cf32a-105">For more information about merge options, see [Merge Options in PLINQ](../../../docs/standard/parallel-programming/merge-options-in-plinq.md).</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="cf32a-106">Bu örnek, kullanımını göstermek için tasarlanmıştır ve nesneleri sorgu için eşdeğer sıralı LINQ daha hızlı çalışmayabilir.</span><span class="sxs-lookup"><span data-stu-id="cf32a-106">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="cf32a-107">Hızlandırmayı hakkında daha fazla bilgi için bkz: [plınq'te hızlandırmayı anlama](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="cf32a-107">For more information about speedup, see [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="cf32a-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="cf32a-108">Example</span></span>  
 <span data-ttu-id="cf32a-109">Aşağıdaki örnek, sırasız bir kaynak ve pahalı bir işlev her öğe için geçerli bir temel senaryosunda birleştirme seçeneklerini davranışını gösterir.</span><span class="sxs-lookup"><span data-stu-id="cf32a-109">The following example demonstrates the behavior of merge options in a basic scenario that has an unordered source and applies an expensive function to every element.</span></span>  
  
 [!code-csharp[PLINQ#23](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#23)]
 [!code-vb[PLINQ#23](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#23)]  
  
 <span data-ttu-id="cf32a-110">Durumlarda burada <xref:System.Linq.ParallelMergeOptions.AutoBuffered> ilk öğeyi veriyor önce seçeneği doğurur istenmeyen bir gecikme süresi, deneyin <xref:System.Linq.ParallelMergeOptions.NotBuffered> sonuç öğeleri daha hızlı ve daha sorunsuz bir şekilde ulaşmazsa seçeneği.</span><span class="sxs-lookup"><span data-stu-id="cf32a-110">In cases where the <xref:System.Linq.ParallelMergeOptions.AutoBuffered> option incurs an undesirable latency before the first element is yielded, try the <xref:System.Linq.ParallelMergeOptions.NotBuffered> option to yield result elements faster and more smoothly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf32a-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cf32a-111">See also</span></span>

- <xref:System.Linq.ParallelMergeOptions>  
- [<span data-ttu-id="cf32a-112">Paralel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="cf32a-112">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
