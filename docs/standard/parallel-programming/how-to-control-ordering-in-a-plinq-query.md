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
ms.openlocfilehash: aaa08106126212345bb594cdeabe6e7281cd7b5e
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44180793"
---
# <a name="how-to-control-ordering-in-a-plinq-query"></a><span data-ttu-id="64ef1-102">Nasıl yapılır: PLINQ Sorgusunda Sıralama Denetimi</span><span class="sxs-lookup"><span data-stu-id="64ef1-102">How to: Control Ordering in a PLINQ Query</span></span>
<span data-ttu-id="64ef1-103">Bu örnekler kullanarak bir PLINQ sorgusunda sıralama denetimi nasıl <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> genişletme yöntemi.</span><span class="sxs-lookup"><span data-stu-id="64ef1-103">These examples show how to control the ordering in a PLINQ query by using the <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> extension method.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="64ef1-104">Bu örnek kullanımını göstermek için tasarlanmıştır ve olabilir veya eşdeğer sıralı LINQ hızlıdır Plınq sorgularının çalışmayabilir.</span><span class="sxs-lookup"><span data-stu-id="64ef1-104">These examples are primarily intended to demonstrate usage, and may or may not run faster than the equivalent sequential LINQ to Objects queries.</span></span>  
  
## <a name="example"></a><span data-ttu-id="64ef1-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="64ef1-105">Example</span></span>  
 <span data-ttu-id="64ef1-106">Aşağıdaki örnek, kaynak dizi sıralamasını korur.</span><span class="sxs-lookup"><span data-stu-id="64ef1-106">The following example preserves the ordering of the source sequence.</span></span> <span data-ttu-id="64ef1-107">Bu bazen gereklidir. Örneğin bazı sorgu işleçleri doğru sonuçlar için bir sıralanmış kaynak dizisi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="64ef1-107">This is sometimes necessary; for example some query operators require an ordered source sequence to produce correct results.</span></span>  
  
 [!code-csharp[PLINQ#12](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#12)]
 [!code-vb[PLINQ#12](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#12)]  
  
## <a name="example"></a><span data-ttu-id="64ef1-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="64ef1-108">Example</span></span>  
 <span data-ttu-id="64ef1-109">Aşağıdaki örnekte gösterildiği bazı sorgu işleçleri olan kaynak dizisi, büyük olasılıkla sıralanabilmesi beklenir.</span><span class="sxs-lookup"><span data-stu-id="64ef1-109">The following example shows some query operators whose source sequence is probably expected to be ordered.</span></span> <span data-ttu-id="64ef1-110">Bu işleçler, sırasız dizileri üzerinde çalışır, ancak beklenmeyen sonuçlara neden.</span><span class="sxs-lookup"><span data-stu-id="64ef1-110">These operators will work on unordered sequences, but they might produce unexpected results.</span></span>  
  
 [!code-csharp[PLINQ#14](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#14)]
 [!code-vb[PLINQ#14](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#14)]  
  
 <span data-ttu-id="64ef1-111">Bu yöntem çalıştırılacak PLINQDataSample sınıfında yapıştırın [PLINQ veri örneği](../../../docs/standard/parallel-programming/plinq-data-sample.md) proje ve F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="64ef1-111">To run this method, paste it into the PLINQDataSample class in the [PLINQ Data Sample](../../../docs/standard/parallel-programming/plinq-data-sample.md) project and press F5.</span></span>  
  
## <a name="example"></a><span data-ttu-id="64ef1-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="64ef1-112">Example</span></span>  
 <span data-ttu-id="64ef1-113">Aşağıdaki örnek, bir sorgu için ilk bölümünü sıralamasını korumak sonra join tümcesinin performansını artırmak için sıralama kaldırma ve sıralama için Sonuç dizisi'ı yeniden gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="64ef1-113">The following example shows how to preserve ordering for the first part of a query, then remove the ordering to increase the performance of a join clause, and then reapply ordering to the final result sequence.</span></span>  
  
 [!code-csharp[PLINQ#15](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#15)]
 [!code-vb[PLINQ#15](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#15)]  
  
 <span data-ttu-id="64ef1-114">Bu yöntem çalıştırılacak PLINQDataSample sınıfında yapıştırın [PLINQ veri örneği](../../../docs/standard/parallel-programming/plinq-data-sample.md) proje ve F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="64ef1-114">To run this method, paste it into the PLINQDataSample class in the [PLINQ Data Sample](../../../docs/standard/parallel-programming/plinq-data-sample.md) project and press F5.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64ef1-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="64ef1-115">See also</span></span>

- <xref:System.Linq.ParallelEnumerable>  
- [<span data-ttu-id="64ef1-116">Paralel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="64ef1-116">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
