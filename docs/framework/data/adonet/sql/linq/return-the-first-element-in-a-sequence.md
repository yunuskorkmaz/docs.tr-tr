---
title: Dizideki İlk Öğeyi Döndürme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ccdc3777-b2c2-44e3-a627-abef8d79a555
ms.openlocfilehash: dca917b3c12b0f9923cc9ea34a2568c412a09831
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62033455"
---
# <a name="return-the-first-element-in-a-sequence"></a><span data-ttu-id="12878-102">Dizideki İlk Öğeyi Döndürme</span><span class="sxs-lookup"><span data-stu-id="12878-102">Return the First Element in a Sequence</span></span>
<span data-ttu-id="12878-103">Kullanım <xref:System.Linq.Enumerable.First%2A> işlecini bir dizideki ilk öğeyi döndürür.</span><span class="sxs-lookup"><span data-stu-id="12878-103">Use the <xref:System.Linq.Enumerable.First%2A> operator to return the first element in a sequence.</span></span> <span data-ttu-id="12878-104">Sorgular kullanan <xref:System.Linq.Enumerable.First%2A> hemen çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="12878-104">Queries that use <xref:System.Linq.Enumerable.First%2A> are executed immediately.</span></span>  
  
> [!NOTE]
>  [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="12878-105">desteklemediği <xref:System.Linq.Enumerable.Last%2A> işleci.</span><span class="sxs-lookup"><span data-stu-id="12878-105">does not support the <xref:System.Linq.Enumerable.Last%2A> operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="12878-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="12878-106">Example</span></span>  
 <span data-ttu-id="12878-107">Aşağıdaki kod ilk bulur `Shipper` tabloda:</span><span class="sxs-lookup"><span data-stu-id="12878-107">The following code finds the first `Shipper` in a table:</span></span>  
  
 <span data-ttu-id="12878-108">Northwind örnek veritabanına karşı bu sorguyu çalıştırmak, sonuçları vardır.</span><span class="sxs-lookup"><span data-stu-id="12878-108">If you run this query against the Northwind sample database, the results are</span></span>  
  
 <span data-ttu-id="12878-109">`ID = 1, Company = Speedy Express`.</span><span class="sxs-lookup"><span data-stu-id="12878-109">`ID = 1, Company = Speedy Express`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#14](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#14)]
 [!code-vb[DLinqQueryExamples#14](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#14)]  
  
## <a name="example"></a><span data-ttu-id="12878-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="12878-110">Example</span></span>  
 <span data-ttu-id="12878-111">Aşağıdaki kod tek bulur `Customer` olan `CustomerID` BONAP.</span><span class="sxs-lookup"><span data-stu-id="12878-111">The following code finds the single `Customer` that has the `CustomerID` BONAP.</span></span>  
  
 <span data-ttu-id="12878-112">Bu sorgu, Northwind örnek veritabanıyla çalıştırırsanız, sonuçları olan `ID = BONAP, Contact = Laurence Lebihan`.</span><span class="sxs-lookup"><span data-stu-id="12878-112">If you run this query against the Northwind sample database, the results are `ID = BONAP, Contact = Laurence Lebihan`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#15](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#15)]
 [!code-vb[DLinqQueryExamples#15](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#15)]  
  
## <a name="see-also"></a><span data-ttu-id="12878-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="12878-113">See also</span></span>

- [<span data-ttu-id="12878-114">Sorgu Örnekleri</span><span class="sxs-lookup"><span data-stu-id="12878-114">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
- [<span data-ttu-id="12878-115">Örnek Veritabanları İndirme</span><span class="sxs-lookup"><span data-stu-id="12878-115">Downloading Sample Databases</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
