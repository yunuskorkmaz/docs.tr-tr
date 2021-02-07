---
description: 'Hakkında daha fazla bilgi edinin: Iki sıra arasındaki küme farkını döndürme'
title: İki Dizi Arasındaki Küme Farkını Döndürme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 62efb546-c898-408f-af21-36e7c6fed217
ms.openlocfilehash: 6836195ac4e1ee678fd3e8089e7c341f7dd247e8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99662994"
---
# <a name="return-the-set-difference-between-two-sequences"></a><span data-ttu-id="37031-103">İki Dizi Arasındaki Küme Farkını Döndürme</span><span class="sxs-lookup"><span data-stu-id="37031-103">Return the Set Difference Between Two Sequences</span></span>

<span data-ttu-id="37031-104"><xref:System.Linq.Queryable.Except%2A>İki sıra arasındaki küme farkını döndürmek için işlecini kullanın.</span><span class="sxs-lookup"><span data-stu-id="37031-104">Use the <xref:System.Linq.Queryable.Except%2A> operator to return the set difference between two sequences.</span></span>  
  
## <a name="example"></a><span data-ttu-id="37031-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="37031-105">Example</span></span>  

 <span data-ttu-id="37031-106">Bu örnek, <xref:System.Linq.Queryable.Except%2A> `Customers` canlı ancak canlı olmayan tüm ülkelerin/bölgelerin bir dizisini döndürmek için kullanır `Employees` .</span><span class="sxs-lookup"><span data-stu-id="37031-106">This example uses <xref:System.Linq.Queryable.Except%2A> to return a sequence of all countries/regions in which `Customers` live but in which no `Employees` live.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#41](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#41)]
 [!code-vb[DLinqQueryExamples#41](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#41)]  
  
 <span data-ttu-id="37031-107">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]' De, <xref:System.Linq.Queryable.Except%2A> işlem yalnızca kümeler üzerinde tanımlıdır.</span><span class="sxs-lookup"><span data-stu-id="37031-107">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the <xref:System.Linq.Queryable.Except%2A> operation is well defined only on sets.</span></span> <span data-ttu-id="37031-108">Multisets semantiği tanımsızdır.</span><span class="sxs-lookup"><span data-stu-id="37031-108">The semantics for multisets is undefined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37031-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="37031-109">See also</span></span>

- [<span data-ttu-id="37031-110">Sorgu örnekleri</span><span class="sxs-lookup"><span data-stu-id="37031-110">Query Examples</span></span>](query-examples.md)
- [<span data-ttu-id="37031-111">Standart Sorgu İşleci Çevirisi</span><span class="sxs-lookup"><span data-stu-id="37031-111">Standard Query Operator Translation</span></span>](standard-query-operator-translation.md)
