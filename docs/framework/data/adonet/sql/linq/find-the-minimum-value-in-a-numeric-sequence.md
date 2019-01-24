---
title: Sayısal dizideki en küçük değeri bulma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 78203093-f242-4572-9b31-9495b10926aa
ms.openlocfilehash: f92558798267760eb6cfd1bfc6365451cdcc1c62
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54530005"
---
# <a name="find-the-minimum-value-in-a-numeric-sequence"></a><span data-ttu-id="6af46-102">Sayısal dizideki en küçük değeri bulma</span><span class="sxs-lookup"><span data-stu-id="6af46-102">Find the Minimum Value in a Numeric Sequence</span></span>
<span data-ttu-id="6af46-103">Kullanım <xref:System.Linq.Enumerable.Min%2A> en düşük değer dizisini sayısal değerler döndürülecek işleci.</span><span class="sxs-lookup"><span data-stu-id="6af46-103">Use the <xref:System.Linq.Enumerable.Min%2A> operator to return the minimum value from a sequence of numeric values.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6af46-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="6af46-104">Example</span></span>  
 <span data-ttu-id="6af46-105">Aşağıdaki örnek, en düşük birim fiyatı üründeki bulur.</span><span class="sxs-lookup"><span data-stu-id="6af46-105">The following example finds the lowest unit price of any product.</span></span>  
  
 <span data-ttu-id="6af46-106">Bu sorgu, Northwind örnek veritabanıyla çalıştırırsanız, çıktı şu şekildedir: `2.5000`.</span><span class="sxs-lookup"><span data-stu-id="6af46-106">If you run this query against the Northwind sample database, the output is: `2.5000`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#9](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#9)]
 [!code-vb[DLinqQueryExamples#9](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#9)]  
  
## <a name="example"></a><span data-ttu-id="6af46-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="6af46-107">Example</span></span>  
 <span data-ttu-id="6af46-108">Aşağıdaki örnek herhangi bir sırada için en düşük freight miktarını bulur.</span><span class="sxs-lookup"><span data-stu-id="6af46-108">The following example finds the lowest freight amount for any order.</span></span>  
  
 <span data-ttu-id="6af46-109">Bu sorgu, Northwind örnek veritabanıyla çalıştırırsanız, çıktı şu şekildedir: `0.0200`.</span><span class="sxs-lookup"><span data-stu-id="6af46-109">If you run this query against the Northwind sample database, the output is: `0.0200`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#10](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#10)]
 [!code-vb[DLinqQueryExamples#10](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#10)]  
  
## <a name="example"></a><span data-ttu-id="6af46-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="6af46-110">Example</span></span>  
 <span data-ttu-id="6af46-111">Aşağıdaki örnek Min bulmak için kullanır. `Products` her kategoride en düşük birim fiyatı vardır.</span><span class="sxs-lookup"><span data-stu-id="6af46-111">The following example uses Min to find the `Products` that have the lowest unit price in each category.</span></span> <span data-ttu-id="6af46-112">Kategoriye göre düzenlenmiş çıktı.</span><span class="sxs-lookup"><span data-stu-id="6af46-112">The output is arranged by category.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#11](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#11)]
 [!code-vb[DLinqQueryExamples#11](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#11)]  
  
 <span data-ttu-id="6af46-113">Northwind örnek veritabanıyla önceki sorguyu çalıştırırsanız, sonuçlar şuna benzer:</span><span class="sxs-lookup"><span data-stu-id="6af46-113">If you run the previous query against the Northwind sample database, your results will resemble the following:</span></span>  
  
 `1`  
  
 `Guaraná Fantástica`  
  
 `2`  
  
 `Aniseed Syrup`  
  
 `3`  
  
 `Teatime Chocolate Biscuits`  
  
 `4`  
  
 `Geitost`  
  
 `5`  
  
 `Filo Mix`  
  
 `6`  
  
 `Tourtière`  
  
 `7`  
  
 `Longlife Tofu`  
  
 `8`  
  
 `Konbu`  
  
## <a name="see-also"></a><span data-ttu-id="6af46-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6af46-114">See also</span></span>
- [<span data-ttu-id="6af46-115">Toplu Sorgular</span><span class="sxs-lookup"><span data-stu-id="6af46-115">Aggregate Queries</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/aggregate-queries.md)
- [<span data-ttu-id="6af46-116">Örnek Veritabanları İndirme</span><span class="sxs-lookup"><span data-stu-id="6af46-116">Downloading Sample Databases</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
