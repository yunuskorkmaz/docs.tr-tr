---
title: 'Nasıl yapılır: Basit bir PLINQ Sorgusu Oluşturma ve Yürütme'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to create
ms.assetid: 983b4213-bddd-4a44-9262-cbe59186df4c
ms.openlocfilehash: c4cd75e55aabb551e5951a902ea6394a5659c9ee
ms.sourcegitcommit: 1c1a1f9ec0bd1efb3040d86a79f7ee94e207cca5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/03/2020
ms.locfileid: "80635849"
---
# <a name="how-to-create-and-execute-a-simple-plinq-query"></a><span data-ttu-id="ddd18-102">Nasıl yapılır: Basit bir PLINQ Sorgusu Oluşturma ve Yürütme</span><span class="sxs-lookup"><span data-stu-id="ddd18-102">How to: Create and Execute a Simple PLINQ Query</span></span>

<span data-ttu-id="ddd18-103">Bu makaledeki örnek, kaynak dizideki uzantı yöntemini <xref:System.Linq.ParallelEnumerable.AsParallel%2A?displayProperty=nameWithType> kullanarak ve <xref:System.Linq.ParallelEnumerable.ForAll%2A?displayProperty=nameWithTyp> yöntemi kullanarak sorguyu yürüterek basit bir Paralel Dil Tümleşik Sorgusu (LINQ) sorgusunun nasıl oluşturuluğun gösteriş olduğunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="ddd18-103">The example in this article shows how to create a simple Parallel Language Integrated Query (LINQ) query by using the <xref:System.Linq.ParallelEnumerable.AsParallel%2A?displayProperty=nameWithType> extension method on the source sequence and executing the query by using the <xref:System.Linq.ParallelEnumerable.ForAll%2A?displayProperty=nameWithTyp> method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ddd18-104">Bu dokümantasyon PLINQ'daki delegeleri tanımlamak için lambda ifadelerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="ddd18-104">This documentation uses lambda expressions to define delegates in PLINQ.</span></span> <span data-ttu-id="ddd18-105">C# veya Visual Basic'teki lambda ifadelerine aşina değilseniz, [PLINQ ve TPL'deki Lambda İfadeleri'ne](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="ddd18-105">If you are not familiar with lambda expressions in C# or Visual Basic, see [Lambda Expressions in PLINQ and TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ddd18-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="ddd18-106">Example</span></span>  
 [!code-csharp[PLINQ#11](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/create1.cs#11)]
 [!code-vb[PLINQ#11](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/create1.vb#11)]  
  
 <span data-ttu-id="ddd18-107">Bu örnek, sonuç sırasının sıralanması önemli olmadığında, herhangi bir Paralel LINQ sorgusu oluşturmak ve yürütmek için temel deseni gösterir.</span><span class="sxs-lookup"><span data-stu-id="ddd18-107">This example demonstrates the basic pattern for creating and executing any Parallel LINQ query when the ordering of the result sequence is not important.</span></span> <span data-ttu-id="ddd18-108">Sıralanmamış sorgular genellikle sıralanan sorgulardan daha hızlıdır.</span><span class="sxs-lookup"><span data-stu-id="ddd18-108">Unordered queries are generally faster than ordered queries.</span></span> <span data-ttu-id="ddd18-109">Sorgu, kaynağı birden çok iş parçacığı üzerinde eşit olarak yürütülen görevlere bölümlere ayırır.</span><span class="sxs-lookup"><span data-stu-id="ddd18-109">The query partitions the source into tasks that are executed asynchronously on multiple threads.</span></span> <span data-ttu-id="ddd18-110">Her görevin tamamlanma sırası yalnızca bölümdeki öğeleri işlemek için ilgili çalışma miktarına değil, aynı zamanda işletim sisteminin her iş parçacığının nasıl zamanladığı gibi dış etkenlere de bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="ddd18-110">The order in which each task completes depends not only on the amount of work involved to process the elements in the partition, but also on external factors such as how the operating system schedules each thread.</span></span> <span data-ttu-id="ddd18-111">Bu örnek, kullanımı göstermek için tasarlanmıştır ve Nesneler sorgusuna eşdeğer ardışık LINQ'dan daha hızlı çalışmayabilir.</span><span class="sxs-lookup"><span data-stu-id="ddd18-111">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="ddd18-112">Hız hakkında daha fazla bilgi için [PLINQ'da Hızları Anlama'ya](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="ddd18-112">For more information about speedup, see [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span></span> <span data-ttu-id="ddd18-113">Bir sorgudaki öğelerin sıralanması nın nasıl korunduğu hakkında daha fazla bilgi için [bkz.](../../../docs/standard/parallel-programming/how-to-control-ordering-in-a-plinq-query.md)</span><span class="sxs-lookup"><span data-stu-id="ddd18-113">For more information about how to preserve the ordering of elements in a query, see [How to: Control Ordering in a PLINQ Query](../../../docs/standard/parallel-programming/how-to-control-ordering-in-a-plinq-query.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ddd18-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ddd18-114">See also</span></span>

- [<span data-ttu-id="ddd18-115">Paralel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="ddd18-115">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/introduction-to-plinq.md)
