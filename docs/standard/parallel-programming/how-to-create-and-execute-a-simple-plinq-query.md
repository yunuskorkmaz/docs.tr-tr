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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 544ea0f89dfa518c2ef18bffe2609d72e6fdee70
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44085046"
---
# <a name="how-to-create-and-execute-a-simple-plinq-query"></a><span data-ttu-id="3456c-102">Nasıl yapılır: Basit bir PLINQ Sorgusu Oluşturma ve Yürütme</span><span class="sxs-lookup"><span data-stu-id="3456c-102">How to: Create and Execute a Simple PLINQ Query</span></span>
<span data-ttu-id="3456c-103">Aşağıdaki örnek, kullanarak basit bir paralel LINQ Sorgu oluşturma işlemi gösterilmektedir <xref:System.Linq.ParallelEnumerable.AsParallel%2A> kaynak sırası ve kullanarak sorgu yürütülürken genişletme yöntemini <xref:System.Linq.ParallelEnumerable.ForAll%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="3456c-103">The following example shows how to create a simple Parallel LINQ query by using the <xref:System.Linq.ParallelEnumerable.AsParallel%2A> extension method on the source sequence, and executing the query by using the <xref:System.Linq.ParallelEnumerable.ForAll%2A> method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3456c-104">Bu belgede lambda ifadeleri PLINQ'te temsilciler tanımlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3456c-104">This documentation uses lambda expressions to define delegates in PLINQ.</span></span> <span data-ttu-id="3456c-105">C# veya Visual Basic'te lambda ifadelerine aşina değilseniz bkz [PLINQ ve TPL'deki Lambda ifadeleri](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).</span><span class="sxs-lookup"><span data-stu-id="3456c-105">If you are not familiar with lambda expressions in C# or Visual Basic, see [Lambda Expressions in PLINQ and TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3456c-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="3456c-106">Example</span></span>  
 [!code-csharp[PLINQ#11](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/create1.cs#11)]
 [!code-vb[PLINQ#11](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/create1.vb#11)]  
  
 <span data-ttu-id="3456c-107">Bu örnek, oluşturmak ve sonucu bir dizi sırası önemli değildir, herhangi bir paralel LINQ Sorgu yürütme için temel düzeni gösterir; Sıralanmamış sorgular genellikle sıralı sorgular hızlıdır.</span><span class="sxs-lookup"><span data-stu-id="3456c-107">This example demonstrates the basic pattern for creating and executing any Parallel LINQ query when the ordering of the result sequence is not important; unordered queries are generally faster than ordered queries.</span></span> <span data-ttu-id="3456c-108">Sorgu, birden çok iş parçacığında zaman uyumsuz olarak yürütülür görevlere kaynak bölümler.</span><span class="sxs-lookup"><span data-stu-id="3456c-108">The query partitions the source into tasks that are executed asynchronously on multiple threads.</span></span> <span data-ttu-id="3456c-109">İçinde her görev tamamlandığında sırası, yalnızca iş öğeleri bölümünde işlemek için aynı zamanda işletim sistemi her iş parçacığı nasıl zamanlamaları gibi dış etkenlerle ilişkilerini bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="3456c-109">The order in which each task completes depends not only on the amount of work involved to process the elements in the partition, but also on external factors such as how the operating system schedules each thread.</span></span> <span data-ttu-id="3456c-110">Bu örnek, kullanımını göstermek için tasarlanmıştır ve nesneleri sorgu için eşdeğer sıralı LINQ daha hızlı çalışmayabilir.</span><span class="sxs-lookup"><span data-stu-id="3456c-110">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="3456c-111">Hızlandırmayı hakkında daha fazla bilgi için bkz: [plınq'te hızlandırmayı anlama](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="3456c-111">For more information about speedup, see [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span></span> <span data-ttu-id="3456c-112">Sorguda öğelerin sıralamasını koruması hakkında daha fazla bilgi için bkz [nasıl yapılır: PLINQ sorgusunda denetimi sıralama](../../../docs/standard/parallel-programming/how-to-control-ordering-in-a-plinq-query.md).</span><span class="sxs-lookup"><span data-stu-id="3456c-112">For more information about how to preserve the ordering of elements in a query, see [How to: Control Ordering in a PLINQ Query](../../../docs/standard/parallel-programming/how-to-control-ordering-in-a-plinq-query.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3456c-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3456c-113">See also</span></span>

- [<span data-ttu-id="3456c-114">Paralel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="3456c-114">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
