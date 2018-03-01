---
title: "Nasıl yapılır: PLINQ Sorgu Performansını Ölçme"
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
helpviewer_keywords:
- PLINQ queries, how to measure performance
ms.assetid: 491ba43b-2c10-473d-9aab-e2cb96446711
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: fe19fd6ae7730a30a9ccc8a39b99a31981f838fa
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-measure-plinq-query-performance"></a><span data-ttu-id="874e4-102">Nasıl yapılır: PLINQ Sorgu Performansını Ölçme</span><span class="sxs-lookup"><span data-stu-id="874e4-102">How to: Measure PLINQ Query Performance</span></span>
<span data-ttu-id="874e4-103">Bu örnek nasıl kullanıldığını gösterir <xref:System.Diagnostics.Stopwatch> bir PLINQ sorgusu çalıştırmak geçen süreyi ölçmek için sınıf.</span><span class="sxs-lookup"><span data-stu-id="874e4-103">This example shows how use the <xref:System.Diagnostics.Stopwatch> class to measure the time it takes for a PLINQ query to execute.</span></span>  
  
## <a name="example"></a><span data-ttu-id="874e4-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="874e4-104">Example</span></span>  
 <span data-ttu-id="874e4-105">Bu örnekte boş bir `foreach` döngü (`For Each` Visual Basic'te) sorguyu yürütmek gereken süreyi ölçmek için.</span><span class="sxs-lookup"><span data-stu-id="874e4-105">This example uses an empty `foreach` loop (`For Each` in Visual Basic) to measure the time it takes for the query to execute.</span></span> <span data-ttu-id="874e4-106">Gerçek kodda döngü genellikle toplam sorgu yürütme zamana ekle ek işleme adımları içerir.</span><span class="sxs-lookup"><span data-stu-id="874e4-106">In real-world code, the loop typically contains additional processing steps that add to the total query execution time.</span></span> <span data-ttu-id="874e4-107">Kronometre değil dikkat edin, yalnızca kadar döngü önce ne zaman olduğundan başlatılan sorgu yürütme başlar.</span><span class="sxs-lookup"><span data-stu-id="874e4-107">Notice that the stopwatch is not started until just before the loop, because that is when the query execution begins.</span></span> <span data-ttu-id="874e4-108">Daha fazla hassas ölçüm gerektiriyorsa, kullanabileceğiniz `ElapsedTicks` özelliği yerine `ElapsedMilliseconds`.</span><span class="sxs-lookup"><span data-stu-id="874e4-108">If you require more fine-grained measurement, you can use the `ElapsedTicks` property instead of `ElapsedMilliseconds`.</span></span>  
  
 [!code-csharp[PLINQ#19](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/measure2.cs#19)]
 [!code-vb[PLINQ#19](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/measure2.vb#19)]  
  
 <span data-ttu-id="874e4-109">Toplam yürütme süresi bir yararlı sorgu uygulamaları ile denemeler ancak Yazının tamamını her zaman söylemez ölçümüdür.</span><span class="sxs-lookup"><span data-stu-id="874e4-109">The total execution time is a useful metric when you are experimenting with query implementations, but it does not always tell the whole story.</span></span> <span data-ttu-id="874e4-110">Birbirleriyle ve diğer çalışan işlemleri ile etkileşim sorgu iş parçacığı daha derin ve daha zengin bir görünümünü almak için eşzamanlılık görselleştiricisi kullanın.</span><span class="sxs-lookup"><span data-stu-id="874e4-110">To get a deeper and richer view of the interaction of the query threads with one another and with other running processes, use the Concurrency Visualizer.</span></span> <span data-ttu-id="874e4-111">Daha fazla bilgi için bkz: [eşzamanlılık görselleştiricisi](/visualstudio/profiling/concurrency-visualizer).</span><span class="sxs-lookup"><span data-stu-id="874e4-111">For more information, see [Concurrency Visualizer](/visualstudio/profiling/concurrency-visualizer).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="874e4-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="874e4-112">See Also</span></span>  
 [<span data-ttu-id="874e4-113">Paralel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="874e4-113">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
