---
title: İki Dizinin Küme Kesişimini Döndürme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d09c344e-3548-4944-a3ed-051880e3f5b8
ms.openlocfilehash: 07f48ab7ef1095ba80b1a955a4bd1ea602a75aa8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59205920"
---
# <a name="return-the-set-intersection-of-two-sequences"></a><span data-ttu-id="822c6-102">İki Dizinin Küme Kesişimini Döndürme</span><span class="sxs-lookup"><span data-stu-id="822c6-102">Return the Set Intersection of Two Sequences</span></span>
<span data-ttu-id="822c6-103">Kullanım <xref:System.Linq.Queryable.Intersect%2A> işlecini iki dizinin küme kesişimini döndürür.</span><span class="sxs-lookup"><span data-stu-id="822c6-103">Use the <xref:System.Linq.Queryable.Intersect%2A> operator to return the set intersection of two sequences.</span></span>  
  
## <a name="example"></a><span data-ttu-id="822c6-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="822c6-104">Example</span></span>  
 <span data-ttu-id="822c6-105">Bu örnekte <xref:System.Linq.Queryable.Intersect%2A> hangi ikisinde tüm ülkeler bir dizisini döndürmek için `Customers` ve `Employees` Canlı.</span><span class="sxs-lookup"><span data-stu-id="822c6-105">This example uses <xref:System.Linq.Queryable.Intersect%2A> to return a sequence of all countries in which both `Customers` and `Employees` live.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#42](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#42)]
 [!code-vb[DLinqQueryExamples#42](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#42)]  
  
 <span data-ttu-id="822c6-106">İçinde [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], <xref:System.Linq.Queryable.Intersect%2A> işlemdir kümelerinde yalnızca iyi tanımlanmış.</span><span class="sxs-lookup"><span data-stu-id="822c6-106">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the <xref:System.Linq.Queryable.Intersect%2A> operation is well defined only on sets.</span></span> <span data-ttu-id="822c6-107">Semantiği multisets için tanımlı değil.</span><span class="sxs-lookup"><span data-stu-id="822c6-107">The semantics for multisets is undefined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="822c6-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="822c6-108">See also</span></span>

- [<span data-ttu-id="822c6-109">Sorgu Örnekleri</span><span class="sxs-lookup"><span data-stu-id="822c6-109">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
- [<span data-ttu-id="822c6-110">Standart Sorgu İşleci Çevirisi</span><span class="sxs-lookup"><span data-stu-id="822c6-110">Standard Query Operator Translation</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md)
