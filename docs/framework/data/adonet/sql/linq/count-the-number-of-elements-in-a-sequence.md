---
title: Dizideki Öğe Sayısını Sayma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ccbe5d54-c9eb-4b14-b0ab-f628483c5f99
ms.openlocfilehash: 74e24aeb64b0097cba3975e76475034e6bb9544d
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70247699"
---
# <a name="count-the-number-of-elements-in-a-sequence"></a><span data-ttu-id="8fa38-102">Dizideki Öğe Sayısını Sayma</span><span class="sxs-lookup"><span data-stu-id="8fa38-102">Count the Number of Elements in a Sequence</span></span>
<span data-ttu-id="8fa38-103">Dizideki öğelerin sayısını saymak için işlecinikullanın.<xref:System.Linq.Enumerable.Count%2A></span><span class="sxs-lookup"><span data-stu-id="8fa38-103">Use the <xref:System.Linq.Enumerable.Count%2A> operator to count the number of elements in a sequence.</span></span>  
  
 <span data-ttu-id="8fa38-104">Bu sorguyu Northwind örnek veritabanına karşı çalıştırmak bir çıktı `91`üretir.</span><span class="sxs-lookup"><span data-stu-id="8fa38-104">Running this query against the Northwind sample database produces an output of `91`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8fa38-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="8fa38-105">Example</span></span>  
 <span data-ttu-id="8fa38-106">Aşağıdaki örnek, veritabanındaki sayısını `Customers` sayar.</span><span class="sxs-lookup"><span data-stu-id="8fa38-106">The following example counts the number of `Customers` in the database.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#4)]
 [!code-vb[DLinqQueryExamples#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#4)]  
  
## <a name="example"></a><span data-ttu-id="8fa38-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="8fa38-107">Example</span></span>  
 <span data-ttu-id="8fa38-108">Aşağıdaki örnek, veritabanında Kullanımdan kaldırılmış olan ürünlerin sayısını sayar.</span><span class="sxs-lookup"><span data-stu-id="8fa38-108">The following example counts the number of products in the database that have not been discontinued.</span></span>  
  
 <span data-ttu-id="8fa38-109">Bu örneği Northwind örnek veritabanına karşı çalıştırmak, çıkışı `69`üretir.</span><span class="sxs-lookup"><span data-stu-id="8fa38-109">Running this example against the Northwind sample database produces an output of `69`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#5)]
 [!code-vb[DLinqQueryExamples#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="8fa38-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8fa38-110">See also</span></span>

- [<span data-ttu-id="8fa38-111">Toplu Sorgular</span><span class="sxs-lookup"><span data-stu-id="8fa38-111">Aggregate Queries</span></span>](aggregate-queries.md)
- [<span data-ttu-id="8fa38-112">Örnek Veritabanları İndirme</span><span class="sxs-lookup"><span data-stu-id="8fa38-112">Downloading Sample Databases</span></span>](downloading-sample-databases.md)
