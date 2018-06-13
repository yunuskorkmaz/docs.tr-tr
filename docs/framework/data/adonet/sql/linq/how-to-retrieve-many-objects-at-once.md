---
title: 'Nasıl yapılır: aynı anda birçok nesne alma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 18aff4d8-bde8-461b-9960-ccabb24e9d22
ms.openlocfilehash: fbe1632abf56beca5abfa209bdf269c6757f9c7a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33359910"
---
# <a name="how-to-retrieve-many-objects-at-once"></a><span data-ttu-id="e7bf1-102">Nasıl yapılır: aynı anda birçok nesne alma</span><span class="sxs-lookup"><span data-stu-id="e7bf1-102">How to: Retrieve Many Objects At Once</span></span>
<span data-ttu-id="e7bf1-103">Kullanarak bir sorgu birçok nesne alabilirsiniz <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A>.</span><span class="sxs-lookup"><span data-stu-id="e7bf1-103">You can retrieve many objects in one query by using <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e7bf1-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="e7bf1-104">Example</span></span>  
 <span data-ttu-id="e7bf1-105">Aşağıdaki kod <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> her ikisi de almak için yöntemini `Customer` ve `Order` nesneleri.</span><span class="sxs-lookup"><span data-stu-id="e7bf1-105">The following code uses the <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> method to retrieve both `Customer` and `Order` objects.</span></span>  
  
 [!code-csharp[DLinqQueryConcepts#9](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#9)]
 [!code-vb[DLinqQueryConcepts#9](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#9)]  
  
## <a name="see-also"></a><span data-ttu-id="e7bf1-106">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e7bf1-106">See Also</span></span>  
 [<span data-ttu-id="e7bf1-107">Sorgu Kavramları</span><span class="sxs-lookup"><span data-stu-id="e7bf1-107">Query Concepts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
