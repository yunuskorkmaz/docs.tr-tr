---
description: 'Hakkında daha fazla bilgi edinin: dizideki Ilk öğeyi döndürün'
title: Dizideki İlk Öğeyi Döndürme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ccdc3777-b2c2-44e3-a627-abef8d79a555
ms.openlocfilehash: 004e9a1f03677f6ba49916404b1c44408df40dfa
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99663020"
---
# <a name="return-the-first-element-in-a-sequence"></a><span data-ttu-id="d39bc-103">Dizideki İlk Öğeyi Döndürme</span><span class="sxs-lookup"><span data-stu-id="d39bc-103">Return the First Element in a Sequence</span></span>

<span data-ttu-id="d39bc-104"><xref:System.Linq.Enumerable.First%2A>Bir dizideki ilk öğeyi döndürmek için işlecini kullanın.</span><span class="sxs-lookup"><span data-stu-id="d39bc-104">Use the <xref:System.Linq.Enumerable.First%2A> operator to return the first element in a sequence.</span></span> <span data-ttu-id="d39bc-105">Kullanan sorgular <xref:System.Linq.Enumerable.First%2A> hemen yürütülür.</span><span class="sxs-lookup"><span data-stu-id="d39bc-105">Queries that use <xref:System.Linq.Enumerable.First%2A> are executed immediately.</span></span>  
  
> [!NOTE]
> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="d39bc-106"><xref:System.Linq.Enumerable.Last%2A>işlecini desteklemez.</span><span class="sxs-lookup"><span data-stu-id="d39bc-106">does not support the <xref:System.Linq.Enumerable.Last%2A> operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d39bc-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="d39bc-107">Example</span></span>  

 <span data-ttu-id="d39bc-108">Aşağıdaki kod, bir tabloda birincni bulur `Shipper` :</span><span class="sxs-lookup"><span data-stu-id="d39bc-108">The following code finds the first `Shipper` in a table:</span></span>  
  
 <span data-ttu-id="d39bc-109">Bu sorguyu Northwind örnek veritabanında çalıştırırsanız, sonuçlar</span><span class="sxs-lookup"><span data-stu-id="d39bc-109">If you run this query against the Northwind sample database, the results are</span></span>  
  
 <span data-ttu-id="d39bc-110">`ID = 1, Company = Speedy Express`.</span><span class="sxs-lookup"><span data-stu-id="d39bc-110">`ID = 1, Company = Speedy Express`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#14](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#14)]
 [!code-vb[DLinqQueryExamples#14](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#14)]  
  
## <a name="example"></a><span data-ttu-id="d39bc-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="d39bc-111">Example</span></span>  

 <span data-ttu-id="d39bc-112">Aşağıdaki kod, `Customer` priap 'ye sahip olan tekli bulur `CustomerID` .</span><span class="sxs-lookup"><span data-stu-id="d39bc-112">The following code finds the single `Customer` that has the `CustomerID` BONAP.</span></span>  
  
 <span data-ttu-id="d39bc-113">Bu sorguyu Northwind örnek veritabanında çalıştırırsanız, sonuçlar olur `ID = BONAP, Contact = Laurence Lebihan` .</span><span class="sxs-lookup"><span data-stu-id="d39bc-113">If you run this query against the Northwind sample database, the results are `ID = BONAP, Contact = Laurence Lebihan`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#15](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#15)]
 [!code-vb[DLinqQueryExamples#15](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#15)]  
  
## <a name="see-also"></a><span data-ttu-id="d39bc-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d39bc-114">See also</span></span>

- [<span data-ttu-id="d39bc-115">Sorgu örnekleri</span><span class="sxs-lookup"><span data-stu-id="d39bc-115">Query Examples</span></span>](query-examples.md)
- [<span data-ttu-id="d39bc-116">Örnek Veritabanları İndirme</span><span class="sxs-lookup"><span data-stu-id="d39bc-116">Downloading Sample Databases</span></span>](downloading-sample-databases.md)
