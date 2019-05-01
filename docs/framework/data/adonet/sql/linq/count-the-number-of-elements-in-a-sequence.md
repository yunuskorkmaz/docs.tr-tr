---
title: Dizideki Öğe Sayısını Sayma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ccbe5d54-c9eb-4b14-b0ab-f628483c5f99
ms.openlocfilehash: b39b0a1487c9f250e32b13330f2f70b7e3c7c877
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62032930"
---
# <a name="count-the-number-of-elements-in-a-sequence"></a><span data-ttu-id="f0207-102">Dizideki Öğe Sayısını Sayma</span><span class="sxs-lookup"><span data-stu-id="f0207-102">Count the Number of Elements in a Sequence</span></span>
<span data-ttu-id="f0207-103">Kullanım <xref:System.Linq.Enumerable.Count%2A> işlecini bir dizideki öğelerin sayısı.</span><span class="sxs-lookup"><span data-stu-id="f0207-103">Use the <xref:System.Linq.Enumerable.Count%2A> operator to count the number of elements in a sequence.</span></span>  
  
 <span data-ttu-id="f0207-104">Bu sorgu, Northwind örnek veritabanına karşı çalışan bir çıktısı üretir `91`.</span><span class="sxs-lookup"><span data-stu-id="f0207-104">Running this query against the Northwind sample database produces an output of `91`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f0207-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="f0207-105">Example</span></span>  
 <span data-ttu-id="f0207-106">Aşağıdaki örnek sayısını sayar `Customers` veritabanında.</span><span class="sxs-lookup"><span data-stu-id="f0207-106">The following example counts the number of `Customers` in the database.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#4)]
 [!code-vb[DLinqQueryExamples#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#4)]  
  
## <a name="example"></a><span data-ttu-id="f0207-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="f0207-107">Example</span></span>  
 <span data-ttu-id="f0207-108">Aşağıdaki örnek veritabanındaki üretilmeyen ürünler sayar.</span><span class="sxs-lookup"><span data-stu-id="f0207-108">The following example counts the number of products in the database that have not been discontinued.</span></span>  
  
 <span data-ttu-id="f0207-109">Bu örnek Northwind örnek veritabanına karşı çalıştırma, bir çıkış üretir `69`.</span><span class="sxs-lookup"><span data-stu-id="f0207-109">Running this example against the Northwind sample database produces an output of `69`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#5)]
 [!code-vb[DLinqQueryExamples#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="f0207-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f0207-110">See also</span></span>

- [<span data-ttu-id="f0207-111">Toplu Sorgular</span><span class="sxs-lookup"><span data-stu-id="f0207-111">Aggregate Queries</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/aggregate-queries.md)
- [<span data-ttu-id="f0207-112">Örnek Veritabanları İndirme</span><span class="sxs-lookup"><span data-stu-id="f0207-112">Downloading Sample Databases</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
