---
title: İki sıranın arasında ayarlanmış farkı döndürür
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 62efb546-c898-408f-af21-36e7c6fed217
ms.openlocfilehash: 282ec36a2ad489e77db9fb5b338d3189c3001f03
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54609037"
---
# <a name="return-the-set-difference-between-two-sequences"></a><span data-ttu-id="901a2-102">İki sıranın arasında ayarlanmış farkı döndürür</span><span class="sxs-lookup"><span data-stu-id="901a2-102">Return the Set Difference Between Two Sequences</span></span>
<span data-ttu-id="901a2-103">Kullanım <xref:System.Linq.Queryable.Except%2A> iki dizileri arasında ayarlanmış farkı döndürülecek işleci.</span><span class="sxs-lookup"><span data-stu-id="901a2-103">Use the <xref:System.Linq.Queryable.Except%2A> operator to return the set difference between two sequences.</span></span>  
  
## <a name="example"></a><span data-ttu-id="901a2-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="901a2-104">Example</span></span>  
 <span data-ttu-id="901a2-105">Bu örnekte <xref:System.Linq.Queryable.Except%2A> , tüm ülkeler bir dizisini döndürmek için `Customers` hangi yok, ancak canlı `Employees` Canlı.</span><span class="sxs-lookup"><span data-stu-id="901a2-105">This example uses <xref:System.Linq.Queryable.Except%2A> to return a sequence of all countries in which `Customers` live but in which no `Employees` live.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#41](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#41)]
 [!code-vb[DLinqQueryExamples#41](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#41)]  
  
 <span data-ttu-id="901a2-106">İçinde [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], <xref:System.Linq.Queryable.Except%2A> işlemdir kümelerinde yalnızca iyi tanımlanmış.</span><span class="sxs-lookup"><span data-stu-id="901a2-106">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the <xref:System.Linq.Queryable.Except%2A> operation is well defined only on sets.</span></span> <span data-ttu-id="901a2-107">Semantiği multisets için tanımlı değil.</span><span class="sxs-lookup"><span data-stu-id="901a2-107">The semantics for multisets is undefined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="901a2-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="901a2-108">See also</span></span>
- [<span data-ttu-id="901a2-109">Sorgu Örnekleri</span><span class="sxs-lookup"><span data-stu-id="901a2-109">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
- [<span data-ttu-id="901a2-110">Standart Sorgu İşleci Çevirisi</span><span class="sxs-lookup"><span data-stu-id="901a2-110">Standard Query Operator Translation</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md)
