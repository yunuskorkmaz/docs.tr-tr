---
title: İki Dizinin Küme Kesişimini Döndürme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d09c344e-3548-4944-a3ed-051880e3f5b8
ms.openlocfilehash: 944d0b2efe1e74f901a493d1c3202d0f180d599d
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70792708"
---
# <a name="return-the-set-intersection-of-two-sequences"></a><span data-ttu-id="4c2e8-102">İki Dizinin Küme Kesişimini Döndürme</span><span class="sxs-lookup"><span data-stu-id="4c2e8-102">Return the Set Intersection of Two Sequences</span></span>
<span data-ttu-id="4c2e8-103">İki sıranın küme kesişimini döndürmek için işlecinikullanın.<xref:System.Linq.Queryable.Intersect%2A></span><span class="sxs-lookup"><span data-stu-id="4c2e8-103">Use the <xref:System.Linq.Queryable.Intersect%2A> operator to return the set intersection of two sequences.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4c2e8-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="4c2e8-104">Example</span></span>  
 <span data-ttu-id="4c2e8-105">Bu örnek, <xref:System.Linq.Queryable.Intersect%2A> `Customers` hemhemdecanlıolantümülkelerin/bölgelerinbirdizisinidöndürmekiçinkullanır.`Employees`</span><span class="sxs-lookup"><span data-stu-id="4c2e8-105">This example uses <xref:System.Linq.Queryable.Intersect%2A> to return a sequence of all countries/regions in which both `Customers` and `Employees` live.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#42](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#42)]
 [!code-vb[DLinqQueryExamples#42](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#42)]  
  
 <span data-ttu-id="4c2e8-106">' De [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], işlemyalnızcakümelerüzerindetanımlıdır.<xref:System.Linq.Queryable.Intersect%2A></span><span class="sxs-lookup"><span data-stu-id="4c2e8-106">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the <xref:System.Linq.Queryable.Intersect%2A> operation is well defined only on sets.</span></span> <span data-ttu-id="4c2e8-107">Multisets semantiği tanımsızdır.</span><span class="sxs-lookup"><span data-stu-id="4c2e8-107">The semantics for multisets is undefined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c2e8-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4c2e8-108">See also</span></span>

- [<span data-ttu-id="4c2e8-109">Sorgu Örnekleri</span><span class="sxs-lookup"><span data-stu-id="4c2e8-109">Query Examples</span></span>](query-examples.md)
- [<span data-ttu-id="4c2e8-110">Standart Sorgu İşleci Çevirisi</span><span class="sxs-lookup"><span data-stu-id="4c2e8-110">Standard Query Operator Translation</span></span>](standard-query-operator-translation.md)
