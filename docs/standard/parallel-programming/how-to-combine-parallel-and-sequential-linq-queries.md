---
title: 'Nasıl yapılır: Paralel ve Sıralı LINQ Sorgularını Birleştirme'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallel queries, combine parallel and sequential
ms.assetid: 1167cfe6-c8aa-4096-94ba-c66c3a4edf4c
ms.openlocfilehash: 99c86e17c57a90d2268acb2a32c69bc4a693338a
ms.sourcegitcommit: 961ec21c22d2f1d55c9cc8a7edf2ade1d1fd92e3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2020
ms.locfileid: "80587996"
---
# <a name="how-to-combine-parallel-and-sequential-linq-queries"></a><span data-ttu-id="61ca8-102">Nasıl yapılır: Paralel ve Sıralı LINQ Sorgularını Birleştirme</span><span class="sxs-lookup"><span data-stu-id="61ca8-102">How to: Combine Parallel and Sequential LINQ Queries</span></span>
<span data-ttu-id="61ca8-103">Bu örnek, PLINQ'a sorgudaki sonraki tüm işleçleri sırayla işlemesi için talimat vermek için <xref:System.Linq.ParallelEnumerable.AsSequential%2A> yöntemin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="61ca8-103">This example shows how to use the <xref:System.Linq.ParallelEnumerable.AsSequential%2A> method to instruct PLINQ to process all subsequent operators in the query sequentially.</span></span> <span data-ttu-id="61ca8-104">Sıralı işleme genellikle paralelden daha yavaş olsa da, bazen doğru sonuçlar üretmek gerekir.</span><span class="sxs-lookup"><span data-stu-id="61ca8-104">Although sequential processing is generally slower than parallel, sometimes it is necessary to produce correct results.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="61ca8-105">Bu örnek, kullanımı göstermek için tasarlanmıştır ve Nesneler sorgusuna eşdeğer ardışık LINQ'dan daha hızlı çalışmayabilir.</span><span class="sxs-lookup"><span data-stu-id="61ca8-105">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="61ca8-106">Hız hakkında daha fazla bilgi için [PLINQ'da Hızları Anlama'ya](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="61ca8-106">For more information about speedup, see [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="61ca8-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="61ca8-107">Example</span></span>  
 <span data-ttu-id="61ca8-108">Aşağıdaki örnekte, sorgunun <xref:System.Linq.ParallelEnumerable.AsSequential%2A> önceki bir yan tümcesinde oluşturulan sırayı korumak için gereken bir senaryo gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="61ca8-108">The following example shows one scenario in which <xref:System.Linq.ParallelEnumerable.AsSequential%2A> is required, namely to preserve the ordering that was established in a previous clause of the query.</span></span>  
  
 [!code-csharp[PLINQ#24](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#24)]
 [!code-vb[PLINQ#24](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#24)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="61ca8-109">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="61ca8-109">Compiling the Code</span></span>  
 <span data-ttu-id="61ca8-110">Bu kodu derlemek ve çalıştırmak için [PLINQ Veri Örneği](../../../docs/standard/parallel-programming/plinq-data-sample.md) projesine yapıştırın, `Main`yöntemi aramak için bir satır ekleyin ve F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="61ca8-110">To compile and run this code, paste it into the [PLINQ Data Sample](../../../docs/standard/parallel-programming/plinq-data-sample.md) project, add a line to call the method from `Main`, and press F5.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61ca8-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="61ca8-111">See also</span></span>

- [<span data-ttu-id="61ca8-112">Paralel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="61ca8-112">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/introduction-to-plinq.md)
