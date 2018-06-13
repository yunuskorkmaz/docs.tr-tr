---
title: Bir sayısal sırada en küçük değeri Bul
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 78203093-f242-4572-9b31-9495b10926aa
ms.openlocfilehash: 9b55c0a188f7e5857ddc5021c820be847ce63600
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33358836"
---
# <a name="find-the-minimum-value-in-a-numeric-sequence"></a><span data-ttu-id="d3d0d-102">Bir sayısal sırada en küçük değeri Bul</span><span class="sxs-lookup"><span data-stu-id="d3d0d-102">Find the Minimum Value in a Numeric Sequence</span></span>
<span data-ttu-id="d3d0d-103">Kullanım <xref:System.Linq.Enumerable.Min%2A> sayısal değerleri dizisinden en düşük değer döndürmek için işleci.</span><span class="sxs-lookup"><span data-stu-id="d3d0d-103">Use the <xref:System.Linq.Enumerable.Min%2A> operator to return the minimum value from a sequence of numeric values.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d3d0d-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="d3d0d-104">Example</span></span>  
 <span data-ttu-id="d3d0d-105">Aşağıdaki örnekte, en düşük birim fiyatı tüm ürün bulur.</span><span class="sxs-lookup"><span data-stu-id="d3d0d-105">The following example finds the lowest unit price of any product.</span></span>  
  
 <span data-ttu-id="d3d0d-106">Northwind örnek veritabanı karşı bu sorguyu çalıştırmak, çıktısı şöyledir: `2.5000`.</span><span class="sxs-lookup"><span data-stu-id="d3d0d-106">If you run this query against the Northwind sample database, the output is: `2.5000`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#9](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#9)]
 [!code-vb[DLinqQueryExamples#9](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#9)]  
  
## <a name="example"></a><span data-ttu-id="d3d0d-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="d3d0d-107">Example</span></span>  
 <span data-ttu-id="d3d0d-108">Aşağıdaki örnekte, en düşük herhangi bir sırada nakliye tutarını bulur.</span><span class="sxs-lookup"><span data-stu-id="d3d0d-108">The following example finds the lowest freight amount for any order.</span></span>  
  
 <span data-ttu-id="d3d0d-109">Northwind örnek veritabanı karşı bu sorguyu çalıştırmak, çıktısı şöyledir: `0.0200`.</span><span class="sxs-lookup"><span data-stu-id="d3d0d-109">If you run this query against the Northwind sample database, the output is: `0.0200`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#10](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#10)]
 [!code-vb[DLinqQueryExamples#10](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#10)]  
  
## <a name="example"></a><span data-ttu-id="d3d0d-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="d3d0d-110">Example</span></span>  
 <span data-ttu-id="d3d0d-111">Aşağıdaki örnek Min bulmak için kullanır. `Products` her kategoride en düşük birim fiyatı sahip.</span><span class="sxs-lookup"><span data-stu-id="d3d0d-111">The following example uses Min to find the `Products` that have the lowest unit price in each category.</span></span> <span data-ttu-id="d3d0d-112">Çıktı kategoriye göre düzenlenmiş.</span><span class="sxs-lookup"><span data-stu-id="d3d0d-112">The output is arranged by category.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#11](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#11)]
 [!code-vb[DLinqQueryExamples#11](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#11)]  
  
 <span data-ttu-id="d3d0d-113">Northwind örnek veritabanı karşı önceki sorgu çalıştırırsanız, sonuçları şuna benzer:</span><span class="sxs-lookup"><span data-stu-id="d3d0d-113">If you run the previous query against the Northwind sample database, your results will resemble the following:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d3d0d-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d3d0d-114">See Also</span></span>  
 [<span data-ttu-id="d3d0d-115">Toplu Sorgular</span><span class="sxs-lookup"><span data-stu-id="d3d0d-115">Aggregate Queries</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/aggregate-queries.md)  
 [<span data-ttu-id="d3d0d-116">Örnek Veritabanları İndirme</span><span class="sxs-lookup"><span data-stu-id="d3d0d-116">Downloading Sample Databases</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
