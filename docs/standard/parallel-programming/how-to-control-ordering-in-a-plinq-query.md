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
ms.openlocfilehash: 80e199d75471eba219f1f3da12d307b6cd1d90cf
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84285462"
---
# <a name="how-to-control-ordering-in-a-plinq-query"></a><span data-ttu-id="e77a5-102">Nasıl yapılır: PLINQ Sorgusunda Sıralama Denetimi</span><span class="sxs-lookup"><span data-stu-id="e77a5-102">How to: Control Ordering in a PLINQ Query</span></span>
<span data-ttu-id="e77a5-103">Bu örneklerde, genişletme yöntemi kullanılarak bir PLıNQ sorgusunda sıralamayı denetleme gösterilmektedir <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> .</span><span class="sxs-lookup"><span data-stu-id="e77a5-103">These examples show how to control the ordering in a PLINQ query by using the <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> extension method.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="e77a5-104">Bu örnekler öncelikle kullanımı göstermeye yöneliktir ve eşdeğer sıralı LINQ to Objects sorgularından daha hızlı çalışmayabilir.</span><span class="sxs-lookup"><span data-stu-id="e77a5-104">These examples are primarily intended to demonstrate usage, and may or may not run faster than the equivalent sequential LINQ to Objects queries.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e77a5-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="e77a5-105">Example</span></span>  
 <span data-ttu-id="e77a5-106">Aşağıdaki örnek, kaynak sırasının sıralamasını korur.</span><span class="sxs-lookup"><span data-stu-id="e77a5-106">The following example preserves the ordering of the source sequence.</span></span> <span data-ttu-id="e77a5-107">Bu bazen gereklidir; Örneğin, bazı sorgu işleçleri doğru sonuçlar üretmek için sıralı bir kaynak sırası gerektirir.</span><span class="sxs-lookup"><span data-stu-id="e77a5-107">This is sometimes necessary; for example some query operators require an ordered source sequence to produce correct results.</span></span>  
  
 [!code-csharp[PLINQ#12](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#12)]
 [!code-vb[PLINQ#12](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#12)]  
  
## <a name="example"></a><span data-ttu-id="e77a5-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="e77a5-108">Example</span></span>  
 <span data-ttu-id="e77a5-109">Aşağıdaki örnek, kaynak sırası büyük olasılıkla sıralanmalıdır beklenen bazı sorgu işleçlerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="e77a5-109">The following example shows some query operators whose source sequence is probably expected to be ordered.</span></span> <span data-ttu-id="e77a5-110">Bu işleçler sıralanmamış diziler üzerinde çalışır, ancak bunlar beklenmedik sonuçlara neden olabilirler.</span><span class="sxs-lookup"><span data-stu-id="e77a5-110">These operators will work on unordered sequences, but they might produce unexpected results.</span></span>  
  
 [!code-csharp[PLINQ#14](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#14)]
 [!code-vb[PLINQ#14](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#14)]  
  
 <span data-ttu-id="e77a5-111">Bu yöntemi çalıştırmak için, [PLINQ veri örneği](plinq-data-sample.md) projesindeki PLINQDataSample sınıfına yapıştırın ve F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="e77a5-111">To run this method, paste it into the PLINQDataSample class in the [PLINQ Data Sample](plinq-data-sample.md) project and press F5.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e77a5-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="e77a5-112">Example</span></span>  
 <span data-ttu-id="e77a5-113">Aşağıdaki örnek, bir sorgunun ilk bölümü için sıralamayı nasıl koruyabileceğiniz gösterir, sonra bir JOIN yan tümcesinin performansını artırmak için sıralamayı kaldırır ve sonra sıralamayı son sonuç dizisine yeniden uygular.</span><span class="sxs-lookup"><span data-stu-id="e77a5-113">The following example shows how to preserve ordering for the first part of a query, then remove the ordering to increase the performance of a join clause, and then reapply ordering to the final result sequence.</span></span>  
  
 [!code-csharp[PLINQ#15](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#15)]
 [!code-vb[PLINQ#15](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#15)]  
  
 <span data-ttu-id="e77a5-114">Bu yöntemi çalıştırmak için, [PLINQ veri örneği](plinq-data-sample.md) projesindeki PLINQDataSample sınıfına yapıştırın ve F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="e77a5-114">To run this method, paste it into the PLINQDataSample class in the [PLINQ Data Sample](plinq-data-sample.md) project and press F5.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e77a5-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e77a5-115">See also</span></span>

- <xref:System.Linq.ParallelEnumerable>
- [<span data-ttu-id="e77a5-116">Paralel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="e77a5-116">Parallel LINQ (PLINQ)</span></span>](introduction-to-plinq.md)
