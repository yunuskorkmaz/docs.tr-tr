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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 120cc6d08d02fd33510903242c44feae3f8ec5c0
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="return-the-set-difference-between-two-sequences"></a><span data-ttu-id="6494c-102">İki sıraları arasında ayarlanmış farkı döndürür</span><span class="sxs-lookup"><span data-stu-id="6494c-102">Return the Set Difference Between Two Sequences</span></span>
<span data-ttu-id="6494c-103">Kullanım <xref:System.Linq.Queryable.Except%2A> iki sıraları arasında ayarlanmış farkı döndürülecek işleci.</span><span class="sxs-lookup"><span data-stu-id="6494c-103">Use the <xref:System.Linq.Queryable.Except%2A> operator to return the set difference between two sequences.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6494c-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="6494c-104">Example</span></span>  
 <span data-ttu-id="6494c-105">Bu örnekte <xref:System.Linq.Queryable.Except%2A> tüm ülkelerde bir dizi içinde dönmek için `Customers` hangi Hayır, Canlı ancak `Employees` Canlı.</span><span class="sxs-lookup"><span data-stu-id="6494c-105">This example uses <xref:System.Linq.Queryable.Except%2A> to return a sequence of all countries in which `Customers` live but in which no `Employees` live.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#41](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#41)]
 [!code-vb[DLinqQueryExamples#41](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#41)]  
  
 <span data-ttu-id="6494c-106">İçinde [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], <xref:System.Linq.Queryable.Except%2A> işlemi yalnızca kümeleri üzerinde iyi tanımlanmış.</span><span class="sxs-lookup"><span data-stu-id="6494c-106">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the <xref:System.Linq.Queryable.Except%2A> operation is well defined only on sets.</span></span> <span data-ttu-id="6494c-107">Multisets anlamları tanımlanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="6494c-107">The semantics for multisets is undefined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6494c-108">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6494c-108">See Also</span></span>  
 [<span data-ttu-id="6494c-109">Sorgu Örnekleri</span><span class="sxs-lookup"><span data-stu-id="6494c-109">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)  
 [<span data-ttu-id="6494c-110">Standart Sorgu İşleci Çevirisi</span><span class="sxs-lookup"><span data-stu-id="6494c-110">Standard Query Operator Translation</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md)
