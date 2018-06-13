---
title: 'Nasıl yapılır: PLINQ Sorgusunda Sıralama Denetimi'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to control ordering
ms.assetid: c67eccc7-004d-4b2f-987e-919cbbd62ef7
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 89e0abf711730326b6391184a2e3a1b55b303957
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33580217"
---
# <a name="how-to-control-ordering-in-a-plinq-query"></a><span data-ttu-id="f58f8-102">Nasıl yapılır: PLINQ Sorgusunda Sıralama Denetimi</span><span class="sxs-lookup"><span data-stu-id="f58f8-102">How to: Control Ordering in a PLINQ Query</span></span>
<span data-ttu-id="f58f8-103">Bu örnekler kullanarak bir PLINQ sorgusunda sıralama denetleme <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> genişletme yöntemi.</span><span class="sxs-lookup"><span data-stu-id="f58f8-103">These examples show how to control the ordering in a PLINQ query by using the <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> extension method.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="f58f8-104">Bu örnekler kullanımını göstermek için tasarlanmıştır ve olabilir veya eşdeğer sıralı LINQ daha hızlı nesneleri sorguları çalışmayabilir.</span><span class="sxs-lookup"><span data-stu-id="f58f8-104">These examples are primarily intended to demonstrate usage, and may or may not run faster than the equivalent sequential LINQ to Objects queries.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f58f8-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="f58f8-105">Example</span></span>  
 <span data-ttu-id="f58f8-106">Aşağıdaki örnekte, kaynak dizi sıralaması korur.</span><span class="sxs-lookup"><span data-stu-id="f58f8-106">The following example preserves the ordering of the source sequence.</span></span> <span data-ttu-id="f58f8-107">Bu bazen gereklidir; Örneğin bazı sorgu işleçleri doğru sonuçlar üretmek için sıralı kaynak dizisi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="f58f8-107">This is sometimes necessary; for example some query operators require an ordered source sequence to produce correct results.</span></span>  
  
 [!code-csharp[PLINQ#12](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#12)]
 [!code-vb[PLINQ#12](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#12)]  
  
## <a name="example"></a><span data-ttu-id="f58f8-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="f58f8-108">Example</span></span>  
 <span data-ttu-id="f58f8-109">Aşağıdaki örnekte, bazı olan kaynak sırası, büyük olasılıkla sıralanmalıdır beklenir işleçleri sorgu görülmektedir.</span><span class="sxs-lookup"><span data-stu-id="f58f8-109">The following example shows some query operators whose source sequence is probably expected to be ordered.</span></span> <span data-ttu-id="f58f8-110">Bu işleçlere sırasız sıraları üzerinde çalışır, ancak beklenmeyen sonuçlara neden.</span><span class="sxs-lookup"><span data-stu-id="f58f8-110">These operators will work on unordered sequences, but they might produce unexpected results.</span></span>  
  
 [!code-csharp[PLINQ#14](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#14)]
 [!code-vb[PLINQ#14](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#14)]  
  
 <span data-ttu-id="f58f8-111">Bu yöntem çalıştırmak için PLINQDataSample sınıfında yapıştırın [PLINQ veri örneği](../../../docs/standard/parallel-programming/plinq-data-sample.md) proje ve F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="f58f8-111">To run this method, paste it into the PLINQDataSample class in the [PLINQ Data Sample](../../../docs/standard/parallel-programming/plinq-data-sample.md) project and press F5.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f58f8-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="f58f8-112">Example</span></span>  
 <span data-ttu-id="f58f8-113">Aşağıdaki örnek, bir sorgu ilk bölümü için sıralama korumak sonra bir JOIN yan tümcesi performansını artırmak için sıralama kaldırın ve son sonucu dizisi sıralama yeniden gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="f58f8-113">The following example shows how to preserve ordering for the first part of a query, then remove the ordering to increase the performance of a join clause, and then reapply ordering to the final result sequence.</span></span>  
  
 [!code-csharp[PLINQ#15](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#15)]
 [!code-vb[PLINQ#15](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#15)]  
  
 <span data-ttu-id="f58f8-114">Bu yöntem çalıştırmak için PLINQDataSample sınıfında yapıştırın [PLINQ veri örneği](../../../docs/standard/parallel-programming/plinq-data-sample.md) proje ve F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="f58f8-114">To run this method, paste it into the PLINQDataSample class in the [PLINQ Data Sample](../../../docs/standard/parallel-programming/plinq-data-sample.md) project and press F5.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f58f8-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f58f8-115">See Also</span></span>  
 <xref:System.Linq.ParallelEnumerable>  
 [<span data-ttu-id="f58f8-116">Paralel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="f58f8-116">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
