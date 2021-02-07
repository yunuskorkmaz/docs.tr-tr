---
description: 'Hakkında daha fazla bilgi edinin: dizideki öğelerin sayısını sayma'
title: Dizideki Öğe Sayısını Sayma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ccbe5d54-c9eb-4b14-b0ab-f628483c5f99
ms.openlocfilehash: 91030516098e900229a1e131ea0c9a7d8bef4034
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99663085"
---
# <a name="count-the-number-of-elements-in-a-sequence"></a><span data-ttu-id="2dd98-103">Dizideki Öğe Sayısını Sayma</span><span class="sxs-lookup"><span data-stu-id="2dd98-103">Count the Number of Elements in a Sequence</span></span>

<span data-ttu-id="2dd98-104"><xref:System.Linq.Enumerable.Count%2A>Dizideki öğelerin sayısını saymak için işlecini kullanın.</span><span class="sxs-lookup"><span data-stu-id="2dd98-104">Use the <xref:System.Linq.Enumerable.Count%2A> operator to count the number of elements in a sequence.</span></span>  
  
 <span data-ttu-id="2dd98-105">Bu sorguyu Northwind örnek veritabanına karşı çalıştırmak bir çıktı üretir `91` .</span><span class="sxs-lookup"><span data-stu-id="2dd98-105">Running this query against the Northwind sample database produces an output of `91`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2dd98-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="2dd98-106">Example</span></span>  

 <span data-ttu-id="2dd98-107">Aşağıdaki örnek, veritabanındaki sayısını sayar `Customers` .</span><span class="sxs-lookup"><span data-stu-id="2dd98-107">The following example counts the number of `Customers` in the database.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#4)]
 [!code-vb[DLinqQueryExamples#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#4)]  
  
## <a name="example"></a><span data-ttu-id="2dd98-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="2dd98-108">Example</span></span>  

 <span data-ttu-id="2dd98-109">Aşağıdaki örnek, veritabanında Kullanımdan kaldırılmış olan ürünlerin sayısını sayar.</span><span class="sxs-lookup"><span data-stu-id="2dd98-109">The following example counts the number of products in the database that have not been discontinued.</span></span>  
  
 <span data-ttu-id="2dd98-110">Bu örneği Northwind örnek veritabanına karşı çalıştırmak, çıkışı üretir `69` .</span><span class="sxs-lookup"><span data-stu-id="2dd98-110">Running this example against the Northwind sample database produces an output of `69`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#5)]
 [!code-vb[DLinqQueryExamples#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="2dd98-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2dd98-111">See also</span></span>

- [<span data-ttu-id="2dd98-112">Toplu Sorgular</span><span class="sxs-lookup"><span data-stu-id="2dd98-112">Aggregate Queries</span></span>](aggregate-queries.md)
- [<span data-ttu-id="2dd98-113">Örnek Veritabanları İndirme</span><span class="sxs-lookup"><span data-stu-id="2dd98-113">Downloading Sample Databases</span></span>](downloading-sample-databases.md)
