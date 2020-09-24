---
title: Sayısal Dizideki En Küçük Değeri Bulma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 78203093-f242-4572-9b31-9495b10926aa
ms.openlocfilehash: 2ffff8b69839d5c1e70e81f9fc6f3a97f57ac6c6
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91155984"
---
# <a name="find-the-minimum-value-in-a-numeric-sequence"></a><span data-ttu-id="43c18-102">Sayısal Dizideki En Küçük Değeri Bulma</span><span class="sxs-lookup"><span data-stu-id="43c18-102">Find the Minimum Value in a Numeric Sequence</span></span>

<span data-ttu-id="43c18-103"><xref:System.Linq.Enumerable.Min%2A>Bir sayısal değer dizisinden en küçük değeri döndürmek için işlecini kullanın.</span><span class="sxs-lookup"><span data-stu-id="43c18-103">Use the <xref:System.Linq.Enumerable.Min%2A> operator to return the minimum value from a sequence of numeric values.</span></span>  
  
## <a name="example"></a><span data-ttu-id="43c18-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="43c18-104">Example</span></span>  

 <span data-ttu-id="43c18-105">Aşağıdaki örnek, herhangi bir ürünün en düşük birim fiyatını bulur.</span><span class="sxs-lookup"><span data-stu-id="43c18-105">The following example finds the lowest unit price of any product.</span></span>  
  
 <span data-ttu-id="43c18-106">Bu sorguyu Northwind örnek veritabanında çalıştırırsanız, çıkış şu şekilde olur: `2.5000` .</span><span class="sxs-lookup"><span data-stu-id="43c18-106">If you run this query against the Northwind sample database, the output is: `2.5000`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#9](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#9)]
 [!code-vb[DLinqQueryExamples#9](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#9)]  
  
## <a name="example"></a><span data-ttu-id="43c18-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="43c18-107">Example</span></span>  

 <span data-ttu-id="43c18-108">Aşağıdaki örnek herhangi bir sipariş için en düşük navlun miktarını bulur.</span><span class="sxs-lookup"><span data-stu-id="43c18-108">The following example finds the lowest freight amount for any order.</span></span>  
  
 <span data-ttu-id="43c18-109">Bu sorguyu Northwind örnek veritabanında çalıştırırsanız, çıkış şu şekilde olur: `0.0200` .</span><span class="sxs-lookup"><span data-stu-id="43c18-109">If you run this query against the Northwind sample database, the output is: `0.0200`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#10](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#10)]
 [!code-vb[DLinqQueryExamples#10](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#10)]  
  
## <a name="example"></a><span data-ttu-id="43c18-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="43c18-110">Example</span></span>  

 <span data-ttu-id="43c18-111">Aşağıdaki örnek, `Products` her kategoride en düşük birim fiyatına sahip olan öğesini bulmak Için min kullanır.</span><span class="sxs-lookup"><span data-stu-id="43c18-111">The following example uses Min to find the `Products` that have the lowest unit price in each category.</span></span> <span data-ttu-id="43c18-112">Çıktı kategoriye göre düzenlenir.</span><span class="sxs-lookup"><span data-stu-id="43c18-112">The output is arranged by category.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#11](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#11)]
 [!code-vb[DLinqQueryExamples#11](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#11)]  
  
 <span data-ttu-id="43c18-113">Önceki sorguyu Northwind örnek veritabanında çalıştırırsanız, sonuçlarınız aşağıdakine benzeyecektir:</span><span class="sxs-lookup"><span data-stu-id="43c18-113">If you run the previous query against the Northwind sample database, your results will resemble the following:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="43c18-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="43c18-114">See also</span></span>

- [<span data-ttu-id="43c18-115">Toplu Sorgular</span><span class="sxs-lookup"><span data-stu-id="43c18-115">Aggregate Queries</span></span>](aggregate-queries.md)
- [<span data-ttu-id="43c18-116">Örnek Veritabanları İndirme</span><span class="sxs-lookup"><span data-stu-id="43c18-116">Downloading Sample Databases</span></span>](downloading-sample-databases.md)
