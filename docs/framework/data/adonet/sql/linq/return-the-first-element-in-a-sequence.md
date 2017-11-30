---
title: "Bir dizisinde ilk öğesini döndürür"
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
ms.assetid: ccdc3777-b2c2-44e3-a627-abef8d79a555
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: cb43e75ae5cf55df87d00f44aa856d353dd25c0d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="return-the-first-element-in-a-sequence"></a><span data-ttu-id="5d2a5-102">Bir dizisinde ilk öğesini döndürür</span><span class="sxs-lookup"><span data-stu-id="5d2a5-102">Return the First Element in a Sequence</span></span>
<span data-ttu-id="5d2a5-103">Kullanım <xref:System.Linq.Enumerable.First%2A> işleci bir dizisinde ilk öğesini döndürür.</span><span class="sxs-lookup"><span data-stu-id="5d2a5-103">Use the <xref:System.Linq.Enumerable.First%2A> operator to return the first element in a sequence.</span></span> <span data-ttu-id="5d2a5-104">Sorgular kullanan <xref:System.Linq.Enumerable.First%2A> hemen çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="5d2a5-104">Queries that use <xref:System.Linq.Enumerable.First%2A> are executed immediately.</span></span>  
  
> [!NOTE]
>  [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="5d2a5-105">desteklemediği <xref:System.Linq.Enumerable.Last%2A> işleci.</span><span class="sxs-lookup"><span data-stu-id="5d2a5-105"> does not support the <xref:System.Linq.Enumerable.Last%2A> operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5d2a5-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="5d2a5-106">Example</span></span>  
 <span data-ttu-id="5d2a5-107">Aşağıdaki kod ilk bulur `Shipper` bir tabloda:</span><span class="sxs-lookup"><span data-stu-id="5d2a5-107">The following code finds the first `Shipper` in a table:</span></span>  
  
 <span data-ttu-id="5d2a5-108">Northwind örnek veritabanı karşı bu sorguyu çalıştırmak, sonuçları demektir.</span><span class="sxs-lookup"><span data-stu-id="5d2a5-108">If you run this query against the Northwind sample database, the results are</span></span>  
  
 <span data-ttu-id="5d2a5-109">`ID = 1, Company = Speedy Express`.</span><span class="sxs-lookup"><span data-stu-id="5d2a5-109">`ID = 1, Company = Speedy Express`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#14](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#14)]
 [!code-vb[DLinqQueryExamples#14](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#14)]  
  
## <a name="example"></a><span data-ttu-id="5d2a5-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="5d2a5-110">Example</span></span>  
 <span data-ttu-id="5d2a5-111">Aşağıdaki kod tek bulur `Customer` olan `CustomerID` BONAP.</span><span class="sxs-lookup"><span data-stu-id="5d2a5-111">The following code finds the single `Customer` that has the `CustomerID` BONAP.</span></span>  
  
 <span data-ttu-id="5d2a5-112">Northwind örnek veritabanı karşı bu sorguyu çalıştırırsanız, sonuçları olan `ID = BONAP, Contact = Laurence Lebihan`.</span><span class="sxs-lookup"><span data-stu-id="5d2a5-112">If you run this query against the Northwind sample database, the results are `ID = BONAP, Contact = Laurence Lebihan`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#15](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#15)]
 [!code-vb[DLinqQueryExamples#15](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#15)]  
  
## <a name="see-also"></a><span data-ttu-id="5d2a5-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5d2a5-113">See Also</span></span>  
 [<span data-ttu-id="5d2a5-114">Sorgu örnekleri</span><span class="sxs-lookup"><span data-stu-id="5d2a5-114">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)  
 [<span data-ttu-id="5d2a5-115">Örnek veritabanları yükleme</span><span class="sxs-lookup"><span data-stu-id="5d2a5-115">Downloading Sample Databases</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
