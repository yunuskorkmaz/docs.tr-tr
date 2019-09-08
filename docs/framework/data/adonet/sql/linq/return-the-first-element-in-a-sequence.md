---
title: Dizideki İlk Öğeyi Döndürme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ccdc3777-b2c2-44e3-a627-abef8d79a555
ms.openlocfilehash: 9faeed754942d7b176872484ac776c1df592bbd8
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70792716"
---
# <a name="return-the-first-element-in-a-sequence"></a><span data-ttu-id="4a389-102">Dizideki İlk Öğeyi Döndürme</span><span class="sxs-lookup"><span data-stu-id="4a389-102">Return the First Element in a Sequence</span></span>
<span data-ttu-id="4a389-103">Bir dizideki ilk öğeyi döndürmek için işlecinikullanın.<xref:System.Linq.Enumerable.First%2A></span><span class="sxs-lookup"><span data-stu-id="4a389-103">Use the <xref:System.Linq.Enumerable.First%2A> operator to return the first element in a sequence.</span></span> <span data-ttu-id="4a389-104"><xref:System.Linq.Enumerable.First%2A> Kullanan sorgular hemen yürütülür.</span><span class="sxs-lookup"><span data-stu-id="4a389-104">Queries that use <xref:System.Linq.Enumerable.First%2A> are executed immediately.</span></span>  
  
> [!NOTE]
> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="4a389-105"><xref:System.Linq.Enumerable.Last%2A> işlecini desteklemez.</span><span class="sxs-lookup"><span data-stu-id="4a389-105">does not support the <xref:System.Linq.Enumerable.Last%2A> operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4a389-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="4a389-106">Example</span></span>  
 <span data-ttu-id="4a389-107">Aşağıdaki kod, bir tabloda birincni `Shipper` bulur:</span><span class="sxs-lookup"><span data-stu-id="4a389-107">The following code finds the first `Shipper` in a table:</span></span>  
  
 <span data-ttu-id="4a389-108">Bu sorguyu Northwind örnek veritabanında çalıştırırsanız, sonuçlar</span><span class="sxs-lookup"><span data-stu-id="4a389-108">If you run this query against the Northwind sample database, the results are</span></span>  
  
 <span data-ttu-id="4a389-109">`ID = 1, Company = Speedy Express`.</span><span class="sxs-lookup"><span data-stu-id="4a389-109">`ID = 1, Company = Speedy Express`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#14](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#14)]
 [!code-vb[DLinqQueryExamples#14](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#14)]  
  
## <a name="example"></a><span data-ttu-id="4a389-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="4a389-110">Example</span></span>  
 <span data-ttu-id="4a389-111">Aşağıdaki kod, `CustomerID` priap 'ye `Customer` sahip olan tekli bulur.</span><span class="sxs-lookup"><span data-stu-id="4a389-111">The following code finds the single `Customer` that has the `CustomerID` BONAP.</span></span>  
  
 <span data-ttu-id="4a389-112">Bu sorguyu Northwind örnek veritabanında çalıştırırsanız, sonuçlar olur `ID = BONAP, Contact = Laurence Lebihan`.</span><span class="sxs-lookup"><span data-stu-id="4a389-112">If you run this query against the Northwind sample database, the results are `ID = BONAP, Contact = Laurence Lebihan`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#15](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#15)]
 [!code-vb[DLinqQueryExamples#15](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#15)]  
  
## <a name="see-also"></a><span data-ttu-id="4a389-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4a389-113">See also</span></span>

- [<span data-ttu-id="4a389-114">Sorgu Örnekleri</span><span class="sxs-lookup"><span data-stu-id="4a389-114">Query Examples</span></span>](query-examples.md)
- [<span data-ttu-id="4a389-115">Örnek Veritabanları İndirme</span><span class="sxs-lookup"><span data-stu-id="4a389-115">Downloading Sample Databases</span></span>](downloading-sample-databases.md)
