---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: PLıNQ sorgusunda sıralama denetimi'
title: 'Nasıl yapılır: PLINQ Sorgusunda Sıralama Denetimi'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to control ordering
ms.assetid: c67eccc7-004d-4b2f-987e-919cbbd62ef7
ms.openlocfilehash: 9c181a9dc7697b1a838d04caaeadb892f9ec4796
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99702138"
---
# <a name="how-to-control-ordering-in-a-plinq-query"></a><span data-ttu-id="a7639-103">Nasıl yapılır: PLINQ Sorgusunda Sıralama Denetimi</span><span class="sxs-lookup"><span data-stu-id="a7639-103">How to: Control Ordering in a PLINQ Query</span></span>

<span data-ttu-id="a7639-104">Bu örneklerde, genişletme yöntemi kullanılarak bir PLıNQ sorgusunda sıralamayı denetleme gösterilmektedir <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> .</span><span class="sxs-lookup"><span data-stu-id="a7639-104">These examples show how to control the ordering in a PLINQ query by using the <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> extension method.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="a7639-105">Bu örnekler öncelikle kullanımı göstermeye yöneliktir ve eşdeğer sıralı LINQ to Objects sorgularından daha hızlı çalışmayabilir.</span><span class="sxs-lookup"><span data-stu-id="a7639-105">These examples are primarily intended to demonstrate usage, and may or may not run faster than the equivalent sequential LINQ to Objects queries.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a7639-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="a7639-106">Example</span></span>  

 <span data-ttu-id="a7639-107">Aşağıdaki örnek, kaynak sırasının sıralamasını korur.</span><span class="sxs-lookup"><span data-stu-id="a7639-107">The following example preserves the ordering of the source sequence.</span></span> <span data-ttu-id="a7639-108">Bu bazen gereklidir; Örneğin, bazı sorgu işleçleri doğru sonuçlar üretmek için sıralı bir kaynak sırası gerektirir.</span><span class="sxs-lookup"><span data-stu-id="a7639-108">This is sometimes necessary; for example some query operators require an ordered source sequence to produce correct results.</span></span>  
  
 [!code-csharp[PLINQ#12](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#12)]
 [!code-vb[PLINQ#12](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#12)]  
  
## <a name="example"></a><span data-ttu-id="a7639-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="a7639-109">Example</span></span>  

 <span data-ttu-id="a7639-110">Aşağıdaki örnek, kaynak sırası büyük olasılıkla sıralanmalıdır beklenen bazı sorgu işleçlerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="a7639-110">The following example shows some query operators whose source sequence is probably expected to be ordered.</span></span> <span data-ttu-id="a7639-111">Bu işleçler sıralanmamış diziler üzerinde çalışır, ancak bunlar beklenmedik sonuçlara neden olabilirler.</span><span class="sxs-lookup"><span data-stu-id="a7639-111">These operators will work on unordered sequences, but they might produce unexpected results.</span></span>  
  
 [!code-csharp[PLINQ#14](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#14)]
 [!code-vb[PLINQ#14](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#14)]  
  
 <span data-ttu-id="a7639-112">Bu yöntemi çalıştırmak için, [PLINQ veri örneği](plinq-data-sample.md) projesindeki PLINQDataSample sınıfına yapıştırın ve F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="a7639-112">To run this method, paste it into the PLINQDataSample class in the [PLINQ Data Sample](plinq-data-sample.md) project and press F5.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a7639-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="a7639-113">Example</span></span>  

 <span data-ttu-id="a7639-114">Aşağıdaki örnek, bir sorgunun ilk bölümü için sıralamayı nasıl koruyabileceğiniz gösterir, sonra bir JOIN yan tümcesinin performansını artırmak için sıralamayı kaldırır ve sonra sıralamayı son sonuç dizisine yeniden uygular.</span><span class="sxs-lookup"><span data-stu-id="a7639-114">The following example shows how to preserve ordering for the first part of a query, then remove the ordering to increase the performance of a join clause, and then reapply ordering to the final result sequence.</span></span>  
  
 [!code-csharp[PLINQ#15](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#15)]
 [!code-vb[PLINQ#15](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#15)]  
  
 <span data-ttu-id="a7639-115">Bu yöntemi çalıştırmak için, [PLINQ veri örneği](plinq-data-sample.md) projesindeki PLINQDataSample sınıfına yapıştırın ve F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="a7639-115">To run this method, paste it into the PLINQDataSample class in the [PLINQ Data Sample](plinq-data-sample.md) project and press F5.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7639-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a7639-116">See also</span></span>

- <xref:System.Linq.ParallelEnumerable>
- [<span data-ttu-id="a7639-117">Paralel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="a7639-117">Parallel LINQ (PLINQ)</span></span>](introduction-to-plinq.md)
