---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: paralel ve sıralı LINQ sorgularını birleştirme'
title: 'Nasıl yapılır: Paralel ve Sıralı LINQ Sorgularını Birleştirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallel queries, combine parallel and sequential
ms.assetid: 1167cfe6-c8aa-4096-94ba-c66c3a4edf4c
ms.openlocfilehash: b3ff966b944516bed6cfb4cacd32cb550455fea9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99702073"
---
# <a name="how-to-combine-parallel-and-sequential-linq-queries"></a><span data-ttu-id="167ce-103">Nasıl yapılır: Paralel ve Sıralı LINQ Sorgularını Birleştirme</span><span class="sxs-lookup"><span data-stu-id="167ce-103">How to: Combine Parallel and Sequential LINQ Queries</span></span>

<span data-ttu-id="167ce-104">Bu örnek, <xref:System.Linq.ParallelEnumerable.AsSequential%2A> PLıNQ 'ın sorgudaki sonraki işleçleri sırayla işlemesini sağlamak için yönteminin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="167ce-104">This example shows how to use the <xref:System.Linq.ParallelEnumerable.AsSequential%2A> method to instruct PLINQ to process all subsequent operators in the query sequentially.</span></span> <span data-ttu-id="167ce-105">Sıralı işleme genellikle paralel olandan daha yavaş olsa da, bazen doğru sonuçlar üretmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="167ce-105">Although sequential processing is often slower than parallel, sometimes it's necessary to produce correct results.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="167ce-106">Bu örnek, kullanımı göstermeye yöneliktir ve eşdeğer sıralı LINQ to Objects sorgusundan daha hızlı çalışmayabilir.</span><span class="sxs-lookup"><span data-stu-id="167ce-106">This example is intended to demonstrate usage and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="167ce-107">Hızlı yedekleme hakkında daha fazla bilgi için bkz. [PLıNQ 'Te hızlı hızlandırı anlama](understanding-speedup-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="167ce-107">For more information about speedup, see [Understanding Speedup in PLINQ](understanding-speedup-in-plinq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="167ce-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="167ce-108">Example</span></span>  

 <span data-ttu-id="167ce-109">Aşağıdaki örnek, <xref:System.Linq.ParallelEnumerable.AsSequential%2A> sorgunun önceki bir yan tümcesinde oluşturulan sıralamayı korumak için gereken bir senaryoyu gösterir.</span><span class="sxs-lookup"><span data-stu-id="167ce-109">The following example shows one scenario in which <xref:System.Linq.ParallelEnumerable.AsSequential%2A> is required, namely to preserve the ordering that was established in a previous clause of the query.</span></span>  
  
 [!code-csharp[PLINQ#24](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#24)]
 [!code-vb[PLINQ#24](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#24)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="167ce-110">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="167ce-110">Compiling the Code</span></span>  

 <span data-ttu-id="167ce-111">Bu kodu derlemek ve çalıştırmak için, [PLINQ veri örneği](plinq-data-sample.md) projesine yapıştırın, öğesinden yöntemi çağırmak için bir satır ekleyin `Main` ve **F5** tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="167ce-111">To compile and run this code, paste it into the [PLINQ Data Sample](plinq-data-sample.md) project, add a line to call the method from `Main`, and press **F5**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="167ce-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="167ce-112">See also</span></span>

- [<span data-ttu-id="167ce-113">Paralel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="167ce-113">Parallel LINQ (PLINQ)</span></span>](introduction-to-plinq.md)
