---
title: İki Dizi Arasındaki Küme Farkını Döndürme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 62efb546-c898-408f-af21-36e7c6fed217
ms.openlocfilehash: 49a8d22377ef1f7d0fde16880a82002754e1bbc4
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91200335"
---
# <a name="return-the-set-difference-between-two-sequences"></a><span data-ttu-id="9564a-102">İki Dizi Arasındaki Küme Farkını Döndürme</span><span class="sxs-lookup"><span data-stu-id="9564a-102">Return the Set Difference Between Two Sequences</span></span>

<span data-ttu-id="9564a-103"><xref:System.Linq.Queryable.Except%2A>İki sıra arasındaki küme farkını döndürmek için işlecini kullanın.</span><span class="sxs-lookup"><span data-stu-id="9564a-103">Use the <xref:System.Linq.Queryable.Except%2A> operator to return the set difference between two sequences.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9564a-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="9564a-104">Example</span></span>  

 <span data-ttu-id="9564a-105">Bu örnek, <xref:System.Linq.Queryable.Except%2A> `Customers` canlı ancak canlı olmayan tüm ülkelerin/bölgelerin bir dizisini döndürmek için kullanır `Employees` .</span><span class="sxs-lookup"><span data-stu-id="9564a-105">This example uses <xref:System.Linq.Queryable.Except%2A> to return a sequence of all countries/regions in which `Customers` live but in which no `Employees` live.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#41](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#41)]
 [!code-vb[DLinqQueryExamples#41](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#41)]  
  
 <span data-ttu-id="9564a-106">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]' De, <xref:System.Linq.Queryable.Except%2A> işlem yalnızca kümeler üzerinde tanımlıdır.</span><span class="sxs-lookup"><span data-stu-id="9564a-106">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the <xref:System.Linq.Queryable.Except%2A> operation is well defined only on sets.</span></span> <span data-ttu-id="9564a-107">Multisets semantiği tanımsızdır.</span><span class="sxs-lookup"><span data-stu-id="9564a-107">The semantics for multisets is undefined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9564a-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9564a-108">See also</span></span>

- [<span data-ttu-id="9564a-109">Sorgu örnekleri</span><span class="sxs-lookup"><span data-stu-id="9564a-109">Query Examples</span></span>](query-examples.md)
- [<span data-ttu-id="9564a-110">Standart Sorgu İşleci Çevirisi</span><span class="sxs-lookup"><span data-stu-id="9564a-110">Standard Query Operator Translation</span></span>](standard-query-operator-translation.md)
