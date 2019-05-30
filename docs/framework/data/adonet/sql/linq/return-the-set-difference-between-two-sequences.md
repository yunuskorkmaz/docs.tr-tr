---
title: İki Dizi Arasındaki Küme Farkını Döndürme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 62efb546-c898-408f-af21-36e7c6fed217
ms.openlocfilehash: 5bb7d797ad2adc4374f7a10c11d66be69feeb7a1
ms.sourcegitcommit: 4735bb7741555bcb870d7b42964d3774f4897a6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/30/2019
ms.locfileid: "66380042"
---
# <a name="return-the-set-difference-between-two-sequences"></a><span data-ttu-id="3d5fb-102">İki Dizi Arasındaki Küme Farkını Döndürme</span><span class="sxs-lookup"><span data-stu-id="3d5fb-102">Return the Set Difference Between Two Sequences</span></span>
<span data-ttu-id="3d5fb-103">Kullanım <xref:System.Linq.Queryable.Except%2A> iki dizileri arasında ayarlanmış farkı döndürülecek işleci.</span><span class="sxs-lookup"><span data-stu-id="3d5fb-103">Use the <xref:System.Linq.Queryable.Except%2A> operator to return the set difference between two sequences.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3d5fb-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="3d5fb-104">Example</span></span>  
 <span data-ttu-id="3d5fb-105">Bu örnekte <xref:System.Linq.Queryable.Except%2A> , tüm ülkeler/bölgeler bir dizisini döndürmek için `Customers` hangi yok, ancak canlı `Employees` Canlı.</span><span class="sxs-lookup"><span data-stu-id="3d5fb-105">This example uses <xref:System.Linq.Queryable.Except%2A> to return a sequence of all countries/regions in which `Customers` live but in which no `Employees` live.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#41](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#41)]
 [!code-vb[DLinqQueryExamples#41](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#41)]  
  
 <span data-ttu-id="3d5fb-106">İçinde [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], <xref:System.Linq.Queryable.Except%2A> işlemdir kümelerinde yalnızca iyi tanımlanmış.</span><span class="sxs-lookup"><span data-stu-id="3d5fb-106">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the <xref:System.Linq.Queryable.Except%2A> operation is well defined only on sets.</span></span> <span data-ttu-id="3d5fb-107">Semantiği multisets için tanımlı değil.</span><span class="sxs-lookup"><span data-stu-id="3d5fb-107">The semantics for multisets is undefined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d5fb-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3d5fb-108">See also</span></span>

- [<span data-ttu-id="3d5fb-109">Sorgu Örnekleri</span><span class="sxs-lookup"><span data-stu-id="3d5fb-109">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
- [<span data-ttu-id="3d5fb-110">Standart Sorgu İşleci Çevirisi</span><span class="sxs-lookup"><span data-stu-id="3d5fb-110">Standard Query Operator Translation</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md)
