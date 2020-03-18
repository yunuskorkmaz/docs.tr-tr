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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73124990"
---
# <a name="how-to-measure-plinq-query-performance"></a><span data-ttu-id="4caea-102">Nasıl yapılır: PLINQ Sorgu Performansını Ölçme</span><span class="sxs-lookup"><span data-stu-id="4caea-102">How to: Measure PLINQ Query Performance</span></span>
<span data-ttu-id="4caea-103">Bu örnek, bir <xref:System.Diagnostics.Stopwatch> PLINQ sorgusunun yürütülmesi için gereken süreyi ölçmek için sınıfın nasıl kullanıldığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="4caea-103">This example shows how use the <xref:System.Diagnostics.Stopwatch> class to measure the time it takes for a PLINQ query to execute.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4caea-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="4caea-104">Example</span></span>  
 <span data-ttu-id="4caea-105">Bu örnek, `foreach` sorgunun`For Each` yürütülmesi için gereken süreyi ölçmek için boş bir döngü (Visual Basic'te) kullanır.</span><span class="sxs-lookup"><span data-stu-id="4caea-105">This example uses an empty `foreach` loop (`For Each` in Visual Basic) to measure the time it takes for the query to execute.</span></span> <span data-ttu-id="4caea-106">Gerçek dünya kodunda, döngü genellikle toplam sorgu yürütme süresine ekleyen ek işleme adımları içerir.</span><span class="sxs-lookup"><span data-stu-id="4caea-106">In real-world code, the loop typically contains additional processing steps that add to the total query execution time.</span></span> <span data-ttu-id="4caea-107">Kronometrenin döngüden hemen öncesine kadar başlatılmadığını, çünkü sorgu yürütmesinin başladığı zaman olduğuna dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="4caea-107">Notice that the stopwatch is not started until just before the loop, because that is when the query execution begins.</span></span> <span data-ttu-id="4caea-108">Daha ince taneli ölçüm eihtiyacınız varsa, `ElapsedTicks` özelliği `ElapsedMilliseconds`' nin yerine kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4caea-108">If you require more fine-grained measurement, you can use the `ElapsedTicks` property instead of `ElapsedMilliseconds`.</span></span>  
  
 [!code-csharp[PLINQ#19](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/measure2.cs#19)]
 [!code-vb[PLINQ#19](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/measure2.vb#19)]  
  
 <span data-ttu-id="4caea-109">Sorgu uygulamalarıyla deneme yaparken toplam yürütme süresi yararlı bir ölçüdür, ancak her zaman tüm hikayeyi anlatmaz.</span><span class="sxs-lookup"><span data-stu-id="4caea-109">The total execution time is a useful metric when you are experimenting with query implementations, but it does not always tell the whole story.</span></span> <span data-ttu-id="4caea-110">Sorgu iş parçacıklarının birbirleriyle ve diğer çalışan işlemlerle etkileşimini daha derin ve daha zengin bir görünüme sahip etmek için Eşzamanlılık Görselleştiricisini kullanın.</span><span class="sxs-lookup"><span data-stu-id="4caea-110">To get a deeper and richer view of the interaction of the query threads with one another and with other running processes, use the Concurrency Visualizer.</span></span> <span data-ttu-id="4caea-111">Daha fazla bilgi için [Concurrency Visualizer'a](/visualstudio/profiling/concurrency-visualizer)bakın.</span><span class="sxs-lookup"><span data-stu-id="4caea-111">For more information, see [Concurrency Visualizer](/visualstudio/profiling/concurrency-visualizer).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4caea-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4caea-112">See also</span></span>

- [<span data-ttu-id="4caea-113">Paralel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="4caea-113">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
