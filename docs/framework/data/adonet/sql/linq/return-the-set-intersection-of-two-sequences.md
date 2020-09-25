---
title: İki Dizinin Küme Kesişimini Döndürme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d09c344e-3548-4944-a3ed-051880e3f5b8
ms.openlocfilehash: 421ec544345e41f910bf80c855a3a6b4de1c46a6
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91200231"
---
# <a name="return-the-set-intersection-of-two-sequences"></a><span data-ttu-id="8e0b4-102">İki Dizinin Küme Kesişimini Döndürme</span><span class="sxs-lookup"><span data-stu-id="8e0b4-102">Return the Set Intersection of Two Sequences</span></span>

<span data-ttu-id="8e0b4-103"><xref:System.Linq.Queryable.Intersect%2A>İki sıranın küme kesişimini döndürmek için işlecini kullanın.</span><span class="sxs-lookup"><span data-stu-id="8e0b4-103">Use the <xref:System.Linq.Queryable.Intersect%2A> operator to return the set intersection of two sequences.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8e0b4-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="8e0b4-104">Example</span></span>  

 <span data-ttu-id="8e0b4-105">Bu örnek, <xref:System.Linq.Queryable.Intersect%2A> hem hem de canlı olan tüm ülkelerin/bölgelerin bir dizisini döndürmek için kullanır `Customers` `Employees` .</span><span class="sxs-lookup"><span data-stu-id="8e0b4-105">This example uses <xref:System.Linq.Queryable.Intersect%2A> to return a sequence of all countries/regions in which both `Customers` and `Employees` live.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#42](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#42)]
 [!code-vb[DLinqQueryExamples#42](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#42)]  
  
 <span data-ttu-id="8e0b4-106">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]' De, <xref:System.Linq.Queryable.Intersect%2A> işlem yalnızca kümeler üzerinde tanımlıdır.</span><span class="sxs-lookup"><span data-stu-id="8e0b4-106">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the <xref:System.Linq.Queryable.Intersect%2A> operation is well defined only on sets.</span></span> <span data-ttu-id="8e0b4-107">Multisets semantiği tanımsızdır.</span><span class="sxs-lookup"><span data-stu-id="8e0b4-107">The semantics for multisets is undefined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e0b4-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8e0b4-108">See also</span></span>

- [<span data-ttu-id="8e0b4-109">Sorgu örnekleri</span><span class="sxs-lookup"><span data-stu-id="8e0b4-109">Query Examples</span></span>](query-examples.md)
- [<span data-ttu-id="8e0b4-110">Standart Sorgu İşleci Çevirisi</span><span class="sxs-lookup"><span data-stu-id="8e0b4-110">Standard Query Operator Translation</span></span>](standard-query-operator-translation.md)
