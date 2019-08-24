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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 026c7d2be678c4b6aeed4e2e6f9eb43283cd04c1
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/23/2019
ms.locfileid: "69988459"
---
# <a name="how-to-combine-parallel-and-sequential-linq-queries"></a><span data-ttu-id="b87ab-102">Nasıl yapılır: Paralel ve Sıralı LINQ Sorgularını Birleştirme</span><span class="sxs-lookup"><span data-stu-id="b87ab-102">How to: Combine Parallel and Sequential LINQ Queries</span></span>
<span data-ttu-id="b87ab-103">Bu örnek, <xref:System.Linq.ParallelEnumerable.AsSequential%2A> PLINQ 'ın sorgudaki sonraki işleçleri sırayla işlemesini sağlamak için yönteminin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="b87ab-103">This example shows how to use the <xref:System.Linq.ParallelEnumerable.AsSequential%2A> method to instruct PLINQ to process all subsequent operators in the query sequentially.</span></span> <span data-ttu-id="b87ab-104">Sıralı işleme genellikle paralel olandan daha yavaş olsa da, bazen doğru sonuçların üretilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="b87ab-104">Although sequential processing is generally slower than parallel, sometimes it is necessary to produce correct results.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="b87ab-105">Bu örnek, kullanımı göstermeye yöneliktir ve eşdeğer sıralı LINQ to Objects sorgusundan daha hızlı çalışmayabilir.</span><span class="sxs-lookup"><span data-stu-id="b87ab-105">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="b87ab-106">Hızlı yedekleme hakkında daha fazla bilgi için bkz. [PLıNQ 'Te hızlı hızlandırı anlama](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="b87ab-106">For more information about speedup, see [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b87ab-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="b87ab-107">Example</span></span>  
 <span data-ttu-id="b87ab-108">Aşağıdaki örnek, sorgunun önceki bir yan tümcesinde <xref:System.Linq.ParallelEnumerable.AsSequential%2A> oluşturulan sıralamayı korumak için gereken bir senaryoyu gösterir.</span><span class="sxs-lookup"><span data-stu-id="b87ab-108">The following example shows one scenario in which <xref:System.Linq.ParallelEnumerable.AsSequential%2A> is required, namely to preserve the ordering that was established in a previous clause of the query.</span></span>  
  
 [!code-csharp[PLINQ#24](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#24)]
 [!code-vb[PLINQ#24](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#24)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b87ab-109">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="b87ab-109">Compiling the Code</span></span>  
 <span data-ttu-id="b87ab-110">Bu kodu derlemek ve çalıştırmak için, [PLINQ veri örneği](../../../docs/standard/parallel-programming/plinq-data-sample.md) projesine yapıştırın, öğesinden `Main`yöntemi çağırmak için bir satır ekleyin ve F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="b87ab-110">To compile and run this code, paste it into the [PLINQ Data Sample](../../../docs/standard/parallel-programming/plinq-data-sample.md) project, add a line to call the method from `Main`, and press F5.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b87ab-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b87ab-111">See also</span></span>

- [<span data-ttu-id="b87ab-112">Paralel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="b87ab-112">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
