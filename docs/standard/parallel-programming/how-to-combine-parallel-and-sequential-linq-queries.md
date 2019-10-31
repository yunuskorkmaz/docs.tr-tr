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
ms.openlocfilehash: 4c04afb23a168a9cff60962bd5a75a65e3ebca4d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134191"
---
# <a name="how-to-combine-parallel-and-sequential-linq-queries"></a><span data-ttu-id="fe651-102">Nasıl yapılır: Paralel ve Sıralı LINQ Sorgularını Birleştirme</span><span class="sxs-lookup"><span data-stu-id="fe651-102">How to: Combine Parallel and Sequential LINQ Queries</span></span>
<span data-ttu-id="fe651-103">Bu örnek, PLıNQ 'ın sorgudaki sonraki işleçleri sırayla işlemesini söylemek için <xref:System.Linq.ParallelEnumerable.AsSequential%2A> yönteminin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="fe651-103">This example shows how to use the <xref:System.Linq.ParallelEnumerable.AsSequential%2A> method to instruct PLINQ to process all subsequent operators in the query sequentially.</span></span> <span data-ttu-id="fe651-104">Sıralı işleme genellikle paralel olandan daha yavaş olsa da, bazen doğru sonuçların üretilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="fe651-104">Although sequential processing is generally slower than parallel, sometimes it is necessary to produce correct results.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="fe651-105">Bu örnek, kullanımı göstermeye yöneliktir ve eşdeğer sıralı LINQ to Objects sorgusundan daha hızlı çalışmayabilir.</span><span class="sxs-lookup"><span data-stu-id="fe651-105">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="fe651-106">Hızlı yedekleme hakkında daha fazla bilgi için bkz. [PLıNQ 'Te hızlı hızlandırı anlama](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="fe651-106">For more information about speedup, see [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="fe651-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="fe651-107">Example</span></span>  
 <span data-ttu-id="fe651-108">Aşağıdaki örnekte, sorgunun önceki bir yan tümcesinde oluşturulan sıralamayı korumak için <xref:System.Linq.ParallelEnumerable.AsSequential%2A> gerekli olduğu bir senaryo gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="fe651-108">The following example shows one scenario in which <xref:System.Linq.ParallelEnumerable.AsSequential%2A> is required, namely to preserve the ordering that was established in a previous clause of the query.</span></span>  
  
 [!code-csharp[PLINQ#24](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#24)]
 [!code-vb[PLINQ#24](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#24)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="fe651-109">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="fe651-109">Compiling the Code</span></span>  
 <span data-ttu-id="fe651-110">Bu kodu derlemek ve çalıştırmak için, [PLINQ veri örneği](../../../docs/standard/parallel-programming/plinq-data-sample.md) projesine yapıştırın, `Main`yöntemi çağırmak için bir satır ekleyin ve F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="fe651-110">To compile and run this code, paste it into the [PLINQ Data Sample](../../../docs/standard/parallel-programming/plinq-data-sample.md) project, add a line to call the method from `Main`, and press F5.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe651-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fe651-111">See also</span></span>

- [<span data-ttu-id="fe651-112">Paralel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="fe651-112">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
