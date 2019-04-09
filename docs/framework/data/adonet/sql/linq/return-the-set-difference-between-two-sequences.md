---
title: İki Dizi Arasındaki Küme Farkını Döndürme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 62efb546-c898-408f-af21-36e7c6fed217
ms.openlocfilehash: 7edc60c7ab8510aadd9ac273529a88adeb41352a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59124286"
---
# <a name="return-the-set-difference-between-two-sequences"></a><span data-ttu-id="08784-102">İki Dizi Arasındaki Küme Farkını Döndürme</span><span class="sxs-lookup"><span data-stu-id="08784-102">Return the Set Difference Between Two Sequences</span></span>
<span data-ttu-id="08784-103">Kullanım <xref:System.Linq.Queryable.Except%2A> iki dizileri arasında ayarlanmış farkı döndürülecek işleci.</span><span class="sxs-lookup"><span data-stu-id="08784-103">Use the <xref:System.Linq.Queryable.Except%2A> operator to return the set difference between two sequences.</span></span>  
  
## <a name="example"></a><span data-ttu-id="08784-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="08784-104">Example</span></span>  
 <span data-ttu-id="08784-105">Bu örnekte <xref:System.Linq.Queryable.Except%2A> , tüm ülkeler bir dizisini döndürmek için `Customers` hangi yok, ancak canlı `Employees` Canlı.</span><span class="sxs-lookup"><span data-stu-id="08784-105">This example uses <xref:System.Linq.Queryable.Except%2A> to return a sequence of all countries in which `Customers` live but in which no `Employees` live.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#41](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#41)]
 [!code-vb[DLinqQueryExamples#41](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#41)]  
  
 <span data-ttu-id="08784-106">İçinde [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], <xref:System.Linq.Queryable.Except%2A> işlemdir kümelerinde yalnızca iyi tanımlanmış.</span><span class="sxs-lookup"><span data-stu-id="08784-106">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the <xref:System.Linq.Queryable.Except%2A> operation is well defined only on sets.</span></span> <span data-ttu-id="08784-107">Semantiği multisets için tanımlı değil.</span><span class="sxs-lookup"><span data-stu-id="08784-107">The semantics for multisets is undefined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08784-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="08784-108">See also</span></span>

- [<span data-ttu-id="08784-109">Sorgu Örnekleri</span><span class="sxs-lookup"><span data-stu-id="08784-109">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
- [<span data-ttu-id="08784-110">Standart Sorgu İşleci Çevirisi</span><span class="sxs-lookup"><span data-stu-id="08784-110">Standard Query Operator Translation</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md)
