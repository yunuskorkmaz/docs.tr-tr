---
title: 'Nasıl yapılır: PLINQ Sorgu Performansını Ölçme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to measure performance
ms.assetid: 491ba43b-2c10-473d-9aab-e2cb96446711
ms.openlocfilehash: 2cbd178d5004d28120ab701a777a474a7e78e09e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95734445"
---
# <a name="how-to-measure-plinq-query-performance"></a><span data-ttu-id="92454-102">Nasıl yapılır: PLINQ Sorgu Performansını Ölçme</span><span class="sxs-lookup"><span data-stu-id="92454-102">How to: Measure PLINQ Query Performance</span></span>

<span data-ttu-id="92454-103">Bu örnek, <xref:System.Diagnostics.Stopwatch> BIR PLıNQ sorgusunun yürütülmesi için geçen süreyi ölçmek için sınıfını nasıl kullanacağınızı gösterir.</span><span class="sxs-lookup"><span data-stu-id="92454-103">This example shows how to use the <xref:System.Diagnostics.Stopwatch> class to measure the time it takes for a PLINQ query to execute.</span></span>  
  
## <a name="example"></a><span data-ttu-id="92454-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="92454-104">Example</span></span>  

 <span data-ttu-id="92454-105">Bu örnek `foreach` `For Each` , sorgunun yürütülmesi için gereken süreyi ölçmek üzere boş bir döngü (Visual Basic olarak) kullanır.</span><span class="sxs-lookup"><span data-stu-id="92454-105">This example uses an empty `foreach` loop (`For Each` in Visual Basic) to measure the time it takes for the query to execute.</span></span> <span data-ttu-id="92454-106">Gerçek dünyada kodda, döngü genellikle toplam sorgu yürütme zamanına eklenen ek işleme adımları içerir.</span><span class="sxs-lookup"><span data-stu-id="92454-106">In real-world code, the loop typically contains additional processing steps that add to the total query execution time.</span></span> <span data-ttu-id="92454-107">Sorgu yürütme başladığında, kronometre 'un döngüden önce başlatıldığına dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="92454-107">Notice that the stopwatch is not started until just before the loop, because that's when the query execution begins.</span></span> <span data-ttu-id="92454-108">Daha ayrıntılı ölçüm gerekiyorsa, `ElapsedTicks` bunun yerine özelliğini kullanabilirsiniz `ElapsedMilliseconds` .</span><span class="sxs-lookup"><span data-stu-id="92454-108">If you require more fine-grained measurement, you can use the `ElapsedTicks` property instead of `ElapsedMilliseconds`.</span></span>  
  
 [!code-csharp[PLINQ#19](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/measure2.cs#19)]
 [!code-vb[PLINQ#19](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/measure2.vb#19)]  
  
 <span data-ttu-id="92454-109">Toplam yürütme süresi, sorgu uygulamalarıyla denemeler yaparken yararlı bir ölçümdür, ancak her zaman hikayenin tamamına söylemez.</span><span class="sxs-lookup"><span data-stu-id="92454-109">The total execution time is a useful metric when you are experimenting with query implementations, but it doesn't always tell the whole story.</span></span> <span data-ttu-id="92454-110">Sorgu iş parçacıklarının bir diğeri ve diğer çalışan işlemlerle etkileşimini daha ayrıntılı ve daha zengin bir şekilde görüntülemek için [Eşzamanlılık görselleştiricisi](/visualstudio/profiling/concurrency-visualizer)kullanın.</span><span class="sxs-lookup"><span data-stu-id="92454-110">To get a deeper and richer view of the interaction of the query threads with one another and with other running processes, use the [Concurrency Visualizer](/visualstudio/profiling/concurrency-visualizer).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92454-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="92454-111">See also</span></span>

- [<span data-ttu-id="92454-112">Paralel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="92454-112">Parallel LINQ (PLINQ)</span></span>](introduction-to-plinq.md)
