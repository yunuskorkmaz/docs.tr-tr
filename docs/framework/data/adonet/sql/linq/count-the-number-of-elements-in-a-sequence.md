---
title: Dizideki Öğe Sayısını Sayma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ccbe5d54-c9eb-4b14-b0ab-f628483c5f99
ms.openlocfilehash: d983bc14f4fda04bda0a6f363db4c11f062c4c48
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91164356"
---
# <a name="count-the-number-of-elements-in-a-sequence"></a><span data-ttu-id="03957-102">Dizideki Öğe Sayısını Sayma</span><span class="sxs-lookup"><span data-stu-id="03957-102">Count the Number of Elements in a Sequence</span></span>

<span data-ttu-id="03957-103"><xref:System.Linq.Enumerable.Count%2A>Dizideki öğelerin sayısını saymak için işlecini kullanın.</span><span class="sxs-lookup"><span data-stu-id="03957-103">Use the <xref:System.Linq.Enumerable.Count%2A> operator to count the number of elements in a sequence.</span></span>  
  
 <span data-ttu-id="03957-104">Bu sorguyu Northwind örnek veritabanına karşı çalıştırmak bir çıktı üretir `91` .</span><span class="sxs-lookup"><span data-stu-id="03957-104">Running this query against the Northwind sample database produces an output of `91`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="03957-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="03957-105">Example</span></span>  

 <span data-ttu-id="03957-106">Aşağıdaki örnek, veritabanındaki sayısını sayar `Customers` .</span><span class="sxs-lookup"><span data-stu-id="03957-106">The following example counts the number of `Customers` in the database.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#4)]
 [!code-vb[DLinqQueryExamples#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#4)]  
  
## <a name="example"></a><span data-ttu-id="03957-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="03957-107">Example</span></span>  

 <span data-ttu-id="03957-108">Aşağıdaki örnek, veritabanında Kullanımdan kaldırılmış olan ürünlerin sayısını sayar.</span><span class="sxs-lookup"><span data-stu-id="03957-108">The following example counts the number of products in the database that have not been discontinued.</span></span>  
  
 <span data-ttu-id="03957-109">Bu örneği Northwind örnek veritabanına karşı çalıştırmak, çıkışı üretir `69` .</span><span class="sxs-lookup"><span data-stu-id="03957-109">Running this example against the Northwind sample database produces an output of `69`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#5)]
 [!code-vb[DLinqQueryExamples#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="03957-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="03957-110">See also</span></span>

- [<span data-ttu-id="03957-111">Toplu Sorgular</span><span class="sxs-lookup"><span data-stu-id="03957-111">Aggregate Queries</span></span>](aggregate-queries.md)
- [<span data-ttu-id="03957-112">Örnek Veritabanları İndirme</span><span class="sxs-lookup"><span data-stu-id="03957-112">Downloading Sample Databases</span></span>](downloading-sample-databases.md)
