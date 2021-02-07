---
description: 'Şu konuda daha fazla bilgi edinin: nasıl yapılır: PLıNQ sorgu performansını ölçme'
title: 'Nasıl yapılır: PLINQ Sorgu Performansını Ölçme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to measure performance
ms.assetid: 491ba43b-2c10-473d-9aab-e2cb96446711
ms.openlocfilehash: b8b447e49c725155559d910708a0b09c104a663f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99701813"
---
# <a name="how-to-measure-plinq-query-performance"></a><span data-ttu-id="a62a5-103">Nasıl yapılır: PLINQ Sorgu Performansını Ölçme</span><span class="sxs-lookup"><span data-stu-id="a62a5-103">How to: Measure PLINQ Query Performance</span></span>

<span data-ttu-id="a62a5-104">Bu örnek, <xref:System.Diagnostics.Stopwatch> BIR PLıNQ sorgusunun yürütülmesi için geçen süreyi ölçmek için sınıfını nasıl kullanacağınızı gösterir.</span><span class="sxs-lookup"><span data-stu-id="a62a5-104">This example shows how to use the <xref:System.Diagnostics.Stopwatch> class to measure the time it takes for a PLINQ query to execute.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a62a5-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="a62a5-105">Example</span></span>  

 <span data-ttu-id="a62a5-106">Bu örnek `foreach` `For Each` , sorgunun yürütülmesi için gereken süreyi ölçmek üzere boş bir döngü (Visual Basic olarak) kullanır.</span><span class="sxs-lookup"><span data-stu-id="a62a5-106">This example uses an empty `foreach` loop (`For Each` in Visual Basic) to measure the time it takes for the query to execute.</span></span> <span data-ttu-id="a62a5-107">Gerçek dünyada kodda, döngü genellikle toplam sorgu yürütme zamanına eklenen ek işleme adımları içerir.</span><span class="sxs-lookup"><span data-stu-id="a62a5-107">In real-world code, the loop typically contains additional processing steps that add to the total query execution time.</span></span> <span data-ttu-id="a62a5-108">Sorgu yürütme başladığında, kronometre 'un döngüden önce başlatıldığına dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="a62a5-108">Notice that the stopwatch is not started until just before the loop, because that's when the query execution begins.</span></span> <span data-ttu-id="a62a5-109">Daha ayrıntılı ölçüm gerekiyorsa, `ElapsedTicks` bunun yerine özelliğini kullanabilirsiniz `ElapsedMilliseconds` .</span><span class="sxs-lookup"><span data-stu-id="a62a5-109">If you require more fine-grained measurement, you can use the `ElapsedTicks` property instead of `ElapsedMilliseconds`.</span></span>  
  
 [!code-csharp[PLINQ#19](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/measure2.cs#19)]
 [!code-vb[PLINQ#19](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/measure2.vb#19)]  
  
 <span data-ttu-id="a62a5-110">Toplam yürütme süresi, sorgu uygulamalarıyla denemeler yaparken yararlı bir ölçümdür, ancak her zaman hikayenin tamamına söylemez.</span><span class="sxs-lookup"><span data-stu-id="a62a5-110">The total execution time is a useful metric when you are experimenting with query implementations, but it doesn't always tell the whole story.</span></span> <span data-ttu-id="a62a5-111">Sorgu iş parçacıklarının bir diğeri ve diğer çalışan işlemlerle etkileşimini daha ayrıntılı ve daha zengin bir şekilde görüntülemek için [Eşzamanlılık görselleştiricisi](/visualstudio/profiling/concurrency-visualizer)kullanın.</span><span class="sxs-lookup"><span data-stu-id="a62a5-111">To get a deeper and richer view of the interaction of the query threads with one another and with other running processes, use the [Concurrency Visualizer](/visualstudio/profiling/concurrency-visualizer).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a62a5-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a62a5-112">See also</span></span>

- [<span data-ttu-id="a62a5-113">Paralel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="a62a5-113">Parallel LINQ (PLINQ)</span></span>](introduction-to-plinq.md)
