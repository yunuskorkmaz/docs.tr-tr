---
title: 'Nasıl yapılır: PLINQ Sorgu Performansını Ölçme'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to measure performance
ms.assetid: 491ba43b-2c10-473d-9aab-e2cb96446711
ms.openlocfilehash: 91b6165be2f4f464626fb25f7152de68de9d86e8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124990"
---
# <a name="how-to-measure-plinq-query-performance"></a><span data-ttu-id="798f8-102">Nasıl yapılır: PLINQ Sorgu Performansını Ölçme</span><span class="sxs-lookup"><span data-stu-id="798f8-102">How to: Measure PLINQ Query Performance</span></span>
<span data-ttu-id="798f8-103">Bu örnek, bir PLıNQ sorgusunun yürütülmesi için geçen süreyi ölçmek için <xref:System.Diagnostics.Stopwatch> sınıfını nasıl kullanacağınızı gösterir.</span><span class="sxs-lookup"><span data-stu-id="798f8-103">This example shows how use the <xref:System.Diagnostics.Stopwatch> class to measure the time it takes for a PLINQ query to execute.</span></span>  
  
## <a name="example"></a><span data-ttu-id="798f8-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="798f8-104">Example</span></span>  
 <span data-ttu-id="798f8-105">Bu örnek, sorgunun yürütülmesi için geçen süreyi ölçmek üzere boş bir `foreach` döngüsünü (Visual Basic`For Each`) kullanır.</span><span class="sxs-lookup"><span data-stu-id="798f8-105">This example uses an empty `foreach` loop (`For Each` in Visual Basic) to measure the time it takes for the query to execute.</span></span> <span data-ttu-id="798f8-106">Gerçek dünyada kodda, döngü genellikle toplam sorgu yürütme zamanına eklenen ek işleme adımları içerir.</span><span class="sxs-lookup"><span data-stu-id="798f8-106">In real-world code, the loop typically contains additional processing steps that add to the total query execution time.</span></span> <span data-ttu-id="798f8-107">Sorgu yürütme başladığında, kronometre 'un döngüden önce başlamadığına dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="798f8-107">Notice that the stopwatch is not started until just before the loop, because that is when the query execution begins.</span></span> <span data-ttu-id="798f8-108">Daha ayrıntılı ölçüm gerekliyse, `ElapsedMilliseconds`yerine `ElapsedTicks` özelliğini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="798f8-108">If you require more fine-grained measurement, you can use the `ElapsedTicks` property instead of `ElapsedMilliseconds`.</span></span>  
  
 [!code-csharp[PLINQ#19](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/measure2.cs#19)]
 [!code-vb[PLINQ#19](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/measure2.vb#19)]  
  
 <span data-ttu-id="798f8-109">Toplam yürütme süresi, sorgu uygulamalarıyla denemeler yaparken yararlı bir ölçümdür, ancak her zaman hikayenin tamamına söylemez.</span><span class="sxs-lookup"><span data-stu-id="798f8-109">The total execution time is a useful metric when you are experimenting with query implementations, but it does not always tell the whole story.</span></span> <span data-ttu-id="798f8-110">Sorgu iş parçacıklarının bir diğeri ve diğer çalışan işlemlerle etkileşimini daha ayrıntılı ve daha zengin bir şekilde görüntülemek için eşzamanlılık görselleştiricisi kullanın.</span><span class="sxs-lookup"><span data-stu-id="798f8-110">To get a deeper and richer view of the interaction of the query threads with one another and with other running processes, use the Concurrency Visualizer.</span></span> <span data-ttu-id="798f8-111">Daha fazla bilgi için bkz. [Eşzamanlılık görselleştiricisi](/visualstudio/profiling/concurrency-visualizer).</span><span class="sxs-lookup"><span data-stu-id="798f8-111">For more information, see [Concurrency Visualizer](/visualstudio/profiling/concurrency-visualizer).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="798f8-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="798f8-112">See also</span></span>

- [<span data-ttu-id="798f8-113">Paralel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="798f8-113">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
