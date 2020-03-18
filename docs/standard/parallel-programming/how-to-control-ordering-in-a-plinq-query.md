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
ms.openlocfilehash: d38c039fa99433d9476d62c1e96dff7e306fd766
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73123117"
---
# <a name="how-to-control-ordering-in-a-plinq-query"></a><span data-ttu-id="d5413-102">Nasıl yapılır: PLINQ Sorgusunda Sıralama Denetimi</span><span class="sxs-lookup"><span data-stu-id="d5413-102">How to: Control Ordering in a PLINQ Query</span></span>
<span data-ttu-id="d5413-103">Bu örnekler, uzantı yöntemini kullanarak PLINQ sorgusunda sıralamanın nasıl denetlenebildiğini <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> gösterir.</span><span class="sxs-lookup"><span data-stu-id="d5413-103">These examples show how to control the ordering in a PLINQ query by using the <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> extension method.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="d5413-104">Bu örnekler öncelikle kullanımı göstermek için tasarlanmıştır ve Nesneler sorgularına eşdeğer ardışık LINQ'dan daha hızlı çalışabilir veya çalışmayabilir.</span><span class="sxs-lookup"><span data-stu-id="d5413-104">These examples are primarily intended to demonstrate usage, and may or may not run faster than the equivalent sequential LINQ to Objects queries.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d5413-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="d5413-105">Example</span></span>  
 <span data-ttu-id="d5413-106">Aşağıdaki örnek, kaynak dizinin sırasını korur.</span><span class="sxs-lookup"><span data-stu-id="d5413-106">The following example preserves the ordering of the source sequence.</span></span> <span data-ttu-id="d5413-107">Bu bazen gereklidir; örneğin, bazı sorgu işleçleri doğru sonuçlar üretmek için sıralı bir kaynak sıragerektirir.</span><span class="sxs-lookup"><span data-stu-id="d5413-107">This is sometimes necessary; for example some query operators require an ordered source sequence to produce correct results.</span></span>  
  
 [!code-csharp[PLINQ#12](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#12)]
 [!code-vb[PLINQ#12](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#12)]  
  
## <a name="example"></a><span data-ttu-id="d5413-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="d5413-108">Example</span></span>  
 <span data-ttu-id="d5413-109">Aşağıdaki örnek, kaynak sırası büyük olasılıkla sıralanmış olması beklenen bazı sorgu işleçleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="d5413-109">The following example shows some query operators whose source sequence is probably expected to be ordered.</span></span> <span data-ttu-id="d5413-110">Bu işleçler sıralanmamış diziler üzerinde çalışır, ancak beklenmeyen sonuçlar üretebilir.</span><span class="sxs-lookup"><span data-stu-id="d5413-110">These operators will work on unordered sequences, but they might produce unexpected results.</span></span>  
  
 [!code-csharp[PLINQ#14](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#14)]
 [!code-vb[PLINQ#14](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#14)]  
  
 <span data-ttu-id="d5413-111">Bu yöntemi çalıştırmak için [PLINQ Data Sample](../../../docs/standard/parallel-programming/plinq-data-sample.md) projesinde PLINQDataSample sınıfına yapıştırın ve F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="d5413-111">To run this method, paste it into the PLINQDataSample class in the [PLINQ Data Sample](../../../docs/standard/parallel-programming/plinq-data-sample.md) project and press F5.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d5413-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="d5413-112">Example</span></span>  
 <span data-ttu-id="d5413-113">Aşağıdaki örnek, sorgunun ilk bölümü için sıralamayı nasıl koruyacağını, ardından birleştirilmiş tümcenin performansını artırmak için sıralamayı nasıl kaldıracağını ve ardından son sonuç dizisine sıralamayı yeniden uygulayacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d5413-113">The following example shows how to preserve ordering for the first part of a query, then remove the ordering to increase the performance of a join clause, and then reapply ordering to the final result sequence.</span></span>  
  
 [!code-csharp[PLINQ#15](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#15)]
 [!code-vb[PLINQ#15](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#15)]  
  
 <span data-ttu-id="d5413-114">Bu yöntemi çalıştırmak için [PLINQ Data Sample](../../../docs/standard/parallel-programming/plinq-data-sample.md) projesinde PLINQDataSample sınıfına yapıştırın ve F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="d5413-114">To run this method, paste it into the PLINQDataSample class in the [PLINQ Data Sample](../../../docs/standard/parallel-programming/plinq-data-sample.md) project and press F5.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5413-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d5413-115">See also</span></span>

- <xref:System.Linq.ParallelEnumerable>
- [<span data-ttu-id="d5413-116">Paralel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="d5413-116">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
