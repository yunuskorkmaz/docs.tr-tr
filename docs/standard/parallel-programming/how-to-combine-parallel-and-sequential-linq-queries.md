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
ms.openlocfilehash: 9fd67d5f0cb5af33dc2b79f86148557a0dca6ec4
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/11/2018
ms.locfileid: "44353427"
---
# <a name="how-to-combine-parallel-and-sequential-linq-queries"></a><span data-ttu-id="eabf7-102">Nasıl yapılır: Paralel ve Sıralı LINQ Sorgularını Birleştirme</span><span class="sxs-lookup"><span data-stu-id="eabf7-102">How to: Combine Parallel and Sequential LINQ Queries</span></span>
<span data-ttu-id="eabf7-103">Bu örnek nasıl kullanılacağını gösterir <xref:System.Linq.ParallelEnumerable.AsSequential%2A> sorgudaki izleyen tüm işleçler sırayla işlemek için PLINQ istemek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="eabf7-103">This example shows how to use the <xref:System.Linq.ParallelEnumerable.AsSequential%2A> method to instruct PLINQ to process all subsequent operators in the query sequentially.</span></span> <span data-ttu-id="eabf7-104">Bazen sıralı işleme paralel genelde daha yavaş olsa da, doğru sonuçlar üretmek için gerekli olabilir.</span><span class="sxs-lookup"><span data-stu-id="eabf7-104">Although sequential processing is generally slower than parallel, sometimes it is necessary to produce correct results.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="eabf7-105">Bu örnek, kullanımını göstermek için tasarlanmıştır ve nesneleri sorgu için eşdeğer sıralı LINQ daha hızlı çalışmayabilir.</span><span class="sxs-lookup"><span data-stu-id="eabf7-105">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="eabf7-106">Hızlandırmayı hakkında daha fazla bilgi için bkz: [plınq'te hızlandırmayı anlama](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="eabf7-106">For more information about speedup, see [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="eabf7-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="eabf7-107">Example</span></span>  
 <span data-ttu-id="eabf7-108">Aşağıdaki örnek bir senaryo gösterilmektedir <xref:System.Linq.ParallelEnumerable.AsSequential%2A> özelliği için gerekli olan bir önceki sorgu yan tümcesi içinde oluşturulmuş sıralamasını koruması.</span><span class="sxs-lookup"><span data-stu-id="eabf7-108">The following example shows one scenario in which <xref:System.Linq.ParallelEnumerable.AsSequential%2A> is required, namely to preserve the ordering that was established in a previous clause of the query.</span></span>  
  
 [!code-csharp[PLINQ#24](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#24)]
 [!code-vb[PLINQ#24](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#24)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="eabf7-109">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="eabf7-109">Compiling the Code</span></span>  
 <span data-ttu-id="eabf7-110">Derleme ve bu kodu çalıştırmak için içine yapıştırın [PLINQ veri örneği](../../../docs/standard/parallel-programming/plinq-data-sample.md) yöntemini çağıracak bir satır ekleyin, proje `Main`, F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="eabf7-110">To compile and run this code, paste it into the [PLINQ Data Sample](../../../docs/standard/parallel-programming/plinq-data-sample.md) project, add a line to call the method from `Main`, and press F5.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eabf7-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="eabf7-111">See also</span></span>

- [<span data-ttu-id="eabf7-112">Paralel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="eabf7-112">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
