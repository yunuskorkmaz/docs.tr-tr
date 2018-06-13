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
ms.openlocfilehash: c69d4d423bbdf72f2af7dad38812aa508df0067c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33580256"
---
# <a name="how-to-combine-parallel-and-sequential-linq-queries"></a><span data-ttu-id="6941f-102">Nasıl yapılır: Paralel ve Sıralı LINQ Sorgularını Birleştirme</span><span class="sxs-lookup"><span data-stu-id="6941f-102">How to: Combine Parallel and Sequential LINQ Queries</span></span>
<span data-ttu-id="6941f-103">Bu örnek nasıl kullanılacağını gösterir <xref:System.Linq.ParallelEnumerable.AsSequential%2A> PLINQ sorgusunda tüm sonraki işleçleri sıralı olarak işlediğinden istemek üzere yöntemi.</span><span class="sxs-lookup"><span data-stu-id="6941f-103">This example shows how to use the <xref:System.Linq.ParallelEnumerable.AsSequential%2A> method to instruct PLINQ to process all subsequent operators in the query sequentially.</span></span> <span data-ttu-id="6941f-104">Bazen sıralı işleme genellikle paralel yavaş olsa da, doğru sonuçlar üretmek için gerekli.</span><span class="sxs-lookup"><span data-stu-id="6941f-104">Although sequential processing is generally slower than parallel, sometimes it is necessary to produce correct results.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="6941f-105">Bu örnek kullanım göstermeye yöneliktir ve eşdeğer sıralı LINQ daha hızlı nesneleri sorguya çalışmayabilir.</span><span class="sxs-lookup"><span data-stu-id="6941f-105">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="6941f-106">Speedup hakkında daha fazla bilgi için bkz: [Plınq'te hızlandırmayı anlama](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="6941f-106">For more information about speedup, see [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6941f-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="6941f-107">Example</span></span>  
 <span data-ttu-id="6941f-108">Aşağıdaki örnek bir senaryo gösterir <xref:System.Linq.ParallelEnumerable.AsSequential%2A> , yani için gereklidir. önceki bir sorgu yan tümcesinde kuruldu sıralama korumak.</span><span class="sxs-lookup"><span data-stu-id="6941f-108">The following example shows one scenario in which <xref:System.Linq.ParallelEnumerable.AsSequential%2A> is required, namely to preserve the ordering that was established in a previous clause of the query.</span></span>  
  
 [!code-csharp[PLINQ#24](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#24)]
 [!code-vb[PLINQ#24](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#24)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="6941f-109">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="6941f-109">Compiling the Code</span></span>  
 <span data-ttu-id="6941f-110">Derlemek ve bu kodu çalıştırmak için yapıştırın [PLINQ veri örneği](../../../docs/standard/parallel-programming/plinq-data-sample.md) yöntemini çağırmak için bir satır ekleyin, proje `Main`, F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="6941f-110">To compile and run this code, paste it into the [PLINQ Data Sample](../../../docs/standard/parallel-programming/plinq-data-sample.md) project, add a line to call the method from `Main`, and press F5.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6941f-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6941f-111">See Also</span></span>  
 [<span data-ttu-id="6941f-112">Paralel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="6941f-112">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
