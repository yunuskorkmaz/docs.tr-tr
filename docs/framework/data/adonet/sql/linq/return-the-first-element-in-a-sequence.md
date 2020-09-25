---
title: Dizideki İlk Öğeyi Döndürme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ccdc3777-b2c2-44e3-a627-abef8d79a555
ms.openlocfilehash: 4506ef1a79c8f7e77160df4d55d0f93ee79f5a41
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91200348"
---
# <a name="return-the-first-element-in-a-sequence"></a><span data-ttu-id="314fe-102">Dizideki İlk Öğeyi Döndürme</span><span class="sxs-lookup"><span data-stu-id="314fe-102">Return the First Element in a Sequence</span></span>

<span data-ttu-id="314fe-103"><xref:System.Linq.Enumerable.First%2A>Bir dizideki ilk öğeyi döndürmek için işlecini kullanın.</span><span class="sxs-lookup"><span data-stu-id="314fe-103">Use the <xref:System.Linq.Enumerable.First%2A> operator to return the first element in a sequence.</span></span> <span data-ttu-id="314fe-104">Kullanan sorgular <xref:System.Linq.Enumerable.First%2A> hemen yürütülür.</span><span class="sxs-lookup"><span data-stu-id="314fe-104">Queries that use <xref:System.Linq.Enumerable.First%2A> are executed immediately.</span></span>  
  
> [!NOTE]
> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="314fe-105"><xref:System.Linq.Enumerable.Last%2A>işlecini desteklemez.</span><span class="sxs-lookup"><span data-stu-id="314fe-105">does not support the <xref:System.Linq.Enumerable.Last%2A> operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="314fe-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="314fe-106">Example</span></span>  

 <span data-ttu-id="314fe-107">Aşağıdaki kod, bir tabloda birincni bulur `Shipper` :</span><span class="sxs-lookup"><span data-stu-id="314fe-107">The following code finds the first `Shipper` in a table:</span></span>  
  
 <span data-ttu-id="314fe-108">Bu sorguyu Northwind örnek veritabanında çalıştırırsanız, sonuçlar</span><span class="sxs-lookup"><span data-stu-id="314fe-108">If you run this query against the Northwind sample database, the results are</span></span>  
  
 <span data-ttu-id="314fe-109">`ID = 1, Company = Speedy Express`.</span><span class="sxs-lookup"><span data-stu-id="314fe-109">`ID = 1, Company = Speedy Express`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#14](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#14)]
 [!code-vb[DLinqQueryExamples#14](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#14)]  
  
## <a name="example"></a><span data-ttu-id="314fe-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="314fe-110">Example</span></span>  

 <span data-ttu-id="314fe-111">Aşağıdaki kod, `Customer` priap 'ye sahip olan tekli bulur `CustomerID` .</span><span class="sxs-lookup"><span data-stu-id="314fe-111">The following code finds the single `Customer` that has the `CustomerID` BONAP.</span></span>  
  
 <span data-ttu-id="314fe-112">Bu sorguyu Northwind örnek veritabanında çalıştırırsanız, sonuçlar olur `ID = BONAP, Contact = Laurence Lebihan` .</span><span class="sxs-lookup"><span data-stu-id="314fe-112">If you run this query against the Northwind sample database, the results are `ID = BONAP, Contact = Laurence Lebihan`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#15](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#15)]
 [!code-vb[DLinqQueryExamples#15](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#15)]  
  
## <a name="see-also"></a><span data-ttu-id="314fe-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="314fe-113">See also</span></span>

- [<span data-ttu-id="314fe-114">Sorgu örnekleri</span><span class="sxs-lookup"><span data-stu-id="314fe-114">Query Examples</span></span>](query-examples.md)
- [<span data-ttu-id="314fe-115">Örnek Veritabanları İndirme</span><span class="sxs-lookup"><span data-stu-id="314fe-115">Downloading Sample Databases</span></span>](downloading-sample-databases.md)
