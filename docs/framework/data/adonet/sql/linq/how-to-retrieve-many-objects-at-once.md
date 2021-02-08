---
description: 'Daha fazla bilgi edinin: nasıl yapılır: aynı anda birçok nesne alma'
title: 'Nasıl yapılır: Tek Seferde Birçok Nesne Alma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 18aff4d8-bde8-461b-9960-ccabb24e9d22
ms.openlocfilehash: 2bc202e09c64f2a1956b8688be30cfd87fb655c0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802014"
---
# <a name="how-to-retrieve-many-objects-at-once"></a><span data-ttu-id="f3dc5-103">Nasıl yapılır: Tek Seferde Birçok Nesne Alma</span><span class="sxs-lookup"><span data-stu-id="f3dc5-103">How to: Retrieve Many Objects At Once</span></span>

<span data-ttu-id="f3dc5-104">Kullanarak, bir sorgudaki birçok nesneyi alabilirsiniz <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> .</span><span class="sxs-lookup"><span data-stu-id="f3dc5-104">You can retrieve many objects in one query by using <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f3dc5-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="f3dc5-105">Example</span></span>  

 <span data-ttu-id="f3dc5-106">Aşağıdaki kod, <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> ve nesnelerini almak için yöntemini kullanır `Customer` `Order` .</span><span class="sxs-lookup"><span data-stu-id="f3dc5-106">The following code uses the <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> method to retrieve both `Customer` and `Order` objects.</span></span>  
  
 [!code-csharp[DLinqQueryConcepts#9](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#9)]
 [!code-vb[DLinqQueryConcepts#9](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#9)]  
  
## <a name="see-also"></a><span data-ttu-id="f3dc5-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f3dc5-107">See also</span></span>

- [<span data-ttu-id="f3dc5-108">Sorgu Kavramları</span><span class="sxs-lookup"><span data-stu-id="f3dc5-108">Query Concepts</span></span>](query-concepts.md)
