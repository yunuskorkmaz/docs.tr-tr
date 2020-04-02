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
ms.openlocfilehash: 86011cff71fabed5e47e085f91b1759238638c9a
ms.sourcegitcommit: 961ec21c22d2f1d55c9cc8a7edf2ade1d1fd92e3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2020
ms.locfileid: "80588498"
---
# <a name="how-to-control-ordering-in-a-plinq-query"></a><span data-ttu-id="d68bc-102">Nasıl yapılır: PLINQ Sorgusunda Sıralama Denetimi</span><span class="sxs-lookup"><span data-stu-id="d68bc-102">How to: Control Ordering in a PLINQ Query</span></span>
<span data-ttu-id="d68bc-103">Bu örnekler, uzantı yöntemini kullanarak PLINQ sorgusunda sıralamanın nasıl denetlenebildiğini <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> gösterir.</span><span class="sxs-lookup"><span data-stu-id="d68bc-103">These examples show how to control the ordering in a PLINQ query by using the <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> extension method.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="d68bc-104">Bu örnekler öncelikle kullanımı göstermek için tasarlanmıştır ve Nesneler sorgularına eşdeğer ardışık LINQ'dan daha hızlı çalışabilir veya çalışmayabilir.</span><span class="sxs-lookup"><span data-stu-id="d68bc-104">These examples are primarily intended to demonstrate usage, and may or may not run faster than the equivalent sequential LINQ to Objects queries.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d68bc-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="d68bc-105">Example</span></span>  
 <span data-ttu-id="d68bc-106">Aşağıdaki örnek, kaynak dizinin sırasını korur.</span><span class="sxs-lookup"><span data-stu-id="d68bc-106">The following example preserves the ordering of the source sequence.</span></span> <span data-ttu-id="d68bc-107">Bu bazen gereklidir; örneğin, bazı sorgu işleçleri doğru sonuçlar üretmek için sıralı bir kaynak sıragerektirir.</span><span class="sxs-lookup"><span data-stu-id="d68bc-107">This is sometimes necessary; for example some query operators require an ordered source sequence to produce correct results.</span></span>  
  
 [!code-csharp[PLINQ#12](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#12)]
 [!code-vb[PLINQ#12](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#12)]  
  
## <a name="example"></a><span data-ttu-id="d68bc-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="d68bc-108">Example</span></span>  
 <span data-ttu-id="d68bc-109">Aşağıdaki örnek, kaynak sırası büyük olasılıkla sıralanmış olması beklenen bazı sorgu işleçleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="d68bc-109">The following example shows some query operators whose source sequence is probably expected to be ordered.</span></span> <span data-ttu-id="d68bc-110">Bu işleçler sıralanmamış diziler üzerinde çalışır, ancak beklenmeyen sonuçlar üretebilir.</span><span class="sxs-lookup"><span data-stu-id="d68bc-110">These operators will work on unordered sequences, but they might produce unexpected results.</span></span>  
  
 [!code-csharp[PLINQ#14](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#14)]
 [!code-vb[PLINQ#14](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#14)]  
  
 <span data-ttu-id="d68bc-111">Bu yöntemi çalıştırmak için [PLINQ Data Sample](../../../docs/standard/parallel-programming/plinq-data-sample.md) projesinde PLINQDataSample sınıfına yapıştırın ve F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="d68bc-111">To run this method, paste it into the PLINQDataSample class in the [PLINQ Data Sample](../../../docs/standard/parallel-programming/plinq-data-sample.md) project and press F5.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d68bc-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="d68bc-112">Example</span></span>  
 <span data-ttu-id="d68bc-113">Aşağıdaki örnek, sorgunun ilk bölümü için sıralamayı nasıl koruyacağını, ardından birleştirilmiş tümcenin performansını artırmak için sıralamayı nasıl kaldıracağını ve ardından son sonuç dizisine sıralamayı yeniden uygulayacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d68bc-113">The following example shows how to preserve ordering for the first part of a query, then remove the ordering to increase the performance of a join clause, and then reapply ordering to the final result sequence.</span></span>  
  
 [!code-csharp[PLINQ#15](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#15)]
 [!code-vb[PLINQ#15](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#15)]  
  
 <span data-ttu-id="d68bc-114">Bu yöntemi çalıştırmak için [PLINQ Data Sample](../../../docs/standard/parallel-programming/plinq-data-sample.md) projesinde PLINQDataSample sınıfına yapıştırın ve F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="d68bc-114">To run this method, paste it into the PLINQDataSample class in the [PLINQ Data Sample](../../../docs/standard/parallel-programming/plinq-data-sample.md) project and press F5.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d68bc-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d68bc-115">See also</span></span>

- <xref:System.Linq.ParallelEnumerable>
- [<span data-ttu-id="d68bc-116">Paralel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="d68bc-116">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/introduction-to-plinq.md)
