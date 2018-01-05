---
title: "Nasıl yapılır: PLINQ'te Birleştirme Seçeneklerini Belirtme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: PLINQ queries, how to use merge options
ms.assetid: 0f33b527-e91a-4550-a39a-e63e396fd831
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 59ffff3019f10874bd2df977b80d46e903d13613
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-specify-merge-options-in-plinq"></a><span data-ttu-id="0a6de-102">Nasıl yapılır: PLINQ'te Birleştirme Seçeneklerini Belirtme</span><span class="sxs-lookup"><span data-stu-id="0a6de-102">How to: Specify Merge Options in PLINQ</span></span>
<span data-ttu-id="0a6de-103">Bu örnekte, tüm sonraki işleçleri PLINQ sorgusunda uygulanacak birleştirme seçeneklerini belirtme gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="0a6de-103">This example shows how to specify the merge options that will apply to all subsequent operators in a PLINQ query.</span></span> <span data-ttu-id="0a6de-104">Birleştirme seçeneklerini açıkça ayarlamak gerekmez, ancak bunu yaparsanız, bu nedenle performansını artırabilir.</span><span class="sxs-lookup"><span data-stu-id="0a6de-104">You do not have to set merge options explicitly, but doing so may improve performance.</span></span> <span data-ttu-id="0a6de-105">Birleştirme seçenekleri hakkında daha fazla bilgi için bkz: [plınq'te birleştirme seçeneklerini](../../../docs/standard/parallel-programming/merge-options-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="0a6de-105">For more information about merge options, see [Merge Options in PLINQ](../../../docs/standard/parallel-programming/merge-options-in-plinq.md).</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="0a6de-106">Bu örnek kullanım göstermeye yöneliktir ve eşdeğer sıralı LINQ daha hızlı nesneleri sorguya çalışmayabilir.</span><span class="sxs-lookup"><span data-stu-id="0a6de-106">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="0a6de-107">Speedup hakkında daha fazla bilgi için bkz: [Plınq'te hızlandırmayı anlama](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="0a6de-107">For more information about speedup, see [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0a6de-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="0a6de-108">Example</span></span>  
 <span data-ttu-id="0a6de-109">Aşağıdaki örnek, sırasız bir kaynak ve her öğeye pahalı işlevi uygular temel bir senaryoda birleştirme seçeneklerini davranışını gösterir.</span><span class="sxs-lookup"><span data-stu-id="0a6de-109">The following example demonstrates the behavior of merge options in a basic scenario that has an unordered source and applies an expensive function to every element.</span></span>  
  
 [!code-csharp[PLINQ#23](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#23)]
 [!code-vb[PLINQ#23](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#23)]  
  
 <span data-ttu-id="0a6de-110">Durumlarda nerede <xref:System.Linq.ParallelMergeOptions.AutoBuffered> seçeneği doğurur istenmeyen bir gecikme süresi ilk öğe verdiğini önce deneyin <xref:System.Linq.ParallelMergeOptions.NotBuffered> sonuç öğeleri daha hızlı ve daha sorunsuz bir şekilde elde etmek üzere seçeneği.</span><span class="sxs-lookup"><span data-stu-id="0a6de-110">In cases where the <xref:System.Linq.ParallelMergeOptions.AutoBuffered> option incurs an undesirable latency before the first element is yielded, try the <xref:System.Linq.ParallelMergeOptions.NotBuffered> option to yield result elements faster and more smoothly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a6de-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0a6de-111">See Also</span></span>  
 <xref:System.Linq.ParallelMergeOptions>  
 [<span data-ttu-id="0a6de-112">Paralel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="0a6de-112">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
