---
title: "Nasıl yapılır: Basit bir PLINQ Sorgusu Oluşturma ve Yürütme"
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
helpviewer_keywords: PLINQ queries, how to create
ms.assetid: 983b4213-bddd-4a44-9262-cbe59186df4c
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 20b1be451e53a81dd0631a89310a5b884aa83166
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-create-and-execute-a-simple-plinq-query"></a><span data-ttu-id="eb911-102">Nasıl yapılır: Basit bir PLINQ Sorgusu Oluşturma ve Yürütme</span><span class="sxs-lookup"><span data-stu-id="eb911-102">How to: Create and Execute a Simple PLINQ Query</span></span>
<span data-ttu-id="eb911-103">Aşağıdaki örnek kullanarak basit bir paralel LINQ sorgu oluşturmak nasıl gösterir <xref:System.Linq.ParallelEnumerable.AsParallel%2A> genişletme yöntemi kaynak sıradaki ve kullanarak sorgu yürütülürken <xref:System.Linq.ParallelEnumerable.ForAll%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="eb911-103">The following example shows how to create a simple Parallel LINQ query by using the <xref:System.Linq.ParallelEnumerable.AsParallel%2A> extension method on the source sequence, and executing the query by using the <xref:System.Linq.ParallelEnumerable.ForAll%2A> method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="eb911-104">Bu belge lambda ifadeleri temsilciler PLINQ'te tanımlamak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="eb911-104">This documentation uses lambda expressions to define delegates in PLINQ.</span></span> <span data-ttu-id="eb911-105">C# veya Visual Basic'deki lambda ifadeleri alışık değilseniz bkz [PLINQ ve TPL'deki Lambda ifadeleri](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).</span><span class="sxs-lookup"><span data-stu-id="eb911-105">If you are not familiar with lambda expressions in C# or Visual Basic, see [Lambda Expressions in PLINQ and TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="eb911-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="eb911-106">Example</span></span>  
 [!code-csharp[PLINQ#11](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/create1.cs#11)]
 [!code-vb[PLINQ#11](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/create1.vb#11)]  
  
 <span data-ttu-id="eb911-107">Örnek oluşturma ve herhangi bir paralel LINQ Sorgu sonuç dizi sıralaması önemli olmadığında yürütme temel düzeni gösterir; Sıralanmamış sorgular genellikle sıralı sorguları hızlıdır.</span><span class="sxs-lookup"><span data-stu-id="eb911-107">This example demonstrates the basic pattern for creating and executing any Parallel LINQ query when the ordering of the result sequence is not important; unordered queries are generally faster than ordered queries.</span></span> <span data-ttu-id="eb911-108">Sorgu zaman uyumsuz olarak birden çok iş parçacığı üzerinde yürütülen görevler içine kaynak bölümler.</span><span class="sxs-lookup"><span data-stu-id="eb911-108">The query partitions the source into tasks that are executed asynchronously on multiple threads.</span></span> <span data-ttu-id="eb911-109">İçinde her görev tamamlandığında sırası yalnızca bölüm öğeleri işlemek için ilgili iş miktarı, aynı zamanda işletim sistemi her iş parçacığı nasıl zamanlar gibi dış faktörlere bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="eb911-109">The order in which each task completes depends not only on the amount of work involved to process the elements in the partition, but also on external factors such as how the operating system schedules each thread.</span></span> <span data-ttu-id="eb911-110">Bu örnek kullanım göstermeye yöneliktir ve eşdeğer sıralı LINQ daha hızlı nesneleri sorguya çalışmayabilir.</span><span class="sxs-lookup"><span data-stu-id="eb911-110">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="eb911-111">Speedup hakkında daha fazla bilgi için bkz: [Plınq'te hızlandırmayı anlama](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="eb911-111">For more information about speedup, see [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span></span> <span data-ttu-id="eb911-112">Sorguda öğeleri sıralama korumak hakkında daha fazla bilgi için bkz: [nasıl yapılır: Denetim sıralama PLINQ sorgusunda](../../../docs/standard/parallel-programming/how-to-control-ordering-in-a-plinq-query.md).</span><span class="sxs-lookup"><span data-stu-id="eb911-112">For more information about how to preserve the ordering of elements in a query, see [How to: Control Ordering in a PLINQ Query](../../../docs/standard/parallel-programming/how-to-control-ordering-in-a-plinq-query.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb911-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="eb911-113">See Also</span></span>  
 [<span data-ttu-id="eb911-114">Paralel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="eb911-114">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
