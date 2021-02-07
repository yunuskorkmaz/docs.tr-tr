---
description: 'Hakkında daha fazla bilgi edinin: Iki sıranın küme kesişimini döndürme'
title: İki Dizinin Küme Kesişimini Döndürme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d09c344e-3548-4944-a3ed-051880e3f5b8
ms.openlocfilehash: 163e138761caadb73b6dc5d672c02353a88a2c22
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99662993"
---
# <a name="return-the-set-intersection-of-two-sequences"></a><span data-ttu-id="3b93d-103">İki Dizinin Küme Kesişimini Döndürme</span><span class="sxs-lookup"><span data-stu-id="3b93d-103">Return the Set Intersection of Two Sequences</span></span>

<span data-ttu-id="3b93d-104"><xref:System.Linq.Queryable.Intersect%2A>İki sıranın küme kesişimini döndürmek için işlecini kullanın.</span><span class="sxs-lookup"><span data-stu-id="3b93d-104">Use the <xref:System.Linq.Queryable.Intersect%2A> operator to return the set intersection of two sequences.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3b93d-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="3b93d-105">Example</span></span>  

 <span data-ttu-id="3b93d-106">Bu örnek, <xref:System.Linq.Queryable.Intersect%2A> hem hem de canlı olan tüm ülkelerin/bölgelerin bir dizisini döndürmek için kullanır `Customers` `Employees` .</span><span class="sxs-lookup"><span data-stu-id="3b93d-106">This example uses <xref:System.Linq.Queryable.Intersect%2A> to return a sequence of all countries/regions in which both `Customers` and `Employees` live.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#42](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#42)]
 [!code-vb[DLinqQueryExamples#42](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#42)]  
  
 <span data-ttu-id="3b93d-107">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]' De, <xref:System.Linq.Queryable.Intersect%2A> işlem yalnızca kümeler üzerinde tanımlıdır.</span><span class="sxs-lookup"><span data-stu-id="3b93d-107">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the <xref:System.Linq.Queryable.Intersect%2A> operation is well defined only on sets.</span></span> <span data-ttu-id="3b93d-108">Multisets semantiği tanımsızdır.</span><span class="sxs-lookup"><span data-stu-id="3b93d-108">The semantics for multisets is undefined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b93d-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3b93d-109">See also</span></span>

- [<span data-ttu-id="3b93d-110">Sorgu örnekleri</span><span class="sxs-lookup"><span data-stu-id="3b93d-110">Query Examples</span></span>](query-examples.md)
- [<span data-ttu-id="3b93d-111">Standart Sorgu İşleci Çevirisi</span><span class="sxs-lookup"><span data-stu-id="3b93d-111">Standard Query Operator Translation</span></span>](standard-query-operator-translation.md)
