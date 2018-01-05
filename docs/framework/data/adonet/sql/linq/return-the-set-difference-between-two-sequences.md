---
title: "İki sıraları arasında ayarlanmış farkı döndürür"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 62efb546-c898-408f-af21-36e7c6fed217
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 7156e6a60527f4fd33e9b8d56504b4697152261e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="return-the-set-difference-between-two-sequences"></a><span data-ttu-id="c95bc-102">İki sıraları arasında ayarlanmış farkı döndürür</span><span class="sxs-lookup"><span data-stu-id="c95bc-102">Return the Set Difference Between Two Sequences</span></span>
<span data-ttu-id="c95bc-103">Kullanım <xref:System.Linq.Queryable.Except%2A> iki sıraları arasında ayarlanmış farkı döndürülecek işleci.</span><span class="sxs-lookup"><span data-stu-id="c95bc-103">Use the <xref:System.Linq.Queryable.Except%2A> operator to return the set difference between two sequences.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c95bc-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="c95bc-104">Example</span></span>  
 <span data-ttu-id="c95bc-105">Bu örnekte <xref:System.Linq.Queryable.Except%2A> tüm ülkelerde bir dizi içinde dönmek için `Customers` hangi Hayır, Canlı ancak `Employees` Canlı.</span><span class="sxs-lookup"><span data-stu-id="c95bc-105">This example uses <xref:System.Linq.Queryable.Except%2A> to return a sequence of all countries in which `Customers` live but in which no `Employees` live.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#41](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#41)]
 [!code-vb[DLinqQueryExamples#41](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#41)]  
  
 <span data-ttu-id="c95bc-106">İçinde [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], <xref:System.Linq.Queryable.Except%2A> işlemi yalnızca kümeleri üzerinde iyi tanımlanmış.</span><span class="sxs-lookup"><span data-stu-id="c95bc-106">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the <xref:System.Linq.Queryable.Except%2A> operation is well defined only on sets.</span></span> <span data-ttu-id="c95bc-107">Multisets anlamları tanımlanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="c95bc-107">The semantics for multisets is undefined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c95bc-108">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c95bc-108">See Also</span></span>  
 [<span data-ttu-id="c95bc-109">Sorgu Örnekleri</span><span class="sxs-lookup"><span data-stu-id="c95bc-109">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)  
 [<span data-ttu-id="c95bc-110">Standart Sorgu İşleci Çevirisi</span><span class="sxs-lookup"><span data-stu-id="c95bc-110">Standard Query Operator Translation</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md)
